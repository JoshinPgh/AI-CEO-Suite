# Truth Ledger Schema

**Location:** `schemas/truth_ledger.md`
**Purpose:** The canonical record of what is known, decided, assumed, and opined within the Geldrich Corporation operating system. Prevents drift. Prevents the system from treating old hypotheses as settled facts.

---

## Entry Types

| Tag | Meaning | Authority to Change |
|---|---|---|
| `VERIFIED` | Confirmed true. Canonical. Contradictions are SEV3. | Human CEO explicit override only. |
| `DECIDED` | Human-approved direction. Do not reverse without explicit override. | Human CEO explicit override only. |
| `HYPOTHESIS` | Working assumption. Not confirmed. Must be labeled as such in any output that references it. | Can be upgraded to VERIFIED or DECIDED, or purged, after review. |
| `OPINION` | Reasoned but unverified. Claude or Human CEO perspective. | Can be challenged and updated freely. |

---

## Schema — Single Entry

```
LEDGER_ID:      [TL-YYYY-NNN — e.g., TL-2026-001]
DATE:           [ISO 8601]
TYPE:           [VERIFIED | DECIDED | HYPOTHESIS | OPINION]
DOMAIN:         [corporate | product | finance | legal | marketing | operations | technical]
STATEMENT:      [The fact, decision, assumption, or opinion — one clear sentence]
SOURCE:         [Where this came from — conversation, document, research, external event]
EVIDENCE:       [Supporting refs, links, docs — empty if none]
CONFIDENCE:     [0–100 — only relevant for HYPOTHESIS and OPINION]
EXPIRES:        [Date or trigger condition after which this entry should be reviewed — optional]
LOGGED_BY:      [Claude | Human CEO]
REVIEWED_BY:    [Human CEO | — if not yet reviewed]
NOTES:          [Anything relevant to interpretation or context]
```

---

## Active Truth Ledger

### Corporate

**TL-2026-001**
```
TYPE:       VERIFIED
DOMAIN:     corporate
STATEMENT:  Geldrich Corporation is a Pennsylvania C-Corp. Sole founder: Legend (Josh Geldrich).
SOURCE:     Founding documentation
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

**TL-2026-002**
```
TYPE:       VERIFIED
DOMAIN:     corporate
STATEMENT:  Zero outside funding. 100% revenue reinvestment until income is established.
SOURCE:     Bootstrapper's Constitution — standing Human CEO directive
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

**TL-2026-003**
```
TYPE:       DECIDED
DOMAIN:     corporate
STATEMENT:  Gemini and other non-Claude AI systems are not named participants in the operating structure. Available as zero-cost external tools if needed; not integrated into the OS.
SOURCE:     Human CEO decision, April 2026
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

**TL-2026-004**
```
TYPE:       VERIFIED
DOMAIN:     corporate
STATEMENT:  Kiss Off Inc is the silent legal publisher across Apple App Store, Google Play, and Chrome Web Store. Never customer-facing.
SOURCE:     Standing corporate structure
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

---

### Product

**TL-2026-005**
```
TYPE:       VERIFIED
DOMAIN:     product
STATEMENT:  Apple Developer Account for ColorDex: GRANTED.
SOURCE:     GitHub commit d515d93, context_dashboard.md update
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

**TL-2026-006**
```
TYPE:       VERIFIED
DOMAIN:     product
STATEMENT:  Google Play Developer access for ColorDex: GRANTED.
SOURCE:     context_dashboard.md
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

**TL-2026-007**
```
TYPE:       DECIDED
DOMAIN:     product
STATEMENT:  ColorDex build pipeline: GitHub Actions only. No local C: Drive builds for production.
SOURCE:     Architecture decision — Android Studio loop resolution
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

**TL-2026-008**
```
TYPE:       DECIDED
DOMAIN:     product
STATEMENT:  TreadSnap is the first instance of the Blue Collar App Suite. Shared scaffold: Voice Parser Module, Firebase, RevenueCat, PDF engine. Domain-specific JSON dictionaries per app.
SOURCE:     PRD v1.1
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

---

### Technical

**TL-2026-009**
```
TYPE:       VERIFIED
DOMAIN:     technical
STATEMENT:  851Mobile-1 (HP laptop) is the primary development machine. Running Cursor and Claude Code CLI via WSL2.
SOURCE:     Hardware stack documentation
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

**TL-2026-010**
```
TYPE:       DECIDED
DOMAIN:     technical
STATEMENT:  Google Drive is the cloud source of truth. MainShare is the operational shared drive.
SOURCE:     Standing infrastructure decision
CONFIDENCE: 100
LOGGED_BY:  Claude
REVIEWED_BY: Human CEO
```

---

*Add new entries below. Follow the schema exactly. Increment LEDGER_ID sequentially.*
