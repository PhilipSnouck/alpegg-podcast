# Developer Documentation — Alpegg Podcast

Technical context for a developer or LLM working on this codebase.

---

## Repo & deployment

- **GitHub:** https://github.com/PhilipSnouck/podcast-alpegg
- **Live:** not live (per ROADMAP.md)
- **Local:** `C:\Users\p.snouckaert\Own AI projects\podcast-alpegg`
- **Deploy:** not documented. README.md says "deploy via GitHub Pages"; no Pages config
  or workflow exists in the repo, so treat the current page as local-only until deployed.

> **Note:** The future episode platform (ROADMAP.md Fase 6 / "Platform bouwen") is planned
> as a separate Next.js site on Vercel (`alpegg.vercel.app`) with private access and audio
> storage on Google Drive or S3. That platform does **not** exist yet — this repo currently
> only contains the static project page.

---

## What this is

A private family podcast project (in Dutch) about the Alpegg chalet. The actual podcast
production (recording, GarageBand editing, Auphonic mastering) happens *outside* this repo —
the repo is the project's home base: a static roadmap page plus planning docs.

---

## Stack

| Layer | Choice | Reason |
|---|---|---|
| Site | Single static `index.html`, zero JS, zero build step | It's a visual roadmap page, nothing more |
| Styling | Inline `<style>` block, CSS custom properties (cream/brown palette in `:root`) | Self-contained single file |
| Fonts | Playfair Display (headings) + Inter (body), Google Fonts `@import` | Warm, editorial look |
| Language | Dutch (`lang="nl"`) | Family audience |

No dependencies, no `package.json`, no environment variables.

---

## File structure

```
index.html            Static project page: header with progress bar, 8 phase cards
                      (Fase 0–7) grouped under section headings (Opnemen / Bewerken /
                      Lanceren), footer. All content hardcoded.
README.md             Short project intro + episode list (Dutch)
ROADMAP.md            Task list in the household roadmap format (Now / Next Build /
                      Future / Done / Notes). Notes section holds the episode list,
                      episode structure, GarageBand track layout, costs, deploy flow.
.claude/launch.json   Local preview config: npx serve -p 3456 .
```

---

## How index.html works

- Each phase is a `.phase` grid row: a left timeline column (`.phase-dot` + `.connector`)
  and a right `.phase-card` with a `.phase-head` (title + badge) and `.tasks` rows.
- Status is fully manual via CSS classes — there is no logic:
  - dot/card/badge: `done` / `active` / `todo` (plus badge `repeat` for recurring phases 4–5)
  - completed task: `.task-row.checked` with `<span class="check yes">✓</span>`;
    open task uses `check no` and `○`
  - completed connector: `.connector.done`
- The last phase (`Fase 7`) deliberately has no `.connector` after its dot.
- Indented `.subtask` divs (used in Fase 3) list the GarageBand track layout.

### Updating progress — the one real quirk

The header progress bar is hardcoded in two places that must be updated together
whenever a phase completes:

1. `.progress-fill { width: 12.5%; }` — comment says "1 of 8 phases done"
2. The label text `<span>1 van 8 fasen afgerond</span>`

Plus the phase's own dot/card/badge/task classes. Nothing recalculates automatically.

---

## Content duplication

The same content lives in three places and is kept in sync **by hand**:

- Episode list: README.md table, ROADMAP.md Notes, (episodes are not listed in index.html)
- Phases/tasks: index.html cards ↔ ROADMAP.md sections
- GarageBand 10-track layout: index.html Fase 3 subtasks ↔ ROADMAP.md Notes

When editing one, check the others.

---

## Running locally

No server needed — open `index.html` directly in a browser. Or, matching
`.claude/launch.json`:

```
npx serve -p 3456 .
```

then visit http://localhost:3456.
