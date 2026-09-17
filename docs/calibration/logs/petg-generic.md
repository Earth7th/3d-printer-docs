# Calibration Log — Generic PETG

A real, worked run of the [Filament Calibration Guide](../filament-calibration.md),
recorded step by step: the setup questions, the answers/decisions, the result, and a
photo of each test. Use it as a filled-in example of what the process actually looks like.

- **Printer:** Creality K2 (+ CFS)
- **Slicer for tests:** OrcaSlicer
- **Filament:** Generic PETG (unlabeled)
- **Started:** 2026-09-17
- **Auto-cal values found?** No clear editable numbers surfaced → treating this as a
  **fresh manual calibration** (the K2's auto flow/PA still runs automatically underneath).
- **Print speed for all tests:** Standard **0.20 mm** process preset, kept constant across
  every step (outer walls ~100–150 mm/s). Calibrate at the speed you actually print.

---

## Step 1 — Temperature

**Setup Q&A**

| Question | Answer / decision |
|----------|-------------------|
| Spool label — nozzle / bed temp? | Unlabeled → assume **~230–250 °C nozzle, ~75–80 °C bed** |
| Verify existing auto-cal values, or fresh? | **Fresh** — no clear auto values found |
| Temp tower range? | **250 °C → 230 °C, 5 °C steps** (blocks at 250 / 245 / 240 / 235 / 230) |
| Fan settings (constant, all steps) | Model fan **50%** (Min=Max), Side fan **0%**, Back fan/filtration **off** |
| Layer height / speed | **0.20 mm**, Standard preset, kept constant |

**Observations per block**

| Temp | Stringing | Overhangs / bridges | Layer shrinkage / bonding |
|------|-----------|---------------------|---------------------------|
| 250 °C | Worst (~3–4 strands), but minor remnants easily removed | Best overhangs; slight bridge droop | **Minimal** (best) |
| 245 °C | Reduced | Less bridge droop | Shrinkage starts to appear |
| ≤ 235 °C | Excessive (~5–6 strands) | — | Worse the lower you go |

**Reasoning:** stringing is fixable later (retraction, Step 4 + drying); layer
shrinkage/bonding is temperature-fundamental and isn't. So favor the higher end for
strength.

**Chosen nozzle temp:** **245 °C** — balance of low shrinkage + reduced stringing.
Fallback **250 °C** if real parts show weak/cracking layers (or drop cooling to ~30%).
→ Set this in the Orca PETG filament profile before the next test.

**Photo:**
![Step 1 temperature tower result](images/petg-01-temp.jpg) <!-- add your photo -->

---

## Step 2 — Flow rate (YOLO)

**Method:** Orca `Calibration → Flow rate → YOLO (Recommended)`, default range −0.05…+0.05,
step 0.01, 11 blocks. Printed at 245 °C, 50% fan, 0.20 mm, standard speed.

**Observations (middle blocks)**

| Modifier | Top surface / join line |
|----------|-------------------------|
| > +0.01 | Bumps + visible union line → over-extruded |
| **+0.01** | **Flattest top, join line only faintly raised, no gaps → best** |
| 0.00 | Some groove ("subsided"), line slightly larger than outer |
| −0.01 | More groove; line width matches outer |
| < −0.01 | Gaps in outer arcs → under-extruded |

**Decision:** best block = **+0.01**. Slight over is the correct side (smooth, watertight
top; grooves/gaps are the worse failure).

**Applied:** `final flow = current + modifier = 0.95 + 0.01 =` **`0.96`** → saved to filament profile.

**Photo:**
![Step 2 flow rate YOLO result](images/petg-02-flow.jpg) <!-- add your photo -->

## Step 3 — Pressure advance
_Pending._

## Step 4 — Retraction
_Pending._

## Step 5 — Max volumetric speed
_Pending._

## Step 6 — Bridging
_Pending._

## Step 7 — Ironing
_Pending._

---

When every step is done, copy the final numbers into the **results table** in
[the guide](../filament-calibration.md#recorded-values-per-filament) as the PETG row.
