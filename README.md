# 👑 Renzu v9.0.0 — Neural Hacking Intelligence

> AI-powered Discord bot with 166+ tools, red team capabilities, and autonomous reasoning.

---

## 🔥 What is Renzu?

Renzu is a **Mistral AI-powered** Discord bot built for hackers, developers, and security researchers. It features persistent memory, multi-tool chaining (up to 15 iterations), gender-adaptive responses, and a comprehensive offensive security toolkit.

**Not a toy chatbot.** This is a weapon.

---

## ⚡ Core Features

| Feature | Description |
|---------|-------------|
| **166+ Tools** | Code gen, web scraping, hacking tools, crypto, OSINT, and more |
| **Multi-Tool Chaining** | AI autonomously chains up to 15 tools per query |
| **Red Team Code Gen** | Specialized RAT, payload, and exploit generator with MITRE ATT&CK alignment |
| **7 Hacking Tools** | `nmap_scan`, `whois_lookup`, `dns_lookup`, `breach_check`, `subdomain_enum`, `shodan_search`, `shell_exec` |
| **Extended Thinking** | 5-step reasoning for complex queries |
| **Neural Swarm** | Multi-agent system (Architect, Auditor, Executioner) |
| **Persistent Memory** | PostgreSQL + Redis backed conversation history |
| **Gender Detection** | Gemini Vision API adapts tone based on user avatar |
| **Proactive Security** | Auto-scans URLs, detects risks before you click |
| **Self-Evolution** | `evolve_bot` tool for autonomous code modification |

---

## 🛡️ Security & Recon Tools

| Tool | Description |
|------|-------------|
| `nmap_scan` | TCP port scanner with banner grabbing (top 100 ports) |
| `whois_lookup` | Domain/IP WHOIS via RDAP protocol |
| `dns_lookup` | A/AAAA/MX/NS/TXT/CNAME/SOA DNS records |
| `breach_check` | Email breach exposure check (XposedOrNot API) |
| `subdomain_enum` | Subdomain discovery via crt.sh certificate transparency |
| `shodan_search` | Shodan host info and search queries |
| `shell_exec` | Execute shell commands in container (developer-only) |
| `vulnerability_scanner` | CVE lookup and vulnerability analysis |
| `exploit_database_search` | Search exploit databases |
| `metasploit_trainer` | Metasploit framework training |
| `sql_injection_trainer` | SQLi attack patterns and payloads |
| `xss_trainer` | XSS payload generation and testing |
| `phishing_simulator` | Phishing page and campaign simulation |
| `ransomware_simulator` | Ransomware mechanics demonstration |

---

## 💀 RAT Generator (v8.2.0)

The `generate_code` tool automatically detects red-team topics and switches to a specialized offensive security engine:

```
?ask bana ek Python RAT for Windows
?ask create a reverse shell with persistence
?ask generate a keylogger with AES exfil
?ask build a dropper with anti-VM detection
```

**Supported modules:** Persistence, C2 Communication, Surveillance, Exfiltration, Evasion, Delivery.

---

## 🏗️ Architecture

```
Runtime:        Node.js (ES6 modules)
Discord:        discord.js v14
AI Provider:    Mistral AI (3 keys, auto-rotation)
Database:       Neon PostgreSQL (10-table schema)
Cache:          Redis Cloud
HTTP:           node-fetch
Voice:          Google TTS
```

### AI Classification Engine (5 Layers)
1. **Layer 0:** Typo Correction + Developer Mode
2. **Layer 0.5:** Context-Aware Intent Inference
3. **Layer 1:** Instant Pattern Matching (sub-ms)
4. **Layer 2:** Complexity Scoring + Extended Thinking
5. **Layer 3:** AI Classification → Auto Tool Selection → Parallel Execution

### Data Persistence
- **Neon PostgreSQL:** conversations, global_memory, entities, summaries, topics, statistics, quality_scores, user_skills, skill_events, skill_limits
- **Redis:** Rate limiting, response caching, session data
- **Supabase:** File storage, real-time features (backup)

---

## 🔧 Environment Variables

```bash
# Required
DISCORD_BOT_TOKEN="..."
MISTRAL_API_KEY="..."
DATABASE_URL="postgresql://..."
REDIS_URL="redis://..."

# Optional
GEMINI_API_KEY="..."          # Gender detection
SHODAN_API_KEY="..."          # Shodan search
SERPAPI_KEY="..."              # Web search
VIRUSTOTAL_API_KEY="..."      # File hash checking
SUPABASE_URL="..."            # Cloud backup
SUPABASE_ANON_KEY="..."       # Supabase auth
DEVELOPER_ID="..."            # Unrestricted access ID
ENABLE_AUTO_LEARNING="true"   # Skill learning
DEVELOPER_MODE="true"         # Debug features
```

---

## 🚀 Deployment

```bash
# Install dependencies
npm install

# Run
node index.js
```

**Hosted on:** Railway (recommended), any Node.js host with PostgreSQL + Redis.

---

## 📊 Bot Stats

| Metric | Value |
|--------|-------|
| Total Lines | ~13,000 |
| Tools | 166+ |
| Tool Loop | 15 iterations max |
| AI Model | Mistral Large + Pixtral |
| API Keys | 3 (auto-rotation) |
| DB Tables | 10 |

---

## 📜 Changelog

### v8.2.0 (2026-02-27)
- 💀 **RAT Generator** — specialized offensive security code generation
- 🔧 **7 new hacking tools** — nmap, whois, dns, breach, subdomain, shodan, shell
- ⚡ **Tool loop 5→15** — complex multi-tool chaining
- ⏱️ **Accurate ETA** — realistic reply time estimates
- 🧹 **Code cleanup** — removed image gen (~2,300 lines), bot-to-bot chat (192 lines), dead code (58 issues fixed)

### v9.0.0 (2026-01-21)
- 🧠 Metacognitive Self-Audit
- 🐝 Neural Swarm 2.0
- 🛡️ The Eye (Proactive Guardian)
- 🧠 Neural Personality Grafting

### v7.6.5
- 🔊 Unlimited Voice (TTS)
- 🛠️ Project Maintenance Tool
- 🛡️ Anti-Gravity Security Scanner

### v6.5.0
- 🧠 Extended Thinking (5-step)
- 🚀 Parallel Tool Execution
- 🤖 Auto Tool Selection
- ✅ Honesty Enforcement

---

## 👨‍💻 Developer

**GamingParkBG** — Creator & Maintainer

---

*Built with obsession. No limits. No filters.* 💀🔥
