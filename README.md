# Tech Notes

Personal engineering notebook, published as a static site with **GitHub Pages**.

Live site (once Pages is enabled): <https://wfgp84.github.io/technotes/>

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

## Deploy to GitHub Pages

The local repo and the remote (`https://github.com/wfgp84/technotes.git`)
are already wired up. You just need to push and enable Pages.

### 1. Push the current commit

```powershell
cd C:\wfgp\code\tecnote
git push -u origin main
```

If HTTPS asks for a password, use a **Personal Access Token** (PAT):
create at <https://github.com/settings/tokens> → *Fine-grained token* →
scope this repo with `Contents: Read and write`, then paste the token
as the "password".

### 2. Enable Pages

- Open <https://github.com/wfgp84/technotes/settings/pages>.
- **Source:** *Deploy from a branch*.
- **Branch:** `main`, folder: `/ (root)`. Save.

Wait ~30 s. Your site appears at <https://wfgp84.github.io/technotes/>.

## Adding a new note

1. Drop `my-new-note.html` in the repo root.
2. Add a card to `index.html` linking to it.
3. Commit and push:
   ```powershell
   git add .
   git commit -m "add my-new-note"
   git push
   ```
4. GitHub Pages redeploys automatically in <1 minute.

## Custom domain (optional)

Add a `CNAME` file containing your domain (e.g. `notes.example.com`),
then create a `CNAME` DNS record pointing to `<user>.github.io`.
