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

## Bot Architecture (v6.5.0 - FULLY WORKING FEATURES)

### Working Features (v6.5.0) ✅
1. **Extended Thinking (5-step process)** - `generateResponseWithThinking()` 
   - Activated for complex queries (complexity >= 7)
   - 5-step reasoning: Understanding → Knowledge Check → Uncertainty Check → Tool Check → Response Plan
   - Enforces honesty rules during thinking process

2. **Response Validation Before Sending** - `validateResponseBeforeSending()`
   - Validates all responses > 100 characters before sending
   - Checks for honesty violations, accuracy, relevance, completeness
   - Can auto-fix or block problematic responses
   - Scoring system (0-100) for response quality

3. **Parallel Tool Execution** - `executeToolsInParallel()`
   - Uses Promise.all for concurrent tool execution
   - Tracks success/failure of each tool
   - Reports execution time and completion status

4. **Auto Tool Selection with AI** - `selectBestToolsAutomatically()`
   - AI-powered tool selection with reasoning
   - Determines PARALLEL vs SEQUENTIAL execution mode
   - Returns tool arguments for optimal execution

5. **Honesty System Enforcement** - Added to all system prompts
   - 10-point ABSOLUTE HONESTY PROTOCOL in system prompts
   - Enforced in response validation layer
   - Flags and corrects honesty violations

### AI Classification Engine (ULTRA AI v6.5.0)
Features a multi-layered classification system (0-4) including:
- Layer 0: Typo Correction + Developer Mode
- Layer 0.5: Context-Aware Intent Inference
- Layer 1: Instant Pattern Matching (sub-ms)
- Layer 1.5: Confusion Detection
- Layer 2: Complexity Scoring
- Layer 2a: Extended Thinking - 5 steps (WORKING)
- Layer 3: AI Classification
- Layer 3.5: Auto Tool Selection (WORKING)
- Layer 3.75: Multi-Tool Parallel Analysis (WORKING)
- Layer 4: Response Validation + Honesty Check (WORKING)

### Multi-Tool Intelligence
Enables parallel tool execution, AI-driven tool selection across 8 categories (Image, Code, Search, Security, Crypto, File, URL, Math), and smart orchestration for complex requests.

### Smart Rate-Limited Web Search
Utilizes DuckDuckGo with exponential backoff to prevent rate limiting, falling back to Wikipedia if necessary.

### Other Features
- Smart Prompt Enhancement for image generation
- Knowledge Base Expansion (120+ topics)
- File Attachment Reading (40+ file types, up to 50KB)
- Self-Awareness System with version tracking
- Developer Recognition System
- Conversation Flow with auto-compression

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
- and many more...

# Recent Changes (v6.5.0) - 2025-11-28

## New Working Features Added:
1. ✅ **Extended Thinking (5-step process)** - Real step-by-step reasoning for complex queries
2. ✅ **Response Validation Before Sending** - Validates honesty, accuracy, quality before sending
3. ✅ **Parallel Tool Execution** - Promise.all based concurrent tool execution
4. ✅ **Auto Tool Selection with AI** - Intelligent tool selection with reasoning
5. ✅ **Honesty System Enforcement** - 10-point protocol enforced in all system prompts

## Functions Added:
- `validateResponseBeforeSending(userMessage, aiResponse, context)` - Validates responses
- `executeToolsInParallel(toolCalls, userId, msg)` - Parallel tool execution
- `selectBestToolsAutomatically(userMessage, availableTools, context)` - AI tool selection
- `generateResponseWithThinking(userMessage, messages, tools, context)` - Thinking process

## System Prompt Updates:
- Added "ABSOLUTE HONESTY PROTOCOL (MANDATORY - v6.5.0)" to all system prompts
- 10 strict honesty rules enforced in every response
- Response validation layer with scoring (0-100)
