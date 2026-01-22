# COLOR-DEX CONTEXT DASHBOARD
> **Status:** STABLE / PRE-BETA
> **Last Updated:** Jan 21, 2026
> **Governing Logic:** Async Shadow Auditor

## 1. Verified Constraints (Immutable Rules)
*All code and decisions MUST adhere to these. Contradictions are SEV3.*

* **Build Pipeline:** GitHub Actions ONLY. No local "C: Drive" builds for production.
* **Distribution Strategy:** Native Wrapper (App Store/Play Store). No loose APKs/Web-only versions.
* **Native Access:** Must utilize native device APIs (Camera, Alarm, Timer) via the wrapper, not web fallbacks.
* **Source of Truth:** The GitHub Repository is the single source of truth.
* **Environment:** CI/CD driven.

## 2. Current State (Mutable)
*Where are we right now?*

* **Active Sprint:** Beta Release Candidates & Store Submission.
* **Current Status:** Stable. Recovered from "crash" phase. Ready for Beta.
* **External Blockers:**
    * **Apple:** Awaiting Apple Developer Account approval (Account level). App NOT submitted yet.
    * **Google:** Google Play Developer access/approval is GRANTED.
* **Immediate Next Step:** Finalize the GitHub Actions workflow to auto-generate the `.ipa` and `.aab` files for the stores.

## 3. Active Risks
*What is threatening the project?*

* **Approval Delays:** Apple Developer verification can take time.
* **Wrapper Regression:** Ensuring the "wrapped" version actually solves the camera/timer glitches seen in the previous version.

## 4. Recent Decisions Log (The Memory)
* **[Critical Pivot]:** STOPPED local development on Windows/C: Drive (Android Studio loop).
* **[Decision]:** MIGRATED build process to GitHub Actions to ensure consistency.
* **[Decision]:** RE-PRIORITIZED "Native Wrapping" to resolve hardware access bugs (Camera/Timer/Alarm) that were plaguing the web version.

## 5. File Map & Resources
* **Code Repo:** ColorDex (Private)
* **Memory Repo:** AI-CEO-Suite
* **CI/CD:** GitHub Actions (Workflows folder)
