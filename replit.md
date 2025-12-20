# 🆕 Multi-Database Auto-Scaling System (v6.9.2)

## Features
- **Support for up to 5 databases** - Automatic rotation when one fills up
- **Auto-rotation at 90% capacity** - Seamless switching to next database
- **Read-only mode** - Old databases preserved and accessible
- **Graceful degradation** - Bot continues reading when all DBs are full
- **Health monitoring** - Automatic checks every 5 minutes
- **Zero downtime** - No service interruption during rotation

## Environment Variables for Multi-Database
```bash
# Primary database (required)
DATABASE_URL_1="postgresql://..."

# Additional databases (optional, add as needed)
DATABASE_URL_2="postgresql://..."
DATABASE_URL_3="postgresql://..."
DATABASE_URL_4="postgresql://..."
DATABASE_URL_5="postgresql://..."

# Active database index (auto-updated by bot)
ACTIVE_DATABASE_INDEX="1"

# Database size limit in MB (default: 1000MB = 1GB)
DATABASE_SIZE_LIMIT_MB="1000"
```

## Expected Startup Logs
```
🔄 Initializing Multi-Database System...
✅ Database 1: Connected
🔥 Active Database for Writes: DB1
📚 Total Databases Available: 1
💾 Multi-Database Auto-Scaling: ENABLED
✅ Database health monitoring started (checks every 5 minutes)
```

---

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
- **Image Generation**: ADIMAGE.APP (PRIMARY - 100 Browser Profiles), Puter.js (fallback), Pollinations.ai (last resort)
- **HTTP Client**: node-fetch
- **Environment Management**: dotenv

## Bot Architecture (v6.9.0 - FULLY WORKING FEATURES)

### Working Features (v6.5.0) ✅
1. **Extended Thinking (5-step process)** - `generateResponseWithThinking()` 
   - Activated for complex queries (complexity >= 7)
   - 5-step reasoning: Understanding → Knowledge Check → Uncertainty Check → Tool Check → Response Plan
   - Enforces honesty rules during thinking process

2. **Parallel Tool Execution** - `executeToolsInParallel()`
   - Uses Promise.all for concurrent tool execution
   - Tracks success/failure of each tool
   - Reports execution time and completion status

3. **Auto Tool Selection with AI** - `selectBestToolsAutomatically()`
   - AI-powered tool selection with reasoning
   - Determines PARALLEL vs SEQUENTIAL execution mode
   - Returns tool arguments for optimal execution

4. **Honesty System Enforcement** - Added to all system prompts
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

## Image Generation System (v6.8.0 - Updated Priority)
- **PRIMARY**: ADIMAGE.APP (Imagen 3.0) - Fast, FREE, unlimited generations. High quality PNG with direct Discord upload. NO API key required.
- **SECONDARY**: Puter.js with KONTEXT Models (e.g., `FLUX.1-kontext-max`, `dall-e-3`) - Use if ADIMAGE fails or user specifically requests.
- **THIRD FALLBACK**: Pollinations.ai - Last resort option.
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
- **ADIMAGE.APP (Imagen 3.0)**: PRIMARY image generation API - FREE, unlimited, high quality.
- **Puter.js (black-forest-labs/FLUX.1-kontext)**: Secondary image generation API.
- **Pollinations.ai**: Third fallback image generation API.

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


# NEW FEATURES ADDED 6.9.0 2025/12/17
## 🔥 100 ULTRA HUMAN-LIKE BROWSER PROFILES (v6.9.0)
- **100 unique browser profiles** for ADIMAGE.APP image generation
- **Batched parallel execution** - 25 profiles per wave (4 batches total)
- **Early winner detection** - Stops when first successful image found
- **999% Human-like behavior** - Undetectable bot requests

### Browser Profile Distribution (100 Total):
| Browser | Count | Variants |
|---------|-------|----------|
| Chrome Windows | 25 | Gamer, Student, Office, Designer, Developer, etc. |
| Chrome Mac | 15 | Designer, Creative, Producer, Editor, etc. |
| Firefox | 12 | Privacy, Developer, Researcher, Journalist, etc. |
| Safari Mac | 10 | Creative, Executive, Premium, Professional, etc. |
| Edge Windows | 10 | Corporate, Enterprise, Business, IT, etc. |
| Chrome Android | 12 | S24Ultra, Pixel8Pro, OnePlus12, Mi14Pro, etc. |
| Safari iOS | 8 | iPhone Power, iPad Pro, Business, etc. |
| Chrome Linux | 4 | Developer, SysAdmin, DevOps, etc. |
| Brave | 4 | Crypto, Privacy, Rewards, Minimalist |

