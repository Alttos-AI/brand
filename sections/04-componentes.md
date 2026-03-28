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
