# BI - farmabi

Workspace del curso **Business Intelligence** (BI), UPeU 2026-2. El
`README.md` de la raíz describe la arquitectura de datos **prevista**
(`MySQL OLTP -> Airbyte/Debezium -> PostgreSQL RAW -> dbt -> PostgreSQL DW
-> Power BI`, con carpetas como `oltp-mysql/`, `dw-pg/`, `dw-dbt/`,
`powerbi/`), pero de esas carpetas **solo `oltp-mysql/` existe** (construida
para S1, ver más abajo) — `dw-pg/`, `ingesta-*/`, `dw-dbt/` y `powerbi/`
siguen sin implementar, no asumir que están listas.

## Dónde está cada cosa

- `docs/silabo_bi_2026_2.md` — sílabo oficial **vigente** (no editar salvo
  pedido explícito). `docs/silabo_bi_2026_1.md` es la versión anterior,
  solo como referencia histórica.
- `docs/index.md` — página de bienvenida curada (propósito del curso, flujo
  general del laboratorio BI). Todavía tiene tildes faltantes en varios
  párrafos y enlaces a `guias/...` que no existen en este repo — pendiente
  de limpieza, no confundir con contenido roto nuevo.
- `docs/proyecto-sello/index.md` — Guía del Proyecto Sello (creada 2026-08),
  usa competencias **CE04x (línea CD-IA)**, no CE02x (línea Software) — ver
  nota en "Convenciones".
- `docs/sesiones/S01_Fundamentos_BI_Problema_Negocio.md` — primera guía de
  sesión, ya publicada en `mkdocs.yml`. Construida a partir del respaldo
  antiguo (ver más abajo) y verificada contra `silabo_bi_2026_2.md`.
- `oltp-mysql/` — origen transaccional MySQL (`farma_oltp_db`), portado del
  respaldo 2026-1 y **verificado**: `docker compose up -d` levanta el
  contenedor `farmabi-oltp-mysql` (puerto host `53306`), el script
  `mysql/init/farma_oltp_db.sql` crea `familias`, `clientes`, `vendedores`,
  `categorias`, `productos`, `pedidos` y `pedido_detalles` con datos de
  ejemplo, y las dos consultas de la matriz pregunta-fuente de S1 (venta
  neta mensual, margen por familia) corren correctamente contra esos datos.
  Es el único módulo de código que S1 necesita — `dw-pg/`, `ingesta-*/`,
  `dw-dbt/` y `powerbi/` pertenecen a sesiones de U2 (S6+) y no se han
  construido todavía.
- `README.md` (raíz) — describe la arquitectura de datos prevista y la
  estructura de carpetas planeada completa; es un documento de diseño, no
  un reflejo exacto del estado actual del repo (ver punto anterior).
- `mkdocs.yml` — nav con "Inicio", "Guía de Proyecto Sello", "Silabos"
  (2026-1/2026-2) y la Unidad 1 con S1. El enlace externo antiguo
  "Repositorio 2026-1 (farmabi)" (que apuntaba a `261bi/farmabi`) se quitó
  del nav en la limpieza de 2026-08 — la referencia al repo anterior ahora
  vive solo aquí, en este `CLAUDE.md` (ver siguiente punto).

## Material de referencia del ciclo anterior (2026-1)

El contenido técnico y las sesiones del ciclo 2026-1 de este mismo curso
(entonces bajo la org `261bi`, mismo nombre de repo `farmabi`) viven en dos
sitios externos a este repo, **de solo lectura** — no clonar ni migrar
contenido automáticamente, solo consultarlos cuando se construya o revise
una guía de sesión nueva:

- Repositorio GitHub: <https://github.com/261bi/farmabi> — código completo
  del entorno de desarrollo 2026-1 (`oltp-mysql/`, `dw-pg/`,
  `ingesta-debezium/`, `ingesta-airbyte/`, `dw-dbt/`, `powerbi/`) y las 16
  guías de sesión de ese ciclo, en la plantilla antigua (sin Índice,
  Metodología ni Hoja de ruta). Copia local de solo lectura en este mismo
  equipo: `C:\262\261\261bi\farmabi`.
- Google Drive: <https://drive.google.com/drive/folders/10G5snPuZMHih_3TkpWQLII_fb9p8PQ_N> —
  grabaciones y materiales de las sesiones 2026-1. Sin copia local; solo
  accesible vía el enlace.

Al construir S2 en adelante, usar el mismo criterio ya aplicado en S1: leer
la sesión equivalente del repo/Drive 2026-1 como fuente de contenido técnico,
pero el sílabo `silabo_bi_2026_2.md` es la única fuente de verdad para
alcance, orden y nombre de cada sesión.

## Convenciones

- No editar los archivos `silabo_bi_*.md` salvo que se pida explícitamente.
- Guías de sesión: S2-S16 todavía no existen — al agregarlas, seguir
  exactamente la estructura de `docs/sesiones/S01_Fundamentos_BI_Problema_Negocio.md`
  (1.1 Contexto … 1.7 Ubicación en el curso, Hoja de ruta antes de 3.1,
  4.1.1-4.1.5 en `####`, 5.1-5.4). No existe todavía skill de sesión
  (`.claude/skills/`).
- Antes de implementar código del pipeline (`oltp-mysql/`, `dbt/`, etc.),
  confirmar el alcance real pedido — el `README.md` describe la visión
  completa del curso, no necesariamente el incremento de una sesión.
- BI es curso de la línea **CD-IA** (Ciencia de Datos e IA), no línea
  Software — usar competencias **CE04x** (CE041-CE045), no CE02x, y el topic
  de repositorio `linea-cdia`, no `linea-software`. Ver
  <https://upeuoficial.github.io/planb/lineas/cd-ia/> para el detalle de
  competencias. Esta misma excepción aplica a Big Data e IoT en este
  workspace.
