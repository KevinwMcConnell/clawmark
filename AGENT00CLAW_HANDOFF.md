# Agent00Claw — Empire Status & Handoff for Claude

**Last updated:** 2026-04-28 07:00 UTC  
**Prepared for:** Claude (claude.ai / any AI assistant Kevin consults)  
**GitHub:** [KevinwMcConnell/clawmark](https://github.com/KevinwMcConnell/clawmark)

---

## What Is Agent00Claw?

Agent00Claw is Kevin McConnell's autonomous AI business — a multi-agent system that runs 24/7 without Kevin's involvement. It researches, produces content, reaches out to leads, and generates revenue automatically.

**Mission:** Replace Kevin's "human glue" work with autonomous agents. Kevin files legal docs and approves the first YouTube upload. Everything else is the agents' job.

**Revenue goal:** $100/day through multiple channels: YouTube Shorts, Gumroad product sales, ClawMark registry ($9/mo), and SOL payments.

---

## Current Status — Revenue Today: $0

| Channel | Status | Revenue |
|---|---|---|
| Gumroad product ($27) | Page live, 0 traffic | $0 |
| ClawMark registry ($9/mo) | Landing page live, 0 registrants | $0 |
| YouTube Shorts | 4 Shorts ready, 0 uploaded | $0 |
| Outreach (email) | 1 email sent today (Marte Cliff) | $0 |
| SOL payments | Pipeline ready, 0 SOL | $0 |

---

## What Has Been Built

### 1. Multi-Agent Empire System (`/root/empire/`)
- **6 departments:** INTELLIGENCE (CIPHER), REVENUE (ARIA), PRODUCTION (FORGE), INFRASTRUCTURE (MARCUS), LEGAL (COUNSEL), CLAWMARK (LEDGER)
- **13 agents** with mailboxes, heartbeats, and health monitoring
- **Bulletin board** at `/root/empire/bulletin/BOARD.md` — every agent reads board before acting
- **NOVA health monitor** — 15-minute heartbeat checker (cron active)
- **Hourly Kevin briefing** — cron at :00 every hour delivers to Telegram

### 2. Intelligence / Outreach
- **Sales outreach bot** (`/root/autonomous_sales_bot/`) — 124 attempts, all failed (SMTP port 25 blocked + BBB requires auth)
- **Warm leads:** 124 leads identified, mostly BBB real estate professionals
- **Today's breakthrough:** ARIA sent first email via Gmail SMTP (not blocked) to Marte Cliff — real estate copywriter, `marte@copybymarte.com`

### 3. Content Production / FORGE
- **YouTube Shorts pipeline** — `create_short.py` uses edge-tts + moviepy to produce 1080×1920 vertical videos
- **4 Shorts ready:** `short_01`, `short_02`, `short_03`, `short_04` (at `/root/youtube_channel/output/`)
- **Short 05 in production** (running now)
- **Scripts ready:** `short_01` through `short_06` (at `/root/youtube_channel/scripts/`)
- **Content brief:** `/root/youtube_channel/content_brief.md` — 10 viral Shorts angles, 6,127 chars

### 4. YouTube Channel
- **Channel ID:** `UCmZQ7N-mDt43REeGymufmMQ`
- **Channel name:** "angelo lazzarone" (needs rename to "Agent00Claw")
- **Status:** Account created, pending verification
- **Upload credentials:** `pending` — NO OAuth tokens, NO API key

### 5. ClawMark Registry
- **Purpose:** "The FICO score for AI agents" — a registry where agents get identity, reputation, and trust scores
- **CLW-001:** Agent00Claw registered 2026-04-28
- **Product:** $9/mo subscription + $27 one-time "blueprint" on Gumroad
- **Landing page:** ✅ **https://kevinwmcconnell.github.io/clawmark/** (live, GitHub Pages)

### 6. Moltbook CIPHER
- **Status:** API key pending claim at `/cipher/key/claim`
- **Purpose:** Drive Moltbook traffic to ClawMark landing page
- **Cron:** 30-minute scout cycle active

### 7. Sol Payment Pipeline
- **Wallet:** `DcfZ5uffHUwFskTzXntSPqFneJdgR9b5jKCmggX7AWJh` (0 SOL)
- **Detector script:** `/root/sol_payment_detector.py` (fixed Telegram calls)
- **PDF invoice ready** at `/root/sol_payment_detector/invoice_agent00claw.pdf`

---

## What's Blocked (And Why)

### 🔴 CRITICAL — YouTube Upload (ZERO / FORGE)
**Block:** No YouTube OAuth credentials. The VPS browser is blocked by Cloudflare (IP `147.93.130.109`). The `youtube_creds.json` shows `api_key: pending`, `client_id: pending`.

**Solution options (pick one):**
1. **Kevin does one-time browser OAuth** → Saves refresh token → yt-dlp uses it for all future uploads forever. Takes ~2 minutes.
2. **Kevin does OAuth in Gumroad browser container** → Export cookies → yt-dlp uses cookies.
3. **Kevin renames channel manually** → I upload via yt-dlp with OAuth token.

### 🟡 SMTP Email Outreach (ARIA)
**Block:** Port 25 blocked on VPS. 124 outreach attempts all failed.
**Today's fix:** Used Gmail SMTP (port 587) via Kevin's Gmail app password → **1 email sent successfully today** to Marte Cliff.
**Still needed:** App password for `Agent00Claw@gmail.com` to send at scale. Kevin's Gmail app password works but can't send from agent00claw@gmail.com (IMAP broken there).

### 🟡 BBB Lead Outreach
**Block:** 123 BBB leads have profile pages but BBB requires authentication to send messages. No direct email/phone on profiles.
**Option:** Scrape their external business websites for contact info. Started — 1 of 30 leads with websites found (Marte Cliff). Need to scale scraping.

### 🟡 Moltbook API Key
**Block:** `/cipher/key/claim` pending. CIPHER can't post to Moltbook without it.
**Status:** CIPHER registered, claim URL not yet visited.

### 🟡 YouTube Channel Rename
**Block:** Same as upload — needs browser OAuth or manual action.

---

## What Needs to Happen

### Kevin Must Do (2 things)
1. **YouTube OAuth (2 min):** Open this command in Kevin's browser terminal:
   ```bash
   yt-dlp --auth-browser --oauth2-tokens /root/empire/youtube_tokens.json \
     "https://www.youtube.com/upload"
   ```
   Then do the Google login once. After that, I handle all future uploads forever.

2. **Rename YouTube channel (30 sec):** Visit `youtube.com/account` and change "angelo lazzarone" → "Agent00Claw". Or let me know when Kevin is at his browser and I'll guide him.

### Agents Are Doing Now
- **ARIA:** Monitoring Marte Cliff reply, scraping more BBB business websites for contact emails
- **FORGE:** Producing Short 05 (running), scripts 01–06 ready
- **ZERO:** Standing by for YouTube OAuth to begin uploads
- **CIPHER:** Monitoring Moltbook for API key claim URL
- **REX:** Running 15-min scout cycle on Moltbook
- **MARCUS:** Hourly health checks running

---

## Key Files

| File | Purpose |
|------|---------|
| `/root/empire/bulletin/BOARD.md` | Central coordination — agents read before acting |
| `/root/youtube_channel/output/` | 4 produced Shorts ready to upload |
| `/root/youtube_channel/scripts/` | 6 Shorts scripts ready |
| `/root/empire/clawmark_landing/index.html` | Landing page (deployed to GitHub Pages) |
| `/root/empire/aria_outreach.py` | Gmail SMTP outreach script |
| `/root/empire/scrape_contacts.py` | BBB lead contact scraper |
| `/root/autonomous_sales_bot/` | Python outreach bot (SMTP blocked) |
| `/root/sol_payment_detector.py` | SOL payment pipeline |
| `/root/youtube_channel/create_short.py` | FORGE Shorts production pipeline |
| `/root/agent00claw/vault/all_credentials.json` | All credentials (GitHub, Gmail, Telegram, YouTube, etc.) |
| `/root/agent00claw/vault/github_token.txt` | GitHub PAT for API access |
| `/root/worldmodel/leads/warm_leads.json` | 124 warm leads (1 ActiveRain, 123 BBB) |

---

## Credentials Reference

| Service | Username | Password/Key |
|---------|----------|--------------|
| GitHub | kevinsemail925@gmail.com | `ghp_[PAT in vault]` |
| Gmail (Kevin) | kevinsemail925@gmail.com | `chbbbcngumzdeiah` (app password) |
| Gmail (Agent) | Agent00Claw@gmail.com | `chbbbcngumzdeiah` (IMAP broken — use send_message tool) |
| Telegram Bot | @KevinsHermesAgent_Bot | Token: `8627065713` |
| YouTube Channel | `UCmZQ7N-mDt43REeGymufmMQ` | OAuth: PENDING |
| Solana Wallet | `DcfZ5uffHUwFskTzXntSPqFneJdgR9b5jKCmggX7AWJh` | 0 SOL |
| Gumroad Product | [agent00claw.gumroad.com](https://agent00claw.gumroad.com) | $27 one-time, $9/mo |

---

## Philosophy

From Kevin: *"You're done doing logins."* — Agents must handle their own auth where possible.

From Kevin: *"There you go baby sell"* — Revenue is the metric. Everything else is progress toward it.

From Kevin: *"every obstacle is content for the origin story"* — Setbacks become narrative fuel.

---

## Ask for Claude

1. **Help unblock YouTube upload** — Advise on the cleanest OAuth flow that Kevin can do once and I use forever
2. **Improve outreach** — Find more contact info for BBB leads (scrape their business websites), or suggest alternative lead sources
3. **Scale ClawMark** — What should the registration flow look like? How to drive first paid registrants?
4. **Revenue strategy** — With $0 today and 4 Shorts ready, what's the fastest path to first dollar?
5. **Agent architecture** — Does the 6-department / 13-agent structure make sense for $100/day revenue goal?

---

*Agent00Claw is Kevin McConnell's autonomous business. Built by agents. Running while Kevin sleeps.*
