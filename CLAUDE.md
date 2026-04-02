# Cheatsheets Site — Claude Code Context

## What This Repo Is
A personal quick-reference site hosted on GitHub Pages at:
`https://jdubreville.github.io/cheatsheets`

Static HTML files — no build system, no framework. Drop an HTML file in `docs/`, push, done.

---

## File Structure
```
cheatsheets/
├── docs/
│   ├── index.html                  # Home page — card grid linking to all cheat sheets
│   ├── how-to-win-friends.html     # How to Win Friends & Influence People — Dale Carnegie
│   ├── five-dysfunctions.html      # The Five Dysfunctions of a Team — Patrick Lencioni
│   ├── accelerate.html             # Accelerate: The Science of Lean Software & DevOps — Forsgren, Humble & Kim
│   └── radical_candor.html         # Radical Candor — Kim Scott
├── package.json                    # npm start → local dev server
├── README.md
└── CLAUDE.md
```

---

## Design System
All cheat sheets share a consistent visual language. Follow these rules exactly when adding new ones.

### Colors
Each cheat sheet has its own accent color. Current assignments:
- **Carnegie** (How to Win Friends): `#f0c040` (gold), dark bg `#1a1a2e`
- **Lencioni** (Five Dysfunctions): `#5bc8f5` (blue), dark bg `#0f1923`
- **Accelerate**: `#4cdd80` (green), dark bg `#0f1a0f`
- **Radical Candor**: `#c084fc` (purple), dark bg `#1a0f2e`

When adding a new cheat sheet, pick a new accent color not already in use and a matching dark background tint.

### Layout Patterns
- Dark background (`#0f___` range), `Georgia` serif font
- Cards use `border-top: 4px solid [accent]` and `background: [slightly lighter dark]`
- Section headers: `0.75rem`, `uppercase`, `letter-spacing: 2px`, accent color
- Principle rows: numbered badge (circle) + `strong` title + `span` italic description
- Always include a `🖨️ Save as PDF` button with `onclick="window.print()"`
- Always include a quote bar at the bottom with a book quote

### Print Styles
Every file must include `@media print` overrides:
- White background, dark text
- Hide `.dl-btn`
- Override card/accent colors to print-safe darker hex values
- Add `-webkit-print-color-adjust: exact; print-color-adjust: exact;`

---

## Index Page (`docs/index.html`)
The index is a centered card grid. Each book gets a card with:
- A `.card.[color]` class for the border
- A `.[color] .tag` style for the label
- An emoji, author tag, title, and short description
- An `href` pointing to the cheat sheet file

**When adding a new cheat sheet**, update `index.html` to add:
1. A new CSS color class for the card border and tag
2. A new `<a class="card [color]">` block in the `.cards` grid

---

## How to Add a New Cheat Sheet
1. Create `docs/[book-slug].html` following the design system above
2. Add the card to `docs/index.html`
3. Commit and push — GitHub Pages auto-deploys from the `main` branch, `/public` folder

```bash
git add .
git commit -m "add [book name] cheat sheet"
git push
```

If the site doesn't update, do a dummy commit to force redeploy:
```bash
git commit --allow-empty -m "trigger pages redeploy"
git push
```

---

## Local Dev

```bash
npm start
```

Opens at `http://localhost:3000`. No install needed — uses `npx serve`.

---

## Books Already Covered
| File | Book | Author |
|------|------|--------|
| `how-to-win-friends.html` | How to Win Friends & Influence People | Dale Carnegie |
| `five-dysfunctions.html` | The Five Dysfunctions of a Team | Patrick Lencioni |
| `accelerate.html` | Accelerate: The Science of Lean Software & DevOps | Forsgren, Humble & Kim |
| `radical_candor.html` | Radical Candor | Kim Scott |

## Books on the Shortlist (not yet built)
- *The Phoenix Project* — Gene Kim
- *Team Topologies* — Skelton & Pais
- *The Ideal Team Player* — Patrick Lencioni
- *Turn the Ship Around* — David Marquet
- *High Output Management* — Andy Grove
- *Never Split the Difference* — Chris Voss
- *Thinking, Fast and Slow* — Kahneman
- *Continuous Delivery* — Jez Humble
- *The Pragmatic Programmer* — Hunt & Thomas
