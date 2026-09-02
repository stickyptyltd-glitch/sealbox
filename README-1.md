# Sealbox

A browser-based, link-paired, end-to-end encrypted anonymous messenger. Single self-contained HTML file — no build step, no server-side code, no dependencies beyond two CDN-loaded libraries (QR display/scan).

## What's in here

- **`index.html`** — the entire app. Open it directly in a browser (or via GitHub Pages, see below) and it runs.

## Hosting this on GitHub Pages (free, works today)

1. Create a new repository on GitHub and upload `index.html` (drag-and-drop works fine from the GitHub web UI, including on mobile).
2. In the repo, go to **Settings → Pages**.
3. Under "Build and deployment," set **Source** to "Deploy from a branch," branch `main`, folder `/ (root)`.
4. Save. GitHub gives you a URL like `https://<your-username>.github.io/<repo-name>/` within a minute or two.
5. Open that URL on your phone — that's a real HTTPS origin, which this app needs (the encryption relies on the Web Crypto API, which browsers only expose on `https://` or `localhost`, not on a raw downloaded file opened via `file://`).

## Redeploying after changes

Delete `index.html` in the repo and re-upload the new version (or use "Edit" if it's a small change) — GitHub Pages rebuilds automatically within a minute of a push to `main`.

## Testing the passcode / self-destruct

Set an app passcode from the home screen, choose 1 or 3 wrong attempts, then deliberately fail that many times. Confirms locally (localStorage) and best-effort deletes any paired conversations from the shared store. This is genuinely irreversible — there's no hidden recovery path, including for you.

## Known limitation of this hosting approach

The `db` capability this app uses for real-time sync between two devices is specific to the Claude artifact environment — it won't be available when self-hosted on GitHub Pages. Self-hosted, the app falls back to local-only demo mode (works within one browser, good for testing the UI and the passcode/wipe flow; two separate phones won't be able to actually pair with each other until you wire it up to a real backend).
