# 🦞 Bot Roadmap — Aish's Personal AI Assistant

---

## Phase 1 — Foundation
- [x] Install Node.js (v24)
- [x] Install OpenClaw
- [x] Connect Telegram
- [x] Set up Ollama
- [x] Pull local models (llama3.1:8b, qwen3.5:9b)
- [x] Configure hybrid model (Ollama + Claude Haiku)

---

## Phase 2 — Integrations
- [x] Get Anthropic API key → connect to Bot
- [x] Set up Zapier MCP account
- [x] Connect Gmail via Zapier MCP
- [ ] Connect Google Calendar via Zapier MCP
- [ ] Test Bot reading your calendar in Telegram
- [x] Test Bot reading your emails in Telegram

---

## Phase 3 — Morning Briefing
- [ ] Write your SOUL.md (Bot's personality + instructions)
- [ ] Configure daily 7am cron schedule in OpenClaw
- [ ] Set morning briefing prompt (calendar + email + news)
- [ ] Test first full morning briefing in Telegram
- [ ] Refine format until you're happy with it

---

## Phase 4 — Two-Way Control
- [ ] Test modifying calendar via Telegram ("move my 3pm to 5pm")
- [ ] Test email drafting via Telegram ("draft a reply to Sarah")
- [ ] Test on-demand queries ("any urgent emails?")

---

## Phase 5 — News Digest
- [ ] Enable OpenClaw web search
- [ ] Configure news sources (tech, cybersecurity, AI)
- [ ] Add news section to morning briefing prompt
- [ ] Test and refine news summaries

---

## Phase 6 — Job Search
- [ ] Feed Bot your CV once (paste into Telegram)
- [ ] Set your job preferences (domains, visa status, experience level)
- [ ] Configure daily job search (Seek, Indeed, Google Jobs)
- [ ] Set up LinkedIn job alert emails → Gmail → Bot reads them
- [ ] Test job digest in morning briefing
- [ ] Set up Google Sheet via Zapier for application tracker
- [ ] Test logging applications ("apply to job 1")
- [ ] Test cover letter drafting ("draft cover letter for job 2")

---

## Phase 7 — Pattern Learning
- [ ] Manually populate calendar for 2–3 weeks
- [ ] Ask Bot to analyse your calendar patterns
- [ ] Test weekly plan suggestions every Sunday night
- [ ] Refine how assertive Bot is (suggest vs auto-book)

---

## Phase 8 — Polish
- [ ] Add cert/study tracker (Security+, AWS, etc.)
- [ ] Add visa-friendly company watchlist
- [ ] Tighten SOUL.md to minimise tokens
- [ ] Set context window cap to keep costs low
- [ ] Enable prompt caching
