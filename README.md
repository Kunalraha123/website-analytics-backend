# Website Analytics Backend

This is a starter implementation of a Website Analytics Backend built with **Node.js + Express + Prisma + PostgreSQL + Redis**.

## Features included
- API key management (register endpoint returns API key)
- Event collection endpoint (`POST /api/analytics/collect`)
- Analytics endpoints (`GET /api/analytics/event-summary`, `GET /api/analytics/user-stats`)
- Swagger documentation at `/docs`
- Docker and docker-compose for local development
- Prisma schema for PostgreSQL
- Basic rate limiting and input validation
- Tests skeleton (Jest + Supertest)

## Quick start (local)
1. Copy `.env.example` to `.env` and edit if needed.
2. Start services:
```bash
docker-compose up --build
```
3. Run migrations (requires prisma CLI):
```bash
docker exec -it <app_container> npx prisma migrate deploy
```
4. Visit API docs: `http://localhost:3000/docs`

## Tests
Run tests locally:
```bash
npm install
npm test
```

## Deployment
You can deploy this app to Render, Railway or Heroku. Ensure `DATABASE_URL` and `REDIS_URL` are set in environment.

## Notes & Next steps
- For production: rotate API keys, store lookup-friendly hash (HMAC) for O(1) lookup, implement queue (Kafka) for high throughput ingestion, add caching with Redis for aggregate endpoints, and full Google OAuth onboarding.
