# Connector Governance Policy

**Location:** `docs/policies/connector_governance.md`

---

## Overview

A connector (also called a snap-in plugin) is any integration between the AI-CEO-Suite system and an external service, API, data store, or tool. Connectors are powerful and therefore dangerous if ungoverned. This policy defines how connectors are approved, scoped, sandboxed, and audited.

**Default posture: deny.** A connector that isn't explicitly approved doesn't run.

---

## Connector Approval Requirements

Before any connector is activated, the following must be documented:

| Field | Description |
|---|---|
| `connector_id` | Unique identifier |
| `service` | What external service this connects to |
| `purpose` | Specific task this connector performs |
| `scope` | Exact permissions required — list every access right |
| `least_privilege_verified` | Confirmation that no excess permissions are requested |
| `data_touched` | What data this connector reads or writes |
| `sandbox` | Whether this runs in isolated environment before production |
| `audit_log` | Where connector activity is logged |
| `approved_by` | Human CEO explicit approval required |
| `review_date` | When this connector's permissions are next reviewed |

No connector ships without all fields populated and Human CEO sign-off.

---

## Sandbox Policy

All new connectors run in sandbox mode first. Sandbox means:
- No writes to production data
- No external communications sent
- No financial transactions initiated
- Output logged for human review before any real action is taken

Sandbox graduation requires Human CEO explicit approval.

---

## Least Privilege

Every connector is scoped to the minimum permissions required to perform its defined task. If a connector requests broad permissions "for future use," it is rejected and resubmitted with scoped permissions only.

When in doubt: narrower is correct.

---

## Egress Controls

Any connector that sends data outside the Geldrich Corporation system (to an external API, a third-party service, a public endpoint) is subject to egress review:

1. What data is leaving?
2. Where is it going?
3. Is it encrypted in transit?
4. Does the destination have appropriate data handling practices?
5. Is this consistent with any privacy policy commitments made to users?

Egress review is required at approval time and again at each review date.

---

## Audit Log Requirements

Every connector must produce a log entry for each activation. Minimum log fields:

```
timestamp:      [ISO 8601]
connector_id:   [identifier]
action:         [what the connector did]
data_touched:   [what was read or written]
outcome:        [success / failure / partial]
triggered_by:   [human / schedule / loop / event]
reviewed:       [yes / no — was this output reviewed by Human CEO]
```

Logs are retained for a minimum of 90 days.

---

## Active Connectors

| ID | Service | Purpose | Status | Last Review |
|---|---|---|---|---|
| — | — | No active connectors yet | — | — |

*Update this table when connectors are approved.*

---

## Connector Pipeline (Under Evaluation)

| Service | Proposed Purpose | Status |
|---|---|---|
| Google Drive API | Read/write to MainShare for workflow outputs | Under evaluation |
| IONOS (web hosting) | Publish policy pages (e.g., GTR privacy policy) | Under evaluation |
| Chrome Web Store API | Submission automation for JSG Labs extensions | Under evaluation |
| Apple App Store Connect API | Build and submission pipeline for ColorDex | Under evaluation |
| Google Play API | Build and submission pipeline for ColorDex | Under evaluation |

*Evaluation does not constitute approval. Each requires full approval process before activation.*
