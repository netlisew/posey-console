# Posey Console

Web console for **[Posey](https://github.com/netlisew/posey-photo-taker)** — the pose-overlay
camera. Live at **https://posey.nethulisewwandi.com** (GitHub Pages, `CNAME` file in this repo).

Single plain HTML, no build step. Google sign-in uses Google Identity Services' popup token
flow with the **Web** OAuth client of the `posey-photo-taker` Cloud project and the
`drive.file` scope, so the console and the phone app share one **Posey** folder in Drive.

## Status

Starter: sign in → Drive access check → find/create the Posey folder. Album management,
background removal and Claude analysis come in Phase 3 (see the app repo's plan).

## Run locally

```bash
python3 -m http.server 4790   # http://localhost:4790 is an authorized origin
```
