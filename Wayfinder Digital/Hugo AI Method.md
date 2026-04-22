# Hugo AI Method

*Source: Notion — https://www.notion.so/2ef6abe00ba480c2b801fe16cfcf1c41*

The reason AI "royally screws up" Hugo conversions is that you are asking it to do two very different cognitive tasks at once: **Creative Design** (making it look good) and **Structural Architecture** (file paths, Go templating, folder hierarchies).

When you ask for both simultaneously, AI hallucinates file paths, forgets to close tags, or puts CSS in the wrong folder.

Here is the **"Vibe Code to Hugo" Protocol** — separate Design from Architecture.

---

## Phase 1: The "Flat" Build (Design First)
**Do not mention Hugo yet.** Goal: get one single `index.html` file that looks perfect in your browser.

**Prompt:** "Create a modern, newsstand-style homepage for a newsletter called 'The Wayfinder'. Use Tailwind CSS via CDN. 4 tabs at top, a grid of 'magazine covers' below, 'Field Kit' list at bottom. Give me one single HTML file with all CSS and JS inside it."

Iterate. "Make the header darker." "Make the cards bigger." Once perfect, **stop**. You have your Master Template.

## Phase 2: The "Surgical" Split (Human Job)
Cut the Master Template into 5 pieces:
- **head** — Everything between `<head>` and `</head>`
- **header** — Logo and Navigation Tabs
- **footer** — Copyright and bottom links
- **body** — Stuff in the middle (Grid of Issues)
- **script** — Any JS at the bottom

## Phase 3: The Hugo Transplant

**Step 1: The Setup** — Create blank Hugo site. Go to `themes/my-theme/layouts/_default/`.

**Step 2: The Base (The Shell)** — Open `baseof.html`:

```html
<!DOCTYPE html>
<html>
{{ partial "head.html" . }}
<body>
{{ partial "header.html" . }}
  <main>
{{ block "main" . }}{{ end }}
  </main>
  {{ partial "footer.html" . }}
</body>
</html>
```

**Step 3: The Partials (Static Stuff)**
- Prompt: "Here is the HTML for my navbar. Convert this into a Hugo partial called `header.html`. Do not change the design."
- Save to `layouts/partials/header.html`
- Repeat for `head.html` and `footer.html`

**Step 4: The Homepage (The Logic)**
- Copy "Grid of Covers" from Master HTML
- Prompt: "Here is the HTML for a single 'Magazine Cover' card. Write a Hugo range loop that generates this card for each post in 'issues'. Use `.Title` for headline and `.Params.cover_image` for image."
- Save to `layouts/index.html` inside `{{ define "main" }}` block

## Phase 4: CSS & Assets ("Dummy Check")

- **Rule:** If you used Tailwind via CDN in Phase 1, keep using it via CDN in `head.html`. Don't try Hugo Pipes/PostCSS yet.
- **Images:** Put logo and default images in `static/` folder.
- **AI Hallucination:** AI will tell you to put them in `assets`. Ignore it. `static/logo.png` becomes `yoursite.com/logo.png`.

## The "R7 Protocol" for AI Prompts

> **Role:** You are a Hugo Syntax Expert.
> **Context:** I have a working HTML design. Manually porting it to Hugo.
> **Task:** Take the HTML snippet below and wrap it in a Hugo range loop for the "issues" content type.
> **Constraint:** Do NOT rewrite the CSS. Do NOT give me the whole file. Just give me the loop logic.
> **Input:** [paste only the card HTML]

## Summary
- **Vibe Code** → One perfect HTML file
- **Slice** → Cut out Head, Header, Footer manually
- **Loop** → Ask AI to turn only the middle content grid into a Hugo Loop
- **Assemble** → Paste parts into the layouts folder

This keeps AI focused on logic (which it's okay at) and stops it from messing up your design (which you already finished).
