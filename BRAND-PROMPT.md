# Selah — brand & website design brief

This is the design system this site was rebuilt against, written so it can be handed to a
designer, another AI session, or your future self to extend the site (new pages, App Store
assets, social graphics) without drifting back into generic template territory. The last
section is a literal, paste-able prompt that regenerates this site's direction from scratch.

## 1. Brand essence

Selah is a word for a pause — a deliberate rest to reflect. The app is an 8-week Christian
discipleship program (Brotherhood/Sisterhood tracks: scripture, prayer, daily tasks,
accountability circles). The site should feel like the product's namesake: unhurried,
warm, quiet confidence — not another SaaS product launch.

**One-line creative direction:** *a quiet editorial page, not a product demo.*

## 2. Voice & tone

Plain, warm, a little literary. Short declarative sentences. No startup jargon
("supercharge," "unlock your potential," "game-changing"). No exclamation points. It's
allowed to sound like it was written by a person who has actually sat with scripture, not
a marketing team.

## 3. Hard design rules — what NOT to do

These are the specific failure modes this site was rebuilt away from. Treat them as
permanent constraints, not one-time fixes:

- **No unicode/emoji glyphs as icons**, ever (`●  ✦  ♥`). Every icon is a hand-authored
  inline SVG, single stroke weight (1.5), rounded caps/joins, `currentColor`.
- **No floating 3D gradient orb/sphere as a hero graphic.** Atmosphere comes from a soft,
  low-opacity radial glow wash behind the type, not from a rendered object.
- **No uniform card grid** (icon-chip + heading + gray body, repeated 4–6×) for feature
  lists. Use an editorial numbered list/row layout instead — it reads as considered, not
  templated.
- **No heavy drop shadows on white cards over a flat background.** Hairline borders
  (`--surface-border`) only. Depth comes from the paper-grain texture and generous
  whitespace, not `box-shadow` soup.
- **No single pill-radius (999px) applied to everything.** Buttons use `--radius-btn`
  (10px), not full pills. Reserve true pills for small status indicators only, and even
  those should be understated (a dot + label, not a filled badge).
- **No badge/orb/two-button hero template.** One primary button + one plain text link
  with an arrow, not two competing buttons of equal visual weight.
- **Vary layout rhythm.** Not every section is centered text + centered content at the
  same width. Alternate alignment, use asymmetric two-column bands.
- **Type needs a voice.** Never ship a page in a single weight of one system sans font.
  Pair a display serif (headlines only) with system sans (body/UI).

## 4. Visual system

**Color** (creme/white paper, warm ink, quiet gold — light-only, no dark mode):

| Token | Value | Use |
|---|---|---|
| `--bg` | `#faf6ee` | Page background |
| `--bg-soft` | `#f3ecdf` | Footer / recessed areas |
| `--surface` | `#ffffff` | Cards, panels |
| `--surface-border` | `#e7ddc9` | Hairline borders/dividers — the only "depth" cue |
| `--ink` | `#29241e` | Primary text |
| `--ink-soft` | `#6b6152` | Body copy |
| `--ink-faint` | `#948a78` | Metadata, numerals |
| `--gold` / `--gold-deep` / `--gold-tint` | `#b6924f` / `#8c6d3a` / `#f1e6cd` | Accent — used sparingly: links, one word of emphasis, icon chips |

A subtle SVG `feTurbulence` grain is blended over the background (`background-blend-mode:
multiply`, ~5% alpha) — this is what keeps flat cream from looking like a flat AI gradient.
Keep it barely perceptible; it should read as paper, not as a texture.

**Typography:**
- Display/headlines only: `Instrument Serif` (Google Fonts, weight 400, italic available)
  — used for `h1`, section `h2`s, and single emphasized words (`<em>`) within a headline.
- Everything else (nav, body, buttons, labels): system sans (`-apple-system` stack). Never
  load a second sans webfont — the serif/system-sans pairing *is* the signature; adding a
  third face dilutes it.

**Radii:** `--radius-lg: 18px` (large panels), `--radius-md: 12px`, `--radius-sm: 8px`,
`--radius-btn: 10px` (buttons specifically — deliberately not a pill).

**Iconography:** custom-drawn, 24×24 viewBox, `stroke="currentColor"`, `stroke-width:
1.5`, round caps/joins, no fill. Housed in a 42px circular chip (`--gold-tint` background,
`--gold-deep` icon color, inverts to solid gold on hover). Never source icons from an
emoji set, a generic icon font, or a component library's default pack — draw the specific
shape the content calls for.

