# resireg.github.io

Project page for **ReSiReg: Towards Spatially Consistent Semantics in Language-Conditioned Robotic Tasks** (CoRL 2026), served by GitHub Pages at <https://resireg.github.io>.

Single static page: `index.html` plus figures in `img/`. No build step; push to `main` deploys. `_config.yml` keeps this README and `future_improvements.md` out of the published site.

## Search engine setup

| Engine | Verification | Status dashboard |
| --- | --- | --- |
| Google | `google03441d120de5419b.html` | [Google Search Console](https://search.google.com/search-console?resource_id=https%3A%2F%2Fresireg.github.io%2F) |
| Bing (also feeds DuckDuckGo, Ecosia, ChatGPT search, Copilot) | `BingSiteAuth.xml` | [Bing Webmaster Tools](https://www.bingwebmastertools.com/) |

Do not delete the verification files.

### Files that matter for findability

- `robots.txt`: allows all crawlers, points to the sitemap.
- `sitemap.xml`: single URL. Bump `<lastmod>` when the page content changes.
- `index.html` `<head>`: canonical URL, Open Graph / Twitter cards, Google Scholar `citation_*` tags, JSON-LD (`ScholarlyArticle` + `WebSite`).
- `favicon.svg`, `favicon-48.png`, `favicon-192.png`, `apple-touch-icon.png`, `favicon.ico`: generated from the robot icon source at <https://github.com/SimonSchwaiger/SimonSchwaiger.github.io/blob/main/img/icons/user-robot.svg>.

### IndexNow (Bing & friends)

`.github/workflows/indexnow.yml` pings <https://api.indexnow.org> after every GitHub Pages build so Bing re-crawls the page within minutes instead of days. The key is the file `0ae775d90c479ae91b183b1b8b0bbbd4.txt` at the repo root; its name is also set in the workflow's `KEY_FILE` env var. Rotate both together if needed.

- Runs automatically on push; can be run by hand from the Actions tab (`workflow_dispatch`).
- A red run on the "Wait until the deployed key file is live" step usually just means the Pages deploy was slow; re-run it.
- Submission status: Bing Webmaster Tools → IndexNow.
- Google does not use IndexNow. After a significant update, use "URL inspection → Request indexing" in Search Console.

## Checking indexing status

- Google: [Search Console](https://search.google.com/search-console?resource_id=https%3A%2F%2Fresireg.github.io%2F) → Pages / URL inspection, or search `site:resireg.github.io`.
- Bing: [Webmaster Tools](https://www.bingwebmastertools.com/) → Site Explorer / URL inspection, or search `site:resireg.github.io` on Bing.
- Rich results / JSON-LD validity: [Rich Results Test](https://search.google.com/test/rich-results?url=https%3A%2F%2Fresireg.github.io%2F).
- Social previews: [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/?q=https%3A%2F%2Fresireg.github.io%2F), [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/).

## When updating the page

1. Edit `index.html`; keep the `<title>`, H1, `og:title`, `citation_title` and JSON-LD `headline` identical to the paper title.
2. Update `<lastmod>` in `sitemap.xml`.
3. Once CoRL proceedings are out: switch the BibTeX from `@article`/arXiv to `@inproceedings`, and update `citation_conference_title`, the JSON-LD `publication` block and the DOI.
4. Push; IndexNow fires automatically. Optionally request indexing in Google Search Console.

Open items are tracked in [`future_improvements.md`](future_improvements.md).
