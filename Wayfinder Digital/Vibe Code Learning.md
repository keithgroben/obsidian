# Vibe Code Learning

*Source: Notion — https://www.notion.so/2ef6abe00ba4803fae38d3a600032a63*

Checklist to move from "Websites" to "Web Apps."

## 1. The "Vibe Coding" Stack (The Tools)

You don't need to learn C++. You just need to know which tools to hook together so your AI can write the code for you.

### The Framework: Next.js (React)
- **What:** Standard way to build modern web apps
- **Why:** Breaks a website into "Components" (Lego blocks). AI is very good at writing Next.js code.
- **Prompt Cursor or Replit:** "Use Next.js and Tailwind CSS."

### The Database: Supabase
- **What:** Open-source database that feels like a spreadsheet but acts like a backend
- **Why:** Where your data lives (clients, invoices, leads). Replaces Notion for heavy lifting. Easy to "save" and "load" data.

### The Bouncer: Clerk (or Supabase Auth)
- **What:** Premade login screens
- **Why:** Never build a login form from scratch. Gives you "Sign in with Google" out of the box. Handles security.

### The UI Library: Shadcn/UI
- **What:** Pre-designed buttons, inputs, cards that look professional immediately
- **Why:** Industry standard for clean, "Apple-like" design. Tell AI: "Use a Shadcn card for the pricing table."

## 2. The Deployment Platform: Vercel

Vercel is the platform that makes your app live on the internet. To Web Apps what Netlify is to Hugo sites, but smarter.

### Why Vercel is the "Space Level" choice
- **Push to Publish Workflow:** Connect to GitHub. Every save → rebuild → live in ~60 seconds.
- **Serverless Functions:** Hide API keys (like OpenAI) without running a backend server 24/7. Write function → Vercel spins up server for the split second it runs, then shuts down.
- **Preview Mode:** Temporary website link for new features to test before merging.

### Cost
- **Hobby:** Free (Personal projects / Wayfinder)
- **Pro:** $20/mo (Commercial apps or real business use like Yoder)

## 3. Commercial Models (R7 Creative)

### Option A: The Internal Tool (High Ticket Service)
- **Pitch:** "I will build you a custom 'Lead Catcher' that automates your follow-up"
- **Commercials:** Setup Fee $3,000-$5,000 + Maintenance Fee $150/mo
- **Why:** Fits "Growth Partner" positioning. Custom system, not SaaS.

### Option B: The Micro-SaaS (Subscription)
- **Pitch:** Build one tool (e.g., "The Quoting Calculator"), sell logins to 50 buried operators
- **Commercials:** $29/month per user
- **Warning:** Requires customer support. Stick to Option A for now.

## Next Steps

1. **Create a Vercel Account** (free). Connect to GitHub.
2. **Pick One Tiny Project.** Don't build the whole CRM. Build a "Vibe Coder" tool first.
   - Idea: Simple page, type "Marketing Problem" → OpenAI key spits out "Direct Response Headline"
3. **Prompt:** "I want to build a Next.js app with Tailwind and Shadcn UI. It should have one input field and a submit button..."
