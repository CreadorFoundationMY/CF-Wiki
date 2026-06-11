---
name: schola-ai-systems-overview
description: Synthesis — how Ola and the comment classifier share taxonomy and serve complementary audiences
metadata:
  type: synthesis
sources:
  - source: manual
    path: default/1781151527388-v11.pdf
  - source: manual
    path: default/1781151527502-actuary_chatbase.txt
  - source: manual
    path: default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf
---

# Schola AI Systems — Overview Synthesis

## Two AI Systems, One Shared Taxonomy

[[schola]] operates two AI systems that both ground their logic in the [[schola-user-intent-taxonomy]]:

| System | Audience | Direction | Taxonomy Role |
|--------|----------|-----------|---------------|
| [[ola]] (chatbot) | Individual student on schola.org.my | Student → Ola | Ola reads intent signals to choose response structure and word cap |
| [[social-media-comment-classifier-pipeline]] | Schola Product team | Comments → Claude → Sheets/Slack | Claude assigns taxonomy codes to classify audience behaviour at scale |

This shared taxonomy creates a coherent analytical frame: the same codes that drive Ola's per-conversation response logic also categorise the aggregate signals coming in from social media — enabling the product team to understand what students collectively need.

## Data Flow

```
Job Guides + Interview Transcripts
        │
        ▼
  [Ola chatbot] ──── answers student questions on schola.org.my
        │
        │  (student questions → chat logs)
        │
        ▼
  [Comment Classifier] ── classifies social media comments
        │
        ▼
  Google Sheets → Slack Report → Product Team Review
        │
        ▼
  Taxonomy refinement → updated Claude prompts (Step 5 review loop)
```

## Knowledge Source Hierarchy

Both systems enforce strict sourcing:

- **Ola:** ONLY job guides + interview transcripts — no general knowledge, no hallucination
- **Classifier:** Processes real user-generated comments — does not generate career advice, only classifies intent

## Shared Constraints

Both systems are designed for a **Malaysian student audience** speaking English, Bahasa Malaysia, and Manglish. Both require semantic understanding of that language mix:

- Ola: responds in-language, matches register
- Classifier: categorises based on underlying meaning, not surface language

## Gap Between Systems

The comment classifier processes **public social media comments** (short, context-poor, often reactive). The Ola chatbot processes **intent-rich conversational turns** within a career-exploration context. This means:

- LOW confidence classifications are more common in the classifier pipeline (noisy social comments)
- Ola's intent types (vague, emotionally uncertain, frustrated) do not map 1:1 to taxonomy codes — they are response-structural signals, not analytical codes

## Prompt Evolution Risk

Both systems depend on the taxonomy version. If the taxonomy evolves (e.g. V3 → V4), **both** the Ola system prompt and the classifier prompt need updating. Currently this is a manual step per the Step 5 review loop. An automated version bump check would reduce drift risk.

## Actuary as a Reference Case

The [[actuary]] job guide illustrates how Schola's content layer works: bilingual, salary-grounded, pathway-specific, expert-sourced. Ola surfaces this content conversationally; the classifier measures whether students on social media are asking about careers like this (Phase 1–2 codes) or seeking emotional support (4.1) or already executing (3.1).

## Related Pages

- [[ola]] — chatbot entity
- [[social-media-comment-classifier-pipeline]] — pipeline concept
- [[schola-user-intent-taxonomy]] — shared classification system
- [[ola-response-rules]] — Ola behavioral rules
- [[schola]] — the platform
