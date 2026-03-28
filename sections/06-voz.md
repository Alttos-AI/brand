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
