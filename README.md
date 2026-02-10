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
* **Local Development with Docker**
* Ready for **Next.js** or standalone Payload usage

---

## 📦 Tech Stack

* Payload CMS
* Supabase (Postgres + Auth + Storage)
* Node.js 18+
* TypeScript
* Docker

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
* Docker

---

### 2. Clone

```bash
git clone https://github.com/your-org/payload-supabase-starter.git
cd payload-supabase-starter
```

---

### 3. Environment Variables

Copy the example env file:

```bash
cp .env.example .env
```

---

### 4. Start Supabase (Local)

```bash
cd supabase
docker compose up -d
```

This will spin up:

* Postgres
* Auth
* Storage
* Studio UI

Supabase Admin UI:

```
http://localhost:8000
```

---

### 5. Run Payload CMS

```bash
cd payload
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
npm i supabase --save-dev
supabase db reset --db-url="postgresql://<user>:<password>@localhost:<db_port>/<database_name>"

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
docker compose up -d
docker compose down

npm run build
npm run dev
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
