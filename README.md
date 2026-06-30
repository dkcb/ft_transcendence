# ft_transcendence

A real-time, full-stack web app — the final project of the 42 / Codam common core — where users **play Pong online** and **chat** with each other. Single-page React frontend, NestJS backend, PostgreSQL database, fully containerized with Docker.

## Features

- **Real-time multiplayer Pong** — play live matches against other users
- **Live chat** — direct messages and channels, with blocking/ignore support
- **Authentication** — login with **two-factor authentication (2FA)**
- **User profiles** — avatars, stats, and **match history**
- **Friends system** — add friends, see online status, block users
- **Achievements** — unlockable achievements tied to play
- **Matchmaking** — pairing players into Pong games

## Tech stack

| Layer | Stack |
|---|---|
| **Frontend** | React, TypeScript, Vite |
| **Backend** | NestJS (Node + TypeScript), WebSockets |
| **Database** | PostgreSQL |
| **Infra** | Docker / docker-compose |

## Architecture

```
frontend/  React + Vite SPA  → :8080
backend/   NestJS API + gateways → :3003   (modules: auth, twostep, users, friends,
           ignores, chat, pong, matches, achievements, connections, database)
postgres   PostgreSQL          → :5432
```

The backend is organized into NestJS feature modules (one folder per domain under `backend/src/`); the frontend is organized by page and feature (`frontend/src/`: `LoginPage`, `AuthenticationPage`, `ProfilePage`, `SettingsPage`, `chat`, `pong`).

## Running it

The whole stack runs via Docker:

```bash
# Provide the required env files (see docker-compose.yml):
#   .env (postgres)  ·  backend/back.env  ·  frontend/front.env

docker-compose up --build
```

Then open the frontend at `http://localhost:8080` (backend API on `:3003`).

> `get_host_hostname.sh` helps set the host address used by the frontend/backend env files when running on a LAN.

## Team & my role

A 42 group project built with Alex ([ahorling](https://github.com/ahorling)), Danila ([dkcb](https://github.com/dkcb)), Frans ([fransholwerda](https://github.com/fransholwerda)), Joel ([fburleson](https://github.com/fburleson)), and Kevin ([kvnok](https://github.com/kvnok)). See the commit history for per-author attribution.
