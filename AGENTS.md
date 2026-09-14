# Brand: single source of truth

**All Darwin branding lives in [`darwin-geospatial/admin-darwin-marketing`](https://github.com/darwin-geospatial/admin-darwin-marketing), under `marketing/branding/`. That is the ONLY source of truth.** Mario owns it; this website just consumes it.

Exact locations in that repo:

| What you need              | Path (in `admin-darwin-marketing`)                        |
| -------------------------- | --------------------------------------------------------- |
| Colours / design tokens    | `marketing/branding/darwin_geospatial/tokens.css`         |
| Brand guide / voice / motifs | `marketing/branding/darwin_geospatial/BRAND.md`, `VOICE.md`, `MOTIFS.md` |
| Darwin logos (svg + png)   | `marketing/branding/darwin_geospatial/logos/`             |
| SoilSaveR brand            | `marketing/branding/soil_saver/`                          |
| Brand-kit PDFs             | `marketing/branding/brandkit/`                            |
| Partner logos / team photos | `marketing/branding/shared/`                             |

Rules:

- Need a colour, palette, or logo? Take it from the paths above — don't reinvent it here.
- Don't add brand values or palette/reference pages to this repo — they drift out of sync.
- The logos/favicons in `assets/brand/` are **mirrors** of `.../darwin_geospatial/logos/`.
  Change them there first, then sync the file here.