## 5. Layout patterns

- **Hero:** small uppercase status line (dot + label, not a filled pill) → serif headline
  (2 lines, one word italicized in gold) → one line of muted sans subhead → one primary
  button + one plain arrow link. Soft radial glow behind, not an object.
- **Feature/benefit lists:** numbered editorial rows (`01`–`0n` in serif, faint), not a
  card grid. Icon chip + heading + description per row, full-width hairline divider
  between rows, no per-row background or shadow.
- **Manifesto/pillars band:** two-column layout, white surface band (bordered top/bottom,
  not shadowed), numbered list on one side rather than colored bullet dots.
- **CTA:** centered, same soft-glow treatment as the hero for bookending, single button.
- **Legal/doc pages:** same nav/footer, serif `h1`, plain sans body, a two-column table of
  contents in a bordered (not shadowed) box, numbered step lists for instructions
  (account deletion, etc.) instead of prose paragraphs.

## 6. Motion

Restrained scroll-reveal only: sections/rows fade up (`opacity 0→1`, `translateY(16px)→0`,
~700ms ease, small stagger per row). Implemented as progressive enhancement
(`motion.js` + `[data-reveal]`) — content is fully visible with no JS and with
`prefers-reduced-motion: reduce`. Hover states are subtle: a 1px underline sliding in on
nav links, an icon chip inverting color, a button lifting 1px, an arrow link's arrow
nudging 4px. No bounce, no parallax, no auto-playing carousels.

## 7. Page inventory (what must exist)

- `index.html` — landing page (hero, program feature list, "built with care" band, CTA)
- `privacy.html` — Privacy Policy (draft banner + `.tbd` markers until legal review)
- `terms.html` — Terms of Use (same draft convention)
- `support.html` — support contact + FAQ + billing/crisis guidance
- `delete-account.html` — Apple Guideline 5.1.1(v) account/data deletion instructions

Every new page shares `styles.css`, `motion.js`, and the same nav/footer markup verbatim.

---

## 8. The regeneration prompt

Paste this to (re)build the site from nothing in this same direction:

> Build a static HTML/CSS marketing site for **Selah**, a Christian discipleship app (an
> 8-week program with Brotherhood/Sisterhood tracks: scripture, prayer, daily tasks,
> community accountability). Plain HTML/CSS, no framework, no build step.
>
> **Design direction:** a quiet editorial page, not a SaaS product demo. Palette: creme/
> white paper (`#faf6ee` background, `#ffffff` surfaces), warm near-black ink
> (`#29241e`/`#6b6152`), a single muted gold accent (`#b6924f`/`#8c6d3a`) used sparingly.
> Add a barely-perceptible paper-grain texture over the background (SVG feTurbulence,
> ~5% alpha, blended with `multiply`).
>
> **Typography:** pair a display serif (Instrument Serif, weight 400, headlines only) with
> system sans for everything else. Headlines get one word italicized in the gold accent.
>
> **Explicitly avoid:** emoji/unicode-character icons, a floating gradient-sphere hero
> graphic, a uniform icon-card grid for features, heavy drop shadows on white cards, a
> single 999px pill radius applied to every button and badge, and a badge+orb+two-button
> hero template. These are the tells of a generated template — every one of them must be
> replaced with an intentional alternative (hand-drawn SVG line icons; a soft radial glow
> wash instead of an object; an editorial numbered row list instead of a card grid;
> hairline borders instead of shadows; a 10px button radius; one primary button plus a
> plain arrow text-link).
>
> **Pages:** a landing page (hero, an editorial numbered feature list of the program's
> pillars, a two-column "why this matters" band, a closing CTA), a Privacy Policy, Terms
> of Use, a Support/FAQ page, and an Account Deletion instructions page (Apple Guideline
> 5.1.1(v)). Share one stylesheet and the same nav/footer across every page. Mark any
> legal content that needs attorney review or a real business decision (minimum age,
> retention windows, governing law, contact inboxes) with a visible inline placeholder —
> never invent final legal terms.
>
> **Motion:** restrained scroll-reveal (fade + translateY) as progressive enhancement,
> fully visible without JS and under `prefers-reduced-motion: reduce`. Subtle hover states
> only — no bounce, no parallax.
