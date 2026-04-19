# Operational Scaling Policy

**Location:** `docs/policies/operational_scaling.md`
**Current Mode:** Phase 1 — Startup Loose

---

## Philosophy

Rules exist to serve the company, not the other way around. At startup scale, excessive process kills speed and smothers creativity — both of which are survival assets. Rules are introduced as the company grows, and only when the absence of a rule is creating actual problems, not hypothetical ones.

The system documents its own evolution. When a rule changes, the change is logged here with a reason.

---

## Phase Definitions

### Phase 1 — Startup Loose *(current)*
**Headcount equivalent:** Solo founder + AI system
**Revenue:** Pre-revenue to early revenue

**Operating rules:**
- Speed and creative output take priority over process.
- Decisions can be made fast and informally. Logging happens after, not before.
- Experimentation is encouraged. Failed experiments are logged, not punished.
- The only hard constraints are the Verified Constraints in `context_dashboard.md`.
- Everything else is a guideline.

**What this looks like in practice:**
- Claude proposes; Legend approves or redirects. Fast loop.
- No standing meetings, no formal reports, no bureaucratic cadence.
- The parking lot (`docs/parking_lot.md`) is used aggressively. Ideas go in; the good ones resurface.
- Financial discipline is strict even in loose phase — spending controls are a Verified Constraint, not a Phase 2 rule.

---

### Phase 2 — Structured Growth *(future)*
**Trigger:** First consistent revenue stream OR first external commitment (contractor, partner, vendor SLA)

**What changes:**
- Formal sprint planning introduced. Work Register is actively maintained, not just logged.
- Decision log reviewed monthly. Stale HYPOTHESIS entries resolved or purged.
- Approval gates reviewed and standing pre-approvals documented.
- Brand voice documentation formalized and enforced across all outputs.
- Financial reporting cadence established (monthly summary minimum).

**What stays the same:**
- Speed bias remains. Process serves execution, not the other way around.
- Human CEO remains final authority on all material decisions.

---

### Phase 3 — Corporate Structure *(future)*
**Trigger:** Multiple active revenue streams OR team expansion (human or autonomous agent)

**What changes:**
- Formal role definitions for any new participants (human or AI agent).
- Documented escalation paths for decisions outside defined authority.
- Compliance review cadence for legal and financial outputs.
- SLAs defined for recurring deliverables.
- Connector governance reviewed quarterly.

**What stays the same:**
- Truth Ledger remains the source of canonical fact.
- Loop + Schedule architecture continues to expand.
- Human CEO retains override authority on any decision.

---

### Phase 4 — Autonomous Operations *(future)*
**Trigger:** System has demonstrated reliable judgment alignment across 12+ months of logged decisions. Human CEO explicitly designates categories for autonomous operation.

**What changes:**
- Designated workflow categories run without per-output approval.
- Human CEO receives exception reports and periodic summaries, not individual approvals.
- Autonomous action boundaries are formally documented and reviewed quarterly.

**What stays the same:**
- G4 gates never become autonomous. Full stop items remain full stop.
- Human CEO can revoke autonomous status on any category at any time.
- Shadow Auditor continues to run on all outputs regardless of autonomy level.

---

## Rule Change Log

| Date | Rule Changed | Reason | New Phase Triggered? |
|---|---|---|---|
| Apr 2026 | Gemini role changed to Unstated | Capability assessment — Claude system sufficient | No |
| Apr 2026 | AI-CEO-Suite designated as full Executive OS | System maturity — repo structured for machine-readable doctrine | No |

*Log all future rule changes here.*
