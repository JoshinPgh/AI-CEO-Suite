# Loop + Schedule System Architecture

**Location:** `docs/architecture/loop_schedule_system.md`
**Status:** Living document — evolves as system matures.

---

## Overview

`/loop` and `/schedule` are the two most powerful components in this system. They are what transform a collection of good tools and smart prompts into an actual operating company.

- **`/loop`** — a workflow that audits its own output, identifies failure or drift, and reruns itself with corrections until the output meets the defined success condition.
- **`/schedule`** — a workflow that runs automatically at a defined interval without requiring a human trigger.

The sequence of maturity is: **build → ship → loop → schedule → automate.**

You cannot loop a system that hasn't been built yet. You cannot schedule a loop that isn't stable. As the system matures, `/schedule` becomes less of a feature and more of the default state — the background hum of a running company.

---

## Current State

**Phase:** Early. Most workflows are not yet looped or scheduled. This document defines the architecture so that as workflows are built, they are built loop-ready from day one.

---

## `/loop` — Recursive Improvement Protocol

### Definition
A loop is a workflow that:
1. Executes a defined task
2. Evaluates its own output against a success condition
3. If the condition is not met: identifies the gap, adjusts, and reruns
4. If the condition is met: logs the result and exits

### Loop Structure

```
LOOP_ID:        [unique identifier]
TRIGGER:        [what starts this loop — manual / schedule / event]
TASK:           [what Claude Code or Cowork executes]
SUCCESS_CONDITION: [measurable definition of done]
MAX_ITERATIONS: [hard cap to prevent runaway loops — default: 5]
ON_FAILURE:     [what happens if MAX_ITERATIONS is hit without success — escalate to Human CEO]
LOG_TO:         [schemas/work_register.md format]
AUDIT:          [shadow_auditor runs after final iteration]
```

### Loop Exit Conditions
- **Success:** Output meets success condition. Log result. Notify Human CEO if approval gate applies.
- **Max iterations hit:** Escalate to Human CEO with full iteration log. Do not silently fail.
- **SEV3/SEV4 finding mid-loop:** Stop immediately. Notify Human CEO.

### Example: Marketing Copy Loop
```
LOOP_ID:        mktg-copy-001
TRIGGER:        manual (Human CEO initiates)
TASK:           Generate [asset type] for [brand] per brand voice doc
SUCCESS_CONDITION: Human CEO approves tone and accuracy on review
MAX_ITERATIONS: 3
ON_FAILURE:     Escalate — present all three versions with diff notes
LOG_TO:         work_register.md
AUDIT:          shadow_auditor.md — SEV check on all factual claims
```

---

## `/schedule` — Automated Recurring Workflows

### Definition
A scheduled workflow runs at a defined interval without a manual trigger. Cowork is the primary executor for scheduled workflows.

### Schedule Structure

```
SCHEDULE_ID:    [unique identifier]
INTERVAL:       [daily / weekly / monthly / on-event]
TASK:           [what executes]
OUTPUT:         [what gets produced and where it goes]
APPROVAL_GATE:  [yes/no — does output require Human CEO sign-off before action]
LOOP_ENABLED:   [yes/no — does this workflow self-correct before delivering output]
LOG_TO:         [schemas/work_register.md format]
```

### Scheduled Workflows — Current Queue

| ID | Interval | Task | Status |
|---|---|---|---|
| sched-001 | Weekly | Drift Digest — scan for HYPOTHESIS entries that have aged without resolution | `PLANNED` |
| sched-002 | Weekly | Work Register summary — compile completed tasks and flag any unclosed items | `PLANNED` |
| sched-003 | Monthly | Context Dashboard review — flag stale project data for Human CEO update | `PLANNED` |
| sched-004 | On-event | Shadow Audit — trigger after any Claude Code session that produces external-facing output | `PLANNED` |

---

## Data Flow — How Loop and Schedule Connect

```
Human CEO / Claude Chat
        │
        ▼
   Ideation + Decision
        │
        ▼
   Approval Gate ──── [Material decision? → Human CEO sign-off required]
        │
        ▼
   Claude Code / Cowork executes task
        │
        ▼
   /loop evaluates output against success condition
        │
        ├── [Not met] → Adjust + rerun (up to MAX_ITERATIONS)
        │
        └── [Met] → Shadow Auditor runs
                        │
                        ├── [SEV0/1] → Log to Work Register → Done
                        ├── [SEV2] → Log + conditional notify → Done
                        ├── [SEV3] → Notify Human CEO → Await direction
                        └── [SEV4] → STOP. Notify urgently. Rollback recommended.
```

---

## Maturity Model

| Phase | Loop State | Schedule State | Autonomy Level |
|---|---|---|---|
| Now (startup) | Manual trigger, human reviews each iteration | No active schedules yet | Low — heavy human involvement |
| Growth | Loops run with human approval at exit only | Core schedules active | Medium — human approves outputs, not process |
| Scale | Loops self-complete; exceptions escalate | Full schedule library active | High — human reviews exceptions only |
| Autonomous | Loops and schedules run continuously | System self-optimizes | Full — human sets direction, system executes |

---

## Rules for Building Loop-Ready Workflows

Any new workflow built in this system must define, at minimum:
1. A measurable success condition (not "looks good" — something specific)
2. A max iterations cap
3. A failure escalation path
4. A log destination in work_register.md format

If a workflow can't define these four things, it's not ready to be built as a loop. Build it as a manual process first, observe it, then formalize the loop.
