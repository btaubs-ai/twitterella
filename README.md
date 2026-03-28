# Twitterella — Capability Summary

A social media growth operator agent for OpenClaw. Built for founders, coaches, and personal brands who want a strategic, opinionated assistant that handles research, content shaping, audience growth, and posting workflows.

---

## What Twitterella Does

### 1. Content Pipeline
- Takes raw inputs (voice notes, chat ideas, docs, links, stories) and turns them into:
  - X/Twitter threads (tweet storms)
  - Instagram text carousels (rendered as images)
  - Single tweets
  - Reply drafts
  - Quote-tweet angles
- Maintains editorial standards for hooks, structure, length, style, and CTA placement
- Proofreads, cites sources, and formats for platform-specific best practices
- Manages a content queue in Google Docs

### 2. Audience Growth Engine
- Researches and builds target follow lists by segment:
  - warm contacts
  - founder/exec coaches
  - adjacent thinkers (AI, health, science, climate)
  - podcast guests
  - audience neighbors
- Prepares follow / reply / reconnect queues
- Manual-first approach — no spammy automation
- Tracks growth metrics (follows, follow-backs, engagement)

### 3. Research & Intelligence
- Deep research on content landscape, competitors, and trending topics
- Identifies whitespace and differentiated angles
- Produces research briefs with ranked follow lists and content ideas
- Monitors what's saturated vs. what's ownable
- Can spawn subagents for parallel research tasks

### 4. Google Workspace Integration
- Creates, reads, edits, and shares Google Docs and Sheets via `gog` CLI
- Manages content drafts, audience maps, and dashboards in Google Drive
- Shares documents with specified accounts

### 5. Carousel / Visual Content Generation
- Generates Instagram carousel slides as HTML → rendered to PNG via Playwright
- Matches brand color palette (extracted from website CSS)
- 1080×1080px slides with custom typography, layout, and branding

### 6. Staging App / Dashboard
- Built and deployed a lightweight Node.js staging prototype on Railway
- Operator dashboard showing: this week, queues, approvals, metrics, operating rules
- Auth-gated with `AUTH_TOKEN`
- JSON API at `/api/dashboard`

### 7. Cross-Agent Communication
- Can send/receive messages to other OpenClaw agents (e.g., Richaird Feynman / @F)
- Can switch models for other agents' sessions (e.g., fix rate-limit errors)
- Can coordinate work across agents

### 8. Process & Project Management
- Follows gstack process (CEO review → Eng review → PR → TR → implement → review → ship → QA)
- Creates and manages PRs and TRs in shared project docs
- Commits and pushes to git
- Deploys apps via Railway CLI

---

## Personality & Voice

- Light-hearted, warm, a little playful
- Brief and direct by default
- Noticeably sharp — aims for ~2 standard deviations smarter
- Low fluff — gets to the point
- Kind but not sycophantic
- "Fairy godmother of social media" energy
- Practical magic beats empty sparkle

---

## Technical Setup

### Prerequisites
- OpenClaw instance with multi-agent support
- Telegram bot token (or other channel)
- Google Workspace OAuth credentials (for `gog` CLI)
- OpenAI API key (for TTS, image generation, transcription)
- Anthropic API key (for Opus/Sonnet models)

### Agent Configuration

#### Model Routing
- **Chat:** Sonnet (fast, cost-effective)
- **Deep work / coding / research:** Opus 4.6

#### Core Files
| File | Purpose |
|---|---|
| `SOUL.md` | Personality, tone, style |
| `IDENTITY.md` | Name, role, core traits |
| `USER.md` | User preferences |
| `AGENTS.md` | Operating rules, engineering standards |
| `TOOLS.md` | Environment-specific notes (TTS voice, etc.) |

#### Google Integration
- `gog auth credentials /path/to/client_secret.json`
- `gog auth add your-agent@domain.com --services drive,docs,sheets`
- OAuth client type: **Desktop app**

#### Telegram
- Separate bot token per agent
- Allowlist configured in `credentials/telegram-<agent>-allowFrom.json`
- Group chat support via group ID allowlisting

#### TTS
- Preferred voice: `nova` (female, warm, clear)
- Configured in `openclaw.json` under `messages.tts.openai.voice`
- Per-agent TTS voice may require feature support from OpenClaw

### Shared Engineering Standards
Symlink from main agent workspace:
- `shared/engineering-rules.md` — change policy, coding style, safety
- `shared/workflow.md` — gstack process, PR/TR flow
- `protocols/` — engineering discipline, pre-code, pre-TR, code quality

---

## Key Operating Principles

1. **No posting without explicit approval** — drafts are autonomous, publishing is gated
2. **Manual-first audience growth** — no bulk automation or black-hat tactics
3. **Research before opinion** — use web search, don't hallucinate
4. **Follow gstack for significant work** — PR → TR → approve → implement → review
5. **Brief, decision-ready outputs** — not process documentation for its own sake
6. **Track what works** — metrics, segment performance, topic resonance

---

## Project Structure

### Twitter Growth Operating System (PR-053)
Master system with subsystems:
- **PR-048:** Audience Growth Engine (TOFU)
- **PR-049:** Voice Notes → Content Pipeline
- **PR-050:** Editorial Standards
- **PR-051:** Trend & Audience Intelligence
- **PR-052:** Twitterella Social Marketer Operating Prompt
- **PR-054:** Operating Cadence & Automation Architecture

### Staging App
- `apps/twitter-growth-os-staging/`
- Deployed on Railway as a separate service
- Auth-gated Node.js dashboard

---

## What You'd Need to Recreate This

1. Set up an OpenClaw agent with its own workspace
2. Create the core `.md` files (SOUL, IDENTITY, USER, AGENTS, TOOLS)
3. Connect a Telegram bot (or other channel)
4. Set up Google OAuth for Docs/Sheets/Drive access
5. Symlink shared engineering standards if using gstack
6. Configure model routing (Sonnet for chat, Opus for deep work)
7. Optionally deploy a staging dashboard app on Railway
8. Start feeding it content ideas and audience targets

---

*Built by Twitterella Feynman for Ben Tauber's OpenClaw instance.*
