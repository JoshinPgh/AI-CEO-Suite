# Work Register Schema

**Location:** `schemas/work_register.md`
**Purpose:** The operational log. Every task Claude Code or Cowork executes gets a Work Register entry. This is the audit trail, the memory of what was done, and the input for loop retrospectives.

---

## Schema — Single Entry

```
TASK_ID:        [WR-YYYY-NNN — e.g., WR-2026-001]
DATE:           [ISO 8601]
INITIATED_BY:   [Human CEO | Claude Chat | Claude Code | Cowork | Schedule | Loop]
EXECUTED_BY:    [Claude Code | Cowork | Claude Chat]
DOMAIN:         [product | marketing | finance | legal | operations | infrastructure | ideation]
BRAND:          [Geldrich Corp | Prism Salon Systems | JSG Labs | ColorDex | TreadSnap | internal]
TASK:           [One clear sentence describing what was done]
OUTPUT:         [What was produced — file path, document title, action taken, or "none"]
SUCCESS_CONDITION: [How success was defined going in]
OUTCOME:        [success | partial | failed | escalated]
APPROVAL_GATE:  [G1 | G2 | G3 | G4 | none]
APPROVED_BY:    [Human CEO | pending | n/a]
LOOP_ID:        [If part of a loop — reference LOOP_ID; otherwise "—"]
SHADOW_AUDIT:   [SEV level of audit result | not run]
NOTES:          [Anything relevant — blockers, decisions made mid-task, context for future]
```

---

## Active Work Register

### WR-2026-001
```
TASK_ID:        WR-2026-001
DATE:           2026-04-19
INITIATED_BY:   Human CEO
EXECUTED_BY:    Claude Chat
DOMAIN:         infrastructure
BRAND:          Geldrich Corp
TASK:           Full rewrite and build-out of AI-CEO-Suite repo — README, context dashboard, schemas, policies, architecture docs, prompts.
OUTPUT:         README.md / docs/context_dashboard.md / docs/prompts/shadow_auditor.md / docs/architecture/loop_schedule_system.md / docs/policies/approval_gates.md / docs/policies/operational_scaling.md / docs/policies/connector_governance.md / docs/parking_lot.md / schemas/truth_ledger.md / schemas/work_register.md / schemas/drift_digest.md / schemas/conflict_ticket.md
SUCCESS_CONDITION: All files complete, professional, machine-readable, and consistent with Human CEO directives from ideation session.
OUTCOME:        success
APPROVAL_GATE:  G2
APPROVED_BY:    pending
LOOP_ID:        —
SHADOW_AUDIT:   not run
NOTES:          Initial system build. Human CEO to review all files and commit approved versions to GitHub repo (JoshinPgh/AI-CEO-Suite).
```

---

*Add new entries below. Follow the schema exactly. Increment TASK_ID sequentially.*
