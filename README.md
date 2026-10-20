# 🩺 Sweet Medical

### Medical Appointment Management Platform

**A full-stack web application for managing medical appointments, professional availability, and patient notifications.**

![Next.js](https://img.shields.io/badge/Next.js-black?logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-149ECA?logo=react&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

*Academic group project · Software Development · Universidad Tecnológica Nacional (UTN FRBA)*

### 🌐 Live Demo

**[Visit Sweet Medical — Live Application](https://sweet-medical-4.netlify.app/)**

Explore the deployed web application directly in your browser.


## Overview

Sweet Medical is a full-stack healthcare appointment management platform designed to connect patients with medical professionals. Patients can search for available appointments, review estimated costs based on their healthcare coverage, and book appointments. Medical professionals can manage their availability and services and track upcoming appointments.

The application uses a REST API, a document-oriented database, role-based authentication, and a responsive web interface.

## Key features

### Patients
- Search available appointments using filters such as specialty, professional, location, and date.
- View estimated appointment costs based on insurance plan coverage.
- Preselect appointments in a client-side cart before booking.
- Book, review, and cancel appointments, subject to business rules.
- View appointment-related notifications.

### Medical professionals
- Manage availability and offered medical services.
- View their appointment agenda and patient information.
- Manage appointment status and receive notifications.

### Platform and business logic
- Authentication using JSON Web Tokens (JWT).
- REST API with request validation using Zod.
- MongoDB persistence using Mongoose.
- Scheduled jobs for generating available appointment slots and sending reminders.
- Atomic appointment reservation to prevent concurrent double bookings.
- Unit, integration, and end-to-end testing.

## Tech stack

| Layer | Technologies |
| --- | --- |
| Frontend | Next.js, React, JavaScript, Ant Design, CSS |
| Backend | Node.js, Express, JavaScript |
| Database | MongoDB, Mongoose |
| Authentication | JWT, bcryptjs |
| Validation | Zod |
| HTTP communication | Native `fetch`, centralized API client |
| Background jobs | node-cron |
| Testing | Jest, Cypress |
| API documentation | Swagger |
| Version control | Git, GitHub |

## Architecture

```text
Patient / Doctor
       │
       ▼
Next.js + React Frontend
       │
       ├── Components / Pages
       ├── Context API (shared state)
       ├── Services (API calls)
       └── HTTP client (fetch + JWT)
                    │
                    ▼
             Express REST API
                    │
       ├── Routes / Middlewares
       ├── Controllers
       ├── Services (business logic)
       ├── Repositories
       └── Mongoose Models
                    │
                    ▼
                 MongoDB

Scheduled jobs: appointment slot generation and reminders
```

### Example: appointment booking flow

1. The patient searches for available appointments using filters.
2. The backend returns results with estimated coverage and costs.
3. The patient preselects an appointment; the selection is managed by React Context and stored locally in the browser.
4. The application requests a final quote and submits the reservation.
5. The backend checks availability and atomically updates the appointment to prevent double booking.
6. The platform processes the corresponding appointment notifications.

## Repository structure

```text
sweet-medical/
├── packages/
│   ├── backend/
│   │   ├── src/
│   │   │   ├── controllers/
│   │   │   ├── domain/
│   │   │   ├── jobs/
│   │   │   ├── middlewares/
│   │   │   ├── models/
│   │   │   ├── repositories/
│   │   │   ├── routes/
│   │   │   ├── services/
│   │   │   └── tests/
│   │   └── index.js
│   └── frontend/
│       ├── public/
│       └── src/
│           ├── app/
│           ├── components/
│           ├── config/
│           ├── context/
│           └── services/
├── cypress/
└── README.md
```

## Getting started

### Prerequisites

- Node.js and a compatible package manager (the project includes pnpm lockfiles).
- Access to a MongoDB instance.

### 1. Clone the repository

```bash
git clone https://github.com/JoaquinMarini/sweet-medical.git
cd sweet-medical
```

### 2. Configure environment variables

Create `packages/backend/.env` locally:

```dotenv
MONGO_URI=<your-mongodb-connection-string>
JWT_SECRET=<your-own-strong-secret>
SERVER_PORT=3001
```

Configure the frontend API URL if needed in `packages/frontend/.env.local`:

```dotenv
NEXT_PUBLIC_API_URL=http://localhost:3001
```

**Never commit real credentials or `.env` files to Git.**

### 3. Install dependencies and run

Install dependencies using the package manager and workspace setup defined by the project's `package.json` files. Start the backend and frontend in separate terminals:

```bash
# Terminal 1: backend
cd packages/backend
npm run dev
```

```bash
# Terminal 2: frontend
cd packages/frontend
npm run dev
```

> Depending on your local workspace configuration, you may need to install workspace dependencies from the repository root first.

## Testing

The project includes:
- **Unit tests:** business logic and validation.
- **Integration tests:** backend HTTP endpoints.
- **End-to-end tests:** frontend appointment-search flow with Cypress.

## Screenshots

_Add screenshots of the landing page, appointment search, patient cart, and doctor dashboard here._

<!-- Example once a screenshot exists in docs/screenshots/:
![Appointment search](docs/screenshots/appointment-search.png)
-->

## Academic context and contribution

Developed as a **team project** for the Software Development course at **UTN FRBA**. The project provided practical experience in frontend and backend integration, REST API design, persistence, validation, testing, and collaborative Git workflows.

**My contributions:** physician-facing screens, reusable UI components, navigation, and frontend integration. This section should be reviewed to accurately reflect my individual work.

## Project status

Academic project. This personal repository contains a code snapshot without the original group repository's Git history. Deployments, external services, and sample data are not included by default.

---

**Sweet Medical** · Software Development Project · UTN FRBA
