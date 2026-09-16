# FeedBox — volumes and networking starter

Repository: https://github.com/kalviumcommunity/feedbox-volumes-networking-starter

FeedBox is a minimal feedback collector: a PostgreSQL database, an Express API, and a static Nginx frontend running as a three-service Docker Compose stack.

## What is in this repository

```
├── server.js          ← Express API  (GET /api/messages, POST /api/messages)
├── Dockerfile         ← API image
├── package.json
├── docker-compose.yml ← db, api, web with a named volume for PostgreSQL
├── .env.example       ← copy to .env before running
├── .dockerignore
├── client/
│   ├── Dockerfile     ← Nginx image
│   └── index.html     ← frontend
```

## Run the stack

```bash
cp .env.example .env
docker compose up --build
```

- API: http://localhost:5000/api/messages
- Frontend: http://localhost:3000

## Create a message

```bash
curl -X POST http://localhost:5000/api/messages \
  -H "Content-Type: application/json" \
  -d '{"text": "Hello FeedBox"}'
```

## Your task

Follow the assignment brief to:

1. Prove that the named volume keeps PostgreSQL data alive across `docker compose down` and `docker compose up`.
2. Create `docker-compose.override.yml` with a bind mount for `server.js` and `nodemon` for hot-reload.
3. Explain in your PR description why `DATABASE_URL` uses `db` as the hostname and what `localhost` would do instead.
