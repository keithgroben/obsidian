# Sturges — Product Spec & Roadmap Notes

*Source: Notion — https://www.notion.so/3356abe00ba480bda68ec592a7968d1c*
*(Voice-transcribed product planning session)*

## Context
Working on Sturges and Sturges components. Laying out the product — what it actually does for my client — and a detailed roadmap according to the new haiku/sonnet/opus/cursor workflow.

## Core Product
**A very appealing, easy-to-use, multi-part form walkthrough that saves as it goes.** Eventually we can use AI to assist with answers as the user progresses.

## Website Brief Principles (UI)
Designing around how users expect to see a website:
- How it tells them exactly what they're getting
- Why they should trust it
- How to get to using the product or service
- Font size, spacing
- Industry legend showing exact order of what's stacked on the homepage

Future expansion: industry legend suggests 5 pages or 3 pages at **$310 per page** — two pricing options.

## The Design Brief Output

What we walk away with from the form: **a design brief for Gemini** that says we're going to build a website for [company name], this industry, this order of things on homepage, this style of navigation bar, this style of footer. Plus color palette, vibe, and 3-5 screenshot inspirations.

### The Workflow

1. **Initial consultation with client** — ask questions, fill blanks, get links to sites they like, colors, brand guidelines
2. **Generate mood board** via Gemini (5 versions) with basic elements (navbar + hero)
3. **Client reviews** on Workbench tool — write notes on each mood board, sends to work queue. No phone call required; can schedule 15-min meeting from Workbench if desired.
4. **Revisions:** Max 3 revisions (client picks 2 mood boards out of 5 → revise → pick 1 → revise). All part of the **$500 implementation fee**.
5. **Generate 2-3 homepage layouts** based on final mood board. Client picks one, can revise once.
6. **Generate rest of site** — inner pages are standard layouts reinforcing homepage.
7. **Capture copy interview** — while revisions in flight. Voice answers. **Max 120 words per page, usually 60-80 on homepage.**
8. **Generate copy** on single file for all selected pages.
9. **Final preview** in HTML/CSS before converting to Hugo.
10. **Convert to Hugo.**

## Blog / Inner Pages

During copywriting interview, ask if they want a blog. If yes:
- Usually just a blog section
- Church: blog + events + sermons (same loop, different thing — costs more)
- **Pitch:** "Managed service. We write blog posts for you, we ensure SEO/AEO growth." Not a CMS they manage themselves — that's WordPress or Wix.
- Blog workflow: client sends idea → we write draft → they put finishing touches via simple markdown preview tool
- Generic markup (H1, H2, list, bold, link) — doesn't need to match their design

## Principles

> **Start with AI. Finish with humans.**

- Human-in-the-loop during mood board (Workbench)
- Human-in-the-loop during homepage selection
- Allow them to mark up webpage and write notes
- 3 mood board generations → 2-3 homepage iterations → copy interview

## Technical Goal
HTML/CSS/JS preview → convert to Hugo. No phone walkthroughs if possible — rely on Workbench for markup and notes.

## The Reading Assignment
Read the "new way" inside the repo — how we are building this roadmap for different AI models (Haiku, Sonnet, Opus). Ideas and iteration done with Sonnet and Cursor (mainly Cursor because Anthropic limits usage heavily on their product despite $100/month).
