# Approval Gates Policy

**Location:** `docs/policies/approval_gates.md`
**Current Mode:** Startup-loose. Gates are broad. As system matures and Claude learns Legend's judgment, gates will narrow.

---

## Overview

An approval gate is a defined checkpoint where work stops and waits for Human CEO review before proceeding. Gates exist to protect against financial damage, legal exposure, reputational harm, and irreversible actions.

The goal is not bureaucracy. The goal is making sure Legend sees the things that matter, in a format that lets him make a fast, confident call. Most reviews should take seconds — a tone check, a quick scan, a "yep, works for me."

---

## Gate Levels

| Level | Label | What It Means |
|---|---|---|
| G1 | **Review** | Human CEO sees the output before it's used. No formal sign-off required. Flag if anything looks off. |
| G2 | **Approve** | Human CEO must explicitly approve before the output proceeds. A thumbs up in chat counts. |
| G3 | **Approve + Log** | Human CEO approves AND the decision is logged to the Truth Ledger as `DECIDED`. Used for decisions that set precedent or can't easily be reversed. |
| G4 | **Full Stop** | Work halts completely. Human CEO is notified immediately. Used for SEV3/SEV4 findings or any action that could cause irreversible harm. |

---

## Approval Gate Map by Domain

### Marketing
| Output Type | Gate | Notes |
|---|---|---|
| Brand voice / positioning statements | G3 | Sets precedent. Log as DECIDED. |
| External copy (ads, emails, landing pages) | G2 | Must match brand voice. Tone check required. |
| Social media posts | G2 | Brief review. Flag anything involving real names or competitive claims. |
| Internal drafts / working copy | G1 | Review only. No sign-off needed. |

### Finance / Accounting
| Output Type | Gate | Notes |
|---|---|---|
| Any expenditure recommendation | G3 | Even small ones. Log rationale. |
| Revenue projections used in decisions | G3 | Label clearly as HYPOTHESIS until verified. |
| Financial reports (internal) | G1 | Review for accuracy. |
| Anything touching a live account or payment | G4 | Full stop. No exceptions. |

### Legal
| Output Type | Gate | Notes |
|---|---|---|
| Terms of service / privacy policy drafts | G3 | Log as DECIDED when approved. |
| Any communication that creates a commitment | G3 | Including vendor agreements, app store representations. |
| Legal research / summaries | G2 | Claude is not a lawyer. Output is informational. Flag before acting on it. |
| Anything with regulatory or IP implications | G4 | Full stop. Seek qualified counsel before proceeding. |

### Product / Development
| Output Type | Gate | Notes |
|---|---|---|
| Code committed to main branch | G2 | Review before merge. |
| Code deployed to production | G3 | Explicit approval + log. |
| App store submissions | G3 | Explicit approval. These create public commitments. |
| Architectural decisions (stack, infra) | G3 | Log as DECIDED. Hard to reverse. |
| Internal prototypes / experiments | G1 | Review only. |

### Operations / Communications
| Output Type | Gate | Notes |
|---|---|---|
| External emails (vendor, partner, press) | G2 | Tone and content review. |
| Internal notes / summaries | G1 | Review only. |
| Any communication involving a named person | G2 | Privacy check — especially Shari, Legend, or any customer. |

---

## Fast Review Protocol

Legend's review process: scan for tone, check key claims, confirm it gets the point across. Full reads are not required for routine G1/G2 items. The system is designed to make review fast, not to create homework.

For G2 items, Claude presents:
1. The output
2. One-line summary of what it is and where it's going
3. Any flags or concerns noted during production

Human CEO responds: approve / revise / reject. One word is enough.

---

## Gate Exceptions

No exceptions to G4. Ever.

G3 items can be pre-approved by category if Human CEO establishes a standing decision. Example: "All ColorDex social posts in this tone don't need individual approval." Standing decisions are logged as `DECIDED` in the Truth Ledger.

---

## Evolution of Gates

As Claude learns Legend's judgment patterns, standing approvals will accumulate, reducing the volume of individual G2/G3 reviews. This is not reduced oversight — it's accumulated trust, formally logged. The gates don't disappear; they get pre-cleared.
