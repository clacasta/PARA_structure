# PARA_structure

Plantilla de estructura de carpetas basada en la metodología **PARA** de Tiago Forte (*Building a Second Brain*).

PARA organiza la información por **acción**, no por tema:

| Carpeta | Qué va aquí | Cuándo entra | Cuándo sale |
|---|---|---|---|
| `00_Inbox/` | Capturas rápidas sin clasificar | Inmediato | Tras procesar (< 1 semana) |
| `01_Projects/` | Proyectos con outcome + deadline | Al iniciar | Al completar → `04_Archives/` |
| `02_Areas/` | Responsabilidades y estándares a mantener | Al adquirir la responsabilidad | Al cerrar la responsabilidad → `04_Archives/` |
| `03_Resources/` | Temas de interés y referencias | Cuando te interesa y puede ser útil | Si queda obsoleto → `04_Archives/` |
| `04_Archives/` | Inactivos, conservados por valor histórico | Al cerrar proyecto / área / recurso | — |

## Cómo usar este repo

1. **Clona** o haz fork.
2. **Borra** el contenido de las subcarpetas (si lo hubiera) y crea las tuyas.
3. **Empieza** por `00_Inbox/`: cada captura nueva va ahí, y semanalmente la mueves a su PARA correspondiente.

## Estructura actual

```
PARA_structure/
├── 00_Inbox/         # capturas pendientes de clasificar
├── 01_Projects/      # proyectos con outcome + deadline
├── 02_Areas/         # responsabilidades a mantener en el tiempo
├── 03_Resources/     # temas de interés y referencias
└── 04_Archives/      # cerrado pero conservado
```

Cada carpeta incluye su propio `README.md` con el criterio PARA que decide qué va dentro.

## Licencia

MIT — úsalo, fórkalo, adáptalo a tu flujo.