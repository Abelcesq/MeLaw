# ME Law Website — Progress Log

> Living record of work on `Abelcesq/MeLaw` (defendmelaw.com). **Append a dated
> entry whenever work is completed, then commit + push.** This file is how a new
> session resumes where the last one left off.

## Project snapshot
- **Repo:** `Abelcesq/MeLaw`  •  **Live site:** https://defendmelaw.com
- **Host:** Squarespace Developer Mode (base template "Wright").
- **Live branch:** `master` (Squarespace auto-syncs it). Work happens on a
  `claude/*` branch and reaches the site only when merged into `master`.
- **Current working branch:** `claude/laughing-wozniak-ro5tfs`

## Completed work (chronological)

### Homepage build & fixes
- **PR #1** — Created `homepage.region` (custom navy/gold homepage from the
  provided design) + registered a `homepage` layout in `template.conf`. Homepage
  assigned to the new template in Squarespace.
- **PR #2** — Added the required `data-content-field="main-content"` placeholder
  to clear the Squarespace Template Audit warning.
- **PR #3** — Removed `SiteLoader` (AJAX nav) from `site.region` so clicking the
  logo/links from interior pages loads the standalone homepage instead of a blank
  page.
- **PR #4** — Straightened the ~1.5° tilt baked into the hero/CTA Capitol photo
  and re-embedded the corrected image on the `--hero-img` variable.

### Content & link updates
- **PR #5** — Homepage team heading → "Meet Your Trusted Team of Attorneys and
  Staff".
- **PR #6** — Interior-page redesign **mockup** (`mockups/interior-page-mockup.html`).
- **PR #7** — Homepage footer/CTA links to real pages: About Us → `/about-melaw`,
  Attorneys → `/attorneys`, "Request a consultation" → `/contact-us`. **Plus**
  interior pages (`site.region`): sticky navy banner (logo + phone/locations +
  editable Squarespace primary nav), cream background, white content card;
  default Squarespace header hidden; content preserved via
  `{squarespace.main-content}`.
- **PR #8** — Interior polish: navigation folder dropdown styled as a white panel
  with navy-blue names (readable); footer restyled to the navy gradient + Inter
  font with gold-accented location buttons.
- **PR #9** — Added a capped height + styled scrollbar to the nav folder dropdown
  for the long team roster.
- **PR #10** — Homepage hero copy: "built to **defend** employers..." (was
  "protect").

### Tooling
- Added this skill (`.claude/skills/melaw-website/`), the SessionStart foundation
  hook, the Stop autosave hook, and `.claude/settings.json`.

## Decisions / conventions
- Interior nav uses the **editable Squarespace navigation** (user controls menu
  items in Pages — no code needed).
- Interior content framing: **white card on cream**.
- Homepage header/footer labels stay "Attorneys" (not renamed to "Team").
- Cross-page links use full `https://www.defendmelaw.com/...` URLs.

## Open items (todo)
- [ ] **Squarespace (CMS):** rename the "Attorneys" nav folder → **"Team"**.
- [ ] **Squarespace (CMS):** add **Joy Aoyama** profile page (photo + bio) inside
      the Team folder so she appears in the dropdown.
- [ ] Merge any still-open PRs (check the GitHub PR list at session start).

## How to update this log
After completing a change: add a dated bullet under "Completed work", update
"Open items", then `git add .claude/skills/melaw-website/PROGRESS.md` and commit
+ push with the rest of the change.
