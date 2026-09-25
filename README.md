# Section Library

A collection of standalone, self-contained landing-page sections.
Every section is **one HTML file** that renders on its own — no build step, no dependencies,
no npm. Open it in a browser and it just works.

Deployed on Cloudflare Pages. The root `index.html` is the gallery that links to every section.

---

## Structure

```
/
├── index.html              # gallery — lists every section by category
├── README.md               # this file (conventions + push rules)
├── fonts/                  # shared DM Sans woff2 (latin + latin-ext)
├── prompts/
│   └── add-section.md      # copy-paste prompt for adding a new section
└── sections/
    ├── hero/
    ├── about/
    ├── features/
    ├── testimonial/        # ← Hugo Testimonial lives here
    ├── pricing/
    ├── faq/
    ├── cta/
    └── footer/
```

### Current contents

| Category | Sections |
|---|---|
| hero | _empty_ |
| about | _empty_ |
| features | _empty_ |
| **testimonial** | `hugo-testimonial.html` |
| pricing | _empty_ |
| faq | _empty_ |
| cta | _empty_ |
| footer | _empty_ |

---

## Conventions

These are the rules every section must follow. An agent adding a section reads
`prompts/add-section.md`, which enforces all of this.

1. **One file per section.** Path: `sections/<category>/<kebab-case-name>.html`.
2. **Fully self-contained.** All CSS inlined in a single `<style>` block in `<head>`.
   No external stylesheets, no CDN scripts, no build step.
3. **Fonts.** DM Sans. Either embed the woff2 as base64, or reference `../../fonts/`.
   Never depend on Google Fonts at runtime (it may be blocked).
4. **Images.** Remote URLs are fine (Unsplash etc.), but the section must still render
   if a single image fails.
5. **Typography defaults.** Headline `font-weight: 500`, `letter-spacing: -2px`.
   Body text `#6b6b6b` on `#ffffff`.
6. **Responsive.** Must hold up at `1024px` and `640px`.
7. **Register it.** Every new section must be added to the `LIBRARY` array in `index.html`.
8. **No new top-level folders.** Adding a category requires asking first.

---

## How to add a section

1. Copy the prompt from [`prompts/add-section.md`](prompts/add-section.md).
2. Paste it to your agent **together with** your reference (screenshot, sketch, or written description).
3. The agent will: pick the category → build the file → update `index.html` → verify.
4. **Review the diff yourself before committing.** Do not let an agent push blind.

---

## Push rules

Follow these exactly so history stays readable and deploys stay safe.

### Branching

- `main` is the **only** long-lived branch and is always deployable.
- Work on a short-lived branch: `section/<category>-<name>`
  ```
  git checkout -b section/testimonial-hugo
  ```
- Never force-push `main`. Ever.

### Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(testimonial): add hover-spotlight testimonial row
fix(testimonial): correct specificity clash on hover state
docs(readme): document push rules
chore(fonts): add DM Sans woff2
```

- Type: `feat` | `fix` | `docs` | `style` | `refactor` | `chore`
- Scope: the category folder name.
- One section per commit. Don't bundle unrelated sections.

### Before pushing

```bash
# 1. confirm what changed
git status
git diff

# 2. open the file in a browser and confirm it renders standalone
open sections/<category>/<name>.html

# 3. confirm index.html lists it
```

### Pushing

```bash
git add -A
git commit -m "feat(<category>): <what you added>"
git push -u origin section/<category>-<name>
```

Then open a Pull Request into `main`. Cloudflare Pages builds a **preview deployment**
for every PR — check that preview before merging.

Merging to `main` triggers the production deploy.

### Never commit

- `node_modules/`, `package-lock.json` (this repo has no build step)
- `.DS_Store`, editor folders
- API keys, tokens, `.env` files

---

## Deployment (Cloudflare Pages)

| Setting | Value |
|---|---|
| Framework preset | None (static) |
| Build command | _(leave empty)_ |
| Build output directory | `/` |
| Root directory | `/` |

There is no build step — Cloudflare serves the files as-is.
`index.html` is the entry point; sections are reachable at
`/sections/<category>/<name>.html`.

---

## License / usage

Free to copy any section into your own project. Each file is self-contained, so you can
paste it directly or lift just the markup and CSS you need.
