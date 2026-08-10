# BI - farmabi

Workspace de documentación del curso **Business Intelligence** (BI), UPeU
2026-2. Actualmente el repo solo contiene documentación (MkDocs); el
`README.md` de la raíz describe la arquitectura de datos **prevista**
(`MySQL OLTP -> Airbyte/Debezium -> PostgreSQL RAW -> dbt -> PostgreSQL DW
-> Power BI`, con carpetas como `oltp-mysql/`), pero esas carpetas de código
**todavía no existen** en el repo — no asumir que están implementadas.

## Dónde está cada cosa

- `docs/silabo_bi_2026_2.md` — sílabo oficial **vigente** (no editar salvo
  pedido explícito). `docs/silabo_bi_2026_1.md` es la versión anterior,
  solo como referencia histórica.
- `docs/index.md` — página de bienvenida curada (propósito del curso, flujo
  general del laboratorio BI).
- `README.md` (raíz) — describe la arquitectura de datos prevista y la
  estructura de carpetas planeada; es un documento de diseño, no un reflejo
  del estado actual del repo.
- `mkdocs.yml` — nav con "Inicio", "Silabos" (2026-1/2026-2) y un enlace
  externo **"Repositorio 2026-1 (farmabi)"** a
  <https://github.com/261bi/farmabi> — el código de referencia del ciclo
  anterior vive en ese otro repositorio (prefijo `261bi`, no `262bi`).

## Convenciones

- No editar los archivos `silabo_bi_*.md` salvo que se pida explícitamente.
- No existen todavía guías de sesión (`S0X_*.md`) ni skill de sesión
  (`.claude/skills/`) — si se agregan, seguir el patrón ya usado en otros
  cursos del workspace (carpeta `docs/sesiones/`, publicadas en
  `mkdocs.yml` por unidad).
- Antes de implementar código del pipeline (`oltp-mysql/`, `dbt/`, etc.),
  confirmar el alcance real pedido — el `README.md` describe la visión
  completa del curso, no necesariamente el incremento de una sesión.
