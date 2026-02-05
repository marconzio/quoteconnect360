# Connect Quote 360

A working demo web app (FastAPI + Postgres + React) that:
- Logs in (JWT)
- Creates quotes with partner selection (TallTree / VaultTPA)
- Runs pricing via a tiny DSL
- Generates PDF + 834 artifacts (stored in Postgres for demo)
- Shows partner mapping tables (rules / REF / plan code maps)

## Run backend (Docker)
From repo root:
```bash
docker compose up --build
```
Backend API: http://localhost:8000/docs

## Run frontend (Node)
```bash
cd frontend
npm install
npm run dev
```
UI: http://localhost:5173

Login:
- admin@connect360.local / admin123
- uw@connect360.local / uw123
- broker@connect360.local / broker123


## Deploy to a real website
See `DEPLOYMENT.md`.
