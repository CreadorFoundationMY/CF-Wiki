---
name: schola-user-intent-taxonomy
description: Schola's official taxonomy for classifying student intent across career exploration, pathway planning, execution, and emotional support — used by both Ola and the comment classifier
type: entity
sources:
  - source: manual
    path: default/1781151527388-v11.pdf
  - source: manual
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# Schola User Intent Taxonomy

Used by [[ola-chatbot]] to shape response strategy, and by the [[comment-taxonomy-pipeline]] to classify social media comments.

## Codes

### Phase 1: Self & Career Exploration
| Code | Description |
|------|-------------|
| 1.1 | No clear direction; wants general career ideas or possibilities |
| 1.2 | No clear direction; wants to understand themselves better (interests, strengths, personality) |
| 1.3 | Wants tailored career suggestions based on interests or preferences |
| 1.4 | Evaluating whether career suggestions / job information fit them |
| 1.5 | Wants factual information about a specific job, field, or role |
| 1.6 | Confirms or affirms a chosen career goal |

### Phase 2: Pathway Planning
| Code | Description |
|------|-------------|
| 2.1 | No clear direction; wants general pathway options or next steps |
| 2.2 | Wants tailored pathway suggestions (courses, training, certs) based on goals or constraints |
| 2.3 | Wants factual info (duration, requirements, cost) about a specific pathway |
| 2.4 | Evaluating which pathways suit them |
| 2.5 | Confirms or affirms their pathway plan |

### Phase 3: Execution
| Code | Description |
|------|-------------|
| 3.1 | Looking for actual job vacancies or steps to get a job |

### Phase 4: Emotional Support
| Code | Description |
|------|-------------|
| 4.1 | Needs encouragement, reassurance, or confidence-building |

### Special
| Code | Description |
|------|-------------|
| OTHER | Does not clearly fit Phase 1–4 (e.g. scholarships without career intent, platform feedback, education outside taxonomy scope) |

## Classification Rules
- Every item gets exactly **one primary tag**
- Secondary tag used only when a second distinct Phase 1–4 intent is clearly present
- Determine dominant intent by reading the **whole message**, not just the first topic
- Tag both expressed desires AND completed actions (e.g. "I found a job!" → 3.1)
- Scholarships as primary topic → OTHER (unless a dominant Phase 1–4 intent exists)

## Confidence Levels
- **HIGH** — explicit or strongly implied by the text
- **MEDIUM** — reasonable inference required
- **LOW** — significant ambiguity; best guess among plausible options

## Example Classifications
| Message | Primary | Secondary | Confidence |
|---------|---------|-----------|------------|
| "Is there a proper guide for filling in UPU?" | 2.3 | — | HIGH |
| "Once you succeed later, everyone will go quiet." | OTHER | — | MEDIUM |
| "This website helped me find my dream job" | 1.6 | — | HIGH |
| "I wish Schola had more subjects to match" | 1.3 | — | MEDIUM |

## Versioning
Current version used in the comment classifier prompt. When taxonomy codes change (e.g. V3 → V4), Product team updates the Claude prompt accordingly.

## Related
- [[ola-chatbot]]
- [[intent-recognition]]
- [[comment-taxonomy-pipeline]]
- [[social-media-taxonomy-classifier]]
