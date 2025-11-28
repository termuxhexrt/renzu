# Overview

This Discord bot, built with Node.js, integrates with Mistral AI to provide an advanced AI conversational interface. It features optional autonomous learning, an intelligent skill learning system, and a dual-database architecture using Neon PostgreSQL and Supabase. The bot aims to deliver natural, engaging, and honest responses, including support for Hinglish and appropriate emojis, without manipulative psychology tactics. A key ambition is to evolve into a highly accurate and transparent AI, capable of complex reasoning and multi-tool orchestration, always admitting limitations and never fabricating information.

# User Preferences

Preferred communication style: Simple, everyday language (Hinglish supported).

# System Architecture

## Application Type
**Discord Bot with AI Integration**
- Runs as a persistent Node.js service using Express.js for health checks.
- Employs an event-driven architecture, responding to Discord messages.

## Core Technologies
- **Runtime**: Node.js with ES6 modules
- **Discord Integration**: discord.js v14.24.2 with Gateway Intents
- **AI Provider**: Mistral AI SDK v1.10.0
- **Primary Database**: Neon PostgreSQL
- **Cloud Database**: Supabase (file storage, real-time features, backup)
- **Image Generation**: Puter.js with KONTEXT Models (primary), Pollinations.ai (fallback)
- **HTTP Client**: node-fetch
- **Environment Management**: dotenv

## Bot Architecture
- **AI Classification Engine (ULTRA AI v6.4.0)**: Features a multi-layered classification system (0-4) including typo correction, context-aware intent inference, confusion detection, complexity scoring, extended thinking (5-step process), AI classification, confidence validation, multi-tool analysis, and a verification layer with auto-correction. It incorporates an "Absolute Honesty System" that prioritizes truthfulness and admits limitations.
- **Multi-Tool Intelligence**: Enables parallel tool execution, AI-driven tool selection across 8 categories (Image, Code, Search, Security, Crypto, File, URL, Math), and smart orchestration for complex requests.
- **Smart Rate-Limited Web Search**: Utilizes DuckDuckGo with exponential backoff to prevent rate limiting, falling back to Wikipedia if necessary.
- **Smart Prompt Enhancement**: Uses Mistral AI to understand and expand vague prompts for image generation, supporting Hinglish.
- **Knowledge Base Expansion**: Incorporates a wide range of topics for autonomous learning, rotating between Wikipedia and DuckDuckGo for data.
- **File Attachment Reading**: Supports reading content from 40+ file types (e.g., .txt, .md, code files) up to 50KB.
- **Self-Awareness System**: Tracks bot version and update history.
- **Developer Recognition System**: Identifies the developer for unrestricted access and specific handling (e.g., bypassing prompt enhancement).
- **Conversation Flow**: Processes user messages, retrieves context, sends to Mistral AI with available tools, executes tools, stores results, and replies as a single Discord message (or .txt file for long responses). Includes auto-compression of conversation history.

## Image Generation System
- **Primary**: Puter.js with KONTEXT Models (e.g., `FLUX.1-kontext-max`, `google/imagen-4.0-fast`, `dall-e-3`, `stable-diffusion-3-medium`) for high-quality, complex realistic images up to 1920x1080 resolution.
- **Fallback**: Pollinations.ai for maximum 2048x2048 resolution with smart style detection, auto-enhancement prompts, negative prompts for defect removal, and fusion mode.
- **Safety Features**: Includes timeout handling, URL length safety (prompt truncation), graceful degradation, and `AbortController` for request cancellation.

## Data Persistence (DUAL DATABASE ARCHITECTURE + SKILL LEARNING)
- **Neon PostgreSQL**: Primary database with a 10-table schema for `conversations`, `global_memory`, `entities`, `summaries`, `topics`, `statistics`, `quality_scores`, `user_skills`, `skill_events`, and `skill_limits`.
- **Supabase**: Cloud database used for file storage buckets, real-time tables, backup system, and row-level security.

# External Dependencies

## AI Service
- **Mistral AI**: Primary LLM provider for conversational responses, complex reasoning, and function calling.

## Communication Platform
- **Discord API**: Integrates the bot with Discord for message handling and presence.

## Database
- **PostgreSQL**: Relational database for persistent storage via Neon.

## Web Search
- **DuckDuckGo (duck-duck-scrape)**: Primary free, unlimited web search.
- **Wikipedia**: Fallback for web search when DuckDuckGo is rate-limited or fails.

## Image Generation
- **Puter.js (black-forest-labs/FLUX.1-kontext)**: Primary image generation API.
- **Pollinations.ai**: Fallback image generation API.

## API Keys / Services (Conditional)
- **SerpAPI**: For specific web search and CVE lookups.
- **Shodan**: For internet-wide scanning.
- **VirusTotal**: For file hash checking.
- **HaveIBeenPwned**: For email breach checking.

## Environment Variables
- `DISCORD_BOT_TOKEN`, `DISCORD_TOKEN`, `MIYU_CHANNEL_ID`
- `MISTRAL_API_KEY`
- `DATABASE_URL`, `SUPABASE_URL`, `SUPABASE_ANON_KEY`
- `SERPAPI_KEY`, `SHODAN_API_KEY`, `VIRUSTOTAL_API_KEY`, `KONTEXT_API_KEY` (Optional)
- `ENABLE_AUTO_LEARNING` (Feature toggle, default: false)
- `DEVELOPER_MODE` (Feature toggle, default: false)
