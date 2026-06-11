---
sources:
  - { source: "manual", path: "default/1781159773926-Copy of The Story of Schola_as at 24 Feb 2026.pptx.md" }
---
# SOP: Wiki Ingest

## Scope
This wiki stores concise, retrieval-optimized markdown synthesized from staged raw inputs under `/home/user/wiki-work/raw/<source>/<sourcePath>`.

## Requirements applied
- Write generated markdown only under `/home/user/wiki-work/wiki`.
- Preserve directories: `index.md`, `log.md`, `concepts/`, `entities/`, `sources/`, `syntheses/`, `outputs/`, and `sops/`.
- Include frontmatter `sources` entries on every generated markdown page, mapping back to the raw input object such as `{ source: "manual", path: "default/..." }`.
- Regenerate only pages needed for pending inputs.
- Keep pages concise, source-grounded, and optimized for later agent retrieval.

## Page pattern
- `sources/`: describe raw inputs and high-value references.
- `entities/`: people, organizations, products, and named systems.
- `concepts/`: reusable ideas, models, and metrics.
- `syntheses/`: cross-slide narratives and timelines.
- `outputs/`: agent-facing summaries.
