# Hot Cache

Last updated: 2026-06-11

## Current context

This wiki covers three Schola AI product artefacts ingested in the initial batch:

1. **Ola v11 system prompt** — full behavioural spec for the student-facing chatbot. Key facts: intent recognition with 5 types + word caps, hard no on institution naming, progressive disclosure pattern, strict source-only knowledge policy.

2. **Actuary job guide** — bilingual EN/BM career data. Key facts: RM2,800–75,000+ salary band; two pathways (Actuarial Science degree or any degree + IFoA/SOA exams); expert voices are Farhana and Anisha Puri (Allianz Malaysia).

3. **Social Media Comment Taxonomy Classifier** — 5-step pipeline (extract → Claude classify → Sheets → Slack report → review loop). Key facts: taxonomy is 4 phases + OTHER; Claude prompt classifies dominant intent; credentials were in the source doc and were redacted.

## Key entities to know

- **Schola** — Malaysian student career platform, schola.org.my
- **Ola** — the chatbot; v11 is current as of this ingest
- **Farhana** — actuary expert (no surname in sources)
- **Anisha Puri** — actuary at Allianz Malaysia

## Cross-source insight

The [[concepts/Schola-User-Intent-Taxonomy]] is the connective tissue: it governs how Ola interprets students (implicitly) AND how Claude labels social media comments (explicitly). Any taxonomy version change affects both systems.
