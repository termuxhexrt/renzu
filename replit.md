# Overview

This Discord bot integrates with Mistral AI to provide an AI-powered conversational interface featuring optional autonomous learning and an intelligent skill learning system. Built with Node.js, it incorporates a dual-database architecture with Neon PostgreSQL and Supabase. The bot delivers natural, clean responses to all users with appropriate emojis and Hinglish support, aiming for an engaging and authentic user experience without manipulative psychology tactics.

**Production Mode**: By default, the bot runs in production mode with clean responses and minimal logging. Autonomous learning is DISABLED by default (enable via `ENABLE_AUTO_LEARNING=true`).

# Recent Changes (November 28, 2025)

## Smart Prompt Enhancement for Image Generation (v6.2.1)
- **AI-Powered Understanding**: Uses Mistral AI to understand user's actual intent from vague/broken prompts
- **Hinglish Support**: Perfect understanding of Hindi+English mix like "space veiw bana"
- **Intent Detection**: Fixes common misunderstandings (e.g., "space view" = outer space, NOT room)
- **Auto-Expansion**: Converts short prompts to detailed, descriptive image prompts
- **Developer Bypass**: Developer's DM prompts go as-is without modification
- **Applies To**: Non-developers everywhere + Developer in server channels (NOT developer in DM)
- **Graceful Fallback**: If enhancement fails, uses original prompt (no breaking changes)

### Example Enhancement:
```
User: "ek clean space veiw image bana"
Enhanced: "breathtaking view of outer space, deep cosmic void filled with millions 
of stars, colorful nebulae in purple and blue hues, distant galaxies, Milky Way 
galaxy core glowing, crystal clear night sky, NASA-style astrophotography"
```

## MASSIVE KNOWLEDGE BASE EXPANSION (v6.2.0)
- **120+ Topics Covered**: Complete world knowledge database for autonomous learning
- **Domains Included**: AI, cybersecurity, crypto, programming, Discord, tech, gaming, science, social media, security tools, productivity, business, mobile dev, databases, cloud, design, data science, career/education
- **Autonomous Learning**: Free unlimited learning on all topics (DuckDuckGo + Wikipedia rotation)
- **Knowledge Rotation**: 70% Wikipedia (reliable, no rate limits) + 30% DuckDuckGo (real-time data)
- **Enable**: Set `ENABLE_AUTO_LEARNING=true` to start autonomous knowledge absorption
- **No API Keys**: Completely free unlimited learning system 🔥

## File Attachment Reading (v6.1.0)
- **Text Files**: Reads .txt, .md, .json, .js, .py, .ts, .html, .css, .xml, .yaml, .csv, and 40+ more file types
- **PDF Detection**: Detects PDF files (text extraction requires additional library)
- **Smart Content Extraction**: Fetches file content from Discord CDN and includes in AI context
- **Size Limit**: Max 50KB per file to prevent token overflow
- **Auto-Detection**: Works in DMs, server channels, and with ?ask command
- **Code Files**: Full support for all major programming languages

## FREE Unlimited Web Search (v6.1.0)
- **Primary**: DuckDuckGo (duck-duck-scrape) - FREE, unlimited, no API key
- **Features**: Auto-retry, news fallback, related topics, instant answers
- **Removed**: Google Custom Search and SerpAPI dependency (were limited)
- **Fallback**: Simplified query retry on failure

## EXTREME Message Classification (v6.1.0)
- **3-Layer Analysis**: Instant pattern match → AI classification → Enhanced regex fallback
- **20+ Categories**: greeting, farewell, gratitude, casual_chat, emotional_support, simple_question, capability_query, image_generation, code_generation, web_search, file_analysis, url_fetch, security_tool, crypto_tool, math_calculation, translation, creative_writing, technical_query, feedback, meta_conversation
- **Multi-Dimensional**: Intent, emotion, urgency, complexity scoring
- **Hinglish Expert**: Perfect Hindi+English mix understanding
- **Anti-Misclassification**: Capability questions never trigger generation
- **Sub-millisecond**: Instant pattern matching for common messages

### Supported File Extensions
```
.txt, .md, .json, .js, .ts, .jsx, .tsx, .py, .java, .c, .cpp, .h,
.css, .html, .xml, .yaml, .yml, .ini, .cfg, .conf, .log, .csv,
.sh, .bash, .zsh, .ps1, .bat, .cmd, .sql, .env, .gitignore,
.dockerfile, .makefile, .gradle, .kt, .swift, .go, .rs, .rb, .php,
.lua, .r, .scala, .dart, .vue, .svelte, .astro
```

## Previous Changes (November 27, 2025)

### EXTREME Image Generation Upgrade
- **Maximum Resolution**: 2048x2048 pixels (MAX quality always)
- **Default Model**: `flux-realism` for photorealistic output
- **Smart Style Detection**: Auto-detects anime/3D/realistic from keywords
- **Quality Boost Prompts**: Auto-enhances every prompt with professional quality keywords
- **Negative Prompts**: Removes all defects (blur, artifacts, bad anatomy, etc.)
- **Fusion Mode**: Generate with multiple models in parallel

