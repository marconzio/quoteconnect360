# Deploying Connect Quote 360

## Option A — VPS / VM with Docker (recommended): Caddy + Docker Compose

### 1) DNS
Point your domain (e.g., `quote.example.com`) A-record to your server's public IP.

### 2) Edit domain in Caddyfile
File: `deploy/Caddyfile`
Replace `example.com` with your domain.

### 3) Start production stack
From repo root:
```bash
cd deploy
docker compose -f docker-compose.prod.yml up --build -d
```

### 4) Verify
- Website: `https://YOUR_DOMAIN`
- API docs: `https://YOUR_DOMAIN/api/docs`

Notes:
- Caddy auto-provisions HTTPS certificates.
- Requests to `/api/*` are reverse-proxied to the backend and the `/api` prefix is stripped.

## Option B — PaaS (Render/Fly/Railway)

Use two services + managed Postgres.

Backend env:
- DATABASE_URL
- JWT_SECRET
- CORS_ORIGINS=https://YOUR_FRONTEND_DOMAIN

Frontend env:
- VITE_API_URL=https://YOUR_BACKEND_DOMAIN   (or use a reverse proxy and keep `/api`)

## Production hardening checklist
- Set JWT_SECRET to a strong secret.
- Move artifacts out of DB (S3/Azure) when storing large PDFs/834.
- Add Alembic migrations for schema changes.
- Add rate limiting + audit logging.
