# 🦞 Bot Roadmap — Aish's Personal AI Assistant

---

## Phase 1 — Setup ✅
- [x] Install Node.js (v24)
- [x] Install OpenClaw
- [x] Connect Telegram
- [x] Set up Ollama
- [x] Pull local models (llama3.1:8b, qwen3.5:9b)
- [x] Configure hybrid model (Ollama + Claude Haiku)
- [x] Write SOUL.md (Bot's personality + instructions)

---

## Phase 2 — Integrations ✅
- [x] Get Anthropic API key → connect to Bot
- [x] Set up Zapier MCP → migrated to Composio MCP
- [x] Connect Gmail via Composio MCP
- [x] Connect Google Calendar via Composio MCP
- [x] Connect Google Tasks via Composio MCP
- [x] Test Bot reading calendar in Telegram
- [x] Test Bot reading emails in Telegram

---

## Phase 3 — Morning Briefing ✅
- [x] Write SOUL.md (Bot's personality + instructions)
- [x] Configure daily 9am cron schedule in OpenClaw
- [x] Set morning briefing prompt (calendar + email + news)
- [x] Test first full morning briefing in Telegram
- [x] Refine format — calendar, emails, and news digest working

---

## Phase 4 — Two-Way Control
- [x] Test modifying calendar via Telegram
- [x] Test creating tasks via Telegram (via Composio)
- [ ] Test email drafting via Telegram ("draft a reply to Sarah")
- [ ] Test on-demand queries ("any urgent emails?")

---

## Phase 5 — News Digest ✅
- [x] Enable OpenClaw web search
- [x] Configure news sources (tech, cybersecurity, AI)
- [x] Add news section to morning briefing
- [x] Test and refine news summaries

---

## Phase 6 — Job Search
- [x] Feed Bot all three CV versions (cybersecurity, data/AI, web dev)
- [x] Feed Bot matching cover letter templates per track
- [x] Set job preferences (485 visa, Melbourne, entry level, all domains)
- [x] Configure daily 10am job search (Seek, Indeed, Google Jobs)
- [x] Set up LinkedIn/Seek/Indeed job alert emails → Gmail → Bot reads them
- [ ] Test job digest when it fires at 10am
- [x] Set up Google Sheet application tracker via Composio
- [ ] Test logging applications ("apply to job 1")
- [ ] Test cover letter drafting end to end
- [ ] Test interview prep prompt

---

## Phase 7 — Pattern Learning
- [ ] Manually populate calendar for 2–3 weeks
- [ ] Ask Bot to analyse calendar patterns
- [ ] Test weekly plan suggestions every Sunday night
- [ ] Refine how assertive Bot is (suggest vs auto-book)

---

## Phase 8 — Polish
- [ ] Revisit email monitor — explore webhook-based trigger instead of polling
- [ ] Fix weather section appearing in morning briefing
- [ ] Add cert/study tracker (Security+, AWS, etc.)
- [ ] Add visa-friendly company watchlist
- [ ] Tighten SOUL.md to minimise tokens
- [ ] Set context window cap to keep costs low
- [ ] Enable prompt caching