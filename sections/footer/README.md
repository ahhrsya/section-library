# footer sections

Site footers, link columns, legal and social rows.

## Status

**Empty** — no sections in this category yet.

## How to add one

1. Copy the prompt from [`../../prompts/add-section.md`](../../prompts/add-section.md).
2. Paste it to your agent along with your reference (screenshot / sketch / description).
3. The agent creates `sections/footer/<kebab-case-name>.html` and registers it in `index.html`.

## Conventions

- One self-contained HTML file per section (all CSS inlined, no build step).
- Font: DM Sans. Embed as base64 or reference `../../fonts/`.
- Headline: `font-weight: 500`, `letter-spacing: -2px`.
- Must render standalone and hold up at 1024px / 640px.
- Register in the `LIBRARY` array in `index.html`.

Push rules live in the root [README](../../README.md#push-rules).
