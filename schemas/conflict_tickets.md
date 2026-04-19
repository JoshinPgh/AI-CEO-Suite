# Conflict Ticket Schema

**Location:** `schemas/conflict_ticket.md`
**Purpose:** When two things in the system contradict each other — two VERIFIED entries that can't both be true, a new decision that conflicts with an old DECIDED entry, a policy that conflicts with a constraint — a Conflict Ticket is opened. It stays open until resolved. Nothing that depends on the conflicting entries proceeds until the conflict is cleared.

---

## When a Conflict Ticket is Opened

- Shadow Auditor detects a contradiction (SEV3 finding triggers automatic ticket)
- Claude Code or Cowork encounters conflicting instructions mid-task
- Human CEO identifies a contradiction during review
- Drift Digest surfaces an unresolved conflict

---

## Schema — Single Conflict Ticket

```
TICKET_ID:      [CT-YYYY-NNN — e.g., CT-2026-001]
DATE_OPENED:    [ISO 8601]
OPENED_BY:      [Shadow Auditor | Claude Code | Cowork | Human CEO | Claude Chat]
STATUS:         [OPEN | IN REVIEW | RESOLVED | PURGED]
SEVERITY:       [SEV2 | SEV3 | SEV4]
BLOCKING:       [yes | no — is active work blocked pending resolution]

CONFLICT:
  entry_a:
    source:     [Truth Ledger ID | Policy doc + section | Work Register ID | other]
    statement:  [Exact claim or rule]
  entry_b:
    source:     [Truth Ledger ID | Policy doc + section | Work Register ID | other]
    statement:  [Exact claim or rule — the conflicting one]
  nature:       [factual contradiction | policy conflict | outdated entry | scope overlap | other]
  why_it_matters: [What decision or action is affected by this conflict]

RESOLUTION:
  resolved_by:  [Human CEO | Claude — if Human CEO approved]
  date:         [ISO 8601]
  action:       [entry_a supersedes | entry_b supersedes | both updated | both purged | new entry created]
  new_entry:    [Truth Ledger ID of replacement entry if applicable]
  notes:        [Rationale for resolution]
```

---

## Active Conflict Tickets

*No open tickets.*

---

## Resolved Conflict Tickets

*No resolved tickets yet.*

---

## Resolution Principles

1. **Newer DECIDED entries supersede older ones** — unless the Human CEO explicitly preserves the older entry.
2. **VERIFIED beats DECIDED beats HYPOTHESIS beats OPINION** — when entries of different types conflict, higher-authority type wins pending Human CEO review.
3. **When in doubt, escalate.** Claude does not resolve conflicts unilaterally. A conflict ticket stays open until the Human CEO makes the call.
4. **Blocking tickets halt dependent work.** No output that depends on conflicting information ships until the conflict is resolved.
