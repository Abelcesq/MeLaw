---
name: melaw-website
description: >-
  ME Law (MacDonald Ebbing & Lloyd, LLP) Squarespace website project memory and
  workflow. Use at the START of any session working in the Abelcesq/MeLaw repo,
  or whenever the user mentions the ME Law / defendmelaw.com website, the
  homepage, interior pages, the navy banner, the attorney/team list, or
  Squarespace developer mode. Recalls everything already completed, runs the
  foundation (health / skills / agent) checks, and enforces the
  commit → push → PR → Squarespace-sync workflow so work is never lost.
---

# ME Law Website

Project memory and operating guide for the **MacDonald Ebbing & Lloyd, LLP**
website (`defendmelaw.com`), hosted on **Squarespace Developer Mode** and backed
by the GitHub repo **`Abelcesq/MeLaw`**.

## What this project is

- A **Squarespace 7.0 Developer Platform** template (base template: "Wright").
- Squarespace keeps the connected GitHub branch in sync. **Only the `master`
  branch is live** — pushing to a `claude/*` working branch does NOT change the
  live site until it is merged into `master`.
- Template language is Squarespace JSON-T (`{.section}`, `{squarespace-headers}`,
  `{squarespace.main-content}`, `<squarespace:navigation .../>`) plus `.less`
  stylesheets. Page content (attorney photos, bios, nav menu) lives in the
  **Squarespace CMS**, not in this repo — it cannot be edited from code.

### Key files
- `template.conf` — layouts/regions registry (must stay valid JSON).
- `homepage.region` — the custom navy/gold homepage (self-contained design,
  includes a large base64 hero image on the `--hero-img` CSS variable).
- `site.region` — the shared template for **all non-homepage (interior) pages**;
  contains the sticky navy banner, cream framing, dropdown, and navy footer CSS.
- `styles/*.less`, `scripts/site-bundle.js`, `blocks/*.block`, `collections/`.

## Start-of-session procedure (do this first, every session)

1. The **SessionStart hook** (`.claude/hooks/session-start.sh`) prints a
   foundation briefing automatically: git status/history, unpushed-work warning,
   list of Markdown docs, the tail of `PROGRESS.md`, a Squarespace template
   **health check**, a **skills check**, and an **agent check**. Read it.
2. Read `.claude/skills/melaw-website/PROGRESS.md` in full to recall context.
3. Skim any other `*.md` files surfaced by the hook.
4. Confirm the working branch and that the tree is clean / pushed before starting
   new work. If the health check shows a `‼️`, fix or flag it before proceeding.

## Workflow rules (keep work safe and the site stable)

- **Develop on the `claude/*` working branch.** Never commit directly to `master`.
- **One change → one descriptive commit → push → open a PR into `master`.** Let
  the user merge. Squarespace goes live only after the merge.
- **Push frequently.** The remote environment is ephemeral; an unpushed commit is
  the only thing that can be lost. Pushing to the feature branch is always safe.
- After each unit of work, **update `PROGRESS.md`** (append to the log) and commit
  it so the next session can resume exactly where this one left off.
- Preserve the giant base64 image on line `--hero-img` in `homepage.region` — edit
  around it programmatically, never paste it into context.
- Keep `template.conf` valid JSON and keep the `data-content-field="main-content"`
  annotation in `homepage.region`.
- Use full `https://www.defendmelaw.com/...` URLs for cross-page links.

## Data-loss protection

- The **Stop hook** (`.claude/hooks/auto-save.sh`) auto-commits and pushes any
  uncommitted work to the current `claude/*` branch at the end of each turn
  (never on `master`). This is the safety net if the local drive is reclaimed.
- Deliberate, well-described commits are still preferred — the autosave is a
  backstop, not a substitute.

## Things that are CMS-only (cannot be done from code)
- Renaming nav items (e.g. "Attorneys" → "Team") — edit in Squarespace Pages.
- Adding/editing attorney profile pages, photos, and bios (e.g. Joy Aoyama).
- Assigning a page to a template; setting the homepage.

## Open follow-ups
See the "Open items" section at the bottom of `PROGRESS.md`.
