# ARCHITECTURE -- darwinlabsweb

> Agentic context map. Read this before touching any file.
> Never copy from another repo -- this file maps only what lives here.
> Last reviewed: 2026-09-26 by @gabrielireland

---

## 1. Repo Map

> DS-STD-001 · DS-STD-001-001 · DS-STD-001-002 · DS-STD-001-003
> Every path listed here is checked by `kb_staleness_audit` on every push to main.

**Purpose:** Public website for Darwin Geospatial (darwingeospatial.com). Plain static HTML, no
build step: Tailwind via CDN, bilingual ES (default) / EN through `data-lang` attributes toggled
by `lang.js`. Whatever is on `main` is what gets served (hosting details and current status in
`CLOUDFLARE.md`). Brand values are consumed from `admin-darwin-marketing`, never defined here.

**Structure:**

| Path | Type | Purpose |
|------|------|---------|
| `AGENTS.md` | file | Agentic context and brand-source rules -- read first every session |
| `CLAUDE.md` | file | Canonical connectivity block (DS-STD-005-004) |
| `ARCHITECTURE.md` | file | This map (DS-STD-001-005) |
| `IDEAS.md` | file | Ideas backlog (DS-STD-001-004) |
| `README.md` | file | One-line repo description |
| `CLOUDFLARE.md` | file | Deployment guide: DNS, Cloudflare Pages vs GitHub Pages status |
| `SEO.md` | file | SEO tag reference and how to add SEO to a new page |
| `PENDING.md` | file | Website restructure proposal (working doc) |
| `SOILSAVER_RESEARCH_GROUP.md` | file | Content brief for `projects/soil_saver/` |
| `index.html` | file | Homepage: hero reveal, mission canvas, solutions, projects, team, contact form |
| `services.html` | file | Services page, partner marquee |
| `privacy.html` | file | Privacy policy |
| `lang.js` | file | Language switching (ES/EN) + mission canvas animation |
| `analytics.js` | file | GA4 loader + GDPR consent banner |
| `CNAME` | file | Custom domain for GitHub Pages |
| `.nojekyll` | file | Disables Jekyll processing on GitHub Pages |
| `.gitattributes` | file | Forces LF line endings |
| `.gitignore` | file | Git ignore rules |
| `favicon.ico` | file | Root favicon |
| `robots.txt` | file | Crawler rules |
| `sitemap.xml` | file | Sitemap for search engines |
| `llms.txt` | file | Site summary for LLM crawlers |
| `openapi.json` | file | Machine-readable site/API description |
| `solutions/` | dir | One landing page per audience or solution (ngo, research, companies, city, public administration, nature assessment, ai agents, software for nature) |
| `projects/` | dir | Project case-study pages, one folder each with `index.html` + `assets/` |
| `projects/darwin_crops_landuse/` | dir | Crops / land-use project page |
| `projects/darwin_maps/` | dir | Darwin Maps project page |
| `projects/darwin_oceans/` | dir | Darwin Oceans project page |
| `projects/darwin_visor/` | dir | Darwin Visor project page (includes demo videos) |
| `projects/guadarramaski/` | dir | Guadarrama Ski project page |
| `projects/soil_saver/` | dir | SoilSaveR research group page (GSAP animations) |
| `projects/cedar_vista/`, `projects/habitat_hub/`, `projects/urban_nature/` | dir | Asset-only folders; banners used as cards on homepage and `solutions/` pages |
| `projects/team/` | dir | Individual team member portfolio pages |
| `blog/` | dir | Blog index and articles |
| `assets/brand/` | dir | Logos and favicons, mirrored from `admin-darwin-marketing` (see `AGENTS.md`) |
| `assets/brand/soilsaver/` | dir | SoilSaveR logos, mirrored from `admin-darwin-marketing` |
| `assets/hero/` | dir | Homepage hero slideshow and reveal images (webp + source png/jpg) |
| `assets/hero/deprecated/` | dir | Retired hero images (see Open findings) |
| `assets/partners/` | dir | Partner and client logos; `transparent/` holds background-removed variants |
| `assets/team/` | dir | Team photos |
| `assets/services/` | dir | Service card images for `services.html` |
| `assets/flags/` | dir | Country / region flags used on project cards |
| `scripts/` | dir | Local maintenance scripts (`README.md` documents them) |
| `scripts/convert-hero-images.sh` | file | Converts hero PNGs to WebP |
| `.claude/settings.local.json` | file | Local Claude Code settings (see Open findings) |

**Entry points:**

| Entry point | Triggered by | What it does |
|-------------|-------------|--------------|
| `index.html` | browser | Homepage; loads `lang.js` and `analytics.js` |
| `services.html`, `privacy.html`, `solutions/*.html`, `projects/*/index.html`, `blog/*.html` | browser | Standalone pages, each self-contained (inline styles + Tailwind CDN) |
| `git push origin main` | human | Publishes the site (see `CLOUDFLARE.md` for which host is live) |
| `scripts/convert-hero-images.sh` | manual | Regenerates hero WebP files |

**External dependencies:**

| Dependency | Type | Declared in |
|-----------|------|-------------|
| `darwin-agent-center` | MCP | `CLAUDE.md` |
| `admin-darwin-marketing` (`marketing/branding/`) | brand source repo | `AGENTS.md` |
| Tailwind CSS (`cdn.tailwindcss.com`) | CDN script | every HTML page |
| Google Fonts | CDN stylesheet | every HTML page |
| GSAP + ScrollTrigger (`cdnjs.cloudflare.com`) | CDN script | `projects/soil_saver/index.html` |
| Google Analytics 4 (`googletagmanager.com`) | analytics | `analytics.js` |
| Formspree | form backend | `index.html` (contact form) |
| `storage.googleapis.com/urban-tree-visor/` | embedded app | `solutions/city-solutions.html` |
| `darwinmaps.web.app` | linked app | `projects/darwin_maps/`, homepage |
| Cloudflare (DNS) / Cloudflare Pages / GitHub Pages | hosting | `CLOUDFLARE.md`, `CNAME` |

Sections 2-5 skipped: no GCP resources owned by this repo (the GCS bucket above is only
embedded, owned elsewhere), no agents, no pipelines, no knowledge graph.

---

## Open findings

Flagged for human review, not fixed:

- `assets/hero/deprecated/` looks orphaned. `forest_rgb.jpg` and `forest_seg.jpg` exist both
  there and in `assets/hero/`. Confirm nothing references the deprecated copies before removing.
- `.darwin/repo.json` is missing (DS-STD-001-002).
- `.claude/settings.local.json` is tracked by git; local settings are usually ignored.
- `CLOUDFLARE.md` (June 2026) says Cloudflare Pages is disconnected and names the repo as
  `darwin-geospatial/darwinlabsweb`, while `origin` points to `gabrielireland/darwinlabsweb`.
  Confirm which host is live and update `CLOUDFLARE.md`.
- `projects/cedar_vista/`, `habitat_hub/`, `urban_nature/` have assets but no `index.html`;
  confirm whether pages are planned or the folders should move under `assets/`.
- `projects/endworldhunger/assets/` exists locally but is empty (untracked).
- No references to `assets/hero/deprecated/` found in any HTML/JS file.
- No `status.md` / `workflow.md` at root, which `AGENTS.md` START HERE expects (DS-STD-003-003-002).
