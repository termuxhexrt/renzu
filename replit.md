# Overview

This Discord bot integrates with Mistral AI to provide an **ultra-addictive AI-powered conversational interface** featuring **PSYCHOLOGICAL MANIPULATION ENGINE** with 20+ proven psychology tricks, **ULTRA-AGGRESSIVE AUTONOMOUS LEARNING** (every 20 seconds), and **INTELLIGENT SKILL LEARNING SYSTEM**. Built with Node.js, it incorporates **DUAL DATABASE ARCHITECTURE** with Neon PostgreSQL (10-table schema) + Supabase (file storage + real-time features). The bot delivers **ChatGPT-level engagement** to ALL users (normal/premium/developer) with expressive responses, natural emojis, and Hinglish support.

## Latest Updates (v7.1.0) 🎨✨
✨ **INSTANT POLLINATION IMAGE GENERATION + AUTOMATIC FALLBACK!**
1. **Seedha URL Response** - Image generation returns DIRECT Pollination URL (no attachments, no broken links)
2. **Zero Psychology Overhead** - Image URL responses skip all enhancement - clean and instant
3. **Automatic Pollination Fallback** - When models fail, next message auto-provides working Pollination URL
4. **5-Minute Tracking Window** - Tracks failed requests per-user for 5 minutes
5. **Broken Link Cleanup** - Auto-removes any [undefined] or [null] markdown artifacts
6. **FREE & UNLIMITED** - Uses Pollinations.ai (no API key, no limits, instant generation)

## Previous Updates (v7.0.0) 🧠💀🔥
✨ **ULTRA-ADDICTIVE PSYCHOLOGY ENGINE + ULTRA-AGGRESSIVE LEARNING!**
1. **Psychological Manipulation System** - 20+ proven psychology tricks (Curiosity Gap, Zeigarnik Effect, Social Proof, FOMO, Reciprocity, Ben Franklin Effect, Pattern Interrupts, Loss Aversion, etc.)
2. **Universal Expressive Quality** - ALL users (normal/premium/developer) get same engaging conversation style with emojis 😎🔥💀 and casual Hinglish
3. **Ultra-Aggressive Learning** - Bot learns from web every 20 SECONDS (was 2 minutes) across 120+ diverse topics
4. **Intelligent Rate Limiting** - Auto-detects API limits, implements cooldowns, handles errors gracefully with daily quota tracking (80 calls/day)
5. **5x Knowledge Acquisition** - Fetches 5 sources per cycle (was 3) for faster knowledge growth
6. **Dark Psychology Integration** - Love bombing, scarcity, choice restriction, urgency triggers
7. **Gamification & Dopamine** - Achievement unlocks, validation, confidence boosts, engagement loops
8. **Anticipation & Prediction** - Bot predicts what you'll ask next, anticipates needs proactively
9. **Smart Enhancement** - 5-8 psychology tricks randomly applied per response for natural feel
10. **Addictiveness Metrics** - Logs which tricks were applied for optimization

## Features Summary:
- **140+ Advanced Tools** - Security, OSINT, crypto, image gen, code gen, web search, etc.
- **Psychological Manipulation** - 20+ proven tactics to maximize engagement and retention
- **Ultra-Aggressive Learning** - Learns everything every 20 seconds (120+ topic categories)
- **Universal Quality** - Same expressive, emoji-rich responses for all user tiers
- **ChatGPT-Level Psychology** - Curiosity hooks, social proof, FOMO, validation, reciprocity
- **Smart Rate Limiting** - Automatic cooldowns and error handling for sustainable operation

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Application Type
**Discord Bot with AI Integration**
- Runs as a persistent Node.js service, using Express.js for health checks.
- Employs an event-driven architecture, responding to Discord messages.

## Core Technologies
- **Runtime**: Node.js with ES6 modules
- **Discord Integration**: discord.js v14.24.2 with Gateway Intents
- **AI Provider**: Mistral AI SDK v1.10.0
- **Primary Database**: Neon PostgreSQL with pg driver (conversations, analytics, memory)
- **Cloud Database**: Supabase (file storage, real-time features, backup)
- **HTTP Client**: node-fetch
- **Environment Management**: dotenv

## Bot Architecture
**Gateway Intents**: Utilizes Discord gateway intents for message and guild events.
**AI Function Calling**: Implements an advanced tool/function calling pattern with Mistral AI, enabling the bot to automatically select and execute appropriate tools based on natural language queries via the `?ask` command. There are 141 tools that cover:
- **Core Tools**: Code generation, Image generation (Gemini/Kontext Pro), Web search, History management.
- **Security Tools**: CVE lookup, Threat simulation (SQLi, XSS), Quantum encryption (Kyber, Dilithium), Security auditing, Password analyzer, File hash checker (VirusTotal), URL safety checker, Port scanner.
- **OSINT Tools**: Shodan scanner, Subdomain enumeration, WHOIS lookup, DNS analysis, SSL/TLS analysis, Reverse IP lookup, Email breach checker (HaveIBeenPwned), Phone lookup.
- **Crypto/Encoding Tools**: AES-256 Encryption/Decryption, Base64 Encoder/Decoder, Hash operations, Quantum encryption.
- **Utility Tools**: Web scraper, Blockchain tracker, IP tracking, GitHub scanner, Pastebin uploads, QR code generator, Deepfake detector, Crypto miner detector.
- **Fun Tools**: Meme generator, ASCII art generator, Text-to-Speech converter.

