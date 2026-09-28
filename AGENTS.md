# Base44 Dev Environment

## Project type
Static HTML landing page (Spanish). No build step, no backend, no package manager.
Files: `index.html`, `css/estilo.css`, `img/`. Uses Bootstrap 5 + Bootstrap Icons via CDN.

## Running
`docker compose -f docker-compose.base44.yml up -d` serves the site on port 3000 via nginx.
- nginx runs as `user: root` because the repo root has restrictive (700) permissions on the host.
- Source is bind-mounted read-only at `/usr/share/nginx/html`, so edits appear on page refresh (no live-reload server; call `reload_preview` after edits to update the preview iframe).

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` → 200
- Check `/css/estilo.css` also returns 200.

## Secrets
None required — fully static site with no external service credentials.