### Image Generation Quality Keywords (Auto-Applied)
**Positive Prompt Enhancement:**
```
masterpiece, best quality, ultra realistic, 8K UHD, RAW photo, highly detailed, 
sharp focus, professional photography, perfect composition, stunning lighting, 
no blur, no artifacts, anatomically correct, perfect proportions, photorealistic, 
cinematic lighting, HDR, intricate details
```

**Negative Prompt (Defect Removal):**
```
blurry, low quality, pixelated, jpeg artifacts, watermark, signature, text, logo, 
extra limbs, extra fingers, mutated hands, poorly drawn hands, poorly drawn face, 
mutation, deformed, ugly, bad anatomy, bad proportions, cloned face, malformed limbs, 
missing arms, missing legs, fused fingers, too many fingers, long neck, error, 
cropped, worst quality, grainy, distorted, amateur, bad lighting
```

### Available Models
| Model | Trigger Keywords | Best For |
|-------|------------------|----------|
| `flux-realism` | (default), realistic, photo, person, portrait | Photorealistic images |
| `flux-anime` | anime, manga, cartoon, waifu, kawaii | Anime/illustration |
| `flux-3d` | 3d, render, blender, cgi | 3D rendered images |

## Previous Changes (November 25, 2025)
- **Fixed duplicate message replies** - Implemented message processing lock (debounce)
- **Single-message responses** - ONE message or .txt file (no streaming chunks)
- **Optimized image replies** - Batches all images + text into ONE message
- **Autonomous learning control** - Disabled by default
- **Model upgrade** - Changed to `mistral-large-latest`

# User Preferences

Preferred communication style: Simple, everyday language (Hinglish supported).

# System Architecture

## Application Type
**Discord Bot with AI Integration**
- Runs as a persistent Node.js service using Express.js for health checks (port 5000).
- Employs an event-driven architecture, responding to Discord messages.

## Core Technologies
- **Runtime**: Node.js with ES6 modules
- **Discord Integration**: discord.js v14.24.2 with Gateway Intents
- **AI Provider**: Mistral AI SDK v1.10.0
- **Primary Database**: Neon PostgreSQL with `pg` driver
- **Cloud Database**: Supabase (file storage, real-time features, backup)
- **Image Generation**: Pollinations.ai API (FREE, no API key required)
- **HTTP Client**: node-fetch
- **Environment Management**: dotenv

## Bot Architecture
**Gateway Intents**: Utilizes Discord gateway intents for message and guild events.
**AI Function Calling**: Implements an advanced tool/function calling pattern with Mistral AI, enabling the bot to automatically select and execute appropriate tools based on natural language queries.
- **Tools**: Includes 160+ advanced tools covering security, OSINT, crypto, image generation, code generation, web search, and developer-specific tools.
- **Self-Awareness System**: Tracks bot version and maintains an update history.
- **Developer Recognition System**: Identifies the developer by Discord user ID for unrestricted access.

## Image Generation System (EXTREME Mode + KONTEXT)

### Primary: Puter.js with KONTEXT Models (FREE - No API Key)
**Provider**: Puter.js SDK (black-forest-labs/FLUX.1-kontext)
**Resolution**: Up to 1920x1080
**Why KONTEXT?**: Better for complex objects (vehicles, machinery, people) - fewer distortions

| Model | ID | Best For |
|-------|-----|----------|
| `kontext-max` | FLUX.1-kontext-max | BEST quality, complex realistic |
| `kontext-pro` | FLUX.1-kontext-pro | High quality |
| `kontext-dev` | FLUX.1-kontext-dev | Faster, good quality |
| `imagen-4` | google/imagen-4.0-fast | Google Imagen 4 |
| `dall-e-3` | dall-e-3 | OpenAI DALL-E 3 |
| `sd3` | stable-diffusion-3-medium | Stable Diffusion 3 |

### Fallback: Pollinations.ai (If Puter.js fails)
**Resolution**: 2048x2048 (Maximum)
**Features**:
- Smart style detection (realistic/anime/3D)
- Auto quality enhancement prompts
- Negative prompts for defect removal
- Fusion mode (parallel model generation)
- Direct Discord upload (no URL links)

**Safety Features**:
- **Timeout Handling**: 60 second timeout for large images (prevents hanging)
- **URL Length Safety**: Auto-truncates prompts if URL exceeds safe length (~1800 chars)
- **Graceful Degradation**: If prompt too long, keeps essential quality keywords
- **AbortController**: Clean cancellation of stuck requests
- **Dual Provider**: Puter.js primary, Pollinations fallback

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
**Express Server**: A minimal HTTP server on port 5000 for health checks.

# External Dependencies

## AI Service
- **Mistral AI**: Primary LLM provider for conversational responses and function calling.

## Communication Platform
- **Discord API**: Handles message delivery and bot presence.

## Database
- **PostgreSQL**: Relational database for persistent storage.

## Image Generation
- **Pollinations.ai**: FREE image generation API with multiple models (flux-realism, flux-anime, flux-3d).

## API Keys / Services (Conditional)
- **SerpAPI**: For web search and CVE lookup.
- **Shodan**: For internet-wide scanning.
- **VirusTotal**: For file hash checking.
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
