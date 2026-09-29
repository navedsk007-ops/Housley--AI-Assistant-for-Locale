# Housley — AI Leasing Assistant

**An AI leasing assistant for rental buildings. It answers prospects' questions 24/7, captures their details and books tours.**

Housley answers rental inquiries instantly, at any hour. Most prospects search in the evenings and on weekends, when leasing offices are closed. Housley answers questions about pricing, availability, pets, amenities and location. It captures the prospect's name, email, phone and unit type, books a tour on the spot, and emails the leasing team right away. It only repeats facts it has been given and never makes up policies.

This demo was built for **Locale**, a 243-unit rental tower at Century City in Surrey, BC.

🔗 **Live demo:** https://swifttech-ai-implementation.netlify.app

---

## Features

- **Instant, 24/7 replies.** Natural conversation powered by Claude (Anthropic).
- **Grounded answers.** It only uses the building facts it is given. If it doesn't know something, it says it will check with the leasing team.
- **Lead capture.** Name, email, phone and preferred unit type.
- **Tour booking.** Prospects pick a time slot inside the chat.
- **Instant email alerts.** The team is emailed when a chat starts, a lead is captured, or a tour is booked (via Resend).
- **Backup record.** Every lead is also saved in Netlify Forms.
- **ROI calculator.** Estimates the value of recovering missed after-hours leads.
- **No build step.** Plain HTML, CSS and JavaScript, plus two serverless functions.

## Tech stack

| Layer | Tool |
|---|---|
| Frontend | HTML, CSS, vanilla JavaScript |
| AI | Claude via the Anthropic Messages API |
| Backend | Netlify Functions (Node.js) |
| Email alerts | Resend |
| Hosting | Netlify |

## Project structure

```
.
├── index.html                  # Page, chat widget and ROI calculator
├── locale-hero.jpg             # Hero image
├── page-bg.jpg                 # Page background
├── netlify.toml                # Netlify config (publish dir, functions dir)
├── netlify/
│   └── functions/
│       ├── chat.mjs            # POST /api/chat   → sends the conversation to Claude
│       └── notify.mjs          # POST /api/notify → emails the leasing team
├── .env.example                # Template for environment variables
└── .gitignore
```

## Environment variables

API keys and personal details are **not** stored in this repo. Set them in Netlify under **Project configuration → Environment variables**:

| Variable | Required | Purpose |
|---|---|---|
| `ANTHROPIC_API_KEY` | Yes | Claude API key |
| `RESEND_API_KEY` | Yes | Resend API key for email alerts |
| `NOTIFY_EMAIL` | Yes | Inbox that receives chat, lead and booking alerts |
| `ANTHROPIC_WORKSPACE_ID` | No | Anthropic workspace to bill usage to |

## Deploy to Netlify

1. Fork or clone this repo.
2. In Netlify, choose **Add new project → Import an existing project → GitHub**, then select this repo.
3. Leave the **build command** empty and set the **publish directory** to `.`.
4. Add the environment variables above.
5. Deploy. Every push to `main` redeploys automatically.

## Run locally

```bash
cp .env.example .env    # add your own keys
npx netlify dev         # starts the site + functions at http://localhost:8888
```

## Customizing for another building

All building details live in the `SYSTEM_PROMPT` in `index.html`: address, amenities, available units, pricing and tone. Edit that text, the page headings and the images to adapt Housley to any rental property. No retraining is needed.

---

## About

Built by **Swift Tech Support**, which provides custom AI assistants for property managers and local businesses.

📧 navid@swifttechsupport.ca · 📞 778-244-4356

> Note: the unit availability and pricing in this demo are sample data.
