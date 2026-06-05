# Scorevant

Scorevant is a tournament management, officiating assistant, and live scoring platform for racket sports (Badminton, Tennis, Table Tennis, Squash, Pickleball).

This repository contains a React + Vite frontend and a NestJS backend (MongoDB + Mongoose). The frontend supports optional realtime updates via Supabase.

## Contents

- `frontend/` — React (TypeScript) application powered by Vite
- `backend/` — NestJS server with Mongoose schemas and JWT auth

## Quick start

Requirements:

- Node.js v18+ (v20 recommended)
- npm (or pnpm/yarn)
- MongoDB (local or remote)

Install dependencies:

```bash
# from repository root
cd frontend && npm install
cd ../backend && npm install
```

Configure environment variables:

- `backend/.env` (example):

```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/scorevant
JWT_SECRET=replace-with-strong-secret
# Optional: SUPABASE config if you use realtime
SUPABASE_URL=https://your.supabase.url
SUPABASE_KEY=anon-or-service-key
```

- `frontend/.env` (example):

```env
VITE_API_BASE_URL=http://localhost:3000
VITE_SUPABASE_URL=https://your.supabase.url
VITE_SUPABASE_ANON_KEY=your-anon-key
```

Run the apps:

```bash
# start backend
cd backend
npm run start

# in a separate terminal: start frontend
cd frontend
npm run dev
```

Open the frontend at `http://localhost:5173` (Vite default) and the backend at `http://localhost:3000`.

## Project structure

Key folders:

- `frontend/src/` — React pages, components, hooks, and `lib/` utilities
- `backend/src/` — NestJS modules (`auth`, `court`, `tournament`), controllers, services, and `schemas/`

## Authentication and API

The backend exposes JWT-based authentication endpoints under `/auth`:

- `POST /auth/register` — create account
- `POST /auth/login` — authenticate and receive JWT
- `GET /auth/me` — returns current user (requires `Authorization: Bearer <token>`)

The frontend automatically includes JWT tokens for protected requests when authenticated.

## Realtime (optional)

Supabase Realtime is supported for live spectator updates. If not configured, the core scoring and tournament features operate normally.

## Development notes

- The match engine is implemented as a pure-function rules engine with `useReducer` for deterministic state transitions and easy undo/redo.
- Frontend uses React hooks, React Query for data fetching, Tailwind CSS for styling, and Framer Motion for animations.
- Backend uses NestJS with Mongoose ODM and JWT authentication.

## Testing

Run available tests (if present) with your package manager inside each package, e.g.:

```bash
cd backend && npm test
cd frontend && npm test
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Open a pull request with tests and a description

## License

This repository does not include a license file. Add an appropriate license in `LICENSE` if you intend to publish.

---

If you'd like, I can commit this README and push it to the remote.
