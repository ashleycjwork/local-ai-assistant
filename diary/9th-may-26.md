# 2026-05-09

## What I Did
Set up OpenClaw on my Mac from scratch. Got the core agent running and connected to a messaging channel, then spent the rest of the session figuring out the right configuration for my use case.

**OpenClaw setup**
- Installed OpenClaw and completed the onboarding process
- Set Claude Opus as the default model to start

**Model cost reality check**
- Realised Opus was burning through tokens fast, nearly $2 in one session just from setup and testing
- Switched to Claude Haiku as the default model, which handles my use case well at a fraction of the cost
- First real lesson: always start with the smallest model that gets the job done

**Channel switch — WhatsApp → Telegram**
- Initially connected WhatsApp as the messaging channel
- Realised my existing WhatsApp "message myself" chat is already used for storing documents and grocery lists — mixing bot messages in there would be messy
- Switched to Telegram for a cleaner, dedicated channel with no history baggage

**Zapier MCP + Gmail**
- Connected Zapier MCP as the integration layer
- Connected Gmail through Zapier
- Asked Bot to fetch my top 5 emails — worked on the first try
- Confirmed the integration pipeline: OpenClaw → Zapier MCP → Gmail → Telegram

## What I Learned
- Opus is overkill for routine tasks like email fetching and summarisation — Haiku handles it fine
- Keeping the bot channel separate from personal use is worth the extra setup step
- Zapier MCP abstracts away a lot of OAuth complexity — much easier than wiring up Google APIs directly
- Local LLMs via Ollama could cut costs to near zero for most daily tasks — worth exploring

## Challenges
- Caught off guard by how quickly Opus token costs added up during casual testing
- WhatsApp removal had a quirk where credentials persisted after the remove command, had to manually delete credential files

## Plan for Next Session
- Set up Ollama and configure a hybrid local/cloud model routing
- Connect Google Tasks via Zapier MCP
- Start building the morning briefing cron job