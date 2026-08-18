# Website UI Redesign — Ridge & Row Bicycle Shop

A UI/UX case study: taking a generic, outdated small-business website and
redesigning it into a clean, modern, brand-appropriate site — built for a
neighborhood bicycle repair shop.

```
task:   Redesign a simple website's UI
goal:   Improve clarity, structure, and visual appeal
id:     task1
```

---

## Live folders

| Folder    | What it is                                              |
|-----------|----------------------------------------------------------|
| `/before` | The original site, as-is — the redesign target           |
| `/after`  | The redesigned site — final deliverable                  |

Both are plain HTML/CSS/JS. No build step, no dependencies.

---

## The brief

The original site (`/before`) is functional but generic: default system fonts,
no visual hierarchy, cramped spacing, a placeholder image box that was never
replaced, and copy that describes the business instead of showing it in
action. It could be any business — nothing about it says "bike shop."

The goal was to identify concrete UI/UX problems and design a version that
fixes them using real design principles, not just a fresh coat of paint.

## Problems identified in the "before" site

1. **No visual hierarchy** — every heading, paragraph, and link competes at
   roughly the same size and weight. The eye has nowhere to land.
2. **Generic, placeholder-driven content** — "Welcome to Our Site," an
   unreplaced `[ IMAGE PLACEHOLDER ]` box, and a button labeled "Click Here"
   that doesn't say what it does.
3. **Default browser styling** — Arial, blue underlined links, unstyled
   buttons. Nothing signals what kind of business this is.
4. **Cramped, inconsistent spacing** — tight line-height, no breathing room
   between sections, no consistent grid.
5. **Weak, generic navigation and structure** — three identical boxy cards
   with no distinction between what's most important.
6. **No responsive behavior** — the layout doesn't adapt below desktop width.

## Design decisions in the "after" site

**Palette** — `#16201C` (ink), `#F3EFE4` (paper), `#B5502E` (rust/chain
accent), `#3C5A63` (steel blue), `#D9A621` (mustard highlight). Grounded in
the shop itself: paper for tickets, rust for tools and chains, steel for
frames, mustard for hazard/safety tape.

**Type** — Oswald (condensed, industrial — headings, labels, nav) paired
with Karla (humanist, readable — body copy). The pairing reads like a shop
sign next to a handwritten receipt.

**Signature element** — the **service ticket card**: a bordered card with a
dashed tear-line and a punch-hole, styled like a real repair tag. It's reused
for the services grid and the booking form, so the whole site feels like one
continuous shop-ticket system rather than a stock template.

**Structure with meaning** — the 4-step repair process (`Drop off → Diagnose
→ Repair → Ride`) is numbered because it's a real, ordered workflow, not
decoration. The group-rides section uses a route-log table instead of prose,
because a shop's ride schedule genuinely is tabular data (day, distance,
pace).

**Motion** — a single deliberate pass: sections fade/rise into view on
scroll (`IntersectionObserver`), respecting `prefers-reduced-motion`. No
scattered hover gimmicks.

**Responsive & accessible baseline** — mobile nav toggle, visible focus
states, a skip-to-content link, semantic HTML (`<nav>`, `<main>`, `<dl>`,
table markup for tabular data).

---

## Folder structure

```
website-ui-redesign/
├── README.md
├── .gitignore
├── before/
│   └── index.html            # original site (self-contained, inline CSS)
└── after/
    ├── index.html            # redesigned site markup
    ├── css/
    │   └── style.css         # design tokens + all styling
    └── js/
        └── main.js           # mobile nav, scroll reveal, demo form handling
```

---

## How to run it

No installation or dependencies required — it's static HTML/CSS/JS.

### Option 1 — just open the file
Double-click `after/index.html` (or `before/index.html`) and it opens in
your default browser.

### Option 2 — serve it locally (recommended, matches production behavior)
From the project root:

```bash
cd after
python3 -m http.server 8000
```

Then open **http://localhost:8000** in your browser.

To view the original for comparison:

```bash
cd before
python3 -m http.server 8001
```

Then open **http://localhost:8001**.

(Any static server works — `npx serve`, VS Code's Live Server extension,
etc. — this is just the zero-install option.)

---

## Pushing this project to Git / GitHub

From inside the `website-ui-redesign` folder:

```bash
# 1. Initialize a repo (skip if you already have one)
git init

# 2. Stage and commit everything
git add .
git commit -m "Initial commit: before/after UI redesign case study"

# 3. Create a new empty repo on GitHub first (via github.com or gh CLI),
#    then connect it as the remote — replace the URL with your repo's:
git remote add origin https://github.com/<your-username>/website-ui-redesign.git

# 4. Set the branch name and push
git branch -M main
git push -u origin main
```

If you'd rather create the GitHub repo from the command line (requires the
[GitHub CLI](https://cli.github.com/)):

```bash
gh repo create website-ui-redesign --public --source=. --remote=origin --push
```

### Future updates

```bash
git add .
git commit -m "Describe what changed"
git push
```

---

## Notes

- The booking form on the "after" site is a static front-end demo — it
  prevents default submission and shows a temporary confirmation state. Wire
  it up to a backend or a form service (Formspree, Netlify Forms, etc.) if
  you want it to actually send data.
- All icons/graphics are inline SVG — no external image assets or licensing
  to worry about.
