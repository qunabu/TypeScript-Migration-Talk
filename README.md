# 30,000 Lines Overnight — Presentation

A single-file HTML presentation about migrating a 342k-line JavaScript library to TypeScript with AI assistance.

## How to run

```bash
npm run start
# or
npm run dev
```

Opens at `http://localhost:3000`. Open `index.html` in your browser.

Requires Node.js. Uses `npx serve` (no install needed — npx downloads it on first run).

## Keyboard shortcuts

| Key | Action |
|-----|--------|
| `Right Arrow` / `Down Arrow` / `Space` | Next slide |
| `Left Arrow` / `Up Arrow` | Previous slide |
| `F` | Toggle fullscreen |
| `Escape` | Exit fullscreen |

Touch/swipe is also supported on mobile.

## Replacing image placeholders

The presentation has 5 image placeholder zones marked with dashed borders and labels like `[IMAGE: ...]`. To replace them with real Silicon Valley screenshots:

1. Save your images to this directory (e.g., `erlich.jpg`, `shocked.jpg`, etc.)
2. Open `index.html` in a text editor
3. Search for `img-placeholder` to find each placeholder
4. Replace the placeholder `<div>` with an `<img>` tag:

```html
<!-- Before -->
<div class="img-placeholder">[IMAGE: Erlich explaining why something is impossible]</div>

<!-- After -->
<img src="erlich.jpg" alt="Erlich at whiteboard" style="width:100%;border-radius:8px;max-height:200px;object-fit:cover;">
```

### Placeholder locations

| Slide | Label | Suggested image |
|-------|-------|-----------------|
| 1 — The Problem | Erlich explaining why something is impossible | Erlich Bachman at whiteboard |
| 5 — The YOLO Prompt | Silicon Valley shocked at screen moment | Gilfoyle or Dinesh shocked at screen |
| 6 — What "It Compiled" Meant | Silicon Valley unexpected success reaction | "Not hotdog" moment or similar |
| 8 — .d.ts Files Lying | Silicon Valley denial/discovery moment | Discovery/denial reaction |
| 13 — Lessons Learned | Richard Hendricks exhausted but done | Richard looking tired but victorious |
