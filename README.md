# Boys Volleyball Rankings

Public site: https://seanyang38.github.io/volleyball-rankings/

A self-contained static site with two tabs:

- **Rankings:** team ratings, profiles, match histories and trajectories.
- **Season tracker:** tournament-level accuracy and aggregate comparison counts, using frozen pre-event model forecasts and tournament opening seeds.

The public tracker shows aggregate results only. Match predictions, detailed analysis and original snapshots remain local. It does not include third-party rating values, ranking lists, snapshot downloads, roster audits or internal reports. An independence and experimental-analysis notice appears in the site footer. Simulations remain local and are no longer published.

## GitHub Pages

Publish from **main → /docs** in Settings → Pages. Only `.gitignore`, `README.md`, `docs/index.html` and `docs/.nojekyll` belong in Git. No server, dependencies or API keys are needed to view the site.

## Update from the local analysis workspace

After registering a completed event with verified pre-event snapshots:

```sh
python3 work/build_season_tracker.py
python3 work/build_clean_report.py
python3 work/prepare_github_site.py
node work/check_report.cjs
node work/check_internal_report.cjs
```

Then review and publish:

```sh
git add .gitignore README.md docs/index.html
git add -u docs
git diff --cached --stat
git commit -m "Update public rankings and season tracker"
git push
```

The source scripts and private evaluation data exist only in the local analysis workspace; this hosting repository contains the finished page. The exporter validates the public payload and removes the retired Simulation endpoint. Keep the root Git allowlist and never force-add local analysis folders or archives.


The public baseline is Tournament Seeding: lower opening seed number predicts the winner. It is calculated independently from TM2 opening-pool assignments and actual results, without using another rating system as a substitute. The current opening seeds were reconstructed after the event; the footer discloses this. Historical internal evaluations remain unchanged.
