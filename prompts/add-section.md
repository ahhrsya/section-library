# Prompt: Add a Section to the Library

Copy everything inside the code block below and paste it to your AI agent together with
your reference (screenshot / sketch / description). The agent will build the section and
file it under the correct category automatically.

---

```text
Add a new section to my Section Library repo.

## Repo layout (already exists)
/
├── index.html                 # gallery — lists every section by category
├── README.md                  # conventions & push rules (read it first)
├── fonts/                     # shared DM Sans woff2 files
├── prompts/add-section.md     # this file
└── sections/
    ├── hero/
    ├── about/
    ├── features/
    ├── testimonial/
    ├── pricing/
    ├── faq/
    ├── cta/
    └── footer/

## Your task
1. Read README.md and follow its conventions.
2. Decide which category the section belongs to, using ONLY these existing categories:
   hero, about, features, testimonial, pricing, faq, cta, footer.
   If the section fits none of them, STOP and ask me before creating a new folder.
3. Build the section as ONE self-contained HTML file:
   - filename: kebab-case, descriptive, e.g. `logo-cloud-marquee.html`
   - path: sections/<category>/<filename>.html
   - inline ALL css in a single <style> block in <head>
   - no build step, no npm, no external JS libs, no CDN scripts
   - fonts: use DM Sans (embed the woff2 as base64 OR reference ../../fonts/)
   - images: remote URLs are fine (e.g. Unsplash), but the file must render offline-ish
   - must render correctly when opened directly as a standalone file
4. Typography defaults (match the existing sections):
   - font-family: 'DM Sans', system-ui, sans-serif
   - headline: font-weight 500, letter-spacing -2px
   - body text: #6b6b6b on #ffffff background
5. Responsive: must hold up at 1024px and 640px breakpoints.
6. Update index.html:
   - add an entry to the LIBRARY array under the matching category
   - include: name, file path (relative), and a one-line desc of the interaction
7. Update sections/<category>/README.md if it exists.

## Before you finish, verify
- [ ] File lives in the correct category folder
- [ ] Filename is kebab-case and unique across the repo
- [ ] Opens and renders standalone (no console errors, no missing assets)
- [ ] Works at desktop / 1024px / 640px
- [ ] index.html LIBRARY array updated
- [ ] No new top-level folders created without asking me

## Do NOT
- create a new category folder without asking
- restructure or rename existing folders
- add package.json, node_modules, or a build pipeline
- commit or push anything (I review first — see README.md push rules)
```

---

## Category cheat-sheet

| Category | What belongs here |
|---|---|
| `hero` | Top-of-page intros: big headline, primary CTA, hero image/video |
| `about` | Company story, mission, team, timeline, stats |
| `features` | Feature grids, benefit lists, product capability blocks |
| `testimonial` | Customer quotes, reviews, ratings, case-study snippets, logo walls |
| `pricing` | Pricing tables, plan cards, feature comparison, billing toggle |
| `faq` | Q&A accordions, help/knowledge blocks |
| `cta` | Conversion blocks, newsletter signup, "get started" bands |
| `footer` | Site footers, link columns, legal/social rows |

If a section genuinely spans two categories, pick the one matching its **primary purpose**
and mention the secondary in the `desc` field in `index.html`.
