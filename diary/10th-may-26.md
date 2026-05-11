# 2026-05-10

## What I Did
**Ollama setup and model exploration**
- Explored different local Ollama models to run tasks without hitting the Claude API
- Added Ollama models into Bot as a hybrid setup alongside Claude Haiku
- Configured model routing: Ollama handles routine tasks, Claude Haiku handles complex ones

**Accidentally broke the bot**
- Tried removing all Claude models to run fully on Ollama and cut API costs to zero
- Bot stopped working entirely — could not perform any tasks
- Root cause: Ollama requires `OLLAMA_API_KEY` to be registered as a provider in OpenClaw, which wasn't set
- Added Claude Haiku back as primary model — bot recovered immediately
- Lesson: always keep at least one working fallback model before removing the primary

**Google Tasks vs Google Calendar**
- Realised all my planned tasks live in Google Tasks, not Google Calendar Events
- Google Calendar and Google Tasks are separate APIs — Zapier MCP handles them differently
- Pivoted: connected Google Tasks via Zapier MCP instead of Google Calendar
- Fetching tasks for the day worked on the first test

**Morning briefing cron job**
- Configured a cron job to send a compiled morning briefing at 9am daily (Melbourne time)
- Briefing includes: tasks due today with time slots + emails needing a reply
- Email filtering working correctly — only surfaces emails that need attention, skips promotionals and newsletters
- Tasks section fetching correctly but time slots not showing up despite being set in Google Tasks
- Spent time refining the job message prompt to be more concise and accurate

## What I Learned
- Running fully on local LLMs sounds great in theory but OpenClaw still needs a cloud model registered as a fallback to function reliably
- Google Tasks and Google Calendar are completely separate — don't assume they sync
- Zapier MCP tool selection matters — need the right actions enabled (List Tasks, Get Task) to pull time data correctly
- Prompt engineering for cron jobs is iterative — the more specific the instruction, the better the output

## Challenges
- Bot completely broke when all Claude models were removed — had to diagnose through logs
- Time slots set in Google Tasks not appearing in the morning briefing output despite being configured
- Cron job timed out at 45 seconds — had to manually edit `jobs.json` to increase to 120 seconds
- CLI kept throwing a scope upgrade pending error — had to manually edit `paired.json` and clear `pending.json` to fix

## Plan for Next Session
- Review the first real 9am morning briefing when it sends
- Fix the time slot display issue in the tasks section
- Continue refining the briefing format based on what the actual output looks like
- Start planning the news digest feature (Phase 5)