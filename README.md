# /design - AI Design Skill for Claude Code

A skill that turns Claude Code into a complete design engine. Interactive quiz, 58 real-world design systems, automatic component research, cascading image generation (free > paid), and seamless project adoption.

## What's included

- **58 DESIGN.md** files extracted from real websites (Vercel, Stripe, Linear, Apple, Supabase, etc.)
- **INDEX.json** with classification by theme, mood, density, style
- **SKILL.md** with complete workflow (quiz > match > research > generate > refine > adopt)
- **design.md** (/design command)
- **Image cascade** - Pollinations (free) > Imagen 4 (~$0.02) > Nano Banana 2 (~$0.07)
- **shadcn/21st.dev integration** via MCP

## Installation (5 min)

### 1. Copy files

```bash
# Design systems (58 DESIGN.md)
cp -r design-systems/ ~/.claude/design-systems/

# Skill
mkdir -p ~/.claude/skills/design-system/
cp SKILL.md ~/.claude/skills/design-system/SKILL.md

# /design command
mkdir -p ~/.claude/commands/
cp design.md ~/.claude/commands/design.md
```

### 2. MCP servers (optional, recommended)

Add to `~/.claude/mcp.json`:

```json
{
  "mcpServers": {
    "shadcn": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@magnusrodseth/shadcn-mcp-server"]
    },
    "21st-magic": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@21st-dev/magic@latest"],
      "env": {
        "API_KEY": "YOUR_21ST_DEV_KEY"
      }
    }
  }
}
```

- shadcn: free, no key needed
- 21st.dev: free key at https://21st.dev/magic/console

### 3. Image cascade (optional)

To use Imagen 4 and Nano Banana 2, add to your shell profile:

```bash
export GEMINI_DESIGN_API_KEY="your_gemini_api_key"
```

Get a free key at https://aistudio.google.com/apikeys

Without this, Tier 1 (Pollinations/Flux) works for free with zero configuration.

### 4. Restart Claude Code

Restart to load the new skill and commands.

## Usage

```
/design                        # Full quiz
/design modern landing page    # Skips Q1, infers product type
/design stripe                 # Skips quiz, uses Stripe design system directly
```

### Workflow

1. Quiz (5 simple questions about what you're building)
2. Top 3 design systems suggested based on your answers
3. Automatic component research via shadcn/21st.dev
4. Generates standalone HTML preview (open in browser)
5. Refine as many times as you want
6. Adopt into your project (converts to React/Next.js components)

### Image generation

Images are generated using a cost-saving cascade:
- **Tier 1:** Pollinations/Flux (free) - default
- **Tier 2:** Imagen 4 Fast (~$0.02/img) - say "upgrade"
- **Tier 3:** Nano Banana 2 (~$0.07/img) - say "upgrade" again or "nb2"

## Included design systems

Airbnb, Airtable, Apple, BMW, Cal, Claude, Clay, ClickHouse, Cohere, Coinbase, Composio, Cursor, ElevenLabs, Expo, Ferrari, Figma, Framer, HashiCorp, IBM, Intercom, Kraken, Lamborghini, Linear, Lovable, Minimax, Mintlify, Miro, Mistral, MongoDB, Notion, NVIDIA, Ollama, OpenCode, Pinterest, PostHog, Raycast, Renault, Replicate, Resend, Revolut, RunwayML, Sanity, Sentry, SpaceX, Spotify, Stripe, Supabase, Superhuman, Tesla, Together.ai, Uber, Vercel, VoltAgent, Warp, Webflow, Wise, x.ai, Zapier

## Credits

- Design systems extracted from https://github.com/VoltAgent/awesome-design-md (MIT)
- Components via shadcn/ui and 21st.dev
