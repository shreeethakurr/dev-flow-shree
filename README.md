# DevFlow

A project and task manager for developers. Create projects, break them into tasks, move tasks across a Kanban board, and see progress on a dashboard.

## Features

- Register and log in (passwords hashed with bcrypt, sessions with JWT)
- Each user only ever sees their own projects and tasks
- Full CRUD for projects and tasks
- Kanban board (To do, In progress, Completed) with drag and drop, plus buttons for keyboard and touch users
- Dashboard with project and task totals, per-project progress bars, and a chart of tasks completed in the last 7 days
- Dark mode (remembers your choice), responsive layout for phone and laptop

## Tech stack

| Layer | Tools |
| --- | --- |
| Frontend | HTML, CSS, vanilla JavaScript (no build step) |
| Backend | Node.js, Express 5 |
| Database | SQLite via better-sqlite3 |
| Auth | bcryptjs, jsonwebtoken |

## Run it locally

```bash
npm install
cp .env.example .env     # then set JWT_SECRET to a long random string
npm start                # http://localhost:3000
```

Run the API checks with `npm test`.

## API

| Method | Route | What it does |
| --- | --- | --- |
| POST | /api/auth/register | Create an account |
| POST | /api/auth/login | Log in, returns a token |
| GET | /api/auth/me | Current user |
| GET, POST | /api/projects | List or create projects |
| GET, PUT, DELETE | /api/projects/:id | Read, update or delete a project |
| POST | /api/projects/:id/tasks | Add a task to a project |
| PUT, DELETE | /api/tasks/:id | Update (title, status) or delete a task |
| GET | /api/stats | Dashboard numbers |

Send the token as `Authorization: Bearer <token>` on every route except register and login.

## Project structure

```
server/   Express app, database setup, auth, routes, smoke test
public/   index.html, styles.css, app.js
```

## Ideas for next steps

- Switch the database to PostgreSQL (the SQL is standard, only db.js and the query calls change)
- Rebuild the frontend in React
- Deploy (Render or Railway) and add the live link here
