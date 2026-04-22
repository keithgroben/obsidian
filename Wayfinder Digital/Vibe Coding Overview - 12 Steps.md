# The 12 Steps to Real Vibe Coding

*Source: Notion — https://www.notion.so/3136abe00ba4801b9868d81192d5bb70*
*(Wayfinder blog post — category: the-workshop, 2026-02-26)*

*"You tried the easy tools. You hit the wall. Here's the roadmap that actually gets your web app built."*

## You Tried the Easy Way. Now Let's Do It Right.

You signed up for an all-in-one vibe coding tool. Maybe Lovable. Maybe Replit or Bolt. You typed in what you wanted, got something impressive that somewhat worked. Then you hit a wall. And no amount of prompting could fix the mess you were in.

I've been there. And I've watched hundreds of people on Reddit go through the same cycle.

There's a clear path forward. It's not complicated, but it does require you to slow down and build on solid ground.

---

## The 12 Steps

### Step 1: Know What You're Getting Into
This is a highly technical process. You're building a **web app**. Many links in the chain. Walk in with your eyes open.

### Step 2: Accept That You'll Outgrow the All-in-One Tools
Lovable. Replit. Bolt. Base44. They're great — they can get you far. For most of us, sooner than you think, they'll hold you back. These tools hide the complexity from you. Which feels great until you need to do something they don't support.

### Step 3: Write a Foundational Spec Before You Build Anything
**The step most people skip or don't know about. The reason most people fail.**

A **foundational spec** is a clear, detailed document that describes what your app does. Keep it simple enough to understand.

> *"The main problem isn't your tools. It's that you started building before you finished thinking."*

Dump thoughts into voice recorder. Transcribe. Chat with AI about it. Paste finished doc into Notion or Google Docs and edit. **No more than 3 pages.**

### Step 4: Learn to Use GitHub
GitHub is where your code lives. Period. Free account. Create your first **repository** (folder for your project). Set to **private**. Two-factor authentication required.

### Step 5: Understand Branches
- **Main branch** — where your working app lives
- **New branch** — where you build and test new features
- Only merge back to main after it works

Saves you hours of frustration. Without branches, you're working directly on the thing that's working.

### Step 6: Commit to Your Desktop or Laptop
You need **file management** and a **terminal**. Real computer, not your phone. If you struggle with file management, fix that first.

### Step 7: Get Comfortable With the Terminal
On PC: **CMD** or **PowerShell**. You don't need to go deep. Know how to open it, run a command, copy/paste.

Install **Claude Code**. You'll need:
- **Administrator mode** to install
- **Node.js**
- **Git Bash** (on PC)
- At least the **Pro version** of Claude

### Step 8: Set Up Your Repo and Clone It
1. Create GitHub repo
2. Add your foundational spec to it
3. Install **GitHub Desktop**
4. Clone repo to your PC

### Step 9: Let Claude Code Read Your Spec and Build a Plan
Start Claude Code. Tell it to navigate to your repository and **read your foundational spec**. Then ask it to write a plan to build your web app with you.

> **Drop the [Project Protocol document](https://keithgroben.notion.site/Project-Protocol) into your repo before asking Claude Code to plan.** It structures the entire planning phase to eliminate ambiguity before a single line of code gets written.

### Step 10: Answer the Hard Questions First
With the Project Protocol doc, Claude Code will ask a bunch of questions. This is "Phase 0."
Goal: **eliminate gray areas**. No "we'll figure it out later." Every unclear decision skipped becomes a problem or a rebuild later.

### Step 11: Preview Your App Locally
Ask Claude Code to **set up a local server**. Preview at `localhost` in your browser. Later, use separate ports for main and feature branches.

### Step 12: Happy Building
You've got the foundation. You've got the tools. Now go build something.

---

> *Proverbs 24:27 — "Put your outdoor work in order and get your fields ready; after that, build your house."*

There's a reason Solomon put it in that order. **Fields first, then the house. Preparation before construction.** The outdoor work — the unglamorous stuff nobody sees — comes before the thing you actually want to build.

> *"The plans of the diligent lead to profit as surely as haste leads to poverty." — Proverbs 21:5*

Most people who fail at vibe coding don't fail because the tools are bad. They fail because they rushed past the preparation. They wanted the house without the fieldwork.

**Do the boring stuff. Ask the hard questions. Write the spec. Set up the repo.**
