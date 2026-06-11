---
name: index
description: Top-level index of the Schola LLM wiki — AI systems for career exploration
metadata:
  type: index
sources: []
---

# Schola LLM Wiki

Knowledge base for Schola's AI systems: the **Ola** career chatbot and the **Social Media Comment Classifier** pipeline.

## Sections

| Section | Purpose |
|---------|---------|
| [sources/](sources/) | Raw ingested documents — one page per source |
| [entities/](entities/) | Named things: platform, jobs, personas |
| [concepts/](concepts/) | System rules, taxonomies, pipelines |
| [syntheses/](syntheses/) | Cross-source analysis and synthesis |
| [outputs/](outputs/) | Generated artifacts |
| [sops/](sops/) | Standard operating procedures |

## Key Pages

| Page | Summary |
|------|---------|
| [Schola Platform](entities/schola.md) | Malaysian career exploration platform for students 13–19 |
| [Ola Chatbot](entities/ola.md) | Schola's student-facing career assistant (LLM persona) |
| [Actuary Job Guide](entities/actuary.md) | Schola job guide: Actuary in Malaysian context |
| [User Intent Taxonomy](concepts/schola-user-intent-taxonomy.md) | 12 classification codes (1.1–4.1 + OTHER) used across Ola and classifier |
| [Ola Response Rules](concepts/ola-response-rules.md) | Intent recognition, word caps, tone, scope, job-matching flows |
| [Comment Classifier Pipeline](concepts/social-media-comment-classifier-pipeline.md) | 5-step automation: extract → classify → deliver → report → review |
| [Schola AI Systems Overview](syntheses/schola-ai-systems-overview.md) | How Ola and the classifier share taxonomy and serve different audiences |
