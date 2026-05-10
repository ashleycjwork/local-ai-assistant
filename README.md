# ai agent dev diary

a personal build log documenting the development of an always-on AI agent and the self-directed learning journey behind it.

---

## the problem

as an international student in melbourne balancing studies, job hunting, and personal growth, i kept running into the same friction points every single day:
- **calendar planning was manual** — i'd open Google Calendar, stare at the week, and try to mentally piece together a plan with no structure or prompts
- **job hunting was exhausting** — filtering through Seek, LinkedIn Jobs, and Indeed manually, checking visa requirements one by one, wasting hours on a process that could be automated
- **tech news was hit or miss** — unless i actively went looking, i'd miss developments in cybersecurity, AI, and the broader tech landscape entirely
- **everything lived in separate tabs** — no single place to get a clear picture of my day, my applications, and what was happening in the industry

i was spending time on overhead instead of the things that actually matter: learning, applying, and living.

---

## the solution

an always-on personal AI agent that runs locally on my Mac and communicates through Telegram. instead of opening five different apps every morning, i get one structured briefing and can make changes conversationally throughout the day.

it handles:

- daily calendar briefing and schedule planning
- email triage and drafting - surfaces what needs a reply and what can wait
- job search across Seek, Indeed, and Google Jobs. filtered automatically for 485 visa-friendly, entry-level roles across cybersecurity, data, AI, networking, and web development
- cybersecurity, AI, and tech news digest — curated daily so i stay across the industry without actively seeking it out
- weekly pattern-based schedule planning — after enough data, suggests how to structure my week based on my own habits

the goal is simple: spend less time on life admin, and more time on the things that actually move the needle: studying, applying, and living.

---

## what this project is really about

this is as much a learning project as it is a productivity tool.

i built this to teach myself how modern AI tooling actually works in practice, not through a course or a tutorial, but by picking a real problem and figuring out how to solve it. along the way i've been learning how to configure local LLMs, work with cloud APIs, manage integrations, think about cost optimisation, and make architectural decisions.

every tool in this stack was new to me when I started. the dev diary exists to document that process honestly: what worked, what didn't, and what i'd do differently.

---

## tech stack

| layer | tool |
|---|---|
| agent framework | OpenClaw |
| cloud llm | Claude Haiku — Anthropic API |
| local llm | Ollama — llama3.1:8b and qwen3.5:9b |
| integrations | Gmail and Google Calendar via Zapier MCP |
| channel | Telegram |
| version control | Git and GitHub |

the architecture uses a hybrid local/cloud model routing approach - routine tasks like summarisation run on Ollama at zero cost, while complex tasks like cover letter drafting and weekly planning escalate to Claude Haiku. this keeps running costs under $0.20/month.

---

## status

🚧 active development — see the [roadmap](./roadmap.md) for what's planned and the [diary](./diary/) for session-by-session progress.
