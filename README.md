# Raccoon Planner — Backend

REST API for Raccoon Planner, a personal productivity app with tasks, time blocks, and Pomodoro sessions.

Built with **NestJS**, **Prisma**, and **PostgreSQL**.

## Features

- JWT authentication with Argon2 password hashing
- Task management with priority levels (low / medium / high)
- Time blocking with drag-and-drop order persistence
- Pomodoro timer with configurable work/break intervals and round tracking
- Per-user settings stored in the database

## Tech Stack

| Layer       | Technology            |
|-------------|-----------------------|
| Framework   | NestJS 10             |
| Language    | TypeScript            |
| ORM         | Prisma 7 + PostgreSQL |
| Auth        | Passport + JWT        |
| Validation  | class-validator       |
| Package mgr | pnpm                  |

## Prerequisites

- Node.js ≥ 18
- pnpm
- PostgreSQL (running locally or via Docker)

## Getting Started

### 1. Install dependencies

```bash
pnpm install
```

### 2. Configure environment

Create a `.env` file in the project root:

```env
DATABASE_URL=postgresql://postgres:password@localhost:5432/raccoon-planner?schema=public
JWT_SECRET=your_secret_here
PORT=3000
```

### 3. Run database migrations

```bash
pnpm prisma migrate dev
```

### 4. Start the development server

```bash
pnpm start:dev
```

The API will be available at `http://localhost:3000/api`.

## Project Structure

```
src/
├── auth/          # Registration, login, JWT strategy
├── user/          # User profile & settings
├── task/          # Task CRUD
├── time-block/    # Time block CRUD + order management
├── pomodoro/      # Pomodoro sessions and rounds
├── prisma.service.ts
└── main.ts
```

## API Overview

| Module      | Base path          |
|-------------|--------------------|
| Auth        | `/api/auth`        |
| User        | `/api/user`        |
| Tasks       | `/api/tasks`       |
| Time Blocks | `/api/time-blocks` |
| Pomodoro    | `/api/pomodoro`    |

All protected routes require a `Bearer` JWT token in the `Authorization` header.

## Scripts

| Command           | Description                     |
|-------------------|---------------------------------|
| `pnpm start:dev`  | Development server (watch mode) |
| `pnpm build`      | Compile TypeScript              |
| `pnpm start:prod` | Run compiled output             |
| `pnpm test`       | Unit tests                      |
| `pnpm test:e2e`   | End-to-end tests                |
| `pnpm test:cov`   | Test coverage report            |
| `pnpm lint`       | Lint + auto-fix                 |

## Related

- [raccoon-planner-front-end](https://github.com/your-username/raccoon-planner-front-end) — React frontend (expects backend on port 3000)
