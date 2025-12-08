**MediLink — Smart Hospital Appointment Booking System**

MediLink is a lightweight, chat-driven healthcare assistant designed to simplify symptom intake, doctor discovery, and hospital appointment booking.
The system uses an interactive chatbot interface to collect patient symptoms, suggest relevant medical departments or doctors, and help schedule appointments efficiently.
It aims to reduce manual workload, minimize waiting time, and improve accessibility in hospital service management.

**Course:**
CSE312 —**Software Development**

**Project Group Members:**
**Md. Saiful Islam **(2260CSE01078)
**Md. Mostakim Ahmed Sakib **(2260CSE01053)

This Project contains a static frontend and a small Express backend that uses SQLite for persistence. The assistant can either proxy to an upstream MediVirtuoso chat endpoint (if configured) or run a local, conservative responder that maps symptom text (including Bangla) to suggested doctors.

**Key Features**
- **Chat intake**: Symptom-based assistant that suggests doctors and booking options.
- **Doctor directory**: Searchable doctor profiles, languages, education, ratings, and next-available slots.
- **Bookings**: Simple appointment creation and a bookings dashboard for authenticated users.
- **Auth**: Email/password authentication with JWTs for session protection and admin routes.
- **Import tooling**: Import or seed doctors from JSON using `backend/scripts/import_doctors.js`.

**Repository Structure**
- **`/Medilink-Smart-Hospital-Appointment-Booking-System-main/frontend/public`**: Static UI (`index.html`, `assistant.html`, `doctors.html`, `bookings.html`, `login.html`, `register.html`) and assets.
- **`/Medilink-Smart-Hospital-Appointment-Booking-System-main/backend`**: Express server, DB initializer and scripts (`server.js`, `db.js`, `scripts/import_doctors.js`).

**Tech Stack**
- Node.js (tested on Node 18+)
- Express
- SQLite (`sqlite3`)
- JWT for auth

**Prerequisites**
- Node.js 18 or later
- npm

**Quick Start**
1. Install dependencies:

```
npm install
```
export JWT_SECRET="change-me"
export PORT=3000
npm start
```

The server serves the static frontend from `backend` so open `http://localhost:3000`.

**Useful npm scripts**
- `npm start` — starts the backend server (`node backend/server.js`).
- `npm run dev` — starts the server in development mode.
- `npm run import:doctors` — runs `backend/scripts/import_doctors.js` to seed doctors defined in that script.

To replace existing doctors when importing:

```
REPLACE=1 npm run import:doctors
```

**Database**
- SQLite database file: `backend/app.db` (created automatically on first run).
- Schema includes `users`, `doctors`, and `bookings` tables.

**Endpoints (summary)**
- `POST /api/medivirtuoso` — local responder (requires authentication).
- `POST /api/auth/login` — user login (returns JWT).
- `POST /api/auth/register` — register a new user.
- `GET /api/bookings`, `POST /api/bookings` — manage bookings (authenticated).

**Seeding & Import**
- A small seeder exists at `backend/scripts/import_doctors.js` — run the script to add example doctors.

**Security & Notes**
- The local assistant implements a conservative symptom-to-doctor mapping and should not be used as a substitute for medical advice.
- Do not import or publish third-party doctors' data without permission.
- For production, set a secure `JWT_SECRET` and run behind HTTPS.

**Contribution**
- Md. Mostakim Ahmed Sakib (Backend)
-Md. Saiful Islam (Frontend)

**License**
- This project does not include a license file. Add one if you intend to open-source the code.

---