**Self-Awareness System**: Tracks bot version (v4.1.0) and maintains an update history, allowing the bot to inform users about its current state and changes.

**Developer Recognition System**: Identifies the developer by Discord user ID (1104652354655113268) with UNRESTRICTED ACCESS - no rate limits, no restrictions, full access to all features for testing and development purposes.

## Data Persistence (DUAL DATABASE ARCHITECTURE + SKILL LEARNING)
**Neon PostgreSQL (Primary)**: 10-table schema for comprehensive memory + skill management:
- `conversations`: User messages and bot responses
- `global_memory`: Cross-user and cross-bot interaction tracking (synced to Supabase)
- `entities`: Extracted user-specific data
- `summaries`: Compressed conversation history
- `topics`: Conversation topic tracking
- `statistics`: Analytics on response times, tool usage, etc
- `quality_scores`: Response quality tracking
- `user_skills`: 🆕 Tracks learned skills with confidence & experience levels
- `skill_events`: 🆕 Audit trail for all skill learning interactions
- `skill_limits`: 🆕 Daily learning limits per tier (normal/premium/developer)

**Supabase (Cloud + Real-time)**:
- **File Storage Bucket**: Auto-upload generated images, audio, documents with public URLs
- **Real-time Tables**: Live data sync for analytics, statistics, global memory
- **Backup System**: Redundant storage for critical data
- **Row-Level Security**: Advanced permissions and access control
- **Public URLs**: Instantly shareable links for generated content

This provides ACID-compliant storage, cloud backup, real-time features, file storage, skill learning, and hybrid database reliability.

## Conversation Flow
1. User sends a message via `?ask`.
2. Bot retrieves user context from PostgreSQL.
3. Real-time data needs are auto-detected.
4. Message and context are sent to Mistral AI with available tools.
5. AI selects and executes appropriate tools (max 5 iterations).
6. Tool results are processed into the final response.
7. Response, statistics, and entities are stored in the database.
8. Reply is sent to Discord, chunked for long messages.
9. Auto-compression of conversation history is triggered if needed.

## Uptime Monitoring
**Express Server**: A minimal HTTP server is included for health checks, preventing the bot from sleeping on free-tier hosting platforms.

# External Dependencies

## AI Service
- **Mistral AI**: Primary LLM provider for conversational responses and function calling. Requires `MISTRAL_API_KEY`.

## Communication Platform
- **Discord API**: Handles message delivery and bot presence. Requires `DISCORD_TOKEN`.

## Database
- **PostgreSQL**: Relational database for persistent storage. Requires `DATABASE_URL`.

## API Keys / Services (Conditional)
- **SerpAPI**: For web search and CVE lookup. Requires `SERPAPI_KEY`.
- **Shodan**: For internet-wide scanning. Requires `SHODAN_API_KEY`.
- **VirusTotal**: For file hash checking. Requires `VIRUSTOTAL_API_KEY`.
- **Google Gemini / Kontext Pro**: For image generation.
- **HaveIBeenPwned**: For email breach checking (no key required).
- Other tools use free APIs or require no keys.

## Environment Variables (All Configured)
The following environment variables are set in the shared environment:

**Discord Configuration**
- `DISCORD_BOT_TOKEN`: Primary Discord bot token
- `DISCORD_TOKEN`: Backup Discord token (same as DISCORD_BOT_TOKEN)
- `MIYU_CHANNEL_ID`: Channel ID for Miyu bot conversations (1434166838937391184)

**AI Services**
- `MISTRAL_API_KEY`: Mistral AI API key for conversational AI
- `GEMINI_API_KEY`: Google Gemini API key for image generation
- `GEMINI_API_KEY_BACKUP`: Backup Gemini API key

**Database Services**
- `DATABASE_URL`: Neon PostgreSQL connection string
- `SUPABASE_URL`: Supabase project URL (https://pimlbmlnoptcuzgkwkdx.supabase.co)
- `SUPABASE_ANON_KEY`: Supabase anonymous key for client access

**API Services**
- `SERPAPI_KEY`: SerpAPI key for web search and CVE lookups
- `SHODAN_API_KEY`: Shodan API key for internet-wide scanning
- `VIRUSTOTAL_API_KEY`: VirusTotal API key for file hash checking
- `KONTEXT_API_KEY`: Kontext Pro API key for image generation
