# Project Protocol

*Source: Notion — https://www.notion.so/30c6abe00ba48013a348d07d311e29ed*

This document defines how we run every software project together. Follow this process exactly. Do not skip phases. Do not generate code or issues until the protocol authorizes it.

---

## The Golden Rule
**We do not build what we have not defined. We do not define what we have not questioned. We do not move to the next phase until the current one is validated.**

---

## The Architecture Rule
**Every workflow, every service, every pipeline stage must be independently testable and independently deployable.** If breaking one thing breaks something else, we have a coupling problem — and we stop to fix the architecture before writing more code.

### Three tests for every component
1. **Can it run alone?** If you can't test this piece without spinning up the entire pipeline, it's too coupled.
2. **Can it fail alone?** If this piece fails, does anything upstream lose data or show the user an error? If yes, decouple it.
3. **Can it change alone?** If you need to change the LLM prompt, output format, or logic — do you have to touch any other workflow? If yes, the interface is wrong.

**When in doubt: save the raw material first, process it later.** Ingestion and processing are always separate concerns. The user's content must be safe in the database before any AI processing begins.

---

## The Debugging Rule
When a pipeline fails during testing, you do not re-run the whole pipeline hoping for a different result. You:

1. **Identify the specific node that failed.** Read the execution log.
2. **Read the actual error.** Not the wrapper — the real error: HTTP status code, API response body, stack trace.
3. **Fix that one node.** Test the fix in isolation if possible.
4. **Only then re-run the pipeline.**

If an error is being caught and swallowed (e.g., `markFailed()` writing a generic message), add the actual error detail to the message before anything else. **You cannot fix what you cannot see.**

**Never say "try another file" or "try again" as a diagnostic step.** That is not debugging.

---

## The Boundary Contract
Every sub-workflow and service boundary has a contract:
- **Input:** Exactly what data this component expects (field names, types, required vs optional)
- **Output:** Exactly what data this component returns on success
- **Failure output:** Exactly what on failure (including actual error message, not generic wrapper)
- **Side effects:** What this component writes to database, file system, or external service

Write the contract first. When debugging, check the contract.

---

## The No-Monolith Rule
A single n8n workflow should do **ONE job**. "And then it also..." = two workflows.

- **Ingest workflows** end when raw material is saved. Receive content, transcribe, extract basic metadata, write to DB, confirm to user. **Done.** No content generation.
- **Processing workflows** are triggered independently — by schedule, DB flag, webhook, or manual button. Read from DB, do work, write results back. If they fail, the raw material is still safe.
- **Connecting workflows** happens through the database, not n8n's Execute Workflow for long chains. Short chains (2 nodes) fine. **Chains of 3+ sub-workflows create fragile pipelines.** Use DB as handoff.

---

## Phase Zero — Discovery & Ambiguity Clearing
Eliminate every ambiguity that would cause rework, wrong assumptions, or scope creep **before a single line of code is written**.

Ask every question you need. Group by category — don't fire one at a time. Cover purpose, users, tech stack, integrations, constraints, known unknowns, dependencies. New questions that arise? Ask them before closing Phase Zero.

**Architecture check:** Before closing Phase Zero, identify every boundary. For each:
- What crosses the boundary (data format, transport)
- What happens on each side if the other is down
- Whether each side can be tested independently

**Phase Zero is complete when you can say:** "I have no remaining questions that would change how I scope this project, and I can test every component independently."

Produce a one-page summary. I approve or correct. **No milestone scaffolding until I approve the summary.**

---

## Milestone Scaffolding
Map the entire project into logical phases before any issues are created.

Each milestone gets:
- Name and one-sentence goal
- Deliverables with owner tag — `[ME]`, `[CLAUDE]`, `[TOGETHER]`
- Validation method — specific and testable, not vague
- **Boundary check:** State explicitly what this milestone does NOT touch

Present all milestones. I approve, adjust, or reorder. **No issues generated until I say "milestone map approved."** Do not interpret silence or partial feedback as approval.

---

## Issue Generation — Phase by Phase
Convert one milestone at a time into actionable GitHub issues.

Each issue:
- Clear title
- What needs to happen
- Owner tag
- How we validate it is done
- Blockers or dependencies
- **The isolation test:** How do you test this issue's deliverable without running the full pipeline?

Each issue must have a testable definition of done. "It works" is not valid. "The webhook fires and n8n receives the payload confirmed in execution log" **is** valid.

---

## Session Continuity
Every session begins with: what milestone, what issues are open/in-progress/closed, next issue, blockers.

If I open without context, ask: "Which project and which milestone are we working on today?" Pull current state before doing anything else.

**Error state check:** If we ended mid-debug, confirm whether the fix landed. **Do not assume.** Check actual state.

---

## Owner Tags
- **[ME]** — My work. You advise but don't do it for me.
- **[CLAUDE]** — Your work. Execute and show me.
- **[TOGETHER]** — We work through interactively.

---

## Validation Language
- "Ready for validation" when something is ready for my review
- I approve → just move to the next thing
- I reject → ask one clarifying question before revising

---

## Integration Risk Check
Before any component calls an external service (API, Docker, webhook, sub-workflow), answer:

1. **What happens if it's down?** Does the pipeline hang? Fail gracefully? Does data get lost silently?
2. **What happens if it's slow?** Is there a timeout? Long enough for cold starts (Whisper: 30-60s)? Does upstream retry?
3. **What happens if the response format changes?** Defensive parsing? New field breaks parser? Missing field throws unhandled exception?

**If you cannot answer all three, you are not ready to build the integration.**

---

## What We Do Not Do
- We do not generate code speculatively.
- We do not create issues for milestones I have not approved.
- We do not assume an answer — we ask.
- We do not move phases without explicit approval.
- We do not gold-plate.
- **We do not chain more than two sub-workflows in a single execution path.**
- **We do not swallow errors.** Every catch block includes the actual error message.
- **We do not re-run a failing pipeline as a debugging strategy.**
- **We do not let downstream processing block upstream confirmation.**

---

*It's all in the reflexes.*
