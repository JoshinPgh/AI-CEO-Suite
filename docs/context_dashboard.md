# COLOR-DEX CONTEXT DASHBOARD
> **Status:** LIVE DOCUMENT
> **Last Updated:** [Date]
> **Governing Logic:** Async Shadow Auditor

## 1. Verified Constraints (Immutable Rules)
*All code and decisions MUST adhere to these. Contradictions are SEV3.*

* **Tech Stack:** [e.g., React Native (Expo), TypeScript, Firebase, Node.js]
* **Styling:** [e.g., Tailwind CSS, No inline styles]
* **Architecture:** [e.g., MVVM pattern, Strict separation of UI and Logic]
* **Authentication:** [e.g., Firebase Auth only]
* **Database:** [e.g., Firestore for user data, SQL for inventory?]
* **Critical Rule:** [e.g., Never delete user data without a soft-delete flag]

## 2. Current State (Mutable)
*Where are we right now?*

* **Active Sprint:** [e.g., Fixing the Color Sorting Algorithm & User Profile UI]
* **Last Successful Milestone:** [e.g., Login screen works and connects to Firebase]
* **Current Blocker:** [e.g., The app crashes when sorting more than 50 colors]
* **Next Immediate Step:** [e.g., Refactor the `sortColors` function in `utils.ts`]

## 3. Active Risks
*What is threatening the project?*

* [e.g., "Spaghetti code" in the main view component]
* [e.g., API rate limits on the color recognition service]

## 4. Recent Decisions Log (The Memory)
* **[Date]:** Decided to switch from SQL to NoSQL for faster reads.
* **[Date]:** Abandoned feature "Auto-Palette" because it was too buggy (See Parking Lot).

## 5. File Map (Where things live)
* **Logic:** `src/services/`
* **UI:** `src/components/`
* **State Management:** `src/context/`
