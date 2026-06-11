# myvideocreator.com — Coming Soon Landing Page

A premium, Apple-style launch page for the Prompt-to-Video engine.

## What's Inside

- `index.html` — Single-file page, zero dependencies, vanilla JS
- `Assets/` — Logo (trimmed), demo video, UI screenshot, favicon

## Getting Started

### Local Preview
```bash
cd landing-page
python -m http.server 8000
# or
npx http-server
```

Visit `http://localhost:8000` to preview.

### Deploy

This folder deploys as-is to any static host:

**Netlify / Vercel / Cloudflare Pages:**
- Point root to this folder
- Or drag-and-drop the folder into the dashboard

**AWS S3:**
```bash
aws s3 sync . s3://your-bucket/
# Then configure CloudFront + Route 53 for myvideocreator.com
```

**GitHub Pages:**
```bash
# In your repo, enable Pages to serve from /landing-page
# Or set up a custom domain via CNAME
```

## Before Going Live

1. **Test the waitlist form** — submit a real email address and confirm it appears in your LaunchList dashboard (`https://app.getlaunchlist.com/`). The page submits silently in the background; if your form key is wrong, signups will fail.

2. **Update the favicon** — currently uses `MyVC logo round Black bg.png`. Point to your final logo if different.

3. **Check the demo video** — `Assets/demo3.mp4` should be your best product demo. If you have a better one, replace it (keep it under 2MB for fast load).

4. **Set the meta image** — The OG image is currently `MyVC logo round Black bg.png`. For social sharing, consider a 1200×630 screenshot of the page or a custom product image.

## Design Specs

- **Colors:** True black background (`#000`), off-white text (`#f5f5f7`), no gradients or accents
- **Fonts:** Inter Tight (display), Instrument Serif (italic accents), system monospace (logs)
- **Motion:** Easing `cubic-bezier(.16,1,.3,1)` throughout; respects `prefers-reduced-motion`
- **Video:** Hero demo runs a typing animation → pipeline states → crossfades to video (3.5s total, can be skipped by scroll/click/tap)
- **Waitlist:** Native form posting to LaunchList endpoint; on success, shows "You're in" message without page reload

## Customization

### Change the Hero Prompt
Edit line ~380 in `index.html`:
```javascript
var PROMPT = 'a fast car race, first-person driver POV';
```

### Change the Manifesto Text
Edit the `WORDS` array around line ~420. Each row is a word or phrase; add `'key'` as the second element to turn it white:
```javascript
var WORDS = [
  ['Your'],['custom'],['words','key'],['here','key'],
  // ...
];
```

### Adjust Colors
Edit the CSS variables in `<style>` near the top:
```css
:root {
  --bg: #000;           /* background */
  --text: #f5f5f7;      /* main text */
  --muted: #86868b;     /* secondary text */
  /* ... */
}
```

### Add Analytics
Drop your Vercel Analytics or Plausible script in the `<head>` — it won't break anything.

## Performance

- **Page weight:** ~4.5 MB (mostly the demo video)
- **Lighthouse:** Aim for 90+ (demo video loading strategy may affect Largest Contentful Paint; consider a smaller/compressed version if needed)
- **First paint:** ~1.2s on 4G (video streams in parallel, doesn't block page render)

## Browser Support

- Chrome/Edge 90+
- Safari 14+
- Firefox 88+
- Mobile Safari 14+

The page uses vanilla JS with no polyfills; it won't work in IE11.

## Questions?

See the code comments in `index.html` for detailed notes on:
- The hero state machine (typing, pipeline, video crossfade)
- Scroll reveal animations
- Parallax on the screenshot
- Form submission handling

---

**© 2026 myvideocreator.com**
