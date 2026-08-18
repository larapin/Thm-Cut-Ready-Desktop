# THM CutReady Desktop Application — Developer Planning Outline

## I. Installation & Packaging
### A. Installer Fundamentals
1. Keep install package as small as possible
2. Update to .NET Framework 4.7.2
   - 4.8 works on W7 but not preinstalled on Ultra 6 W10 1809 systems
   - 4.7.2 avoids bloating the Ultra 6 install
3. ~~Fix CutReady.dll paths~~ ✅
4. Verify clean MDF file
5. Is existing EULA acceptable?
6. Hide install option to select imperial/metric?

### B. Bundled Content Decisions
1. ~300MB of videos — mostly useless for desktop
   - **Decision:** Exclude; deliver via update system
2. Bundle eCabinets?
   - **Decision:** No; deliver via update system
3. InfoDocs files — are they necessary?
4. ~~Is `C:\temp` required?~~ ✅ (CutReadyData\temp)

### C. Paths & Configuration
1. Which paths in local config are necessary?
2. Wizard data path?
3. Finalize Control Nesting install/build

### D. Installer Updates & Distribution
1. How to handle installer/updates going forward?

---

## II. First-Launch Setup Wizard
### A. Overview
- Wizard triggers on first launch after install
- Goal: configure the desktop instance for the correct CutCenter

### B. Wizard Flow (Proposed)
1. **Step 1 — CutCenter Sync**
   - Sync from a CutReady machine via:
     - Import file, or
     - Network search
   - How do we update the MSU file and other files to the right CutCenter name/machine name?
   - How do we add a second CutCenter's sync info? Via settings or the startup wizard?
2. **Step 2 — Registration**
   - User registers after sync
3. **Step 3 — Content Download**
   - Download required software and libraries tied to that CutCenter

### C. Ongoing Sync Options (Post-Wizard)
1. Can CutCenter sync an online backup to WebAPI at shutdown or via settings on the machine?
2. Should sync be available at startup or on the nest screen?

---

## III. Nesting & Multi-Machine Scenarios
### A. Targeting a CutCenter for Nesting
1. If a nested job is expected to run on a machine without preprocessing at the machine, do we target a CutCenter?
2. Different machines = different tool setups, inputs/outputs, and options — how is this handled?
3. Example: Customer has a CutCenter and a CR43 (e.g., Ten South) — which machine does the desktop nest target?

### B. Multiple CutCenter Support
1. How do we add a second CutCenter's sync info — settings or startup wizard?
2. History and recut jobs on desktop with multiple machine CutCenters — how do we handle this?

### C. Software Version Parity
1. How do we ensure desktop and machine are at the same software level when publishing jobs?

---

## IV. Offfall Management
1. Can the user add sheets from the CutCenter on the desktop?
2. Ten South shares an offfall database between machines — offfall can be used on either machine
3. Will the sync retrieve the correct `offfall.mdb`?
4. How is offfall handled across multiple CutCenters on desktop?
