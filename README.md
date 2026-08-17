# malikhettige portfolio

Two files. That's it.

- `index.html` — the whole site (design, layout, logic)
- `posts.json` — every writeup / update. Edit this to publish something new.

## Publish to GitHub Pages

1. Create a new GitHub repo. If you want it at `malikhettige.github.io`, name the repo **exactly** `malikhettige.github.io` (replace `malikhettige` with your actual GitHub username). Any other repo name still works, it just lives at `username.github.io/repo-name` instead of the root.
2. Upload `index.html` and `posts.json` to the repo (drag-and-drop on github.com works fine, or `git push`).
3. Go to the repo → **Settings → Pages** → under "Build and deployment", set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. Wait ~1 minute, then visit the URL GitHub gives you.

To later point your own domain (e.g. malikdishanhettige.com) at it: same Settings → Pages page has a "Custom domain" field. GitHub will show you what DNS records to add wherever you buy the domain.

## Adding a new writeup

Open `posts.json` and add a new object to the top of the array:

```json
{
  "id": "idor-example-program",
  "title": "IDOR in [Program] user profile endpoint",
  "date": "2026-08-18",
  "type": "writeup",
  "tags": ["idor", "access-control"],
  "summary": "One-line summary shown in the feed list.",
  "body": "First paragraph.\n\nSecond paragraph. Use \\n\\n between paragraphs."
}
```

Rules:
- `id` must be unique and URL-safe (lowercase, hyphens, no spaces) — it becomes the link.
- `date` format: `YYYY-MM-DD`. Posts sort newest-first automatically.
- `type` is a free label shown as a small tag — use `writeup`, `note`, `log`, `report-analysis`, whatever fits.
- `tags` is optional, shown as `#hashtags`.
- `body` supports plain paragraphs only (split on `\n\n`). No other formatting yet.

Save, push to GitHub, done — no rebuild step, the page reads `posts.json` live.

## Local preview

Because the page fetches `posts.json`, opening `index.html` directly from disk (`file://`) will fail to load posts in some browsers due to CORS. Run a tiny local server instead:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.
