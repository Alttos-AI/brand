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
