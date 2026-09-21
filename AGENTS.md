# Brand: single source of truth


## START HERE — RULES BEFORE WORK STARTS

1. Check if `darwin-agent-center` is connected via `/mcp`.
   - Connected: pull `kb_standards()` and `kb_agent_template()` immediately.
   - Not connected: ask the user to connect. Do not proceed until connected.
2. Read `status.md` in the folder you are working in.
3. Read that folder's `workflow.md`.
4. Follow the Key Agentic Loop (Section 2 of any `workflow.md`). Do not skip it.

No file may be touched until steps 1–4 are complete.

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
