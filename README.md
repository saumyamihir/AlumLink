# AlumLink

AlumLink is a mentorship platform built with Next.js App Router, React, Tailwind CSS, MongoDB, and Mongoose. Students can discover verified alumni mentors, send requests, manage mentorships, schedule sessions, and track goals. Alumni can submit verification details and manage mentoring activity. Administrators can review alumni and monitor users and engagement.

## Requirements

- Node.js 20.9 or later
- npm
- A running local MongoDB instance, or a MongoDB Atlas cluster

## Local setup

1. Install dependencies:

   ```bash
   npm install
   ```

2. Copy `.env.example` to `.env.local`. The default URI uses a local MongoDB server on port `27017`:

   ```env
   MONGODB_URI=mongodb://127.0.0.1:27017/alumlink
   SESSION_SECRET=<a-random-secret-at-least-32-characters-long>
   ```

   The database name is `alumlink`. If using Atlas instead, replace the URI with your Atlas connection string. Do not commit `.env.local` or real credentials.

3. Optionally add the development demo accounts and sample mentorship data:

   ```bash
   npm run seed
   ```

   The seed script is idempotent and does not clear collections. Demo login credentials:

   - Admin: `admin@alumlink.demo` / `Demo@123`
   - Student: `student1@alumlink.demo` / `Demo@123`
   - Alumni: `alumni1@alumlink.demo` / `Demo@123`

   These credentials are for local testing only. Never deploy the demo accounts or password as production credentials.

4. Start the development server:

   ```bash
   npm run dev
   ```

   Visit [http://localhost:3000](http://localhost:3000).

## Scripts

- `npm run dev` — Start the development server
- `npm run lint` — Run ESLint
- `npm run build` — Create a production build
- `npm run start` — Serve the production build
- `npm run seed` — Add or update the clearly named demo records

## Application areas

- Public landing and about pages
- Persistent light/dark mode and selectable accent-color palette
- Student dashboard, profiles, mentor discovery and match explanations, requests, mentorships, sessions, goals, and feedback
- Alumni profile, verification submission, availability, requests, students, and sessions
- Admin dashboard, alumni verification, user management, mentorship monitoring, and analytics
- REST-style API handlers under `src/app/api`

Mentor discovery only returns active, verified alumni with capacity. Match scores use the weighted profile fields defined in `src/lib/matching.js`; demo records are sample data and landing-page visuals are illustrative, not live platform statistics. Use the sun/moon control to change light/dark mode and the palette control to choose a saved accent color.

## Deployment

Deploy to a Node.js host that supports Next.js. Configure `MONGODB_URI` and a unique, random `SESSION_SECRET` of at least 32 characters as deployment secrets. Restrict MongoDB network access to the deployment environment, use production-grade credentials, and do not run the demo seed script against production data.
