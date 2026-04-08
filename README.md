# /design - AI Design Skill for Claude Code

A skill that turns Claude Code into a complete design engine. Interactive quiz, 58 real-world design systems, industry-specific design intelligence, automatic component research, cascading image generation (free > paid), and seamless project adoption.

## What's included

### Visual references (58 real-world design systems)
- **58 DESIGN.md** files extracted from real websites (Vercel, Stripe, Linear, Apple, Supabase, etc.) with exact hex values, shadows, typography, component specs
- **INDEX.json** with classification by theme, mood, density, style

### Design intelligence (from UI UX Pro Max)
- **161 color palettes** - complete design token sets (Primary, Secondary, Accent, Background, Card, Border, Ring) per product type, WCAG-adjusted
- **73 font pairings** - with Google Fonts URL, CSS import, and Tailwind config ready to paste
- **161 industry reasoning rules** - maps product type to recommended pattern, style, colors, typography, effects, and anti-patterns
- **99 UX guidelines** - with do/don't and code examples, covering accessibility, touch, animation, forms, navigation
- **34 landing page patterns** - section order, CTA placement, conversion strategies
- **85 UI styles** - from Minimalism to Glassmorphism to Cyberpunk, with 22 attributes each
- **25 chart types** - with library recommendations and accessibility grades
- **16 framework-specific guidelines** - React, Next.js, Vue, Svelte, shadcn, Tailwind, and more

### Workflow
- **SKILL.md** with complete 6-phase workflow (quiz > match > research > generate > refine > adopt)
- **design.md** (/design command)
- **Image cascade** - Pollinations (free) > Imagen 4 (~$0.02) > Nano Banana 2 (~$0.07)
- **Component research** via shadcn/21st.dev MCP integration
- **UX quality gate** - silently validates against 99 UX guidelines before delivery

## Installation (5 min)

### 1. Copy files

```bash
# Everything (design systems + intelligence data + skill)
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

Get a key at https://aistudio.google.com/apikeys

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

1. **Quiz** - 5 simple questions about what you're building
2. **Match** - Top 3 design systems + industry intelligence (colors, fonts, patterns, anti-patterns)
3. **Component research** - automatic search via shadcn/21st.dev MCP
4. **Generate** - standalone HTML preview with Tailwind + Google Fonts (open in browser)
5. **Refine** - as many times as you want
6. **Adopt** - converts to real framework components with framework-specific guidelines applied
7. **UX quality gate** - silently validates accessibility, touch targets, typography, animations

### Image generation

Images are generated using a cost-saving cascade:
- **Tier 1:** Pollinations/Flux (free) - default
- **Tier 2:** Imagen 4 Fast (~$0.02/img) - say "upgrade"
- **Tier 3:** Nano Banana 2 (~$0.07/img) - say "upgrade" again or "nb2"

## Included design systems

Airbnb, Airtable, Apple, BMW, Cal, Claude, Clay, ClickHouse, Cohere, Coinbase, Composio, Cursor, ElevenLabs, Expo, Ferrari, Figma, Framer, HashiCorp, IBM, Intercom, Kraken, Lamborghini, Linear, Lovable, Minimax, Mintlify, Miro, Mistral, MongoDB, Notion, NVIDIA, Ollama, OpenCode, Pinterest, PostHog, Raycast, Renault, Replicate, Resend, Revolut, RunwayML, Sanity, Sentry, SpaceX, Spotify, Stripe, Supabase, Superhuman, Tesla, Together.ai, Uber, Vercel, VoltAgent, Warp, Webflow, Wise, x.ai, Zapier

## Credits

- Design systems extracted from [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) (MIT)
- Design intelligence data from [ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (MIT)
- Components via [shadcn/ui](https://ui.shadcn.com) and [21st.dev](https://21st.dev)
