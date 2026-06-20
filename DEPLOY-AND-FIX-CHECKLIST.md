# CheckEPCRating.uk — Deploy & Fix Checklist

## What was actually wrong (plain English)

Your website was rebuilt from old-style addresses ending in **`.html`**
(e.g. `epc-bedford.html`) to clean addresses (e.g. **`epc-bedford`**).
The new clean pages work perfectly. **But the old `.html` addresses were
never redirected — so they now return "404 Not Found".**

Google still has those old `.html` addresses in its memory. Every time you
(or Google) ask it to index one, Google fetches it, gets a 404, and replies:

> *"Indexing request rejected — indexing issues were detected with the URL."*

It is **not** a robots.txt block and **not** a noindex tag — the live pages are
fully crawlable. The problem is simply **dead old URLs with no redirect.**

Two extra notes:
- `/epc-check-bedford.html` and `/epc-check-cambridge.html` 404 for the same
  reason. The correct live pages are `/epc-bedford` and `/epc-cambridge`.
- `https://checkepcrating.uk/#areas` is **not a separate page** — `#areas` is
  just a jump-link to a section of the homepage. Never submit a `#` URL to
  Google; submit the real area pages instead.

---

## Files in this bundle

| File | Where it goes | What it does |
|------|---------------|--------------|
| `_redirects` | site root | 301-redirects every dead `.html` URL to its live clean URL (the main fix) |
| `sitemap.xml` | site root | Lists only the live clean URLs for Google |
| `robots.txt` | site root | Lets all crawlers in, points to the sitemap |
| `netlify.toml` | repo root | Security/cache headers + pretty-URL setting |
| `structured-data-homepage.html` | paste into homepage `<head>` | Local-business schema for Map Pack / rich results |

---

## Deploy steps (Netlify)

1. Put `_redirects`, `sitemap.xml` and `robots.txt` in the **same folder that
   Netlify publishes** (your site root — the folder with your `index.html`).
   If you use a build folder like `dist/` or `public/`, put them there.
2. Put `netlify.toml` in the **root of the repo**.
3. Open your homepage HTML, paste the contents of
   `structured-data-homepage.html` just before `</head>`, save.
4. Commit + push (or drag-and-drop the folder into Netlify → Deploys).
5. After deploy, test these in your browser — each should now land on the
   clean page, not a 404:
   - `https://checkepcrating.uk/epc-check-bedford.html`  → `/epc-bedford`
   - `https://checkepcrating.uk/epc-bedford.html`        → `/epc-bedford`
   - `https://checkepcrating.uk/epc-buckinghamshire.html`→ `/epc-buckinghamshire`

---

## Google Search Console steps (do these after deploy)

1. **Sitemaps** → remove any old sitemap, then submit:
   `https://checkepcrating.uk/sitemap.xml`
2. **URL Inspection** → paste a **clean** URL (e.g. `https://checkepcrating.uk/epc-cambridge`)
   → "Request indexing". Do this for your priority pages (Bedford, Cambridge,
   Milton Keynes, Luton first).
3. For the old 404 errors under **Pages → Not indexed → Not found (404)**:
   once redirects are live, click **Validate Fix**. Google will recrawl the
   old `.html` URLs, see the 301, and move the ranking to the clean URL.
4. Stop requesting indexing on any `.html` or `#` URL — they will always fail.

> Re-indexing is not instant. Expect a few days to ~2 weeks for the 404s to
> clear and the clean pages to settle. The redirects make it permanent.

---

## To actually get the phone ringing (ranking + leads)

Fixing indexing gets you *eligible* to rank. For "EPC near me / EPC Cambridge"
searches, the biggest lever is **local**, not the website alone:

1. **Google Business Profile** — claim/verify it for the Bedford base. The map
   results ("Local Pack") sit above normal results for local service searches
   and are driven almost entirely by your Business Profile + reviews. This is
   the single highest-impact action for getting calls.
2. **Reviews** — ask every customer for a Google review; reply to each one.
3. **NAP consistency** — same business name, address, phone everywhere
   (website, Business Profile, directories).
4. **The schema** in `structured-data-homepage.html` reinforces all of the
   above and can win you a star-rating rich result.
5. Keep the **click-to-call** button prominent on mobile (you already have
   `tel:+447345295687` — good).
