# vayvian.com static site — Caddy with automatic HTTPS.
# Build/run from the deploy/ directory:
#   docker compose up -d --build
FROM caddy:2-alpine

COPY deploy/Caddyfile /etc/caddy/Caddyfile

COPY index.html privacy-policy.html robots.txt sitemap.xml /srv/
COPY assets /srv/assets
