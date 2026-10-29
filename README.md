# Whiteout Rally Timer (PWA)

Static web app. No build step. Files:

- `index.html` – the app
- `manifest.webmanifest` – install info (name, colours, icons)
- `sw.js` – service worker (offline + updates)
- `icons/` – app icons

## Publish on GitHub Pages
1. Create a new public repository on github.com (for example `rally-timer`).
2. Unzip this folder and upload **the contents** (index.html, manifest.webmanifest, sw.js, README.md and the icons folder) with *Add file → Upload files*. Keep `index.html` in the repository root.
3. Go to *Settings → Pages*. Under *Build and deployment* choose *Deploy from a branch*, branch `main`, folder `/ (root)`, then Save.
4. After a minute the site is live at `https://YOUR-NAME.github.io/rally-timer/`.

## Install on a phone or computer
- Android (Chrome): menu → Install app.
- iPhone (Safari): Share → Add to Home Screen.
- Desktop Chrome/Edge: install icon in the address bar.

## Updating
Upload the new `index.html`, then change `rally-timer-v2` to `rally-timer-v2` (and so on) in `sw.js`. Without that, installed copies can keep showing the old version.

## Notes
- Keep the app on screen while timing. It asks the browser to keep the screen awake while a timer runs.
- Leaders, groups and settings are saved in the browser on each device, not shared between devices.
