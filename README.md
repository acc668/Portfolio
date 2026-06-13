# Ink & Aether — Personal Portfolio Website

A personal portfolio site for Alexandra Curry, showcasing writing, character art, game design, and coding work. Built with plain HTML, CSS, and vanilla JavaScript, and deployed via GitHub Pages with a custom domain.

🔗 **Live site:** [alexandracurry.dev](https://alexandracurry.dev)

---

## Pages

| File | Description |
|---|---|
| `index.html` | Home page — intro, about section, and navigation hub |
| `writing.html` | Writing samples, character profiles, and a live RP feed |
| `art.html` | Character art and illustration gallery with lightbox viewer |
| `coding.html` | Coding projects and technical work |
| `gamedesign.html` | TTRPG campaigns and game design portfolio |
| `styles.css` | Shared stylesheet for the entire site |

---

## Features

- **Site-wide search** — every page includes a search bar that indexes content across all pages
- **Tabbed content** — writing and art pages organize content into filterable tabs/categories
- **Lightbox image viewer** — click any art piece to view it enlarged
- **Live RP Feed** — a real-time feed of messages from a Discord roleplay channel, displayed on the Writing page
- **Scroll-reveal animations** — content fades/slides in as you scroll
- **Responsive design** — adapts to mobile and desktop layouts

---

## Live RP Feed Setup

The "Live RP Feed" tab on `writing.html` connects to a small Discord bot + Socket.io server that listens for messages in a specific Discord channel and broadcasts them to the website in real time.

**This requires the bot server to be running and publicly accessible.** The bot code is maintained separately (not included in this repo).

1. Deploy the bot server (e.g., to [Railway](https://railway.app)) so it runs 24/7
2. Update the Socket.io connection URL in `writing.html`:
   ```js
   const socket = io('https://your-bot-url.com'); // must be HTTPS
   ```
3. If the bot server isn't reachable, the feed will simply show "⬤ Offline" — the rest of the site is unaffected

---

## 🖼️ Adding Images

Images are organized under the `images/` directory:

```
images/
├── art/        # Character art and illustrations
└── profile/    # Personal/profile photos
```

To add new art:
1. Drop the image file into `images/art/`
2. In `art.html`, replace a placeholder `.art-card` (or add a new one) with an `<img>` tag pointing to the new file
3. Add an entry to the `searchIndex` array in **every** HTML page so the piece is searchable site-wide

---

## Deployment (GitHub Pages + Custom Domain)

This site is deployed via GitHub Pages with a custom domain (`alexandracurry.dev`) through Namecheap.

**DNS Configuration (Namecheap → Advanced DNS):**

| Type | Host | Value |
|---|---|---|
| A Record | @ | 185.199.108.153 |
| A Record | @ | 185.199.109.153 |
| A Record | @ | 185.199.110.153 |
| A Record | @ | 185.199.111.153 |
| CNAME Record | www | `<username>.github.io` |

A `CNAME` file containing `alexandracurry.dev` must exist in the repo root.

**To deploy changes:**
1. Push changes to the repo's default branch (or the branch configured for Pages)
2. GitHub Pages automatically rebuilds and redeploys the site
3. Changes typically go live within 1–2 minutes (hard-refresh your browser to bypass cache)

---

## Local Development

No build tools required — this is a static site.

1. Clone the repo
2. Open any `.html` file directly in a browser, or run a simple local server:
   ```bash
   python3 -m http.server 8080
   ```
3. Visit `http://localhost:8080`

---

## Notes

- All internal links use relative paths (e.g., `writing.html`, `images/art/alura.png`) so the site works correctly under a custom domain
- The search index is duplicated across each HTML file — when adding new content, remember to update the `searchIndex` array everywhere relevant
