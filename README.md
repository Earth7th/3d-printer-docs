# 3D Print Calibration Docs

Practical, readable 3D-printing calibration guides. Written to work on **any FDM printer**
using **OrcaSlicer** — the author's reference machine is a **Creality K2**.

## Guides

- **[Filament Calibration Guide (Any 3D Printer)](docs/calibration/filament-calibration.md)** —
  step-by-step, in-order tuning of a filament (temperature → flow → pressure advance →
  retraction → max flow → bridging → ironing), with under/correct/over photo comparisons.
  - Worked example: **[Generic PETG calibration log](docs/calibration/logs/petg-generic.md)** — a real step-by-step run.

Machine-level (hardware) calibration is planned as a separate guide.

## Reference

- **[Drying Filament (Wet Filament Fix)](docs/reference/filament-drying.md)** — how to
  spot wet filament, drying temps/times per material, and storage.

## How it's organised

- `docs/calibration/` — the guides and their `images/`
- `docs/adr/` — short notes on *why* key decisions were made
- `CONTEXT.md` — glossary of terms used across the docs
