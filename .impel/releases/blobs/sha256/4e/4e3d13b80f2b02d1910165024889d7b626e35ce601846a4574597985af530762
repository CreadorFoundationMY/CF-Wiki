---
name: schola-ai-stack
description: Cross-source synthesis of how Ola, job guides, and the comment classifier form Schola's AI stack — shared taxonomy, divergent data flows, and integration points
type: synthesis
sources:
  - source: manual
    path: default/1781151527388-v11.pdf
  - source: manual
    path: default/1781151527502-actuary_chatbase.txt
  - source: manual
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# Schola AI Stack — Synthesis

## The Three Layers

```
┌─────────────────────────────────────────────────────────┐
│  KNOWLEDGE LAYER                                        │
│  Job Guides (bilingual, structured, authoritative)      │
│  Interview Transcripts (lived experience)               │
└────────────────────────┬────────────────────────────────┘
                         │ feeds
          ┌──────────────▼──────────────────┐
          │  CONVERSATION LAYER             │
          │  Ola Chatbot (System Prompt v11) │
          │  Intent recognition → responses  │
          └──────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│  SIGNALS LAYER                                          │
│  Social Media (Instagram, TikTok)                       │
│        ↓ extract & translate                            │
│  Comment Taxonomy Pipeline (Claude)                     │
│        ↓ classify against shared taxonomy               │
│  Google Sheets + Slack Reports                          │
└─────────────────────────────────────────────────────────┘
```

## Shared Component: The Taxonomy
The [[schola-user-intent-taxonomy]] is the **single shared vocabulary** across both AI products:
- [[ola-chatbot]] uses it implicitly — intent types 1–4 map to the taxonomy phases, shaping response strategy
- The [[comment-taxonomy-pipeline]] applies the full taxonomy explicitly, tagging social media comments with codes and confidence levels

This creates a feedback loop: comment classification data could theoretically inform which job topics students ask about most → inform what job guides to prioritise → improve Ola's source quality.

## Divergent Concerns

| Dimension | Ola (Chatbot) | Comment Classifier |
|-----------|--------------|-------------------|
| Input | Live student messages | Batch social media comments |
| Output | Conversational response | Structured dataset |
| Taxonomy use | Response strategy selection | Explicit code tagging |
| Language | Matched to user (EN/BM/Manglish) | Translated to EN before classification |
| Human-in-loop | None (Ola operates autonomously) | Product team review each cycle |
| Refinement trigger | Prompt version updates (v11 → v12) | Cycle review → prompt updates |

## Key Design Patterns

### Source Fidelity
Both products enforce strict source boundaries:
- Ola: only job guides + interviews; no general knowledge
- Comment classifier: maps to taxonomy only; unclassifiable → OTHER

### Confidence Signalling
The comment classifier returns explicit confidence levels (HIGH/MEDIUM/LOW). Ola's equivalent is the progressive disclosure model — lead with contained answer, let student pull more depth.

### Graceful Degradation
Both have defined fallbacks when content is unavailable:
- Ola: states limitation → redirects to approved destinations (counsellor, upu.mohe.gov.my)
- Classifier: labels ambiguous items OTHER → surfaces in cycle report as outliers for human review

## Integration Gaps (Observed)
1. No direct feedback path from comment classifier results → job guide content priorities
2. Ola's intent taxonomy is implicit; the chatbot prompt doesn't use numeric codes — the comment classifier does. These are parallel implementations of the same taxonomy.
3. The Review Loop for comment classification (Step 5) relies on manual Product team review — partial automation opportunity exists for outlier flagging

## Related
- [[ola-chatbot]]
- [[comment-taxonomy-pipeline]]
- [[schola-user-intent-taxonomy]]
- [[job-guide-schema]]
- [[schola]]
