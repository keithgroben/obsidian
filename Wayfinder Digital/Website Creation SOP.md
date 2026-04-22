# Website Creation — SOP

*Source: Notion — https://www.notion.so/2da6abe00ba48065b708c37a7928db80*

## Website Development Framework

### Phase 1: The Intake (Common to Both)
- **Identify Fit:** Confirm client needs a 5-page service-based site, not a custom dev project.
- **Onboarding:** Complete Brand Pillars (Pre-requisite).
- **Website Interview:** Record/Transcribe interview covering "Look & Feel" and "Page Selection."
- **Copy Generation:** Feed transcript into Claude Project to generate all page copy.

---

## 🏗️ Pathway A: The Current "Bespoke" Process
*Use when the client has a very specific vision or a unique industry.*

1. **Visual Ideation:** Use Gemini to generate and refine a custom component gallery (HTML/CSS/JS) based on client specs.
2. **Assembly:** Feed chosen components and Claude's copy back to Gemini to build the "Master" Homepage file.
3. **Environment Setup:** Push files to GitHub; connect to Netlify (hosting) and Claude Code (editing).
4. **Refinement:** Use Claude Code to separate files (CSS/JS/HTML), create sub-pages, and insert placeholder images (`placehold.co`).
5. **Static Conversion:** Convert the finalized site into Hugo for better element management and long-term hosting.
6. **Client Review:** Share Netlify preview links for final revisions.

---

## 🚀 Pathway B: The "Scalable" Process (The Goal)
*Use this to eliminate "imagination gaps" and speed up delivery.*

1. **Pre-Selection:** Client chooses from 20+ Pre-Defined Component Libraries (categorized by style: Corporate, Minimal, Bold).
2. **Style Pairing:** Client selects a Font Pair and Color Palette from a curated list.
3. **Automated Assembly:**
   - Pull the selected library from your internal repository
   - Use Claude Code to inject the client's specific copy and brand colors into the chosen template
4. **Environment Setup:** Deploy to GitHub/Netlify immediately.
5. **Hugo Integration:** Since libraries are pre-made, they're already in Hugo format, skipping the conversion step.
6. **Polishing:** Minor tweaks via Claude Code based on specific brand assets (logo/images).

---

## 📊 Key Differences

| Feature | Pathway A (Current) | Pathway B (Future) |
|---|---|---|
| Design Phase | Back-and-forth with Gemini | Client picks from menu |
| Predictability | High variability/risk | Guaranteed "WYSIWYG" |
| Speed | 1–2 days of "messing" with AI | Hours to a working draft |
| Tech Stack | HTML → Hugo Conversion | Native Hugo Templates |
