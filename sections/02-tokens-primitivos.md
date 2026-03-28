# 02 — Tokens Primitivos

Valores "crudos" del sistema. Los tokens semánticos de la capa 03 mapean desde estos.

## Paleta de color

### Fondos (dark surfaces)

| Token | Hex | Uso |
|-------|-----|-----|
| `--p-black` | `#030303` | Base background |
| `--p-surface-1` | `#0E0E10` | Primary surface (card) |
| `--p-surface-2` | `#16161A` | Raised surface (popover) |
| `--p-surface-3` | `#1E1E24` | Overlay surface (modal) |

### Acento primario — Teal

| Token | Hex | Uso |
|-------|-----|-----|
| `--p-teal-300` | `#5EEAD4` | Light teal |
| `--p-teal-400` | `#2DD4BF` | Bright teal / hover dark |
| `--p-teal-500` | `#14B8A6` | **PRIMARY brand color** |
| `--p-teal-600` | `#0D9488` | Dark teal / primary light mode |

### Acento secundario — Indigo

| Token | Hex | Uso |
|-------|-----|-----|
| `--p-indigo-400` | `#818CF8` | Light indigo / gradient end |
| `--p-indigo-500` | `#6366F1` | **SECONDARY accent** |
| `--p-indigo-600` | `#4F46E5` | Dark indigo / accent light mode |

### Texto y grises

| Token | Hex | Uso |
|-------|-----|-----|
| `--p-white` | `#FAFAFA` | Primary text (dark mode) |
| `--p-gray-100` | `#F4F4F5` | |
| `--p-gray-400` | `#A1A1AA` | Muted text |
| `--p-gray-500` | `#71717A` | Subtle text / inactive badge |
| `--p-gray-600` | `#52525B` | Subtle secondary |
| `--p-gray-700` | `#3F3F46` | |

### Feedback

| Token | Dark hex | Light hex |
|-------|----------|-----------|
| success | `#22C55E` | `#16A34A` |
| warning | `#F59E0B` | `#D97706` |
| danger | `#EF4444` | `#DC2626` |

## Tipografía

| Token | Valor |
|-------|-------|
| `--font-display` | Inter Display (local WOFF2) |
| `--font-body` | Inter (local WOFF2) |
| Fallback | `ui-sans-serif, system-ui, sans-serif` |

### Pesos disponibles (ambas familias)

| Peso | Nombre | Clase Tailwind |
|------|--------|----------------|
| 400 | Regular | `font-normal` |
| 500 | Medium | `font-medium` |
| 600 | SemiBold | `font-semibold` |
| 700 | Bold | `font-bold` |

> Solo usar estos 4 pesos. Nunca sintetizar negrita ni itálica.

## Espaciado y radio

| Token (primitivo) | Valor | Clase Tailwind (shadcn) |
|-------------------|-------|------------------------|
| `--radius-sm` | 4px | `rounded-sm` (`--radius - 4px`) |
| `--radius-md` | 6px | `rounded-md` (`--radius - 2px`) |
| `--radius-lg` | 12px | `rounded-xl` (`--radius + 4px`) ← **usar para cards** |
| `--radius-full` | 9999px | `rounded-full` ← **usar para CTAs y pills** |

> Nota: `rounded-lg` en shadcn = `var(--radius)` = 8px. Para cards (12px) usar `rounded-xl`.

## Gradientes de marca

```css
/* Texto destacado, hero graphics, indicadores premium — no en CTAs */
--gradient-brand: linear-gradient(90deg, #2DD4BF, #818CF8);

/* Fondos decorativos grandes */
--gradient-hero: linear-gradient(135deg, #0D9488 0%, #4F46E5 100%);
```

> **Uso en código:** estas variables contienen `linear-gradient(...)` — deben usarse como valor completo de `background`, no con `bg-[var(...)]` de Tailwind.
> ```tsx
> // Correcto
> <div style={{ background: 'var(--gradient-brand)' }} />
> // Incorrecto — no funciona en Tailwind
> <div className="bg-[var(--gradient-brand)]" />
> ```
