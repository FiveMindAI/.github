<p align="center">
  <img src="https://fivemind.io/fivemind-logo.svg" alt="FiveMind" width="80" />
</p>

<h1 align="center">FiveMind</h1>

<p align="center">
  <strong>AI-powered development platform for FiveM</strong>
</p>

<p align="center">
  <a href="https://fivemind.io">Website</a> &middot;
  <a href="https://discord.gg/fivemind">Discord</a> &middot;
  <a href="https://docs.fivemind.io">Docs</a>
</p>

---

FiveMind gives FiveM developers AI tools that understand their codebase, their server, and their community. Write scripts, manage servers, and automate Discord — all from one platform.

## Tools

### Script Studio

AI-assisted code generation purpose-built for FiveM. Describe what you want in plain English and get production-ready Lua resources with client/server separation, NUI interfaces, database queries, and framework integration out of the box.

- **Full resource scaffolding** — Generates complete resources with `fxmanifest.lua`, client, server, shared modules, and NUI (React + Tailwind) when needed
- **Context-aware editing** — The AI reads your existing files, understands your project structure, and makes targeted edits without breaking what already works
- **Framework support** — Native understanding of ox_lib, ESX, QBCore, VORP, and standalone patterns
- **Live preview** — See NUI changes in a browser-based sandbox before deploying
- **One-click deploy** — Push finished resources directly to your connected FiveM server

### Server Agent

A persistent AI agent that connects to your live FiveM server through a lightweight desktop client. It sees what you see — console output, database state, running resources — and can act on it.

- **Real-time console** — Stream server output directly in the browser with search and filtering
- **Database access** — Query and inspect your MySQL database, understand schema relationships, and debug data issues
- **Resource management** — Restart resources, execute server commands, and manage files on the live server
- **Intelligent debugging** — Describe a bug, and the agent reads your server logs, traces the relevant code, and suggests or applies fixes
- **RPC bridge** — Secure WebSocket tunnel between the platform and your server — no ports to open, no config to manage

### Discord Agent

An AI-powered Discord bot that knows your server, your rules, and your community. It handles the repetitive parts of community management so your staff can focus on what matters.

- **Knowledge base** — Feed it your server rules, changelogs, and FAQs. It answers player questions accurately, citing your own docs
- **Ticket assistance** — AI-suggested responses for support tickets based on conversation context and your knowledge base
- **Custom personality** — Configure tone, response style, and boundaries to match your community's vibe
- **Guild-aware** — Understands your Discord roles, channels, and server-specific context

## Architecture

```
Browser ── WebSocket ──> Express API ──> AI Pipeline ──> Anthropic Claude
                              |               |
                              |-- MySQL       |-- Haiku (fast) -> Sonnet (complex)
                              |-- Stripe      |-- Per-tool agent configs
                              '-- Discord.js  '-- Streaming + incremental credits

FiveM Server ── Agent App ── WebSocket ──> Express API ──> Server Tools (RPC)
```

**AI Pipeline** — Requests start on Claude Haiku for speed and cost efficiency. When the task requires code generation or complex reasoning, the pipeline seamlessly escalates to Claude Sonnet with full context preserved. Credits are charged incrementally as tokens accrue — no surprise bills, and crashes never lose billing state.

## Tech Stack

| Layer | Stack |
|-------|-------|
| **Frontend** | React 19, Vite 6, Mantine v8, Framer Motion, Zustand, TanStack Query |
| **Backend** | Express, TypeScript, MySQL, WebSocket |
| **AI** | Anthropic Claude (Haiku + Sonnet), OMA agent framework |
| **Desktop** | Electron, auto-updater via GitHub Releases |
| **Payments** | Stripe (subscriptions + credit packs) |
| **Infrastructure** | Caddy, PM2, Windows Server |

## Getting Started

```bash
# Server
cd server && npm install && npm run dev

# Web (separate terminal)
cd web && npm install && npm run dev
```

The web dev server runs on `:5180` and the API on `:3003`.

## License

Proprietary. All rights reserved.
