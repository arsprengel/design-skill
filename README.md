# /design - AI Design Skill for Claude Code

Skill que transforma o Claude Code em um design engine completo. Quiz interativo, 58 design systems reais, pesquisa automatica de componentes, geracao de imagens em cascata (gratis > pago), e adocao direto no projeto.

## O que inclui

- **58 DESIGN.md** extraidos de sites reais (Vercel, Stripe, Linear, Apple, Supabase, etc.)
- **INDEX.json** com classificacao por tema, mood, densidade, estilo
- **SKILL.md** com workflow completo (quiz > match > pesquisa > gera > refina > aplica)
- **design.md** (comando /design)
- **Cascade de imagens** - Pollinations (gratis) > Imagen 4 (~R$0.11) > Nano Banana 2 (~R$0.38)
- **Integracao shadcn/21st.dev** via MCP

## Instalacao (5 min)

### 1. Copiar arquivos

```bash
# Design systems (58 DESIGN.md)
cp -r design-systems/ ~/.claude/design-systems/

# Skill
mkdir -p ~/.claude/skills/design-system/
cp SKILL.md ~/.claude/skills/design-system/SKILL.md

# Comando /design
mkdir -p ~/.claude/commands/
cp design.md ~/.claude/commands/design.md
```

### 2. MCPs (opcional, recomendado)

Adicionar ao `~/.claude/mcp.json`:

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
        "API_KEY": "SUA_KEY_DO_21ST_DEV"
      }
    }
  }
}
```

- shadcn: gratis, sem key
- 21st.dev: key gratis em https://21st.dev/magic/console

### 3. Cascade de imagens (opcional)

Para usar Imagen 4 e Nano Banana 2, adicionar ao `~/.bashrc`:

```bash
export GEMINI_DESIGN_API_KEY="sua_gemini_api_key"
```

Pegar key gratis em https://aistudio.google.com/apikeys

Sem isso, o Tier 1 (Pollinations/Flux) funciona gratis sem configuracao.

### 4. Reiniciar Claude Code

```bash
# Sair e entrar novamente para carregar tudo
```

## Uso

```
/design                        # Quiz completo
/design landing page moderna   # Pula Q1, infere tipo
/design stripe                 # Vai direto pro design system
```

### Fluxo

1. Quiz (5 perguntas simples sobre o que voce quer)
2. Top 3 design systems sugeridos
3. Pesquisa automatica de componentes no shadcn/21st.dev
4. Gera preview HTML (abre no browser)
5. Refina quantas vezes quiser
6. Aplica no projeto (converte pra React/Next.js)

### Imagens

O sistema de imagens funciona em cascata:
- Tier 1: Pollinations/Flux (gratis) - padrao
- Tier 2: Imagen 4 Fast (~R$0.11) - diga "upgrade"
- Tier 3: Nano Banana 2 (~R$0.38) - diga "upgrade" de novo ou "nb2"

## Design systems inclusos

Airbnb, Airtable, Apple, BMW, Cal, Claude, Clay, ClickHouse, Cohere, Coinbase, Composio, Cursor, ElevenLabs, Expo, Ferrari, Figma, Framer, HashiCorp, IBM, Intercom, Kraken, Lamborghini, Linear, Lovable, Minimax, Mintlify, Miro, Mistral, MongoDB, Notion, NVIDIA, Ollama, OpenCode, Pinterest, PostHog, Raycast, Renault, Replicate, Resend, Revolut, RunwayML, Sanity, Sentry, SpaceX, Spotify, Stripe, Supabase, Superhuman, Tesla, Together.ai, Uber, Vercel, VoltAgent, Warp, Webflow, Wise, x.ai, Zapier

## Creditos

- Design systems extraidos de https://github.com/VoltAgent/awesome-design-md (MIT)
- Componentes via shadcn/ui e 21st.dev
