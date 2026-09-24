# Selah — marketing & legal site

Static HTML/CSS site for Selah's public pages: landing page plus the documents Apple
requires links to before App Store submission (Privacy Policy, Terms of Use, Support,
Account Deletion instructions). No build step — open any `.html` file directly, or serve
the folder with any static host (GitHub Pages, Vercel, Netlify, S3).

## Structure

- `index.html` — landing page
- `privacy.html` — Privacy Policy (**draft**, needs legal review)
- `terms.html` — Terms of Use (**draft**, needs legal review)
- `support.html` — support contact + FAQ
- `delete-account.html` — account/data deletion instructions (Apple Guideline 5.1.1(v))
- `styles.css` — shared stylesheet (creme/white palette, gold accent, Instrument Serif display type)
- `motion.js` — progressive-enhancement scroll-reveal (no-op without JS or with reduced motion)
- `assets/` — the Selah app icon lockup, exported at the sizes the site references:
  `selah-mark-1024.png` (master, also the App Store Connect 1024×1024 icon upload),
  `512`/`180`/`64`/`32` px PNGs for the hero mark, apple-touch-icon, and favicons/nav/footer
- `BRAND-PROMPT.md` — the design system/brief this site follows, plus a paste-able prompt to regenerate it in the same direction for future pages

## Before this goes live / gets submitted with the App Store listing

Search for `class="tbd"` across the HTML files — each one is an unresolved field:

- Confirm `supportselahapp@gmail.com` is actually monitored before publishing.
- Minimum age, data retention/deletion timeframe, governing-law jurisdiction, and the
  company's legal name.
- Attorney review of `privacy.html` and `terms.html` — both are accurate to what the app
  actually collects (per the engineering handoff) but have **not** been legally reviewed.
- Replace "Last updated" placeholder dates once the copy is final.

## Deploying

Nothing here depends on a framework or package manager. The simplest path is GitHub
Pages: enable Pages for this repo (Settings → Pages → deploy from `main`), or point any
static host at the repo root.
