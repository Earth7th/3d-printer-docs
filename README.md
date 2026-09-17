# 3D Print Docs

A practical 3D-printing knowledge base — calibration, materials, hardware, slicer tips,
and troubleshooting. Written to work on **any FDM printer** using **OrcaSlicer**, with the
author's **Creality K2** as the reference machine.

## Sections

| Topic | What's inside |
|-------|---------------|
| **[Calibration](docs/calibration/)** | Step-by-step filament tuning guides + real per-run logs |
| **[Materials](docs/materials/)** | Per-filament reference — settings, drying, storage, quirks |
| **[Hardware](docs/hardware/)** | Printer setup, mods, upgrades, and [maintenance](docs/hardware/maintenance/) |
| **[Slicer](docs/slicer/)** | OrcaSlicer / Creality Print — settings explained, profiles, tips |
| **[Troubleshooting](docs/troubleshooting/)** | Symptom → cause → fix (stringing, warping, clogs…) |
| **[Reference](docs/reference/)** | Cross-cutting references (e.g. filament drying) |
| **[Printers](docs/printers/)** | Machine-specific notes (e.g. Creality K2) |

## Featured

- **[Filament Calibration Guide (Any 3D Printer)](docs/calibration/filament-calibration.md)** —
  the flagship guide: temperature → flow → pressure advance → retraction → max flow →
  bridging → overhang → ironing, with under/correct/over photo comparisons.
- **[Drying Filament (Wet Filament Fix)](docs/reference/filament-drying.md)**

## How it's organised

- Segmented **by topic** (not by printer or material) so a method is written once and
  applies everywhere; printer/material specifics live *inside* the relevant topic doc.
- `docs/adr/` — short notes on *why* key decisions were made.
- `CONTEXT.md` — glossary of terms used across the docs.
