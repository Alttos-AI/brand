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
