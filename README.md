# Payload + Supabase Starter Kit

A modern **Payload CMS** starter kit integrated with **Supabase** for authentication, Postgres, storage, and real-time capabilities. Designed for local development and production-ready deployments.

---

## ✨ Features

* **Payload CMS** (Local API + Admin UI)
* **Supabase**

  * Postgres database
  * Auth (email/password, OAuth-ready)
  * Storage buckets
  * Row Level Security (RLS)
* **TypeScript-first** setup
* **Docker & Supabase CLI** friendly
* Ready for **Next.js** or standalone Payload usage

---

## 📦 Tech Stack

* Payload CMS
* Supabase (Postgres + Auth + Storage)
* Node.js 18+
* TypeScript
* Docker (optional but recommended)

---

## 📁 Project Structure

```text
.
├── payload/
│   ├── collections/
│   ├── payload.config.ts
│   └── server.ts
├── supabase/
│   ├── migrations/
│   └── seed.sql
├── .env.example
├── docker-compose.yml
├── package.json
└── README.md
```

---

## 🚀 Getting Started

### 1. Prerequisites

* Node.js **18+**
* Docker (recommended)
* Supabase CLI

```bash
npm install -g supabase
```

---

### 2. Clone & Install

```bash
git clone https://github.com/your-org/payload-supabase-starter.git
cd payload-supabase-starter
npm install
```

---

### 3. Environment Variables

Copy the example env file:

```bash
cp .env.example .env
```

Example `.env`:

```env
PAYLOAD_SECRET=super-secret-key
PAYLOAD_PUBLIC_SERVER_URL=http://localhost:3000

SUPABASE_URL=http://localhost:54321
SUPABASE_ANON_KEY=your-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
DATABASE_URL=postgres://postgres:postgres@localhost:54322/postgres
```

---

### 4. Start Supabase (Local)

```bash
supabase start
```

This will spin up:

* Postgres
* Auth
* Storage
* Studio UI

---

### 5. Run Payload CMS

```bash
npm run dev
```

Payload Admin UI:

```
http://localhost:3000/admin
```

---

## 🔐 Authentication Strategy

* Supabase handles **user authentication**
* Payload stores **application data**
* Supabase `user.id` can be mirrored into Payload collections

Example pattern:

```ts
// On user signup
payload.create({
  collection: 'users',
  data: {
    supabaseUserId: user.id,
    email: user.email,
  },
})
```

---

## 🗄️ Database & Migrations

* Supabase migrations live in `supabase/migrations`
* Apply migrations:

```bash
supabase db reset
```

---

## 📂 File Storage

* Supabase Storage buckets for media
* Payload Media collection can store Supabase file URLs

---

## 🔒 Security Notes

* Enable **Row Level Security (RLS)** on all Supabase tables
* Use **Service Role Key** only on the server
* Never expose service keys to the browser

---

## 📦 Deployment

### Payload

* Node server (Railway, Fly.io, Render, VPS)

### Supabase

* Supabase Cloud **or** self-hosted

Make sure production env vars are set correctly.

---

## 🧪 Useful Commands

```bash
supabase status
supabase db reset
npm run build
npm run start
```

---

## 🛣️ Roadmap

* [ ] Next.js App Router integration
* [ ] Supabase OAuth providers
* [ ] Realtime subscriptions
* [ ] Payload access control via Supabase roles

---

## 📄 License

MIT

---

## 🤝 Contributing

PRs welcome. Open an issue for discussions or feature requests.

---

## 📬 Questions

If you’re using this as a starter for a real project and want help wiring **Payload ↔ Supabase** cleanly (RLS, auth sync, or local devcontainers), feel free to ask.
