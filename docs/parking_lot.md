# Parking Lot

**Location:** `docs/parking_lot.md`
**Purpose:** Raw ideas, deferred topics, future architecture candidates. Nothing here is a commitment. Everything here is fair game for the next ideation session.

Entries are dated and tagged. Tags: `[ARCH]` architecture, `[PRODUCT]` product, `[MKTG]` marketing, `[LEGAL]` legal, `[FINANCE]` finance, `[OPS]` operations, `[INFRA]` infrastructure.

---

## Active Parking Lot

### Connector Snap-In System — Human-Gated Plugin Architecture
`[ARCH]` `[INFRA]`
The vision: connectors to external services (Google Drive, app stores, payment processors, email, etc.) are modular "snap-ins" that can be activated or deactivated by the Human CEO. Each snap-in is sandboxed, least-privilege, with a full audit log. The governance policy (`docs/policies/connector_governance.md`) is already drafted. The snap-in framework itself — how Claude Code activates, scopes, and brokers these connections — needs architectural design.
**Next step:** Design the broker layer. How does Claude Code request a connector activation? What's the handshake?

---

### Sandbox + Broker + Egress Control Layer
`[ARCH]` `[INFRA]`
Related to the snap-in system. The broker sits between Claude Code / Cowork and any external service. It enforces: sandbox mode for new connectors, least-privilege scoping, egress data review, audit logging. This is a system component that doesn't exist yet but needs to be designed before connectors go live.
**Next step:** Spec the broker. Define what it intercepts, what it logs, what it blocks by default.

---

### SonglineMemory — Persistent Memory Architecture
`[ARCH]` `[INFRA]`
SQLite-based persistent memory system. Designed to serve Claude, Gemini (if needed), and Gemma. The goal is a unique filing and retrieval system — not just a database dump. OB1/OB2 (Nate Jones' open-source project) was under evaluation as the retrieval/injection layer. Current status: in development, not yet integrated into the main system.
**Note:** Memory-agnostic posture maintained at the system level. SonglineMemory is the current candidate but not the locked answer. Better architectures may emerge — the system should be able to swap them in.
**Next step:** Define the filing taxonomy. What is a "memory" in this system? How is it tagged? How is it retrieved?

---

### Blue Collar App Suite — Shared Scaffold
`[PRODUCT]` `[ARCH]`
TreadSnap is the first instance. The suite shares: Voice Parser Module, Firebase, RevenueCat, PDF engine. Domain-specific JSON dictionaries per app. Pipeline: RoofLog, PipeNote, WireSnap, LandscapeLog.
**Next step:** After TreadSnap v1 ships, abstract the shared scaffold into a documented template repo. Each new app should be a clone + new JSON dictionary, not a rebuild.

---

### GTR v2.0 — Model-Agnostic Context Relay
`[PRODUCT]`
GTR v1.2 is a Gemini-only Chrome extension. v2.0 vision: model-agnostic, targeting ChatGPT, Copilot, Gemini, Claude, Perplexity, Grok. Was ~75–80% complete in early April 2026 before v1.2 submission became the priority. Monetization: Ko-fi "buy me a coffee" + founder pricing upgrade path.
**Next step:** Resume after v1.2 is live on CWS.

---

### AI-CEO-Suite — Prism Salon Systems Integration
`[OPS]`
The current Executive OS is Geldrich Corp-wide but has no Prism-specific playbooks yet. Prism has its own domain logic (salon industry, Shari's expertise, B2B SaaS sales). A Prism-specific context dashboard and operational playbook would make the system more useful when working on Prism.
**Next step:** Schedule a dedicated session to build the Prism context dashboard.

---

### Financial Reporting Cadence
`[FINANCE]`
No formal financial reporting cadence exists yet. Phase 2 trigger will require a monthly summary minimum. The schema for financial reporting should be designed before it's needed so it can be looped and scheduled automatically.
**Next step:** Design the monthly financial summary schema. What does Legend need to see? What does Claude need to produce it?

---

### Standing Approval Pre-Clearances
`[OPS]`
As Claude learns Legend's judgment patterns, certain output categories can be pre-approved — reducing per-output G2/G3 review volume. The mechanism for logging standing approvals as `DECIDED` in the Truth Ledger needs to be formalized.
**Next step:** After 30 days of system operation, review which output categories are candidates for standing pre-approval.

---

## Resolved / Graduated from Parking Lot

| Item | Resolution | Date |
|---|---|---|
| Gemini as COO | Removed. Gemini role changed to Unstated. | Apr 2026 |
| Shadow Auditor removal | Reversed. Shadow Auditor restored to docs/prompts/. | Apr 2026 |
| EA as named AI role | EA function absorbed into Claude. No separate agent. | Apr 2026 |
