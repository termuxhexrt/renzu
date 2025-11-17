# Overview

This Discord bot integrates with Mistral AI to provide an AI-powered conversational interface, featuring **141 specialized tools** for cybersecurity training, automation, web scraping, reverse engineering, code optimization, compliance management, and more. Built with Node.js, it incorporates persistent storage via PostgreSQL with a 7-table schema for comprehensive memory management and analytics. The bot includes self-awareness features like version tracking (v4.1.0) and a developer recognition system with unrestricted access for the creator.

## Latest Updates (v4.1.0)
✨ **7 NEW PROFESSIONAL TOOLS ADDED:**
1. **Code Optimization & Security Module** - Real minification + obfuscation for JS/Python/CSS
2. **Network Research Simulator** - Proxy rotation + randomized user-agents for privacy research
3. **Project Uptime Monitor** - Prevent idle timeouts during long research sessions
4. **Data Management Utility** - Safe dataset reset with production data protection
5. **Digital Forensics Trainer** - Steganography + metadata embedding/extraction
6. **Performance Logging System** - Smart log suppression for high-load testing
7. **Compliance & Ethics Generator** - Auto-generate usage guidelines and disclaimers

## Tool Count: 141 Total
- **34 Core Tools** (v1.0-3.0)
- **100 Advanced Tools** (v4.0)
- **7 Professional Tools** (v4.1)

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
- **Database**: PostgreSQL with pg driver
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

## Data Persistence
**PostgreSQL Database**: Uses a 7-table schema for comprehensive memory management, including:
- `conversations`: User messages and bot responses.
- `global_memory`: Cross-user and cross-bot interaction tracking.
- `entities`: Extracted user-specific data.
- `summaries`: Compressed conversation history.
- `topics`: Conversation topic tracking.
- `statistics`: Analytics on response times, tool usage, etc.
- `quality_scores`: Response quality tracking.
This provides ACID-compliant storage, supports concurrent conversations, enables personalized responses through entity extraction, and offers advanced analytics.

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

## Optional Environment Variables
- `MIYU_BOT_ID`: For bot-to-bot conversations.
- `MIYU_CHANNEL_ID`: For Miyu conversation channel.
