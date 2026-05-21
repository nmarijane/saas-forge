<div align="center">

# saas-forge

**SaaS project scaffolder for Claude Code**

*Go from idea to full-stack SaaS app without leaving your terminal.*

</div>

---

## What is saas-forge?

saas-forge is a Claude Code plugin that turns a one-line SaaS idea into a ready-to-run Next.js codebase in minutes. It combines an AI brainstorming phase with automated project scaffolding — so you skip the boilerplate setup and start shipping features immediately.

---

## Why saas-forge?

- **Zero config** — one command, and your project is live: `/saas-forge:saas Your idea here`
- **Opinionated but flexible** — ships with auth, email, and dashboard by default; billing, i18n, and admin are optional
- **Production-grade stack** — Next.js 15, Drizzle ORM, Better Auth, shadcn/ui, Stripe
- **No lock-in** — outputs plain files you own; no runtime dependency on saas-forge
- **Claude Code native** — runs as a pure Markdown plugin, no build step required

---

## How does saas-forge compare to alternatives?

| | saas-forge | create-t3-app | shipfast | custom boilerplate |
|---|---|---|---|---|
| Interactive brainstorming | ✅ | ❌ | ❌ | ❌ |
| Removes unused features | ✅ | ❌ | ❌ | ❌ |
| Generates business models | ✅ | ❌ | ❌ | ❌ |
| Auth (self-hosted) | ✅ Better Auth | ✅ NextAuth | ✅ Supabase | varies |
| Billing | ✅ optional | ❌ | ✅ Stripe | varies |
| Setup time | ~5 min | ~10 min | ~30 min | hours |

<div align="center">

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Install with skills.sh](https://img.shields.io/badge/skills.sh-install-ff6600)](https://skills.sh)
[![Claude Code Plugin](https://img.shields.io/badge/claude--code-plugin-blueviolet)](https://code.claude.com/docs/en/plugins)

</div>

---

## The Problem

You want to build a SaaS. So you:

1. Search "best Next.js SaaS boilerplate"
2. Clone a template
3. Spend 2 hours reading docs
4. Figure out which features to keep
5. Delete code you don't need
6. Realize something broke
7. Manually wire up your business logic
8. ...

**What if you could just type one command?**

```
/saas-forge:saas A project management tool for freelancers
```

saas-forge brainstorms the idea with you, scaffolds the project, removes what you don't need, generates your data models, features, and pages. Ready to `npm run dev`.

---

## Features

### `/saas-forge:saas` — Idea to codebase in one command

```
/saas-forge:saas A project management tool for freelancers
/saas-forge:saas An invoicing app for small agencies --yes
```

**Phase 1: Brainstorming** — Refines your idea interactively:
- Clarifies the concept, target users, value proposition
- Designs the data model (Drizzle schemas)
- Maps user flows and pages
- Presents the boilerplate features with keep/remove recommendations

**Phase 2: Scaffolding** — Dispatches the builder agent to:
- Clone and initialize from `nmarijane/saas-boilerplate`
- Remove unused features cleanly (billing, onboarding, i18n, etc.)
- Generate business models, queries, actions, components
- Wire up routes, navigation, and seed data
- Verify TypeScript and lint pass

**Phase 3: Summary** — Hands you the keys:
- What was created, kept, and removed
- How to start (`npm install && npm run dev`)
- Environment variables to configure
- Recommended next steps

---

## What's in the Boilerplate

The scaffolder builds on [`nmarijane/saas-boilerplate`](https://github.com/nmarijane/saas-boilerplate), which includes:

| Always included | Optional (keep or remove) |
|----------------|--------------------------|
| Auth (Better Auth — self-hosted, organizations, RBAC) | Billing (Stripe) |
| Email (React Email + Nodemailer) | Onboarding wizard |
| Dashboard (base layout + navigation) | Notifications in-app |
| | Feedback widget |
| | File upload (S3) |
| | Admin panel |
| | i18n (next-intl) |

You don't need to know which features exist — the brainstorming phase presents each one with a recommendation tailored to your project.

---

## Quick Start

### Option A: Install via skills.sh (recommended)

```bash
npx skills add nmarijane/saas-forge
```

### Option B: Install as Claude Code plugin

```bash
git clone https://github.com/nmarijane/saas-forge.git
claude --plugin-dir ./saas-forge
```

### Start using it

```
/saas-forge:saas Your SaaS idea here
```

---

## Architecture

saas-forge is a **pure-skills plugin** — every file is Markdown.

```
saas-forge/
  .claude-plugin/plugin.json       # Plugin manifest
  skills/
    saas/SKILL.md                  # Brainstorm + scaffold workflow
  agents/
    saas-builder.md                # Subagent: project scaffolding
```

No TypeScript. No build step. No `node_modules`. Just Markdown files that tell Claude what to do.

**Want to add a feature?** Edit a `.md` file and submit a PR.

---

## Tech Stack (generated projects)

- **Framework:** Next.js 15 (App Router, Server Components)
- **Database:** PostgreSQL + Drizzle ORM
- **Auth:** Better Auth (self-hosted, organizations, RBAC)
- **UI:** shadcn/ui + Tailwind CSS
- **Email:** React Email + Nodemailer
- **Payments:** Stripe (optional)
- **Validation:** Zod
- **Forms:** react-hook-form

---

## Contributing

1. **Fork** the repository
2. **Create** a feature branch
3. **Edit** the relevant `SKILL.md` or agent file
4. **Test** with `claude --plugin-dir ./saas-forge`
5. **Submit** a pull request

### Ideas for contributions

- Add more boilerplate features (analytics, changelog, docs site)
- Support alternative stacks (Prisma, Lucia Auth, etc.)
- Add a `/saas-forge:feature` command to add features to existing projects
- Post-scaffold health checks

---

## FAQ

**Does saas-forge work with existing projects?**
Not yet — it scaffolds new projects from scratch. A `/saas-forge:feature` command to add features to existing apps is on the roadmap.

**What database does it use?**
PostgreSQL with Drizzle ORM by default. The scaffolded schema is generated from your idea during brainstorming.

**Is auth self-hosted?**
Yes. saas-forge uses [Better Auth](https://www.better-auth.com/), which runs on your own infrastructure — no third-party auth vendor dependency.

**Can I use it without Claude Code?**
saas-forge is built as a Claude Code plugin and requires Claude Code to run. There is no standalone CLI.

**How is it different from just cloning saas-boilerplate?**
Cloning gives you all features and you decide what to cut. saas-forge brainstorms your idea first, then scaffolds only what you need — including your business models, pages, and routes — already wired up.

---

## License

[MIT](LICENSE) — do whatever you want with it.
