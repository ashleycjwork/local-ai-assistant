# 2026-05-18

## What I Did

**Email monitor failed — Zapier free trial ended**

The email-monitor cron job stopped working entirely. Root cause: Zapier's 14-day free trial expired and the account reverted to the free tier — which only includes 100 tasks per month, with each MCP tool call counting as 2 tasks. The morning briefing and email monitor combined were consuming ~675 tasks per month — well beyond the free limit of 50 effective MCP calls.

Decided to migrate everything from Zapier to Composio rather than pay for Zapier.

---

**Migrated everything from Zapier to Composio**

Compared free tiers:

| | Zapier | Composio |
|---|---|---|
| Free monthly limit | 100 tasks (50 MCP calls) | 20,000 tool calls |
| Estimated monthly usage | ~675 tasks needed | ~1,350 calls needed |
| Verdict | Unusable on free | 6.75% of free limit used |

Migration steps completed:
- Connected Gmail to Composio and authenticated with Google account
- Connected Google Calendar to Composio and authenticated
- Google Tasks already connected from earlier session
- Updated `openclaw.json` to replace Zapier MCP URL with Composio MCP URL
- Updated both cron jobs in `jobs.json` to use `mcpServers: ["composio"]` instead of `["zapier"]`
- Restarted gateway
- Tested all three connections via Telegram — calendar, Gmail, and Google Tasks all confirmed working

Composio is now the sole MCP provider for all integrations.

---

**Set up job search use case**

Fed all three CV versions into Bot memory, one per career track:
- CV 1 — Cybersecurity & Networking
- CV 2 — Data & AI
- CV 3 — Web Development & Tech Consulting

Fed matching cover letter templates for each track.

Configured routing rules in SOUL.md — Bot automatically selects the matching CV and cover letter template based on the role type. If a role spans multiple tracks, Bot asks which CV to use.

Sent all 8 job search setup prompts to Bot:

1. CV profiles stored in memory per track
2. Job preferences set — 485 visa, Melbourne, entry level, graduate, junior, casual, part-time, contract across all target domains
3. Daily 10am job search configured — searches Seek, Indeed, and Google Jobs across all target domains, filters for visa-friendly and entry-level only, posts in last 24 hours, max 5 results per day
4. LinkedIn/Seek/Indeed job alert emails configured — Bot extracts listings from job alert emails during email monitor checks and adds to daily digest, no duplicates
5. Google Sheet application tracker set up — columns: Date Applied, Company, Role, Source, Status, Visa Friendly, Notes. Auto-logs when "apply" is said
6. Cover letter drafting configured — fetches job description, tailors professional summary, shows for approval, drafts full cover letter addressing 485 visa proactively
7. Interview prep configured — searches company news, tech stack, culture, generates 10 Q&A based on CV
8. SOUL.md updated — always prioritise visa-friendly roles, never suggest citizenship-required roles, proactively check visa sponsorship, track all applications in Google Sheet

**Email monitor put on halt**

Disabled the email-monitor cron job indefinitely. Three reasons:

1. **Inconsistent execution** — some runs worked correctly, most failed or lost Zapier/Composio tool context entirely
2. **Poor filtering** — even on successful runs, promotional emails were still appearing in the priority alerts despite explicit exclusion rules
3. **API cost** — running every 30 minutes between 8am–10pm means 28 Claude API calls per day purely for email monitoring, consuming Anthropic credits even when no priority emails exist

Decision: pause email monitoring for now and revisit with a better approach later — possibly a webhook-based trigger instead of polling, or a dedicated script outside of OpenClaw.

---

## What I Learned

- Polling-based email monitoring every 30 minutes is expensive and unreliable — webhook triggers would be far more efficient
- Zapier's free tier is completely unworkable for MCP-based agent workflows — 50 effective MCP calls per month runs out in 2 days at normal usage
- Composio's 20,000 free tool calls is effectively unlimited for a personal AI agent at this scale
- Having three CV tracks requires clear routing rules — without explicit instructions Bot would default to one CV for everything
- Cover letter templates need to be stored per track, not as a single generic template
- Proactively addressing the 485 visa in cover letters is better than leaving it to the employer to ask

## Challenges

- Zapier expiry was unexpected — no warning before the email monitor started failing
- Migration required updating both `openclaw.json` and `jobs.json` — easy to miss one
- Storing multiple CV versions in Bot memory requires clear labelling to prevent mixing

## Plan for Next Session

- Test the 10am job search digest when it fires tomorrow
- Verify application tracker logs correctly when "apply" is used
- Test cover letter drafting end to end with a real job listing
- Test interview prep prompt with a real company
- Monitor morning briefing at 9am to confirm Composio connections are stable