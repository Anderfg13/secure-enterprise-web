# Secure Web System as an Enterprise Risk Control

- **Deployed URL:** https://enterprise-risk-anderson.duckdns.org
- `backend/` — Spring Boot 4 / Java 21 backend (OAuth2 Resource Server, validates Auth0 JWT issuer + audience).
- `frontend/` — Vite React SPA using `@auth0/auth0-react`.
- `deploy/` — systemd unit and Apache vhost templates.

## Run locally
1. Set `issuer-uri` in `backend/src/main/resources/application.properties` and the CORS origin in `SecurityConfig.java`.
2. `cd backend && mvn spring-boot:run` — `GET /api/risk-status` without a token returns 401.
3. `cd frontend && cp .env.example .env.local` (fill in values, never commit it), `npm install && npm run dev` → http://localhost:5173.

## Evidence
Details of each screenshot: [docs/README.md](docs/README.md).

| Evidence | Screenshot |
|---|---|
| Auth0 SPA application | ![](docs/01-auth0-application.png) |
| Auth0 API | ![](docs/02-auth0-api.png) |
| API rejects requests without a token (401) | ![](docs/03-api-401.png) |
| Auth0 login | ![](docs/04-login-auth0.png) |
| Authenticated API call | ![](docs/05-api-call.png) |
| Valid TLS certificate | ![](docs/06-certificate.png) |
| Deployed application | ![](docs/07-deployed-app.png) |
| Services running on the server | ![](docs/08-server-services.png) |
