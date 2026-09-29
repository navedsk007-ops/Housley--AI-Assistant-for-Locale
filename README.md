# Housley — AI Leasing Assistant (Locale demo)

A live demo of **Housley**, an AI leasing assistant built for Locale, a rental building in Surrey, BC. Prospects can ask about pricing, availability, pets and amenities, share their details, and book a tour. The leasing team gets an email alert right away.

Built by [Swift Tech Support](mailto:navid@swifttechsupport.ca).

## How it works

- `index.html` — the page and chat widget (plain HTML/CSS/JS)
- `netlify/functions/chat.mjs` — `/api/chat`, sends the conversation to Claude (Anthropic API)
- `netlify/functions/notify.mjs` — `/api/notify`, emails new chats, leads and bookings via Resend
- `netlify.toml` — Netlify config (no build step)

## Environment variables

Set these in Netlify under **Project configuration → Environment variables**. They are **not** in this repo.

| Variable | Required | Purpose |
|---|---|---|
| `ANTHROPIC_API_KEY` | Yes | Claude API key |
| `RESEND_API_KEY` | Yes | Resend API key for email alerts |
| `NOTIFY_EMAIL` | Yes | Inbox that receives lead and booking alerts |
| `ANTHROPIC_WORKSPACE_ID` | No | Anthropic workspace to bill usage to |

## Deploy

Link this repo to a Netlify project. Leave the build command empty and set the publish directory to `.`. Every push to `main` redeploys.

## Local development

```bash
cp .env.example .env   # fill in your own keys
npx netlify dev
```
