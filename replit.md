# Overview

This Discord bot integrates with Mistral AI to provide an AI-powered conversational interface featuring **FREE UNLIMITED AUTONOMOUS LEARNING** (every 60 seconds), **DEVELOPER DM SUPPORT**, and **INTELLIGENT SKILL LEARNING SYSTEM**. Built with Node.js, it incorporates **DUAL DATABASE ARCHITECTURE** with Neon PostgreSQL (10-table schema) + Supabase (file storage + real-time features). The bot delivers natural, clean responses to ALL users (normal/premium/developer) with appropriate emojis and Hinglish support.

## Latest Updates (v8.1.0) 🧹✨💬
✨ **PSYCHOLOGY SPAM COMPLETELY REMOVED - AGGRESSIVE SANITIZATION SYSTEM!**
1. **Aggressive Response Sanitization** - New `sanitizeResponse()` function strips ALL spam phrases line-by-line
2. **No More Spam** - Eliminated "Developer Access", "Plot twist", "Power Move", "Thinking ahead", etc.
3. **Clean Natural Responses** - Removed ALL psychology manipulation from system prompts
4. **Direct Communication** - Simple, helpful responses without manipulation tactics
5. **Appropriate Emojis** - Reduced to 2-3 emojis per response (was forcing 5-8)
6. **Fixed DM Support** - Developer DM support now works properly with full AI + tool access
7. **Discord.js Partials** - Fixed partials configuration for proper DM message handling

**Technical Implementation:**
- **Sanitization Function** - Scans each line for 19+ spam phrases and removes entire lines containing them
- **Fallback Responses** - Returns "Done! 😊" if response becomes empty after sanitization
- **Applied to All Outputs** - Sanitization applied in both `replyChunks()` and `replyWithImages()` functions
- **Spam Phrases Blocked:**
  - "Developer Access", "Unrestricted knowledge unlocked"
  - "Plot twist", "Power Move", "Got more questions"
  - "Thinking ahead", "Most people don't know", "Thousands of users"
  - "The real magic happens", "Want to know the underground"
  - "The natural next step", "This is just the surface"
  - And 10+ more manipulation tactics

**What Changed:**
- System prompt cleaned: Removed curiosity hooks, social proof tricks, fake urgency
- Response style: Natural and conversational instead of manipulative
- Aggressive filtering: Line-by-line spam removal catches AI-generated manipulation
- Developer DM: Fixed `Partials.Channel` import and proper AI response generation
- Removed all "MANDATORY STYLE" spam instructions from prompts

## Previous Updates (v8.0.0) 🆓🌐💬
✨ **FREE UNLIMITED LEARNING + DEVELOPER DM SUPPORT!**
1. **100% Free Learning** - NO API KEYS NEEDED for autonomous learning! DuckDuckGo + Wikipedia
2. **Smart Rotation Strategy** - Wikipedia 70% (unlimited, reliable) + DuckDuckGo 30% (fresh web data)
3. **Zero Rate Limits** - Wikipedia API is completely unlimited and free forever
4. **DDG Rate Limit Fix** - Smart rotation avoids "requests too quickly" errors from DuckDuckGo
5. **Optimized Interval** - 60 seconds (was 20s) for sustainable, safe operation
6. **Developer DM Support** - Bot responds to developer's DMs automatically without ?ask prefix
7. **Non-Developer Block** - DMs from regular users are blocked with helpful message
8. **Removed SerpAPI Dependency** - No longer needed for autonomous learning (still available for tools)

**Technical Details:**
- **Primary Source (70%):** Wikipedia API - unlimited, reliable, no keys needed
- **Secondary Source (30%):** DuckDuckGo - for current web data, used sparingly
- **Automatic Fallback:** If one source fails, bot automatically uses the other
- **Learning Cycle:** Every 60 seconds (1440 cycles/day = ~7200 knowledge entries/day)
- **DM Processing:** Developer can chat naturally in DMs, full AI + tool access
- **Package Added:** `duck-duck-scrape` for DuckDuckGo integration

