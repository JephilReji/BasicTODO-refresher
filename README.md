# Basic TODO App

This is a repo for a basic TODO app with:
- Svelte frontend (with basic CSS)
- Node.js + Express backend
- MongoDB database

- LINK : https://basictodo-jr.vercel.app/

## Structure
- `frontend/` — Svelte app
- `backend/` — Express API server

## Setup

### 1. Backend
- Configure your MongoDB connection string in `backend/.env` (see `.env.example`).
- Run `npm install` in `backend/`.
- Start the server with `npm run dev`.

### 2. Frontend
- Run `npm install` in `frontend/`.
- Start the dev server with `npm run dev`.

### 3. Git & Deployment
- Initialize git in the root folder and push to your remote repo.
- Deploy the frontend to Vercel (see Vercel docs for SvelteKit or static Svelte).
- Deploy the backend to a suitable Node.js host (Vercel, Render, Railway, etc.).

---

## Features
- Add, view, update, and delete TODOs
- RESTful API
- Simple, clean UI

---

## License
MIT

