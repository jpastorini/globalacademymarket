# globalacademymarket.com

Static site for Netlify. No build step: every page is a folder with an `index.html`.

```
/                      Home + guide catalog
/about/  /support/     Company and help
/terms/ /privacy/ /refunds/ /disclaimer/   Policies (complete the [PLACEHOLDERS])
/guides/example-guide/ Landing template (noindex). Copy it for each new guide.
/assets/               site.css, landing.css, mark.svg, img/ (Unsplash photos, see CREDITS.md)
404.html, robots.txt, sitemap.xml, netlify.toml
```

## How updates go live
1. Claude edits the files in this folder (C:\Claude\Projects\GlobalAcademyMarket\globalacademymarket).
2. Jorge reviews the changes in GitHub Desktop, then Commit to main → Push origin.
3. Netlify is linked to github.com/jpastorini/globalacademymarket (branch main, no build command,
   publish directory `.`) and publishes every push in ~30 s. Roll back from Netlify → Deploys.
- DNS: Netlify DNS (nameservers dns1–4.p02.nsone.net set at Porkbun). Keep the Porkbun MX/SPF records in Netlify DNS for email forwarding.

## Before the first ad
- Replace `[LEGAL NAME]` and `[Business address]` in every footer and complete the policy placeholders.
- Fill a real guide from template 12, set its `CHECKOUT_URL` (Hotmart), paste its Meta pixel, add the catalog row on the home page and the URL to `sitemap.xml`.
- Remove the `<meta name="robots" content="noindex…">` line on real guide pages.
- Run `16-compliance-checklist.md`, test on a phone, deploy.

## New guide
```
copy guides/example-guide → guides/<slug>
```
Then follow the checklist in `21-site-brand.md`.

## Design (v2, iPhone style)
- Mobile first (98% of traffic is phones). System font = SF Pro on iPhone, no web fonts to download.
- Building blocks in site.css: glass nav, `.iphone` device frame with a reader screen, iOS notification, App Store
  "story" rails and "Today" card, widgets, settings-style grouped lists. landing.css adds iMessage pain bubbles,
  an Apple Pay–style offer sheet, bonus rail and the sticky bottom bar.
- Images: WebP, 720×900 (portrait) or 900×600 (landscape), under ~90 KB each, `loading="lazy"` below the fold.
