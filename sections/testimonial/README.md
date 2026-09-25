# testimonial sections

Customer quotes, reviews, ratings, case-study snippets, logo walls.

## Contents

| File | Description |
|---|---|
| [`hugo-testimonial.html`](hugo-testimonial.html) | Hover-spotlight row. Five portrait cards sharing one flex row; hovering any card turns it into a landscape rectangle and reveals the full quote. Card 1 is the default spotlight. |

## Interaction pattern (hugo-testimonial.html)

- All cards are `flex: 1 1 0`, filling the container equally.
- The spotlight card (default: first card, or the hovered one) gets `flex-grow: 5`.
- Because total width is fixed, the other cards auto-shrink — the row never shifts or overflows.
- Overlay text (quote + author) is hidden on compact cards and shown only on the spotlight card.
- Uses `:has()` + `:not(:hover)` to avoid a CSS specificity clash:
  ```css
  .card:first-child, .card:hover { flex-grow: 5; }
  .carousel:has(.card:hover) .card:not(:hover) { flex-grow: 1; }
  ```
  Do **not** replace this with `.carousel:has(.card:hover) .card { flex-grow: 1 }` —
  that selector is more specific and will prevent hovered cards from expanding.

## Fonts

DM Sans is embedded as base64 in this file, so it renders even with Google Fonts blocked.

## How to add another

1. Copy the prompt from [`../../prompts/add-section.md`](../../prompts/add-section.md).
2. Paste it to your agent along with your reference.
3. Register the new file in the `LIBRARY` array in `index.html`.

Push rules live in the root [README](../../README.md#push-rules).
