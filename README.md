# ETABSPY

A Python desktop application that automates the shear wall pier force extraction and S-CONCRETE file generation workflow for multi-story building structural analysis. Built to replace a tedious manual process — retrieving pier forces from ETABS, copying results into Excel, post-processing spreadsheets, and manually preparing S-CONCRETE input files — with a single, controlled, automated pipeline.

ETABSPY connects directly to an analyzed ETABS model via COM API, extracts all required datasets (geometry, load cases, load combinations, pier forces, material properties), and generates ready-to-use `.sco` S-CONCRETE design files in seconds. Once data is retrieved, it can be saved as a `.pkl` snapshot and reloaded later without needing ETABS open — enabling a fully offline processing mode.

Key engineering logic includes seismic shear force magnification (Rd application), where ETABSPY deconstructs each load combination into its individual load cases, applies the user-defined seismic magnification factor only to seismic shear components (V2, V3), then reconstructs the combination to produce the final magnified forces. It also computes moment distribution factors (Cm) and organizes output files by story grouping, with user control over how stories are batched into each S-CONCRETE file via the Pier Forces Viewer.

---

## Features

- **Live ETABS Integration** — Connects to running ETABS instances via COM API to extract model data in real time
- **SCONCRETE File Generation** — Automatically generates `.sco` analysis files from pier forces and load combinations
- **Seismic Load Magnification** — Implements vectorized seismic magnification algorithms across thousands of load combinations
- **Pier Forces Viewer** — Interactive step chart visualization of pier forces across building stories
- **Data Persistence** — Save and load model snapshots via `.pkl` files for offline processing
- **High-Performance Data Processing** — Handles millions of rows using optimized `pandas` DataFrame operations
- **Responsive GUI** — PyQt5 interface with background threading to keep UI non-blocking during heavy operations
- **Centralized Logging** — SQLite-based analytics and session logging for corporate deployment tracking
- **Network Security** — Domain validation and connectivity checks for enterprise environments

---

## Tech Stack

| Layer | Technologies |
|---|---|
| GUI | PyQt5 |
| Data Processing | pandas, NumPy |
| ETABS Integration | comtypes, pywin32 (COM API) |
| Persistence | pickle, SQLite |
| Packaging | PyInstaller, setup.py |


