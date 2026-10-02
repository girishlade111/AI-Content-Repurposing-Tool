# AI Content Repurposing Tool

Transform one piece of content into many. Paste text (or a YouTube URL), pick a format, and get platform-ready content generated with AI: summaries, social posts, newsletters, video scripts, and more.

## Features

- **AI repurposing engine** — transforms source content into summaries, social posts, newsletters, and video scripts via OpenRouter.ai
- **YouTube transcript import** — pulls transcripts directly from YouTube videos for repurposing
- **Bulk processing** — repurpose multiple content items in one go
- **Content library** — save, browse, and reuse generated content
- **Templates** — reusable repurposing templates
- **Analytics dashboard** — track usage and output
- **Social integrations** — manage connected social accounts
- **User auth** — NextAuth (credentials) with credit-based usage tiers (free tier included)
- **Dark/light theme** with animated, modern UI

## Tech Stack

- **Framework:** Next.js 14 (App Router) + React 18 + TypeScript
- **Styling:** Tailwind CSS, shadcn-style UI components, lucide-react icons
- **Auth:** NextAuth.js v4 (credentials provider, bcrypt password hashing)
- **Database:** Prisma ORM with SQLite (dev) — swap `DATABASE_URL` for Postgres in production
- **AI:** OpenRouter.ai (any chat model via one API)

## Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Configure environment
cp .env.example .env
# Fill in OPENROUTER_API_KEY, NEXTAUTH_SECRET, DATABASE_URL

# 3. Set up the database
npx prisma db push

# 4. Run the dev server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). Register an account, then start repurposing from the dashboard.

## Project Structure

```
app/
  api/            # API routes: auth, repurpose, bulk, library, templates,
                  # analytics, credits, export, social, youtube
  auth/           # login / register pages
  dashboard/      # app pages: new, results, library, bulk, templates,
                  # analytics, social
components/      # layout, dashboard, sections, ui components
contexts/        # theme + toast contexts
lib/             # auth options, openrouter client, prisma client, utils
prisma/          # schema.prisma (User, RepurposingJob, Template, Analytics, ...)
```

## Environment Variables

| Variable | Description |
|---|---|
| `OPENROUTER_API_KEY` | OpenRouter.ai API key for AI generation |
| `NEXTAUTH_SECRET` | Secret for NextAuth session encryption |
| `NEXTAUTH_URL` | Public URL of the app (e.g. `https://your-app.com`) |
| `DATABASE_URL` | Prisma connection string (SQLite by default) |

## Deploy Notes

This is a **dynamic** Next.js app — it needs a Node server plus a database and the env vars above. Recommended: Netlify, Vercel, or any Node host. It cannot run as a static export (API routes + auth + Prisma).

## License

MIT

---

Built by [Girish Lade](https://ladestack.in)
