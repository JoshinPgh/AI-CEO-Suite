# Geldrich Corporation — Master Context Dashboard

**Status:** ACTIVE | **Last Updated:** See commit history | **Governing Logic:** Async Shadow Auditor (SEV0–SEV4)

---

## 1. Verified Constraints (Immutable Rules)
*Contradictions to these are SEV3. Do not override without explicit Human CEO approval.*

| # | Constraint | Status |
|---|---|---|
| VC-01 | Zero outside funding. 100% revenue reinvestment until income is established. | `VERIFIED` |
| VC-02 | Open source and self-hosted first. Purchase only when building or free options are ruled out. | `VERIFIED` |
| VC-03 | Google ecosystem preferred for cloud, storage, and productivity infrastructure. | `VERIFIED` |
| VC-04 | Google Drive is the cloud source of truth. MainShare is the operational shared drive. | `VERIFIED` |
| VC-05 | GitHub is the source of truth for all code repos. | `VERIFIED` |
| VC-06 | Kiss Off Inc is the silent legal publisher. Never customer-facing. | `VERIFIED` |
| VC-07 | Do not connect Legend's or Shari's personal identities to the Prism or ColorDex brands publicly. | `VERIFIED` |
| VC-08 | All code delivered as complete, paste-ready files. Never snippets or partial blocks. | `VERIFIED` |
| VC-09 | Human CEO approves all material outputs before external publication or financial commitment. | `VERIFIED` |
| VC-10 | Aggressively growth-oriented by default. Income conserved aggressively. Expenditures strictly targeted. | `VERIFIED` |

---

## 2. Corporate Structure

**Entity:** Geldrich Corporation (Pennsylvania C-Corp)

| Person | Role | Domain |
|---|---|---|
| Legend (Josh Geldrich) | Human CEO / Founder | Final authority on all decisions |
| Shari Geldrich | Domain Partner — Beauty vertical | Industry expertise for Prism Salon Systems |

**Brands:**

| Brand | Vertical | Publisher Entity |
|---|---|---|
| Prism Salon Systems | Beauty industry software | Kiss Off Inc (silent) |
| JSG Labs | AI tools, Chrome extensions, SaaS | Kiss Off Inc (silent) |

**Internal Infrastructure:**

| System | Role |
|---|---|
| AI-CEO-Suite (this repo) | Executive OS — doctrine, schemas, dashboards, auditing |
| SonglineMemory | Persistent memory architecture (SQLite-based) — in development |

---

## 3. Hardware Stack

| Machine | ID | Primary Role |
|---|---|---|
| HP Laptop | 851Mobile-1 | Primary dev machine. Cursor + Claude Code CLI via WSL2. |
| ASUS Ryzen Desktop | 851Office-1 | Secondary workstation |
| ASUS Ryzen Desktop | 851Office-2 | Secondary workstation |
| MacBook Air | — | iOS/Xcode utility only |
| Travel Laptop | — | Mobile work |

---

## 4. Active Projects

### 4a. GTR — Gemini Thread Relay
**Brand:** JSG Labs | **Status:** v1.2 — CWS Submission In Progress

| Field | Detail |
|---|---|
| Description | Chrome extension for cross-session AI context relay |
| Current Version | v1.2 |
| All four core extension files | `VERIFIED` — Finalized |
| Store assets | `VERIFIED` — Complete |
| Remaining tasks | Resize screenshots to CWS spec; publish privacy policy to prismsalonsystems.com/gtr-privacy via IONOS; complete submission |
| Next milestone | Chrome Web Store live |

---

### 4b. ColorDex
**Brand:** Prism Salon Systems | **Status:** Pre-Beta / Stable

| Field | Detail |
|---|---|
| Description | React Native/Expo app for hair stylists. Native timer support. Dark luxury aesthetic. |
| Stack | React Native + Expo |
| Repo | `colordex-native/` — screens in `src/screens/` |
| Build pipeline | GitHub Actions ONLY. No local C: Drive builds for production. |
| Distribution | Native wrapper (App Store + Play Store). No loose APKs or web-only. |
| Apple Developer | `VERIFIED` — GRANTED |
| Google Play | `VERIFIED` — GRANTED |
| Immediate next step | Finalize GitHub Actions workflow to auto-generate `.ipa` and `.aab` files |
| Design constants | Background `#0a0a0a` / Accent-mauve `#c4917a` / Playfair Display Bold / Montserrat Regular / Inter Light |
| Known risk | Navigation layer (App.tsx connections) — recovery path: reconnect screens one at a time, test in Expo Go after each |

---

### 4c. TreadSnap
**Brand:** JSG Labs | **Status:** PRD Complete — Pre-Build

| Field | Detail |
|---|---|
| Description | Field estimation and job protection SaaS for tradesmen |
| Modules | Liability Shield (timestamped photo documentation) / Takeoff Engine (quantity surveying / BOM) / Field Communicator (voice-first notes + change orders) |
| Stack | Expo / React Native / TypeScript / Firebase (Auth, Firestore, Storage, Cloud Functions) / Cursor / Claude Code |
| PRD version | v1.1 — complete |
| UX philosophy | TB;CD ("Too Busy, Couldn't Do") — shared with ColorDex |
| Suite context | First instance of Blue Collar App Suite — shared scaffold (Voice Parser Module, Firebase, RevenueCat, PDF engine) with domain-specific JSON dictionaries per app |
| Suite pipeline | RoofLog / PipeNote / WireSnap / LandscapeLog — queued |

---

## 5. Active Risks

| Risk | Project | Severity | Notes |
|---|---|---|---|
| CWS screenshot spec | GTR v1.2 | Medium | Must resize before submission |
| Privacy policy publication | GTR v1.2 | Medium | IONOS publish to prismsalonsystems.com/gtr-privacy required |
| Navigation layer fragility | ColorDex | Medium | Known issue — reconnect screens one at a time |
| GitHub Actions wrapper regression | ColorDex | Medium | Camera/timer must be verified in native build |

---

## 6. Recent Decisions Log

| Date | Decision | Status |
|---|---|---|
| Apr 2026 | Gemini role changed to Unstated. Not a named OS participant. Available as zero-cost external driver only if needed. | `DECIDED` |
| Apr 2026 | AI-CEO-Suite designated as Geldrich Corp Executive OS. Full rewrite initiated. | `DECIDED` |
| Apr 2026 | SonglineMemory retained as memory architecture. Acknowledged as early-stage; memory-agnostic posture maintained at system level. | `DECIDED` |
| Apr 2026 | Shadow Auditor restored to docs/prompts/. SEV0–SEV4 framework retained. | `DECIDED` |
| Earlier | Migrated ColorDex build process to GitHub Actions. | `DECIDED` |
| Earlier | Re-prioritized native wrapping for ColorDex to resolve camera/timer hardware access bugs. | `DECIDED` |
| Earlier | Stopped local development on Windows/C: Drive (Android Studio loop). | `DECIDED` |

---

## 7. System Architecture Notes

- `/loop` and `/schedule` are first-class system components. See `docs/architecture/loop_schedule_system.md`.
- Approval gate thresholds are defined in `docs/policies/approval_gates.md`.
- Operational rules are currently in startup-loose mode. Scaling rules are defined in `docs/policies/operational_scaling.md`.
