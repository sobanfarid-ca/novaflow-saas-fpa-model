# How to publish this on GitHub

Everything in this folder is ready to push. Suggested repo name: **novaflow-saas-fpa-model**.

## Files that will be published

- `NovaFlow_Analytics_FPA_Model_v1.xlsx` — the model
- `README.md` — project overview (shows the dashboard image)
- `assets/kpi-dashboard.png` — dashboard preview used in the README
- `LICENSE` — MIT
- `.gitignore`
- `LinkedIn_post.md` and `PUBLISHING.md` are helper files. If you don't want them in the repo, delete them before committing, or add them to `.gitignore`.

## Option A — GitHub CLI (fastest)

Requires the `gh` CLI installed and signed in (`gh auth login`). In a terminal:

```bash
cd "C:\Users\green\OneDrive\Desktop\FP&A"
git init
git add .
git commit -m "Initial commit: NovaFlow three-year SaaS FP&A model (V1)"
gh repo create novaflow-saas-fpa-model --public --source=. --remote=origin --push
```

That creates the repo and pushes in one step. Done.

## Option B — Create the repo on the website first

1. Go to https://github.com/new
2. Name it `novaflow-saas-fpa-model`, set Public, and do **not** add a README or license (this folder already has them).
3. Click Create repository, then run:

```bash
cd "C:\Users\green\OneDrive\Desktop\FP&A"
git init
git add .
git commit -m "Initial commit: NovaFlow three-year SaaS FP&A model (V1)"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/novaflow-saas-fpa-model.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

## After it's live

1. Open the repo page and confirm the dashboard image renders in the README.
2. Copy the repo URL.
3. Open `LinkedIn_post.md`, replace `[GitHub link]` with that URL, and post.

Tip: pin the repo on your GitHub profile (Profile > Customize your pins) so it shows up first for recruiters.
