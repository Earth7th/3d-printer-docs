# PETG

PETG (polyethylene terephthalate glycol) is a strong, slightly flexible, impact- and
chemical-resistant filament — a good middle ground between easy PLA and tough ABS. It
prints without a heated chamber, resists moisture and UV once printed, and handles more
heat than PLA. Its main downsides: it's **very hygroscopic** (soaks up moisture fast),
prone to **stringing**, and it can **stick too well** to smooth build plates.

## Recommended settings (general starting points)

These are typical ranges — dial them in per spool with the
[Filament Calibration Guide](../calibration/filament-calibration.md).

| Setting | Typical range | Notes |
|---------|---------------|-------|
| Nozzle temp | 230–250 °C | Higher = stronger layers but more stringing |
| Bed temp | 70–85 °C | |
| Part cooling | 30–50 % | Keep low — too much cooling weakens PETG layers |
| Print speed | Moderate | PETG dislikes very high speeds |
| Retraction | 0.4–1 mm (direct drive) / 2–5 mm (Bowden) | |
| Flow ratio | ~0.95 | PETG tends to over-extrude slightly |
| First layer Z | A touch higher than usual | PETG bonds hard — see adhesion note |

## Drying & storage

PETG is one of the thirstiest common filaments. Wet PETG causes pockmarks, popping, and
heavy stringing no matter how well it's tuned.

- **Dry:** ~60–65 °C for 6–8 h. Full guide → [Drying Filament](../reference/filament-drying.md).
- **Store:** sealed box/bag with fresh desiccant; print from a dry box if possible.

## Quirks & tips

- **Bed adhesion — it sticks *too* well.** On smooth PEI or glass, PETG can rip chunks out
  of the plate. Use a release barrier (glue stick) or a textured plate, and raise the
  first-layer Z slightly so it isn't over-squished.
- **Stringing:** dry filament + tuned retraction is the fix, not higher retraction alone.
- **Bridging/overhangs:** PETG sags more than PLA — tune cooling and speed (finishing steps
  in the calibration guide).
- **Moisture pockmarks:** little dots/bubbles on strands = wet filament → dry it.

## Variants

### Generic PETG

Unbranded / no-name PETG (no manufacturer label with recommended temps). Treat the general
ranges above as the starting point and calibrate.

**Author's calibrated values (Creality K2, OrcaSlicer):** from the worked run in the
[Generic PETG calibration log](../calibration/logs/petg-generic.md).

| Nozzle | Bed | Flow | Pressure advance | Retraction | Max vol. speed |
|--------|-----|------|------------------|------------|----------------|
| 245 °C | ~75–80 °C | 0.96 | 0.076 | 0.4 mm | 17.5 mm³/s |

> These are the author's measured values on one specific machine/spool — **yours will
> differ.** Use them as a sanity-check ballpark, not a copy-paste.

![Generic PETG information](images/PETG-infomation.jfif)
*Caption: ________________________________________*
