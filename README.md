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

1. Create a public repo (e.g. `NormanFrog/jellydraw-guides`) and copy this folder's contents into it.
2. Add a `CNAME` file containing `guides.jellydraw.app`.
3. Repo Settings → Pages → Deploy from branch `main`, root.
4. Porkbun DNS: `CNAME guides → normanfrog.github.io`. Back in Pages, tick Enforce HTTPS.
5. Link to the guide from the jellydraw.app footer, so search engines find it and it inherits
   some of the homepage's authority.
6. Submit the URL in Google Search Console and Bing Webmaster Tools (Bing feeds ChatGPT search
   and Copilot).

The pages' `canonical` and `og:url` assume `https://guides.jellydraw.app/<folder>/`. Change them
if the guides end up somewhere else.

## Keeping them honest

Competitor facts come from each developer's own page on the date in the article. Re-check them
and bump the "Updated" date and `dateModified` every few months: stale or wrong claims cost
trust with readers, search engines and AI assistants alike, and false comparative claims are a
legal risk. Don't add ratings or reviews to the structured data that aren't real.

The CTA links to `jellydraw.app/buy`, which works once the Carrd `/buy` redirect is added at
launch. Publish guides only after Download and Buy work.
