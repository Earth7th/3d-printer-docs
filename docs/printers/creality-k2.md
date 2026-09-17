# Creality K2

The author's reference machine. Base **K2** with the **CFS** (Creality Filament System)
multi-material unit — the "K2 Combo".

## Key specs

| | |
|---|---|
| Motion | CoreXY, enclosed |
| Extruder | Direct drive |
| Nozzle | 0.4 mm default (0.2 / 0.6 / 0.8 mm compatible), all-metal hotend |
| Max nozzle temp | 300 °C |
| Max bed temp | 100 °C |
| Max speed | 600 mm/s |
| Layer height | 0.05–0.3 mm |
| Multi-material | CFS unit |

## Notable features

- **AI camera** — auto flow-rate and pressure-advance tuning at print start.
- **Auto bed leveling** and **input shaping** (resonance compensation).
- **Klipper-based** firmware/OS.
- Enclosed heated-ish chamber (good for PETG/ABS).

## K2-specific notes

- Auto flow/PA is applied automatically and isn't always shown as an editable number —
  manual [calibration](../calibration/filament-calibration.md) refines or replaces it.
- The **CFS is not an active dryer** — add desiccant packs; dry wet spools separately
  (see [Drying Filament](../reference/filament-drying.md)).
- Calibration tests are generated in **OrcaSlicer**; auto-cal values live in Creality's
  ecosystem — don't confuse the two.

## Slicers

- **Creality Print** (official) and **OrcaSlicer** (preferred here for its calibration tools).
