# assets

Design Tokens y estilos CSS del Documentation Framework, consumidos por los diagramas HTML en `docs/architecture/diagrams/` (por ejemplo `architecture-overview.html`).

| Archivo | Propósito |
|---|---|
| `css/reset.css` | Reset base. |
| `css/tokens.css` | Design Tokens (color, espaciado, tipografía). |
| `css/typography.css` | Escala tipográfica. |
| `css/layout.css` | Estructura de layout (`dds-shell`, grillas). |
| `css/components.css` | Componentes reutilizables (`dds-header`, `dds-hero`, `dds-badge`, etc.). |
| `css/diagrams.css` | Estilos específicos para la representación de diagramas. |
| `css/utilities.css` | Utilidades de espaciado y color (`p-xl`, `mt-md`, `bg-default`, etc.). |
| `css/print.css` | Reglas para impresión A4 (`diagram-rules.md` exige que todo diagrama sea imprimible). |

Estos estilos son consumidos localmente por este proyecto; el framework oficial (`AI-SDOS-DDS`, ver `documentation-framework.md`) es la fuente de verdad conceptual para Design Tokens, Components y Patterns.
