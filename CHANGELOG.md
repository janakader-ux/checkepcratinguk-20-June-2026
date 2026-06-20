# SEO & GEO Fixes Applied — 19 April 2026

This bundle contains the updated `checkepcrating.uk` website with every fix in the SEO guide that could be done at the file level.

## Files changed

| File                  | Change                                                                                                                              |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| `robots.txt`          | Rewritten. Explicitly allows GPTBot, OAI-SearchBot, ChatGPT-User, ClaudeBot, Claude-Web, anthropic-ai, PerplexityBot, Google-Extended, Applebot-Extended, Bingbot, Amazonbot and 8 others. Sitemap URL corrected to `https://checkepcrating.uk/sitemap.xml`. |
| `sitemap.xml`         | Regenerated. 61 URLs across canonical domain, with priorities and changefreq. Includes all 24 new pages + 37 blog posts.              |
| `_redirects`          | Added 301 `checkepcrating.co.uk` → `checkepcrating.uk` (Fix 5). Added force-HTTPS, canonical host, and 24 clean-URL aliases.           |
| `llms.txt` **(new)**  | GEO file that ChatGPT, Claude, Perplexity, Gemini and Bing Copilot use to understand and cite the site.                             |
| `index.html`          | Canonical URL + Open Graph + Twitter Cards + geo meta. Seven JSON-LD schemas: LocalBusiness, WebSite+SearchAction, three Service blocks, FAQPage, BreadcrumbList. Areas section turned into internal-linking hub. Footer wired to new landing pages. |

## New pages (23)

Each new page is ~2,000 words of unique, location-specific content with its own Service + FAQPage + BreadcrumbList schema, canonical tag, OG/Twitter cards and geo meta.

| URL                                        | Covers                              |
|--------------------------------------------|-------------------------------------|
| `/retrofit-assessment-bedford.html`        | PAS 2035 / ECO4 / heat-pump prep    |
| `/pat-testing-milton-keynes.html`          | PAT testing MK1–MK19                |
| `/pat-testing-luton.html`                  | PAT testing LU1–LU6                 |
| `/pat-testing-cambridge.html`              | PAT testing CB1–CB5 + villages      |
| `/pat-testing-hertfordshire.html`          | PAT testing SG/AL/WD/HP/EN          |
| `/pat-testing-st-albans.html`              | PAT testing AL1–AL4                 |
| `/pat-testing-stevenage.html`              | PAT testing SG1–SG2                 |
| `/pat-testing-cambridgeshire.html`         | PAT testing CB/PE/SG                |
| `/pat-testing-buckinghamshire.html`        | PAT testing MK/HP/SL                |
| `/pat-testing-aylesbury.html`              | PAT testing HP17–HP22               |
| `/fire-door-inspection-milton-keynes.html` | Fire door MK1–MK19                  |
| `/fire-door-inspection-luton.html`         | Fire door LU1–LU6                   |
| `/fire-door-inspection-cambridge.html`     | Fire door CB1–CB5                   |
| `/fire-door-inspection-hertfordshire.html` | Fire door SG/AL/WD/HP/EN            |
| `/fire-door-inspection-st-albans.html`     | Fire door AL1–AL4                   |
| `/fire-door-inspection-stevenage.html`     | Fire door SG1–SG2                   |
| `/fire-door-inspection-cambridgeshire.html`| Fire door CB/PE/SG                  |
| `/fire-door-inspection-buckinghamshire.html`| Fire door MK/HP/SL                 |
| `/fire-door-inspection-aylesbury.html`     | Fire door HP17–HP22                 |
| `/commercial-epc-bedford.html`             | Non-domestic SBEM EPC Bedford       |
| `/commercial-epc-milton-keynes.html`       | Non-domestic SBEM EPC MK            |
| `/hmo-compliance-bedford.html`             | EPC + PAT + Fire Door bundle — HMO  |
| `/epc-compliance-bundle.html`              | 3-service bundle, multi-location    |

## Blog posts (37)

All 37 posts now have:
- `<link rel="canonical">` to their final URL
- Open Graph `article` tags (og:type, og:image, og:locale, article:published_time)
- Twitter summary_large_image cards
- Geo meta
- Full `BlogPosting` JSON-LD schema with Naseem Jana as author and EPC Bedford UK as publisher
- `BreadcrumbList` JSON-LD schema

## Validation

All 61 pages parse as valid HTML with valid JSON-LD structured data. Test on a live deployment with:

- <https://search.google.com/test/rich-results> — paste any URL
- <https://validator.schema.org/> — paste a URL or the JSON-LD blob
- <https://www.xml-sitemaps.com/validate-xml-sitemap.html> — paste the sitemap URL
- <https://pagespeed.web.dev/> — for Core Web Vitals

## What was NOT done (requires a human)

These items from the SEO guide need action outside the file system:

1. **Google Business Profile (Fix 1)** — must be created, verified by post, and filled in.
2. **Google Search Console (Fix 2)** — must be logged in and sitemap submitted at <https://checkepcrating.uk/sitemap.xml>.
3. **Real YouTube embeds (Fix 6)** — placeholder cards still link to channel. Replace with `<iframe>` embeds once individual video IDs are known.
4. **Local citation listings (Fix 7)** — Checkatrade, Bark, Yell, Yelp UK, Trustpilot etc. must be registered manually.
5. **Google Reviews (Fix 11)** — review generation campaign needs a human touch.
6. **Backlinks (Fix 12)** — outreach work.
7. **Core Web Vitals / image compression (Fix 10)** — pagespeed.web.dev test + image compression must be done after deploy.
8. **Blog content gaps (Fix 9)** — the 6 new articles in the guide still need to be written.

## Human review before going live

**IMPORTANT.** The 23 new landing pages contain specific claims about UK regulations (MEES thresholds, HMO licensing conditions, Regulation 10 fire door frequencies, ECO4 requirements) and specific local authority names. Every page should be read by Naseem or another qualified person before deployment — regulations change, council boundaries change, and a customer reading a stale fact on your site is a worse outcome than a missing page.

Look carefully at:
- MEES 2028/2030 dates (proposed, not yet enacted)
- Named councils on each location page
- Prices stated in £ (I've used the prices from the homepage — confirm they still match)
- TrustMark licence #4116746 (confirm it's still active)

## Deployment

This is the whole site. Upload the contents of this folder to the `checkepcrating.uk` Netlify project (or whatever host is being used) and re-deploy. The `_redirects` file is Netlify-specific; on other platforms you'll need to recreate those rules at the host level.