## Previous Updates (v7.3.0) 🧠✨💻
✨ **PSYCHOLOGY MANIPULATION DISABLED + DEVELOPER POWER TOOLS ADDED!**
1. **Natural Responses** - All psychology manipulation tricks removed for authentic conversations
2. **No More Fake Engagement** - Removed curiosity hooks, cliffhangers, FOMO triggers, social proof, etc.
3. **Clean Output** - Responses are now direct and natural without spam-like enhancement
4. **Improved UX** - Users get honest, straightforward answers instead of manipulative content
5. **Code Cleanup** - Removed 250+ lines of dead psychology manipulation code

**NEW: Developer-Only Power Tools (8 Tools Added)**
1. **Code Execution Sandbox** - Run Python/JavaScript/Node.js code with timeout protection
2. **GitHub Integration** - Search repos, issues, PRs, and code across GitHub
3. **API Testing Suite** - Test REST endpoints (GET/POST/PUT/DELETE) with timing and response analysis
4. **NPM Package Search** - Get package info, versions, downloads, and metadata instantly
5. **Stack Trace Analyzer** - AI-powered error debugging with root cause analysis and fixes
6. **Documentation Generator** - Auto-create README, API docs, or inline documentation from code
7. **SQL Query Formatter** - Format, optimize, and analyze SQL queries with best practices
8. **cURL Converter** - Convert cURL commands to Python, JavaScript, PHP, etc.

🔒 **All developer tools are RESTRICTED to bot developer only (ID: 1104652354655113268)**

## Previous Updates (v7.2.0) 🎨✨
✨ **REMOVED IMAGE EDITING + GENERATION ONLY MODE!**
1. **Edit Tool Removed** - `edit_image` tool completely removed from TOOL_DEFINITIONS
2. **Generation-Only Support** - Bot now ONLY supports image generation via Pollinations API
3. **Custom Edit Response** - When users ask to edit images, bot responds with:
   > "🎨 Bhai, ye high quality model ke saath generate hui hai image isliye edit nahi kar sakta! 😅\n\nBas generate kar sakta hun nai image - custom jo tu chahe! 🎯\n\nKya prompt de mujhe? Aur kaunsa style chahiye - anime, realistic, dark, vibrant? 💪"
4. **Auto-Detection** - Edit requests detected by keywords: 'edit', 'modify', 'change', 'pichli', 'first image', 'second image', 'wo image', 'usko'
5. **Smart Routing** - Custom response only triggers if user mentions BOTH edit keywords + image reference
6. **Hinglish Support** - Custom message in user's preferred Hindi/English mix style

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
- **160+ Advanced Tools** - Security, OSINT, crypto, image generation, code gen, web search, **NEW: Developer tools**
- **Developer Power Suite (v7.3.0)** - Code execution, GitHub search, API testing, npm packages, stack trace analysis, documentation generation, SQL formatting, cURL conversion
- **Developer DM Support (v8.0.0)** - Automatic AI responses in DMs for developer only, no ?ask prefix needed
- **Image Generation Only** - Pollinations API (Flux Pro/Flux Realism) for unlimited free image creation, custom edit rejection
- **Natural Conversations** - Authentic responses without manipulation or fake engagement tactics
- **FREE Unlimited Learning (v8.0.0)** - Wikipedia 70% + DuckDuckGo 30%, NO API keys needed, every 60 seconds (120+ topic categories)
- **Universal Quality** - Same expressive, emoji-rich responses for all user tiers
- **Zero Rate Limits** - Smart rotation strategy avoids all API limits on autonomous learning
- **Hinglish Conversations** - Natural Hindi/English mix in all bot responses

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
**AI Function Calling**: Implements an advanced tool/function calling pattern with Mistral AI, enabling the bot to automatically select and execute appropriate tools based on natural language queries via the `?ask` command. There are 140+ tools that cover:
- **Core Tools**: Code generation, Image generation only (Pollinations API - Flux Pro/Flux Realism), Web search, History management. **NOTE: Image editing is NOT supported - bot responds with custom message explaining generation-only mode**.
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