### Ultra Human-Like Features (Verified):
- **43 Accept-Language locales** (en-US, de-DE, ja-JP, hi-IN, ar-SA, zh-CN, etc.)
- **24 screen resolutions** with DPR (1920x1080, 2560x1440, 4K, mobile 390x844, etc.)
- **10 network conditions** (downlink 1.5-100 Mbps, RTT 5-300ms, ECT 3g/4g)
- **30 timezones** (America/New_York to Pacific/Auckland)
- **10 device memory values** (2GB to 32GB simulation)
- **10 hardware concurrency values** (2 to 16 cores)
- **Human timing jitter** (8 human actions: 1.33s min - 6.28s max per request)
  - Page load perception, mouse movement, input focus, typing, reading, button hover, click
- **Random optional headers** (DNT 40%, Cache-Control 30%, Pragma 20%, X-Requested-With 70%)
- **Chromium Client Hints** (Sec-Ch-Ua-*, viewport width/height, DPR, device memory)

### Execution Strategy:
1. **Batch 1**: Profiles 1-25 launch with human-like staggered delays
2. **Early Winner Check**: If good image found (>50KB), abort remaining
3. **Batch 2-4**: Only run if needed, with inter-batch delays (500-2000ms)
4. **Best Quality Selection**: Largest file size = best quality
5. **Fallback Chain**: If all 100 fail → UNRESTRICTED → Puter.js

### Previous v6.8.0 Features:
- Prompt Bypass System (sensitive words → artistic language)
- ✅ Fallback Chain - ADIMAGE → UNRESTRICTED → Puter.js

## Image Generation Priority Fixed:
- ✅ **ADIMAGE is now PRIMARY** - No need to say "adimage se" anymore
- ✅ **Tool Priority:** ADIMAGE → Puter.js → Pollinations
- ✅ **Fixed fake text responses** - Bot now actually calls tools instead of just describing images
- ✅ **CRITICAL TOOL USAGE RULES** added to ALL system prompts
- ✅ **Direct tool call** for image_generation now uses generate_adimage

---

# Previous Changes (v6.7.0) - 2025-12-12

## ADIMAGE.APP Integration Added:
- ✅ **New Tool:** `generate_adimage` - Uses ADIMAGE.APP API (Imagen 3.0)
- ✅ **FREE & Unlimited** - No API key required
- ✅ **High Quality PNG** - Direct Discord upload
- ✅ **Smart Prompt Enhancement** - AI-powered prompt improvement
- ✅ **Image History Tracking** - Saves to PostgreSQL database
- ✅ **Fallback Support** - Can be used if Puter.js fails

---

# Previous Changes (v6.6.0) - 2025-12-10

## Advanced Image Generation Suite Added:
1. ✅ **Style Generation** (`img2img_transform`) - Generate images in specific styles (anime, cyberpunk, ghibli, etc.)
2. ✅ **Outpaint Only** (`inpaint_outpaint`) - Extend image canvas using Sharp (REAL - downloads and processes actual image)
3. ✅ **Style Mixing** (`style_mixing`) - Combine multiple art styles in one image
4. ✅ **Portrait Generator** (`face_swap`) - Generate portrait/face images from descriptions
5. ✅ **AI Upscaling** (`ai_upscale`) - Upscale images using Sharp (REAL local processing up to 4K)
6. ✅ **Background Tool** (`background_tool`) - Process backgrounds with Sharp
7. ✅ **Pose Generator** (`controlnet_generate`) - Generate images with pose descriptions
8. ✅ **Multi-Image Grid** (`multi_image_grid`) - Generate 4 variations in 2x2 grid (REAL - uses Sharp)
9. ✅ **Image Remix** (`image_remix`) - Access history from DB and remix (REAL - uses PostgreSQL)

## File Attachment Limit Increased:
- **Old Limit:** 50KB
- **New Limit:** 25MB (25 * 1024 * 1024 bytes)

## All New Tools Use FREE APIs:
- Pollinations.ai (unlimited, no API key)
- Sharp library (local processing, unlimited)
- PostgreSQL for image history

---

# Previous Changes (v6.5.0) - 2025-11-28

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
