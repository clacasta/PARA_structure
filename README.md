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

## Uso con Obsidian

Obsidian trata cada carpeta como un conjunto de notas indexado. PARA encaja tal cual porque Obsidian no exige jerarquías temáticas — solo carpetas planas con `[[wikilinks]]` entre notas.

**Ajustes recomendados dentro de Obsidian:**

- **Tratar `00_Inbox/` como la "Quick Add" nativa** — Obsidian tiene un plugin core (*"Capture"*) o puedes vincular la carpeta al plugin *QuickAdd* para que cada captura aterrice ahí sin pensar.
- **No crear subcarpetas dentro de cada PARA** durante semanas; deja que los `[[wikilinks]]` y los *tags* emerjan solos. Subdividir prematuramente es el anti-PARA clásico.
- **Usar el plugin *Dataview*** para listar notas por PARA:
  ```dataview
  TABLE deadline, status
  FROM "01_Projects"
  SORT deadline ASC
  ```
- **Mapas de contenido (MOCs)** en `02_Areas/` — un `MOC.md` por área que enlaza a todas las notas relacionadas, sin duplicar la nota original.
- **Vault como git repo** — sincroniza el vault con este repositorio (o con uno paralelo) usando el plugin *Obsidian Git* para tener backup y versionado.

## Uso con LLMs (Claude, GPT, modelos locales)

PARA es una estructura amigable para asistentes IA porque da contexto de **para qué existe cada nota** sin tener que leer todo el vault.

**Patrones prácticos:**

- **Inbox triage con LLM.** Pasa el contenido de `00_Inbox/` a un modelo con un prompt tipo *"Clasifica cada captura en Project / Area / Resource, sugiere nombre de archivo y carpeta destino"*. La sección "00_Inbox — Reglas" del README de Inbox ya le da al modelo el criterio que necesita.
- **Recuperación aumentada (RAG).** Indexa solo las carpetas activas (`01_Projects` + `02_Areas`) — `04_Archives` rara vez es contexto útil y dispara tokens. PARA hace ese filtro trivial.
- **Memoria persistente del agente.** Apunta al agente a `02_Areas/<área>` como su nota de referencia canónica antes de cada conversación larga. Acotar por PARA = menos ruido = menos alucinaciones.
- **Plantillas por carpeta.** Define un *template* distinto en Obsidian para Projects (`tasks.md`, `deadline`, `outcome`) y Areas (`checklists.md`, `criterio de salud`). El LLM aprende el formato tras 2-3 ejemplos.
- **Frontmatter uniforme.** Un YAML mínimo en cada nota (`type: project|area|resource|archive`, `status:`, `tags:`) permite que el LLM clasifique y filtre con `jq` antes de pasarle el contenido.

> Regla de oro: la IA clasifica y resume, **tú decides**. PARA le da al modelo el "dónde va", pero el juicio de prioridad sigue siendo humano.

## License / Licencia

MIT — úsalo, fórkalo, adáptalo a tu flujo.

---

# PARA_structure (English)

Folder-structure template based on Tiago Forte's **PARA** method (*Building a Second Brain*).

PARA organizes information by **action**, not by topic:

| Folder | What goes here | When it enters | When it leaves |
|---|---|---|---|
| `00_Inbox/` | Unclassified quick captures | Immediately | After processing (< 1 week) |
| `01_Projects/` | Projects with outcome + deadline | When started | When done → `04_Archives/` |
| `02_Areas/` | Responsibilities and standards to maintain | When you take ownership | When you stop owning it → `04_Archives/` |
| `03_Resources/` | Topics of interest and references | When it's useful to you | When it becomes outdated → `04_Archives/` |
| `04_Archives/` | Inactive, kept for historical value | When the project/area/resource closes | — |

## How to use this repo

1. **Clone** or fork it.
2. **Clear** the contents of each subfolder (if any) and create your own.
3. **Start at `00_Inbox/`** — every new capture lands there, and weekly you move it to its proper PARA bucket.

## Current structure

```
PARA_structure/
├── 00_Inbox/         # pending classification
├── 01_Projects/      # projects with outcome + deadline
├── 02_Areas/         # ongoing responsibilities
├── 03_Resources/     # topics of interest and references
└── 04_Archives/      # closed but preserved
```

Each folder has a `README.md` describing the PARA criterion for what belongs inside.

## Using it with Obsidian

Obsidian treats each folder as an indexed set of notes. PARA fits natively because Obsidian does not require topical hierarchies — just flat folders with `[[wikilinks]]` between notes.

**Recommended Obsidian tweaks:**

- **Wire `00_Inbox/` to a Quick Capture plugin** so every capture lands there without thinking (the core *Capture* plugin or community *QuickAdd* both work).
- **Avoid subfolders inside each PARA for the first weeks.** Let `[[wikilinks]]` and tags emerge on their own. Premature subdivision is the classic anti-PARA trap.
- **Use the *Dataview* plugin** to list notes by PARA:
  ```dataview
  TABLE deadline, status
  FROM "01_Projects"
  SORT deadline ASC
  ```
- **Maps of Content (MOCs) inside `02_Areas/`** — one `MOC.md` per area, linking to all related notes without duplicating them.
- **Vault as git repo** — sync the vault with this repo (or a parallel one) using the *Obsidian Git* plugin for backup and version control.

## Using it with LLMs (Claude, GPT, local models)

PARA is LLM-friendly because it gives each note a clear **purpose**, so the model does not need to read the whole vault to act on it.

**Practical patterns:**

- **Inbox triage with an LLM.** Feed the contents of `00_Inbox/` to a model with a prompt like *"Classify each capture as Project / Area / Resource, suggest a filename and target folder."* The "00_Inbox — Rules" section of that README already encodes the criterion the model needs.
- **Retrieval-Augmented Generation (RAG).** Index only the active folders (`01_Projects` + `02_Areas`) — `04_Archives/` is rarely useful context and burns tokens. PARA makes that filter trivial.
- **Agent persistent memory.** Point your agent at `02_Areas/<area>` as its canonical reference note before each long conversation. Scoping by PARA = less noise = fewer hallucinations.
- **Templates per folder.** Use distinct Obsidian templates for Projects (`tasks.md`, `deadline`, `outcome`) and Areas (`checklists.md`, `health criterion`). The LLM learns the format after 2–3 examples.
- **Uniform frontmatter.** Minimal YAML on every note (`type: project|area|resource|archive`, `status:`, `tags:`) lets the LLM classify and filter with `jq` before sending the content.

> Golden rule: the AI classifies and summarizes, **you decide**. PARA tells the model *where things go*, but priority judgment stays human.

## License

MIT — use it, fork it, adapt it to your workflow.