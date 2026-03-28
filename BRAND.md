# Alttos.ai — Brand Identity Manual

> Single source of truth for visual identity, design tokens, voice, and component patterns.
> **For AI models:** This file contains the full manual. Load it with WebFetch and apply directly.
> Last updated: 2026-03-28

---

# 01 — Marca

## Nombre y dominio

- **Marca:** Alttos
- **Dominio:** alttos.ai
- **Regla:** `.ai` siempre en teal (#14B8A6) cuando se escribe el dominio completo en UI.

## Logo

- Marca geométrica isométrica (poliedro de 7 caras), fill blanco (#FFFFFF).
- Wordmark: "Alttos" en Inter Display Bold + ".ai" en teal (#14B8A6).
- Archivo SVG: `assets/alttos-logo.svg`

### Tamaños de uso

| Contexto | Tamaño |
|----------|--------|
| Topbar / header | 28px |
| Footer | 24px |
| Favicon PNG | 512×512px |
| Apple touch icon | 180×180px |

### Regla de fondo

El SVG del logo es white-only. **El topbar y el header del sidebar siempre usan fondo oscuro (`#0E0E10`) independientemente del modo claro/oscuro de la app**, de modo que el logo blanco siempre sea legible.

> Variante para fondo claro: pendiente (P1 para lanzamiento de light mode).

## Tagline

| Contexto | Texto |
|----------|-------|
| Marketing / landing | "Sistemas de IA para empresas" |
| Apps / UI | "Tu empresa, automatizada" |

## Valores de marca

**Velocidad · Confianza · Resultado · Simplicidad**

## Foco geográfico

Colombia · Latam · España

## Posicionamiento

Alttos automatiza la atención al cliente y los procesos empresariales de PYMEs con IA — chatbots, agentes de voz y flujos personalizados que trabajan 24/7.


---

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


---

# 03 — Tokens Semánticos × shadcn/ui

Valores para pegar directamente en `globals.css` de cualquier proyecto de dashboard que use shadcn/ui.

## Dark mode

```css
.dark {
  /* Backgrounds */
  --background: 0 0% 1%;           /* #030303 */
  --foreground: 0 0% 98%;          /* #FAFAFA */
  --card: 240 5% 6%;               /* #0E0E10 */
  --card-foreground: 0 0% 98%;
  --popover: 240 6% 10%;           /* #16161A */
  --popover-foreground: 0 0% 98%;

  /* Primary = Teal — Button default, focus rings */
  --primary: 174 80% 40%;          /* #14B8A6 */
  --primary-foreground: 0 0% 0%;   /* texto negro sobre teal */

  /* Secondary = dark surface */
  --secondary: 240 5% 12%;         /* #1E1E24 */
  --secondary-foreground: 0 0% 98%;

  /* Muted */
  --muted: 240 5% 12%;
  --muted-foreground: 240 5% 65%;  /* #A1A1AA */

  /* Accent = Indigo — nav hover, badges de categoría */
  --accent: 239 84% 67%;           /* #6366F1 */
  --accent-foreground: 0 0% 98%;

  /* Destructive */
  --destructive: 0 84% 60%;        /* #EF4444 */
  --destructive-foreground: 0 0% 98%;

  /* Borders & inputs
     Nota: valores opacos HSL — colocar solo sobre fondos oscuros conocidos */
  --border: 240 5% 12%;
  --input: 240 6% 10%;             /* #16161A = --p-surface-2 */
  --ring: 174 80% 40%;             /* teal focus ring = --primary */

  /* Charts (shadcn Chart components) */
  --chart-1: 174 80% 40%;          /* teal — serie primaria */
  --chart-2: 239 84% 67%;          /* indigo — serie secundaria */
  --chart-3: 38 92% 50%;           /* amber #F59E0B */
  --chart-4: 142 71% 45%;          /* green #22C55E */
  --chart-5: 350 89% 60%;          /* rose #F43F5E */
  --chart-6: 217 91% 60%;          /* blue #3B82F6 */

  --radius: 0.5rem;
}
```

## Light mode

```css
:root {
  /* Backgrounds */
  --background: 210 40% 98%;       /* #F8FAFC */
  --foreground: 222 47% 11%;       /* #0F172A */

  /* --card = blanco para contenido. Sidebar usa --secondary (ver Layout).
     Topbar siempre usa fondo oscuro (#0E0E10) en ambos modos. */
  --card: 0 0% 100%;               /* #FFFFFF */
  --card-foreground: 222 47% 11%;
  --popover: 0 0% 100%;
  --popover-foreground: 222 47% 11%;

  /* Primary = Teal-600 — más oscuro para contraste WCAG sobre blanco */
  --primary: 174 84% 31%;          /* #0D9488 */
  --primary-foreground: 0 0% 100%;

  /* Secondary — usar como fondo del sidebar en light mode */
  --secondary: 210 40% 96%;        /* #F1F5F9 */
  --secondary-foreground: 222 47% 11%;

  /* Muted */
  --muted: 210 40% 96%;
  --muted-foreground: 215 16% 47%; /* #64748B */

  /* Accent = Indigo-600 — más oscuro para light bg */
  --accent: 243 75% 59%;           /* #4F46E5 */
  --accent-foreground: 0 0% 100%;

  /* Destructive */
  --destructive: 0 84% 60%;        /* #EF4444 */
  --destructive-foreground: 0 0% 100%;

  /* Borders & inputs */
  --border: 214 32% 91%;           /* #E2E8F0 */
  --input: 214 32% 91%;
  --ring: 174 84% 31%;             /* = --primary */

  /* Charts (shadcn Chart components) */
  --chart-1: 174 84% 31%;          /* teal-600 */
  --chart-2: 243 75% 59%;          /* indigo-600 */
  --chart-3: 38 92% 45%;           /* amber #D97706 */
  --chart-4: 142 71% 38%;          /* green #16A34A */
  --chart-5: 350 89% 55%;          /* rose #E11D48 */
  --chart-6: 217 91% 55%;          /* blue #2563EB */

  --radius: 0.5rem;
}
```

## Decisiones clave

| Variable shadcn | Rol Alttos | Por qué |
|-----------------|-----------|---------|
| `--primary` | Teal (`#14B8A6` dark / `#0D9488` light) | `<Button>` default — color de acción primaria |
| `--accent` | Indigo (`#6366F1` dark / `#4F46E5` light) | Nav hover, badges de categoría — nunca en CTAs |
| `--ring` | Teal (igual que `--primary`) | Focus ring consistente con la identidad |
| `--radius` | `0.5rem` → `rounded-md` = 6px vía offset shadcn | Consistente con el landing |
| `--chart-1…6` | Teal, Indigo, Amber, Green, Rose, Blue | Visualizaciones de datos multi-serie |

## Cómo usar en un proyecto nuevo

1. En `app/globals.css` (o equivalente), agregar los bloques `:root` y `.dark` de arriba.
2. Asegurarse que el `<html>` tenga clase `.dark` cuando corresponda (next-themes, etc.).
3. No redefinir variables shadcn en componentes individuales — extender con clases custom.


---

# 04 — Componentes

Todos los componentes se construyen con primitivos de shadcn/ui. Las clases custom extienden, nunca reemplazan.

## Botones

| Variante | shadcn variant | Descripción visual |
|----------|---------------|-------------------|
| Primary CTA | `default` | bg teal, texto negro, `rounded-full`, sombra teal |
| Secondary | `outline` | borde `--border-strong`, bg transparente, `rounded-md` |
| Ghost | `ghost` | transparente, hover sutil |
| Danger | `destructive` | bg red/12, texto red, borde red/20 |
| Disabled | any + `disabled` | opacity 50%, `cursor-not-allowed` |

### Override para Primary CTA (agregar a globals.css)

```css
.btn-cta {
  border-radius: 9999px;
  box-shadow: 0 0 40px hsl(var(--primary) / 0.25);
}
.btn-cta:hover {
  filter: brightness(1.1);
  transform: scale(1.03);
}
.btn-cta:active {
  transform: scale(0.98) translateY(1px);
}
```

```tsx
<Button className="btn-cta">Conectar modelo</Button>
```

## Badges / Pills de estado

Estructura: `bg-[color]/12 border border-[color]/30 text-[color] rounded-full text-xs font-semibold uppercase tracking-wide`

| Estado | Color base | Ejemplo Tailwind |
|--------|-----------|-----------------|
| Activo | teal (`--primary`) | `bg-primary/12 border-primary/30 text-primary` |
| Pendiente | amber (`#F59E0B`) | `bg-amber-500/12 border-amber-500/30 text-amber-500` |
| Error | red (`--destructive`) | `bg-destructive/12 border-destructive/30 text-destructive` |
| IA / AI | indigo (`--accent`) | `bg-accent/12 border-accent/30 text-accent` |
| Inactivo | muted (`#71717A`) | `bg-muted border-border text-muted-foreground` |

### Dot de estado (opcional)

```tsx
<span className="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-full bg-primary/12 border border-primary/30 text-primary text-xs font-semibold uppercase tracking-wide">
  <span className="w-1.5 h-1.5 rounded-full bg-primary animate-pulse" />
  Activo
</span>
```

## Cards

| Tipo | Border | Background | Uso |
|------|--------|-----------|-----|
| Stat card | `border-border` | `bg-card` | Métricas KPI |
| Module card (activo) | `border-primary/25` + `shadow-[0_0_20px_hsl(var(--primary)/0.05)]` | `bg-card` | Modelos IA activos, canales |
| Empty state | `border-dashed border-border` | `bg-card` | Prompt para agregar primer item |

```tsx
// Card hover — aplicar a todas las cards interactivas
className="transition-all duration-200 hover:-translate-y-0.5 hover:border-primary/40 cursor-pointer"
```

### Stat card completa

```tsx
<div className="bg-card border border-border rounded-xl p-6 flex flex-col gap-1">
  <p className="text-xs font-semibold text-muted-foreground uppercase tracking-wide">
    Conversaciones
  </p>
  <p className="text-2xl font-medium tracking-tight">1,284</p>
  <p className="text-xs text-green-500">↑ 12% esta semana</p>
</div>
```

## Inputs

```tsx
// Label estándar
<label className="text-xs font-semibold text-muted-foreground uppercase tracking-wide mb-1.5 block">
  Nombre del asistente
</label>

// Input estándar (shadcn <Input /> lo aplica via --input y --ring)
<Input placeholder="ej. Alttos Chat v2" />

// Select estándar (shadcn <Select />)
<Select>
  <SelectTrigger>
    <SelectValue placeholder="Seleccionar modelo" />
  </SelectTrigger>
  <SelectContent>
    <SelectItem value="claude-sonnet-4-6">claude-sonnet-4-6</SelectItem>
  </SelectContent>
</Select>
```

Estados:
- Default: `--border`
- Focus: `--primary` + `ring-2 ring-primary/30` (automático en shadcn vía `--ring`)
- Error: `--destructive` — agregar `className="border-destructive"` al Input

## Sidebar navigation item

```tsx
// Activo
<Link className="flex items-center gap-3 px-3 py-2 rounded-md text-sm font-medium bg-primary/10 text-primary transition-colors">
  <Icon className="w-4 h-4" />
  Dashboard
</Link>

// Inactivo
<Link className="flex items-center gap-3 px-3 py-2 rounded-md text-sm text-muted-foreground hover:bg-secondary hover:text-foreground transition-colors">
  <Icon className="w-4 h-4" />
  Modelos IA
</Link>
```


---

# 05 — Patrones de Layout

## App Shell del Dashboard

```
┌─────────────────────────────────────────────┐
│  Topbar (h-14 = 56px, sticky top-0, z-40)   │
├────────────────┬────────────────────────────┤
│                │                            │
│  Sidebar       │  Content area              │
│  w-[220px]     │  p-6 bg-background         │
│  bg-card (D)   │  flex-1 overflow-y-auto    │
│  bg-secondary  │                            │
│  (L)           │                            │
│  z-30          │                            │
└────────────────┴────────────────────────────┘
```

`(D)` = dark mode · `(L)` = light mode

### Topbar

```tsx
<header className="sticky top-0 z-40 h-14 bg-card border-b border-border flex items-center px-4 gap-4">
  {/* Logo — siempre sobre fondo oscuro (#0E0E10 = bg-card en dark) */}
  <div className="flex items-center gap-2">
    <img src="/alttos-logo.svg" alt="Alttos" className="w-7 h-7" />
    <span className="font-bold text-base">
      Alttos<span className="text-primary">.ai</span>
    </span>
  </div>

  {/* Breadcrumb / módulo actual */}
  <span className="text-sm text-muted-foreground">/ Hub</span>

  {/* Spacer */}
  <div className="flex-1" />

  {/* Acciones de usuario */}
  <Button variant="ghost" size="icon"><Bell className="w-4 h-4" /></Button>
  <Avatar className="w-8 h-8" />

  {/* Mobile: hamburger — visible solo en < md */}
  <Button variant="ghost" size="icon" className="md:hidden" onClick={openSidebar}>
    <Menu className="w-5 h-5" />
  </Button>
</header>
```

### Sidebar — Desktop

```tsx
<aside className="
  hidden md:flex flex-col
  w-[220px] shrink-0
  sticky top-14 h-[calc(100dvh-56px)]
  bg-secondary dark:bg-card
  border-r border-border
  overflow-y-auto
  p-3 gap-1
  z-30
">
{/* bg-secondary en light (#F1F5F9) · bg-card en dark (#0E0E10).
    Requiere que el proveedor de temas (next-themes, etc.) añada
    clase .dark al <html> en dark mode. */}
  {/* Nav items — ver sección 04 Componentes */}
</aside>
```

### Sidebar — Mobile (Sheet)

```tsx
import { Sheet, SheetContent } from "@/components/ui/sheet"

<Sheet open={open} onOpenChange={setOpen}>
  <SheetContent side="left" className="w-[220px] p-3">
    {/* Mismo contenido que sidebar desktop */}
  </SheetContent>
</Sheet>
```

- Trigger: botón hamburger en topbar (visible solo `< md`)
- Tipo: `side="left"`, ancho fijo `w-[220px]`
- El `SheetContent` hereda `bg-card` de shadcn

### Content area

```tsx
<main className="flex-1 overflow-y-auto p-6">
  {/* Page title */}
  <div className="mb-6">
    <h1 className="text-2xl font-medium tracking-tight">Dashboard</h1>
    <p className="text-sm text-muted-foreground mt-1">Bienvenido — hoy es viernes</p>
  </div>

  {/* Stat row */}
  <div className="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
    {/* <StatCard /> × N */}
  </div>

  {/* Main grid */}
  <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
    {/* Cards de módulo, tablas, etc. */}
    {/* Full-width: col-span-full */}
  </div>
</main>
```

## Breakpoints

| Breakpoint | px | Cambio |
|-----------|-----|--------|
| `sm` | 640px | (no usado en dashboard shell) |
| `md` | 768px | Sidebar visible; stat grid 4 columnas |
| `lg` | 1024px | Content grid 3 columnas |
| `xl` | 1280px | (contenido interno puede expandirse) |

## Escala tipográfica — Dashboard

Adopta la escala de Tailwind. Desviaciones específicas para dashboards:

| Rol | Clase Tailwind | Familia | Uso |
|-----|---------------|---------|-----|
| Page title | `text-2xl font-medium tracking-tight` | Inter Display | Nombre de la página/módulo |
| Section title | `text-lg font-medium` | Inter Display | Títulos de sección dentro de la página |
| Body | `text-sm` (14px) | Inter | Párrafos, descripciones — más denso que landing (16px) |
| Label | `text-xs font-semibold uppercase tracking-wide text-muted-foreground` | Inter | Labels de inputs, column headers de tabla |
| Caption | `text-[11px] text-muted-foreground` | Inter | Timestamps, notas al pie |
| Stat number | `text-2xl font-medium tracking-tight` | Inter Display | Valores numéricos en stat cards |

> Inter Display se carga como custom font. En proyectos donde no esté disponible, Inter regular es el fallback.


---

# 06 — Voz & Mensajería

## Tono

### Sí ✓
- Directo, sin jerga técnica innecesaria
- Orientado a resultados: "Guardado", "Listo", "Conectado"
- Empático en errores: "Algo salió mal — intenta de nuevo"
- Activo en confirmaciones: "Asistente activado"
- Tuteo consistente (tú) en toda la UI
- Español neutro latinoamericano como idioma primario

### No ✗
- Tecnicismos sin contexto: ~~"API endpoint configured"~~
- Pasivo en acciones: ~~"El proceso ha sido completado"~~
- Mezclar usted/tú dentro del mismo flujo
- Errores vagos: ~~"Error 500"~~
- Mayúsculas innecesarias en labels: ~~"NOMBRE DEL ASISTENTE"~~ → "Nombre del asistente"
- Exclamaciones excesivas: ~~"¡Tu asistente está listo!"~~ → "Asistente listo"

## Nombres de módulo

Patrón: **Alttos [sustantivo en inglés]** — consistente entre idiomas.

| Módulo | Nombre oficial | Ruta |
|--------|---------------|------|
| Dashboard principal | **Alttos Hub** | `/dashboard` |
| Modelos IA y asistentes | **Alttos Mind** | `/models` |
| Canales de atención | **Alttos Channels** | `/channels` |
| Facturación | **Alttos Finance** | `/finance` |
| Bases de datos | **Alttos Data** | `/data` |

> Los nombres son ajustables. El **patrón** (Alttos + sustantivo en inglés) es obligatorio.

## Copy estándar de UI

| Situación | Español |
|-----------|---------|
| Carga genérica | "Cargando…" |
| Carga específica | "Conectando con [Modelo]…" |
| Cambio guardado | "Guardado" |
| Módulo activado | "[Nombre] activado" |
| API conectada | "Conexión establecida" |
| Error genérico | "Algo salió mal. Intenta de nuevo." |
| Error de conexión | "No se pudo conectar — verifica tu API key" |
| Sin internet | "Sin conexión a internet" |
| Sesión expirada | "Sesión expirada — inicia sesión de nuevo" |
| Estado vacío | "Aún no tienes [módulos] — [CTA]" |
| Sin resultados | "Sin resultados para tu búsqueda" |

## Reglas de idioma

| Tipo | Regla |
|------|-------|
| Nombres de módulo | Siempre en inglés: "Alttos Finance", nunca "Alttos Finanzas" |
| UI copy | Español neutro latinoamericano por defecto |
| Términos técnicos sin traducción natural | Mantener en inglés: "API key", "webhook", "token", "prompt" |
| i18n | Clave en inglés, valor en español: `{ "saved": "Guardado" }` |
