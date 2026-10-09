# Posey Console

Web console for **[Posey](https://github.com/netlisew/posey-photo-taker)** — the pose-overlay
camera. Live at **https://posey.nethulisewwandi.com** (GitHub Pages, `CNAME` file in this repo).

Single plain HTML, no build step. Google sign-in uses Google Identity Services' popup token
flow with the **Web** OAuth client of the `posey-photo-taker` Cloud project and the
`drive.file` scope, so the console and the phone app share one **Posey** folder in Drive.

## What it does

- **Albums** from the shared `Posey` folder in Drive — the same library the phone syncs
  (format: `posey-photo-taker/docs/drive-format.md`). Create, rename, delete.
- **Add images** (button or drag & drop anywhere): each photo is downscaled, its
  background removed **in the browser** (`@imgly/background-removal`, AGPL‑3.0 — this repo is
  public), framed 1080×1920 like the app's poses, then **checked + analysed by Claude**
  (one person? head to feet in frame? + body keypoints) with the same prompt and schema as
  the app. Rejects show a red chip; open one to *Keep anyway*.
- **Pose detail**: drag Claude's keypoints to correct them and **Save points** (marked
  `manual`), re‑analyse, move to another album, or delete.
- **Settings (⚙)**: Anthropic API key (kept in this browser's localStorage only) and model.
- Writes merge with what the phone wrote in the meantime (albums.json is re‑read before
  every save); the phone picks changes up on its next sync.

Pinned CDN versions: `@anthropic-ai/sdk@0.128.0`, `@imgly/background-removal@1.7.0`.
Bump `VERSION` in `index.html` on every deploy — it's shown in the footer.

## Run locally

```bash
python3 -m http.server 4790   # http://localhost:4790 is an authorized origin
```
