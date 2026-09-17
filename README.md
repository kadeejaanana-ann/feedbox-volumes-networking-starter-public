# FeedBox volumes and networking starter

FeedBox is a minimal feedback collector with PostgreSQL (`db`), Express (`api`), and an Nginx-served frontend (`web`).

## Project structure

```text
├── server.js
├── Dockerfile
├── package.json
├── package-lock.json
├── docker-compose.yml
├── .env.example
└── client/
    ├── Dockerfile
    └── index.html
```

## Run the starter

```bash
cp .env.example .env
docker compose up --build
```

- API: http://localhost:5000/api/messages
- Frontend: http://localhost:3000

## Assignment scope

Complete the Compose configuration by:

1. adding the `feedbox_data` named volume for PostgreSQL;
2. adding isolated `frontend` and `backend` networks; and
3. creating `docker-compose.override.yml` for API hot-reload.

Validate your work with:

```bash
docker compose config -q
docker compose up --build
```

Do not commit `.env` or `node_modules`.
