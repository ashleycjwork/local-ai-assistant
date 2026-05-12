# 2026-05-12

## What I Did

**Morning briefing received — first scheduled run**
The 9am briefing fired but had several issues:
- Tasks section missing the 11am job application slot despite it being in Google Calendar
- Bot discovered it only had access to the primary calendar — missing work and personal calendars
- Fixed by explicitly telling Bot to query all three calendars: ashleycjwork@gmail.com (work), personal, and Holidays in Australia

**Google Calendar vs Google Tasks — final decision**
Confirmed that Google Tasks API fundamentally does not support due times — it's not a Zapier limitation, it's a Google API limitation. Composio was tested and returned the same result. Final architecture settled:

- Google Calendar → all timed events and tasks with specific times → morning briefing
- Google Tasks → floating to-dos with no time requirement → managed via Composio
- Removed Google Tasks from Zapier MCP, kept Composio for task creation

**Two-way calendar control tested**
- Successfully created a Google Calendar event via Telegram
- Successfully moved an event to 6:30 PM – 8:30 PM Melbourne time with 2-hour duration via Telegram
- Discovered Bot was confusing Google Tasks and Google Calendar — updated SOUL.md to route correctly:
  - Anything with a specific time → Google Calendar via Zapier
  - Anything without a time → Google Tasks via Composio

**Email monitor cron job set up**
- Created a new cron job called `email-monitor` running every 30 minutes between 8am–10pm Melbourne time
- Monitors Gmail for priority emails: job-related (interviews, offers, application updates) and urgent replies
- Silently ignores: promotional, newsletters, social media, automated emails
- Sends Telegram alert in format: sender, subject, one-line summary, reply needed yes/no
- If yes replied, Bot drafts a professional reply for review before sending
- Tested with a fake interview invitation email — still pending confirmation from next cycle

**News digest added to morning briefing**
- Enabled web search on Bot — set to proactively search without asking permission
- Added STEP 3 to morning briefing prompt covering cybersecurity, AI, and tech news
- Max 3 headlines per category, urgent items flagged with ⚠️
- Tested standalone news fetch — good quality results returned

**Morning briefing format issues**
- Bot kept adding weather section despite it not being in the prompt
- Tried multiple fixes: stronger opening instructions, sessionTarget switching between isolated and continue
- Calendar, emails, and news digest all working correctly — weather removal still pending
- Settled on moving forward despite the weather section appearing

**Cron job prompt engineering**
- Continued iterating on jobs.json message field to get Bot to follow exact format
- Key learning: isolated session targets don't carry MCP context, continue session targets carry too much conversational context and Bot goes rogue
- Added `mcpServers: ["zapier", "composio"]` explicitly to payload
- Increased timeout to 180 seconds to handle web search step

## What I Learned
- Google Tasks API does not support due times at all — confirmed across both Zapier and Composio
- Bot in isolated cron sessions tends to default to its own briefing format unless the prompt is extremely explicit
- sessionTarget "continue" causes Bot to carry conversational baggage and override instructions
- Explicit MCP server declaration in cron payload is essential for tool availability in scheduled runs
- Two-way calendar control works well via natural language — moving and creating events is seamless
- Email monitoring via 30-minute polling window has a gap — emails arriving just before a scan window can be missed

## Challenges
- Bot persistently adding weather section despite explicit instructions not to
- Email monitor missed the fake interview email because it arrived outside the 30-minute scan window
- sessionTarget tuning — isolated loses tools, continue loses prompt discipline
- Zapier Google Tasks confirmed to strip due times — had to fully migrate timed items to Google Calendar

## Plan for Next Session
- Confirm email monitor picks up the resent fake email in next cycle
- Start Phase 6: job search feature
- Feed CV into Bot memory
- Configure daily job search across Seek, Indeed, and Google Jobs filtered for 485 visa-friendly entry-level roles
- Begin modifying CV before feeding it to Bot