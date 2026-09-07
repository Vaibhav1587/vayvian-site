# vayvian.com

Personal-projects site of VAYVIAN TECHNOLOGIES (Vaibhav). Static HTML, no build step.

| Path | Contents |
|---|---|
| `index.html` | Single-page intro + project showcase (The Royale Lab, Yoga Companion, Little Shop: Math Adventure), SEO meta + JSON-LD |
| `privacy-policy.html` | Privacy policy for **Little Shop: Math Adventure** (`com.vayvian.mathadventure`). Source of truth is `littleshop-mathadventure/docs/privacy-policy.html`; copy it here when it changes. |
| `assets/` | Optimised WebP images used by the index page |
| `robots.txt`, `sitemap.xml` | Crawler hints |
| `deploy/` | Caddy + Docker for self-hosting with automatic HTTPS |
| `CNAME` | GitHub Pages custom-domain record (kept so Pages can serve the same tree) |

## Run with Docker

```bash
cd deploy
docker compose up -d --build
```

The container listens on host port **8444** (HTTPS). Forward public 443 to it. Certificates are
persisted in the `privacy_caddy_data` volume so they survive rebuilds. This stack replaces the
older privacy-only container from the game repo (`deploy/privacy/`); stop that one first as both
use the container name `vayvian-privacy`.

Local check without DNS:

```bash
docker run --rm -p 8085:80 $(docker build -q -f deploy/Dockerfile .)
```

then open <http://localhost:8085>.
