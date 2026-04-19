# Drift Digest Schema

**Location:** `schemas/drift_digest.md`
**Purpose:** Periodic scan for system drift — HYPOTHESIS entries that have aged without resolution, OPINION entries being treated as fact, outdated VERIFIED entries that may no longer be true, and gaps between what the system says it does and what it actually does.

Drift is silent and cumulative. The Drift Digest is the mechanism that catches it before it becomes a SEV3 finding.

---

## When to Run

- Weekly (scheduled via `/schedule` — see `docs/architecture/loop_schedule_system.md`)
- After any major decision that changes previously VERIFIED or DECIDED entries
- Before any significant product launch or external commitment
- On demand by Human CEO

---

## Schema — Single Digest Entry

```
DIGEST_ID:      [DD-YYYY-NNN — e.g., DD-2026-001]
DATE:           [ISO 8601]
PERIOD_COVERED: [Date range scanned]
RUN_BY:         [Cowork | Claude Code | Claude Chat]
REVIEWED_BY:    [Human CEO | pending]

HYPOTHESIS_REVIEW:
  [List of HYPOTHESIS entries from Truth Ledger older than 30 days]
  - LEDGER_ID: [TL-XXXX-NNN]
    AGE:        [Days since logged]
    STATEMENT:  [Original hypothesis]
    RESOLUTION: [upgrade to VERIFIED | upgrade to DECIDED | purge | extend with note]
    ACTION:     [What was done]

STALE_VERIFIED_REVIEW:
  [List of VERIFIED entries that may be outdated due to external changes]
  - LEDGER_ID: [TL-XXXX-NNN]
    STATEMENT:  [Verified fact]
    TRIGGER:    [Why this might be stale — time, external event, new information]
    STATUS:     [still current | needs update | purged]

OPINION_DRIFT_CHECK:
  [Any instances found where OPINION entries were used as if VERIFIED in outputs]
  - SOURCE:     [Work Register task ID or conversation reference]
    OPINION:    [The opinion that drifted]
    HOW_USED:   [How it was presented]
    SEVERITY:   [SEV level]
    ACTION:     [Correction made or flagged]

PROCESS_GAP_SCAN:
  [Workflows described in docs that don't have corresponding Work Register entries — system doing things differently than documented]
  - GAP:        [Description]
    IMPACT:     [Low | Medium | High]
    ACTION:     [Update docs | Update process | Flag for review]

SUMMARY:
  drift_level:  [none | low | moderate | high]
  findings:     [count]
  escalated:    [yes | no]
  notes:        [Free text summary]
```

---

## Digest Log

*No digests run yet. First scheduled digest: 7 days after system activation.*

---

## Drift Level Definitions

| Level | Meaning | Action |
|---|---|---|
| None | System operating as documented. No stale entries. | Log and close. |
| Low | 1–2 minor hypothesis entries unresolved. No OPINION drift. | Resolve in next session. |
| Moderate | Multiple stale entries OR one OPINION drift instance found. | Human CEO review recommended. |
| High | VERIFIED entry found to be outdated OR OPINION treated as VERIFIED in an output affecting a real decision. | Human CEO review required. Treat as SEV3. |
