# Boys Volleyball Rankings

A self-contained static ranking site for GitHub Pages. No build tools, server, API keys, or dependencies are required.

## Publish

1. Create an empty GitHub repository.
2. Commit and push only `.gitignore`, `README.md`, `docs/index.html`, `docs/simulation.html`, and `docs/.nojekyll` to its `main` branch.
3. In the repository, open **Settings → Pages**. Set **Source** to **Deploy from a branch**, choose **main** and **/docs**, then save.
4. GitHub Pages will display the site URL when deployment completes.

From this directory, with Git installed:

```sh
git init -b main
git add .gitignore README.md docs/index.html docs/simulation.html docs/.nojekyll
git diff --cached --name-only
git commit -m "Publish volleyball ranking site"
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

Confirm the staged list contains only the five files above before committing. See [GitHub's publishing-source instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Update

On the original local analysis workspace, regenerate the report and run:

```sh
python3 work/prepare_github_site.py
```

Then commit and push `docs/index.html`. The exported page contains the public standings, team match histories, and trajectories. The Simulation tab includes 100 synthetic tournaments and is intentionally public. No roster audit, internal review tabs, info page, or local downloads are included.

The root Git allowlist excludes all analysis inputs, scripts, archives, outputs, and internal reports. Keep that allowlist when updating the site. Never force-add local analysis folders. The hosting repository contains only the exported site; the model and source evidence remain in the local workspace.


The Simulation tab uses `docs/simulation.html`. Its local source is `outputs/simulation_dashboard.html`, exported alongside the main report by the local preparation script. Commit both HTML pages when their data changes.
