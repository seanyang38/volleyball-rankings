# Boys Volleyball Rankings

Public site: https://seanyang38.github.io/volleyball-rankings/

A self-contained static site with two tabs:

- **Rankings:** team ratings, movement since the previous completed tournament, profiles, match histories and trajectories. A snapshot selector preserves the original kickoff standings alongside the latest completed tournament.
- **Season tracker:** tournament-level accuracy and aggregate comparison counts, using frozen pre-event model forecasts and tournament opening seeds.

The public tracker shows aggregate results only. Detailed match predictions, evaluation snapshots and analysis remain local. The rankings snapshot selector contains only this project’s own historical ranking releases. It does not include third-party rating values, ranking lists, snapshot downloads, roster audits or internal reports. An independence and experimental-analysis notice appears in the site footer. Simulations remain local and are no longer published.

## GitHub Pages

Publish from **main → /docs** in Settings → Pages. Only `.gitignore`, `README.md`, `docs/index.html` and `docs/.nojekyll` belong in Git. No server, dependencies or API keys are needed to view the site.

## Update from the local analysis workspace

After registering a completed event with verified pre-event snapshots:

```sh
python3 work/build_internal_snapshot_report.py
python3 work/build_season_tracker.py
python3 work/build_clean_report.py
python3 work/prepare_github_site.py
node work/check_report.cjs
node work/check_internal_report.cjs
node work/check_internal_snapshots.cjs
```

Then review and publish:

```sh
git add .gitignore README.md docs/index.html
git add -u docs
git diff --cached --stat
git commit -m "Update public rankings and season tracker"
git push
```

The source scripts and private evaluation data exist only in the local analysis workspace; this hosting repository contains the finished page. The exporter validates an explicit public-data schema and removes the retired Simulation endpoint. Internal roster tables, prior-season audits, third-party rankings and tracker match details are excluded. The public page shares the approved ranking layout, compact charts, snapshot navigation and match replay with the internal page. Keep the root Git allowlist and never force-add local analysis folders or archives.


The public baseline is Tournament Seeding: lower opening seed number predicts the winner. It is calculated independently from TM2 opening-pool assignments and actual results, without using another rating system as a substitute. The current opening seeds were reconstructed after the event; the footer discloses this. Historical internal evaluations remain unchanged.


## Current ranking release

The latest release includes all Power 1 age divisions, completed October 24, 2026:
69 teams and 306 season matches. Power 1 uses 50% previous rating / 50%
regularized event performance, with performance weighted 25% sets / 75% points.
The original kickoff release is preserved. Profile checkpoints replay completed
results chronologically against each event's fixed anchor; they are reconstructed
checkpoints, not ratings published live during the tournament. Rank movement
compares with kickoff in this first update and follows the selected age group.
The tracker retains its original frozen pre-event predictions; post-event ranking
updates do not rewrite prediction accuracy.
