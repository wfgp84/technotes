# Tech Notes

Personal engineering notebook, published as a static site with **GitHub Pages**.

Live site: `https://<your-github-username>.github.io/tecnote/`

## Contents

| Note | File |
|---|---|
| Landing page | [`index.html`](./index.html) |
| C++ `std::vector` — sort, merge, `push_back` vs `emplace_back`, benchmarks | [`cpp-vector-notes.html`](./cpp-vector-notes.html) |

## How this site is deployed

Pure static HTML/CSS — no build step. GitHub Pages serves the files
in the `main` branch's root directly.

- `index.html` is the landing page (auto-served at `/`).
- `.nojekyll` disables Jekyll processing so filenames starting with `_` still work.

## First-time deploy checklist

1. **Create a GitHub repo** called `tecnote` (public).
   - Go to <https://github.com/new>.
   - Owner: your account · Name: `tecnote` · Public · **do not** initialize with README/gitignore.
2. **Push this folder** (see commands below).
3. **Enable Pages**:
   - Repo → *Settings* → *Pages*.
   - Source: **Deploy from a branch**.
   - Branch: `main`, folder: `/ (root)`. Save.
4. Wait ~30 s. The site appears at `https://<user>.github.io/tecnote/`.

## Push commands (from this directory)

```powershell
# One-time git identity setup (skip if already configured globally)
git config --global user.name  "Your Name"
git config --global user.email "you@example.com"

# The local repo is already initialised. Just add the remote and push:
git remote add origin https://github.com/<your-github-username>/tecnote.git
git branch -M main
git push -u origin main
```

If HTTPS asks for a password, use a **Personal Access Token** (PAT):
Create at <https://github.com/settings/tokens> → *Fine-grained token* →
scope this repo with `Contents: Read and write`.

## Adding a new note

1. Drop `my-new-note.html` in the repo root.
2. Add a card to `index.html` linking to it.
3. `git add . && git commit -m "add my-new-note" && git push`.
4. GitHub Pages redeploys automatically in <1 minute.

## Custom domain (optional)

Add a `CNAME` file containing your domain (e.g. `notes.example.com`),
then create a `CNAME` DNS record pointing to `<user>.github.io`.
