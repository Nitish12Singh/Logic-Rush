# ⚡ LogicRush — Multiplayer Aptitude & Logic Quiz Platform

**Think fast. Play smart. Outsmart everyone.**

LogicRush is a full-stack, real-time quiz application for aptitude practice, placement preparation, and competitive multiplayer learning. Students can practise independently, join live quiz rooms, track performance, and compete on leaderboards. Hosts can create and manage quiz sessions.

**Maintained by:** Nitish Kumar Singh  
**Email:** [nitishofficial9026@gmail.com](mailto:nitishofficial9026@gmail.com)  
**GitHub:** [@Nitish12Singh](https://github.com/Nitish12Singh)

> **Demo links from the project configuration:** [Frontend](https://client-gamma-ten-18.vercel.app/) · [Backend health endpoint](https://logic-rush-api.onrender.com/api/health). Availability has not been independently verified.

## Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [How to Use](#how-to-use)
- [Testing](#testing)
- [Deployment](#deployment)
- [Security Notes](#security-notes)
- [Contact](#contact)

## Features

- **Live multiplayer quizzes:** Join rooms with shareable codes, real-time questions, timers, scoring, and leaderboards.
- **Solo practice:** Practise aptitude and reasoning topics at your own pace.
- **Host portal:** Create quiz rooms, manage questions and question sets, review attempts, and export results.
- **Student dashboard:** Review progress, accuracy, and performance trends.
- **Topic-based learning:** Quantitative aptitude, logical reasoning, verbal ability, data interpretation, programming, and more.
- **Leagues and challenges:** Team competition, daily challenges, achievements, and rankings.
- **Fairer scoring:** Server-side answer checking, timing, and option randomization.
- **Accessibility options:** Adjustable text size, high-contrast presentation, low-data mode, and audio controls.

## Technology Stack

| Layer | Technologies |
| --- | --- |
| Frontend | React 18, TypeScript, Vite, Tailwind CSS |
| UI and charts | Framer Motion, Lucide React, Recharts |
| Backend | Node.js, Express |
| Real-time communication | Socket.IO |
| Database | SQLite (local), PostgreSQL (configured deployments) |
| Authentication | JWT, bcryptjs |
| Deployment configuration | Vercel (client), Render (server) |

## Project Structure

```text
LOGIC-RUSH-main/
├── client/                 # React and TypeScript frontend
│   ├── public/             # Images and static assets
│   ├── src/
│   │   ├── components/     # Quiz, dashboard, host and lobby UI
│   │   ├── context/        # Authentication context
│   │   ├── services/       # REST and Socket.IO clients
│   │   └── types/          # TypeScript types
│   ├── .env.example
│   └── package.json
├── server/                 # Express API and Socket.IO backend
│   ├── src/
│   │   ├── data/           # Seed questions
│   │   └── db/             # Database schema and access
│   ├── tests/              # Backend tests and simulation
│   ├── .env.example
│   └── package.json
├── .github/workflows/      # CI workflow
├── render.yaml             # Render deployment blueprint
└── README.md
```

## Getting Started

### Prerequisites

- Node.js **18 or newer**
- npm
- A terminal and a code editor (such as VS Code)

### 1. Get the source code

Download and extract the project ZIP, or clone your repository after uploading it to GitHub. Open a terminal in the extracted `LOGIC-RUSH-main` folder.

### 2. Start the backend

```bash
cd server
npm install
```

Create a local `.env` from the example:

```bash
cp .env.example .env
```

On Windows Command Prompt, use `copy .env.example .env` instead. Set a unique `JWT_SECRET` in `.env`, then run:

```bash
npm run dev
```

The backend uses **port 4000** by default. For local development, SQLite is used when `DATABASE_URL` is not set.

### 3. Start the frontend

Open a **second terminal** at the project root:

```bash
cd client
npm install
npm run dev
```

Open **http://localhost:5173** in your browser. The Vite development configuration proxies API and Socket.IO requests to the local backend.

## Environment Variables

### Backend (`server/.env`)

| Variable | Purpose | Local example |
| --- | --- | --- |
| `PORT` | Backend port | `4000` |
| `NODE_ENV` | Runtime mode | `development` |
| `JWT_SECRET` | Signs authentication tokens | Set a unique random secret |
| `CLIENT_URL` | Allowed frontend origin | `http://localhost:5173` |
| `DATABASE_URL` | Optional PostgreSQL connection | Leave unset for local SQLite |

### Frontend (`client/.env`, for deployed environments)

| Variable | Purpose |
| --- | --- |
| `VITE_API_URL` | Backend API URL, ending in `/api` |
| `VITE_SOCKET_URL` | Backend origin used for Socket.IO |

For local development, the existing Vite proxy handles backend requests. Use the supplied `.env.example` files as templates. **Never commit actual `.env` files or secrets.**

## How to Use

1. Open the frontend and sign up or sign in.
2. Select solo practice to work on questions independently, or join a multiplayer room using its code.
3. A host can create a room, select or author questions, and invite participants.
4. Answer questions before the timer expires and view round results and the final leaderboard.
5. Check the dashboard and analytics to identify topics that need more practice.

## Testing

Run backend tests:

```bash
cd server
npm test
```

Run the multiplayer load simulation (requires the relevant local server setup):

```bash
cd server
npm run simulate-50
```

Build the frontend:

```bash
cd client
npm run build
```

These are the project-provided commands; this README update does **not** claim that tests were executed.

## Deployment

**Frontend:** Deploy the `client` directory to Vercel. Set `VITE_API_URL` and `VITE_SOCKET_URL` to your deployed backend endpoints, then build and deploy.

**Backend:** Deploy the `server` directory to a persistent Node.js host that supports WebSockets (such as Render). Configure `NODE_ENV=production`, `DATABASE_URL`, `JWT_SECRET`, and `CLIENT_URL`. The repository includes a `render.yaml` blueprint.

**Important:** Live multiplayer rooms are stored in server memory. Multiple backend instances require additional shared state and a Socket.IO adapter. Do not rely on an ephemeral SQLite file for production data.

## Security Notes

- Passwords are hashed using `bcryptjs`.
- Authentication uses JWT tokens and role-based authorization.
- Server-side validation and scoring help protect quiz fairness.
- Use HTTPS in production and strong, private environment secrets.
- Review the application and its dependencies before production deployment.

## Contact

**Nitish Kumar Singh**  
Email: [nitishofficial9026@gmail.com](mailto:nitishofficial9026@gmail.com)  
GitHub: [github.com/Nitish12Singh](https://github.com/Nitish12Singh)

---

*LogicRush — Think fast. Play smart. Outsmart everyone.*

