# From folder to GitHub repo with VS Code

## 0. One-time prerequisites
1. Install **Git** (https://git-scm.com) and **VS Code** with the *Python* and *Jupyter* extensions.
2. Create a free account at https://github.com.
3. Tell Git who you are (once per machine):
   ```bash
   git config --global user.name  "Your Name"
   git config --global user.email "you@example.com"
   ```

## 1. Unzip and open
1. Unzip `defi-forensic-yield-aggregator.zip` somewhere **outside** your old `DeFi yield aggregator` working folder.
2. VS Code → **File → Open Folder…** → pick `defi-forensic-yield-aggregator`.
3. Your five `.ipynb` files are in `notebooks/`, unchanged. Move your existing `artifacts/` and `data/` folders into `notebooks/` only if you want to reuse the cache locally; `.gitignore` keeps them out of Git.

## 2. Initialise Git (VS Code UI)
1. Left bar → **Source Control** (branch icon) → **Initialize Repository**.
2. You will see all files listed under *Changes*. Confirm `artifacts/` and `data/` are **not** listed.
3. Type a message such as `Initial commit: five notebook versions, README` and click **Commit** (choose *Yes* to stage all).

Terminal alternative (Ctrl+`):
```bash
git init -b main
git add .
git commit -m "Initial commit: five notebook versions, README"
```

## 3. Publish to GitHub
**Option A, VS Code:** Source Control → **Publish Branch** → sign in to GitHub → choose **Public** or **Private** → done.

**Option B, website + terminal:**
1. github.com → **New repository** → name `defi-forensic-yield-aggregator` → leave "Add README/.gitignore/license" **unchecked** → Create.
2. Run the commands GitHub shows:
   ```bash
   git remote add origin https://github.com/<your-username>/defi-forensic-yield-aggregator.git
   git push -u origin main
   ```

## 4. Check the result
- The README renders on the repo front page (the lineage diagram is Mermaid and renders on GitHub).
- Notebooks open in GitHub's viewer, including saved outputs.
- Large notebooks (300–400 KB each) are fine; GitHub's hard limit is 100 MB per file.

## 5. Optional polish
- **Repo description / topics:** repo page → ⚙ next to *About* → add `defi`, `machine-learning`, `anomaly-detection`, `jupyter-notebook`, `time-series`.
- **Release tags per version** so each iteration is easy to cite:
  ```bash
  git tag -a v1.0-notebooks -m "All five notebook versions"
  git push origin --tags
  ```
- **Strip outputs** (only if you ever want lighter diffs) using `nbstripout` — *not* applied here because you asked for no changes to the notebooks.
- Change the author name in `LICENSE` if "Eric Jonathan" is not what you want shown.

## 6. Everyday workflow
```bash
git add -A
git commit -m "Describe what changed"
git push
```
New experiment? Save it as a new notebook (e.g. `defi_..._v5.ipynb`) in `notebooks/` and add a section for it in the README table.
