# Guides (SEO / AI-search articles)

Standalone static pages that answer the questions people ask Google and AI assistants
("best app to draw on my Mac screen", "annotations that follow a window"). Carrd can't host
them: its sections are `#hash` URLs, which search engines treat as the homepage, with no
title or description of their own. Each guide here is a plain folder with an `index.html`.

| Guide | Folder |
|---|---|
| Best screen drawing apps for Mac (2026) | `best-screen-annotation-apps-mac/` |

## Preview

`python3 -m http.server 8766 --directory marketing/guides`, then open
`http://localhost:8766/best-screen-annotation-apps-mac/`.

## Publish (GitHub Pages on guides.jellydraw.app)

This folder is the whole site: `index.html` lists the guides, plus `CNAME`, `robots.txt`,
`sitemap.xml` and `.nojekyll`. It's published from its own repo, `NormanFrog/jellydraw-guides`,
cloned at `../jellydraw-guides` next to this repo. Its history is this folder's history
(`git subtree split`), so this folder stays the source of truth: never edit the clone directly.

First time:

1. On github.com, create an empty public repo `NormanFrog/jellydraw-guides` (no README). ✅
2. Add `../jellydraw-guides` in GitHub Desktop and push it. (Command-line git has no GitHub
   login on this Mac, so pushes go through GitHub Desktop.)
3. In jellydraw-guides: Settings → Pages → Deploy from a branch → `main`, `/ (root)`.
   Custom domain should read `guides.jellydraw.app` (from `CNAME`).
4. Porkbun DNS for jellydraw.app: add `CNAME`, host `guides`, answer `normanfrog.github.io`.
5. When GitHub's DNS check passes, tick Enforce HTTPS. Optionally verify the domain under your
   GitHub account's Settings → Pages so nobody else can claim the subdomain.
6. In Carrd, link to `https://guides.jellydraw.app/best-screen-annotation-apps-mac/` from the
   homepage (footer is fine), so search engines find it through jellydraw.app.
7. Google Search Console: add a Domain property for `jellydraw.app` (a TXT record at Porkbun;
   covers the subdomain), then submit `https://guides.jellydraw.app/sitemap.xml`. In Bing
   Webmaster Tools, import from Search Console (Bing feeds ChatGPT search and Copilot).

After editing a guide or adding one (add it to `index.html` and `sitemap.xml`), commit here,
run `scripts/sync_guides.sh`, and push `jellydraw-guides` from GitHub Desktop.

The pages' `canonical` and `og:url` assume `https://guides.jellydraw.app/<folder>/`. Change them
if the guides end up somewhere else.

## Keeping them honest

Competitor facts come from each developer's own page on the date in the article. Re-check them
and bump the "Updated" date and `dateModified` every few months: stale or wrong claims cost
trust with readers, search engines and AI assistants alike, and false comparative claims are a
legal risk. Don't add ratings or reviews to the structured data that aren't real.

Buttons link straight to the always-latest DMG and the live Lemon Squeezy checkout
(`jellydraw.app/buy` is a 404: Carrd redirects need a higher plan).
