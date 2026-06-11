# myvideocreator.com — Coming Soon Landing Page

A premium, Apple-style launch page for the Prompt-to-Video engine.

## Structure

```
.
├── index.html          # The page — single file, zero dependencies, vanilla JS
├── Assets/             # Only the 4 files the page uses
│   ├── logo-trimmed.png
│   ├── demo3.mp4
│   ├── Screenshot of UI.png
│   └── MyVC logo round Black bg.png   (favicon / OG image)
└── README.md
```

`index.html` is at the repository root, so **Vercel / Netlify / GitHub Pages serve it with zero configuration.**

## Local Preview

```bash
python -m http.server 8000
# or
npx http-server
```

Visit `http://localhost:8000`.

## Deploy

**Vercel:** Import the repo → no settings needed (root has `index.html`) → Deploy.

**Netlify:** Drag-and-drop the folder, or connect the repo with publish directory = `/`.

**GitHub Pages:** Settings → Pages → Source: `main` branch, `/ (root)`.

## Before Going Live

1. **Test the waitlist** — submit a real email on the page, then confirm it lands in your LaunchList dashboard (`app.getlaunchlist.com`). The form posts silently in the background to `getlaunchlist.com/s/AhM0S8`.
2. **Demo video** — `Assets/demo3.mp4` (1.7 MB) is the hero clip. Swap for a better one if you have it; keep it under ~2 MB.
3. **OG / social image** — currently the round logo. For richer link previews, drop in a 1200×630 image and update the `og:image` meta tag.

## Customization

- **Hero prompt** — edit `var PROMPT = '...'` in the `<script>` near the bottom of `index.html`.
- **Manifesto text** — edit the `WORDS` array; add `'key'` as the second item to make a word white.
- **Colors** — edit the CSS variables under `:root` at the top of the `<style>` block.

---

**© 2026 myvideocreator.com**
