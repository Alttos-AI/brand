# Alttos.ai Brand Identity Manual

> Single source of truth for visual identity, design tokens, voice, and component patterns across the Alttos.ai ecosystem.

## For AI models (Claude Code, etc.)

Fetch the full manual in one request:

```
https://raw.githubusercontent.com/alttos-ai/brand/main/BRAND.md
```

Or load only the section you need:
- `sections/03-tokens-shadcn.md` — shadcn/ui globals.css (dark + light)
- `sections/04-componentes.md` — component anatomy and Tailwind classes
- `sections/05-layout.md` — dashboard shell and layout patterns

## For humans

| Section | Contents |
|---------|----------|
| [01 — Marca](sections/01-marca.md) | Logo, tagline, brand values |
| [02 — Tokens Primitivos](sections/02-tokens-primitivos.md) | Hex colors, typography, spacing |
| [03 — Tokens shadcn](sections/03-tokens-shadcn.md) | globals.css for dark + light mode |
| [04 — Componentes](sections/04-componentes.md) | Buttons, badges, cards, inputs |
| [05 — Layout](sections/05-layout.md) | Dashboard shell, sidebar, grid |
| [06 — Voz](sections/06-voz.md) | Tone, module names, UI copy |

## Ecosystem

All apps in the Alttos.ai ecosystem reference this manual. To add the reference to a new project, add to `CLAUDE.md`:

```markdown
## Brand Manual
Brand manual: https://raw.githubusercontent.com/alttos-ai/brand/main/BRAND.md
Consult before making any UI, token, naming, or copy decisions.
When building dashboards: load sections/03-tokens-shadcn.md for globals.css values.
```
