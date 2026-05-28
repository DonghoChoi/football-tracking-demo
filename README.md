# Tracking Play Explorer

A single-file, player-tracking play visualization — built as a portfolio piece for a **Football Data Science Assistant** role. It animates all 22 players plus the ball on a to-scale field, lets you scrub frame-by-frame, and computes **receiver separation at the catch** from the tracking streams.

No build step, no dependencies, no install. One `index.html`.

## Run it locally
Double-click `index.html`, or:
```bash
# optional: serve it so fonts/relative paths behave exactly like production
python3 -m http.server 8000   # then open http://localhost:8000
```

## Publish it (the part recruiters actually click)
The goal is a **link**, not a repo to clone. Easiest path — GitHub Pages, ~2 minutes:
1. Create a new public repo, e.g. `football-tracking-demo`.
2. Upload `index.html` (and this README) to the root.
3. **Settings → Pages → Source: `main` / root → Save.**
4. Wait ~1 min. Your live link: `https://<username>.github.io/football-tracking-demo/`

Put that URL at the top of your résumé / application. That single link demonstrates *building and deploying an analytical app* — a stated requirement — without anyone running your code.

> Faster-still alternatives for class: paste into **CodeSandbox** or **StackBlitz** for an instant shareable link with live preview + visible source. Use **Vercel** if you upgrade to a React build.

## Swap in real tracking data
The synthetic streams are structured exactly like real data. To go real, replace the `PLAYERS` / `BALL` waypoints with frames parsed from the **NFL Big Data Bowl** tracking CSVs (Kaggle): each row is roughly `frameId, nflId, x, y, team`. Group by player, sort by `frameId`, and the render loop is unchanged.
- Big Data Bowl tracking data → the canonical public source for this exact skill.
- `nfl_data_py` / `nflfastR` (nflverse) → play-by-play + EPA for tendency/opponent dashboards.

## Why this maps to the job (your portfolio rubric)
| JD requirement | How this piece shows it |
|---|---|
| *Player tracking data (a "significant advantage")* | The whole artifact is built on per-player x/y streams |
| *Build & deploy analytical applications* | Deployed, link-shareable app — not a notebook |
| *Transform datasets into actionable insights* | Live separation-at-catch metric, not just a chart |
| *Present to non-technical stakeholders* | Broadcast-style UI a coach could read in 5 seconds |
| *Technical documentation* | This README + heavily commented source |
| *Knowledge of football* | Coverage, separation, line-to-gain framed in football terms |

## Customize
- Colors live in the `:root` CSS variables — re-theme in one place. You may use a team's **colors**, but do **not** use any team logos or trademarks in something you publish publicly.
- The `index.html` source is commented section-by-section (data model → canvas → field → players → analytics → playback) so it reads as a teaching artifact.
