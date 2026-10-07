# Future improvements

Findability items from the Oct 2026 SEO review that still need manual image work.

## 1. Image weight / Core Web Vitals (highest impact)

The three figures total ~5.4 MB of RGBA PNG, far above what is displayed:

| File | Size | Pixels | Displayed at |
| --- | --- | --- | --- |
| `img/resireg_appendix_qualitative.drawio.png` | 3.9 MB | 4293 × 2856 | 1024 px wide |
| `img/resireg_teaser_img.drawio.png` (hero / LCP) | 778 KB | 1707 × 450 | 1024 px wide |
| `img/resireg_method_overview.drawio.png` | 749 KB | 2248 × 1360 | 1024 px wide |

Largest Contentful Paint is a ranking signal, and the hero image is the LCP element.

To do:

- Re-export each figure from draw.io at 1x (1024 px) and 2x (2048 px) width, flatten the alpha channel if transparency is not needed.
- Encode as WebP (or AVIF with WebP fallback) and keep a PNG fallback.
- Serve via `<picture>` / `srcset` with `sizes="(max-width: 1120px) 100vw, 1024px"`.
- Target: hero < 150 KB, each other figure < 300 KB.

## 5. Dedicated social preview card

`og:image` and `twitter:image` currently reuse the 1707 × 450 teaser (≈3.8:1). Twitter `summary_large_image`, Facebook, LinkedIn and Slack expect ≈1.91:1 and crop the centre heavily.

To do:

- Design a 1200 × 630 card (title, one-line claim, a cropped teaser panel, CoRL 2026 badge). Keep it under 300 KB (JPEG/PNG; WebP is not reliably supported by all scrapers).
- Save as `img/resireg_social_card.png` and point `og:image`, `twitter:image` and the JSON-LD `image` at it.
- Add `<meta property="og:image:width" content="1200">` and `<meta property="og:image:height" content="630">`.
- Verify with the Facebook Sharing Debugger, LinkedIn Post Inspector and X Card Validator.