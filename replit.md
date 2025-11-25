# Overview

This Discord bot integrates with Mistral AI to provide an AI-powered conversational interface featuring optional autonomous learning and an intelligent skill learning system. Built with Node.js, it incorporates a dual-database architecture with Neon PostgreSQL and Supabase. The bot delivers natural, clean responses to all users with appropriate emojis and Hinglish support, aiming for an engaging and authentic user experience without manipulative psychology tactics.

**Production Mode**: By default, the bot runs in production mode with clean responses and minimal logging. Autonomous learning is DISABLED by default (enable via `ENABLE_AUTO_LEARNING=true`).

# Recent Changes (November 25, 2025)

## Duplicate Reply Fix & Production Hardening
- **Fixed duplicate message replies** - Implemented message processing lock (debounce) to prevent concurrent handlers
- **Single-message responses** - Converted `replyChunks` to send ONE message or .txt file (no more streaming chunks)
- **Optimized image replies** - `replyWithImages` batches all images + text into ONE message with robust 2000-char limit handling
- **Autonomous learning control** - Disabled by default, requires `ENABLE_AUTO_LEARNING=true` env variable to enable
- **Developer mode toggle** - Added `DEVELOPER_MODE` env variable for easy feature management
- **DM handler fix** - Fixed bug causing "🤔 No response." instead of actual AI-generated content
- **Model upgrade** - All instances changed from `mistral-small-latest` to `mistral-large-latest`

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Application Type
**Discord Bot with AI Integration**
- Runs as a persistent Node.js service using Express.js for health checks.
- Employs an event-driven architecture, responding to Discord messages.

## Core Technologies
- **Runtime**: Node.js with ES6 modules
- **Discord Integration**: discord.js v14.24.2 with Gateway Intents
- **AI Provider**: Mistral AI SDK v1.10.0
- **Primary Database**: Neon PostgreSQL with `pg` driver
- **Cloud Database**: Supabase (file storage, real-time features, backup)
- **HTTP Client**: node-fetch
- **Environment Management**: dotenv

## Bot Architecture
**Gateway Intents**: Utilizes Discord gateway intents for message and guild events.
**AI Function Calling**: Implements an advanced tool/function calling pattern with Mistral AI, enabling the bot to automatically select and execute appropriate tools based on natural language queries via the `?ask` command.
- **Tools**: Includes 160+ advanced tools covering security, OSINT, crypto, image generation (generation only, no editing), code generation, web search, and developer-specific tools (e.g., code execution sandbox, GitHub integration, API testing).
- **Self-Awareness System**: Tracks bot version and maintains an update history.
- **Developer Recognition System**: Identifies the developer by Discord user ID for unrestricted access.

## Data Persistence (DUAL DATABASE ARCHITECTURE + SKILL LEARNING)
**Neon PostgreSQL (Primary)**: A 10-table schema for comprehensive memory and skill management, including `conversations`, `global_memory`, `entities`, `summaries`, `topics`, `statistics`, `quality_scores`, `user_skills`, `skill_events`, and `skill_limits`.
**Supabase (Cloud + Real-time)**: Utilized for file storage buckets, real-time tables for live data sync, backup system, and row-level security.

## Conversation Flow
1. User sends a message (message processing lock prevents duplicates).
2. Bot retrieves user context from PostgreSQL.
3. Message and context sent to Mistral AI (`mistral-large-latest`) with available tools.
4. AI selects and executes appropriate tools.
5. Tool results processed into the final response.
6. Response, statistics, and entities stored in the database.
7. Reply sent to Discord as **SINGLE MESSAGE** (or .txt file if >2000 chars).
8. Auto-compression of conversation history if needed.
9. Autonomous learning (DISABLED by default, enable with `ENABLE_AUTO_LEARNING=true`).

## Uptime Monitoring
**Express Server**: A minimal HTTP server is included for health checks.

# External Dependencies

## AI Service
- **Mistral AI**: Primary LLM provider for conversational responses and function calling.

## Communication Platform
- **Discord API**: Handles message delivery and bot presence.

## Database
- **PostgreSQL**: Relational database for persistent storage.

## API Keys / Services (Conditional)
- **SerpAPI**: For web search and CVE lookup.
- **Shodan**: For internet-wide scanning.
- **VirusTotal**: For file hash checking.
- **Pollinations API (Flux Pro/Flux Realism)**: For image generation.
- **HaveIBeenPwned**: For email breach checking.

## Environment Variables
**Core Configuration:**
- `DISCORD_BOT_TOKEN`, `DISCORD_TOKEN`, `MIYU_CHANNEL_ID`
- `MISTRAL_API_KEY`, `GEMINI_API_KEY`, `GEMINI_API_KEY_BACKUP`
- `DATABASE_URL`, `SUPABASE_URL`, `SUPABASE_ANON_KEY`

**API Keys (Optional):**
- `SERPAPI_KEY`, `SHODAN_API_KEY`, `VIRUSTOTAL_API_KEY`, `KONTEXT_API_KEY`

**Feature Toggles:**
- `ENABLE_AUTO_LEARNING` - Enable autonomous learning interval (default: false)
- `DEVELOPER_MODE` - Enable enhanced logging and debug features (default: false)
