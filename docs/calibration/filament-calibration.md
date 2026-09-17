# Filament Calibration Guide (Any 3D Printer)

A step-by-step guide to hand-tuning a filament on **any FDM 3D printer** using
**OrcaSlicer**. The process is the same on every machine — only the menu names and
starting numbers change. If your printer already ran an auto-calibration, this guide is
the manual refinement that actually makes prints clean.

> **Author's machine:** these steps were written and tested on a **Creality K2** (with
> the CFS multi-material unit). Where the K2 does something specific — like AI
> auto-calibration — it's called out as an example, not a requirement.

> **New to this?** You don't need to understand everything. Do the steps **in order**,
> save each value, and your prints will improve.

---

## Why calibrate by hand if auto-calibration ran?

Many modern printers auto-tune some parameters — the author's K2, for example, uses an AI
camera to set **flow** and **pressure advance** and runs auto bed leveling + input
shaping. That gets you 80% of the way. But the auto pass is often a little off for a
specific spool, and it can't tune temperature, retraction, top-surface finish, or
bridging. Manual calibration closes that gap — and you only redo it **per filament type**,
not every print. If your printer has no auto-calibration at all, this guide is your full
calibration.

**When to (re)calibrate a filament:**
- A new brand or type of filament (e.g. switching PLA → PETG, or Brand A PETG → Brand B PETG)
- Visible defects: stringing, blobs, rough tops, gaps in walls, sagging bridges
- After a nozzle change or major firmware update (redo the whole machine setup too)

---

## Before you start

Do these every time, or the tests below will lie to you:

1. **Clean the nozzle** — no burnt residue on the tip.
2. **Clean the bed** — wash with dish soap or wipe with IPA. No fingerprints.
3. **Dry the filament** — PETG especially absorbs moisture; wet filament strings, pops, and leaves pockmarks no matter how well you calibrate. See **[Drying Filament](../reference/filament-drying.md)** for temps, times, and how to spot wet filament.
4. **Let auto-cal finish** — if your printer has a built-in calibration (like the K2), run it first. This guide *refines* its result.
5. **Pick ONE filament** to calibrate at a time. If you use a multi-material unit (e.g. the K2's CFS), load it in a known slot and note which one.
6. **Use a standard print speed and keep it constant** across all 8 steps. Calibrate at the speed you actually print — don't use max speed, or you'll be testing speed instead of the parameter. Changing speed later can shift earlier results.

> **How to read the photos in each step:** every step shows three results —
> ❌ **too low / under**, ✅ **correct**, ❌ **too high / over**. Match your own print to
> the middle one. Your numbers will differ from the examples; that's expected.

---

## The order matters

Each step assumes the previous one is correct. **Do not skip ahead.**

**Core (dimensional accuracy):**
1. Temperature
2. Flow rate
3. Pressure advance
4. Retraction
5. Max volumetric speed

**Finishing (surface quality):**
6. Bridging
7. Overhang
8. Ironing (top surface)

In OrcaSlicer, most tests live under the **Calibration** menu in the top bar. Steps 6–8
are printed test models where you adjust settings and reprint.

**Where each value gets saved** — Orca has two profiles, and it matters which one:
- **Filament settings** (per-material): temperature, flow ratio, pressure advance,
  retraction (as an override), max volumetric speed → Steps 1–5.
- **Process settings** (per print/quality profile): bridging, overhang, and ironing → Steps 6–8.

Each step below ends with a **"Where to set it in Orca"** line giving the exact path.

---

## Step 1 — Temperature

**What it fixes:** Layer bonding, stringing, and surface finish. Everything downstream
shifts with temperature, so lock this first.

**How to run it (Orca):** `Calibration → Temperature`. Set the range for your material
(PETG example: **250 °C down to 230 °C** in 5 °C steps). Orca prints a tower where each
block is a different temperature.

**How to read it:**
- ❌ *Too hot:* stringing, drooping, blobs, shiny-but-messy overhangs.
- ✅ *Correct:* clean layers, strong bonding, minimal strings, good bridging on the tower's overhang test.
- ❌ *Too cold:* weak layer adhesion (blocks snap apart easily), gaps, matte/rough surface.

Pick the **lowest temperature that still bonds strongly and looks clean**.

| Result | Photo |
|--------|-------|
| ❌ Too hot | ![Temperature too hot — stringing and drooping](images/01-temp-too-hot.jpg) |
| ✅ Correct | ![Temperature correct — clean, well bonded](images/01-temp-correct.jpg) |
| ❌ Too cold | ![Temperature too cold — weak bonding, gaps](images/01-temp-too-cold.jpg) |

**Where to set it in Orca:** **Filament settings** (edit your filament profile) → **Filament**
tab → **Nozzle temperature** (set "Other layers"; first layer can be +5 °C). Save the profile.

---

## Step 2 — Flow rate

**What it fixes:** How *much* plastic comes out. Too much = bulging tops and elephant
skin; too little = gaps between lines.

**How to run it (Orca — YOLO, recommended):** `Calibration → Flow rate → YOLO (Recommended)`.
It prints **11 blocks**, each nudging your current flow ratio by an additive modifier
(default range **−0.05 … +0.05**, step **0.01**; "perfectionist" is −0.04 … +0.035, step
0.005). Pick the best block, then **`new flow = old flow + that block's modifier`**
(e.g. 0.98 + 0.01 = 0.99). One print, done.

> **Legacy alternative (Pass 1 / Pass 2):** older two-print method using a *multiplicative*
> formula `old × (100 + modifier) / 100`. YOLO replaces it — only use it if your Orca
> version lacks YOLO.

**How to read it:**
- ❌ *Too low:* visible gaps/lines between infill top strands, translucent thin top.
- ✅ *Correct:* smooth, flat top surface with no gaps and no ridges.
- ❌ *Too high:* raised ridges, rough "over-stuffed" top, dimensional swelling.

| Result | Photo |
|--------|-------|
| ❌ Too low | ![Flow too low — gaps in top surface](images/02-flow-too-low.jpg) |
| ✅ Correct | ![Flow correct — smooth flat top](images/02-flow-correct.jpg) |
| ❌ Too high | ![Flow too high — raised ridges](images/02-flow-too-high.jpg) |

**Where to set it in Orca:** **Filament settings** → **Filament** tab → **Flow ratio**.
Enter the final number (`old + modifier`). Save the profile.

---

## Step 3 — Pressure advance

**What it fixes:** Corners and line consistency. Controls how the printer manages
pressure when it starts/stops extruding, so corners aren't bulged and thin lines aren't
patchy. If your printer auto-set a value (the K2 does), **verify it here and refine if
the test looks off.**

**How to run it (Orca):** `Calibration → Pressure advance`. Orca has three methods:
**Pattern** (most accurate — recommended, and works well on Klipper firmware like the
K2's), **Line** (quick single-layer), and **Tower**. Choose the **direct-drive** test
variant for the K2 (Bowden setups use a much wider range). Recommended range for
direct-drive: **start 0, end 0.08, step 0.002**. Orca labels each section with its PA
value.

**How to read it:**
- ❌ *Too low:* bulging, blobby corners; thick line ends.
- ✅ *Correct:* sharp, even corners; uniform line width throughout.
- ❌ *Too high:* gaps/thinning right at corners; dashed-looking line starts.

Read the value off the cleanest section.

| Result | Photo |
|--------|-------|
| ❌ Too low | ![PA too low — bulging corners](images/03-pa-too-low.jpg) |
| ✅ Correct | ![PA correct — sharp even corners](images/03-pa-correct.jpg) |
| ❌ Too high | ![PA too high — gaps at corners](images/03-pa-too-high.jpg) |

**Where to set it in Orca:** **Filament settings** → **Setting Overrides** tab → tick
**Pressure advance** and enter the value. Save the profile. (On Klipper machines like the
K2 this writes the `pressure_advance` value for prints sliced from Orca.)

---

## Step 4 — Retraction

**What it fixes:** Stringing and blobs during travel moves. Only meaningful once flow and
PA are correct.

**How to run it (Orca):** `Calibration → Retraction test`. Prints two towers with travel
moves between them, increasing retraction distance up the height. Find the lowest height
(= lowest retraction) where strings disappear.

**How to read it:**
- ❌ *Too low:* wispy strings/hairs between the towers.
- ✅ *Correct:* clean gap, no strings, no surface scarring on the towers.
- ❌ *Too high:* gaps/under-extrusion after travels, clicking extruder, ground filament.

| Result | Photo |
|--------|-------|
| ❌ Too low | ![Retraction too low — stringing](images/04-retraction-too-low.jpg) |
| ✅ Correct | ![Retraction correct — clean, no strings](images/04-retraction-correct.jpg) |
| ❌ Too high | ![Retraction too high — under-extrusion](images/04-retraction-too-high.jpg) |

**Where to set it in Orca:** two options —
- **Per filament (recommended):** **Filament settings** → **Setting Overrides** tab →
  under **Retraction**, tick **Length** and set the value. Keeps it tied to this filament.
- **Global:** **Printer settings** → **Extruder 1** → **Retraction** → **Length**. Applies
  to every filament.

Save after setting.

---

## Step 5 — Max volumetric speed

**What it fixes:** The real speed ceiling for this spool — how fast the hotend can melt
plastic before it under-extrudes. Prevents "printed too fast, walls got thin" defects.

**How to run it (Orca):** `Calibration → Max flowrate` (max volumetric speed). Orca prints
a tower that speeds up as it rises. Find the height where the surface starts to degrade —
that flow rate (mm³/s) is your limit.

**How to read it:**
- ✅ *Below the limit:* consistent, opaque, smooth walls.
- ❌ *Above the limit:* the surface turns rough/translucent and under-extruded near the top.

Set the value slightly **below** where degradation starts.

| Result | Photo |
|--------|-------|
| ✅ Correct (below limit) | ![Below max flow — smooth walls](images/05-maxflow-correct.jpg) |
| ❌ Too fast (above limit) | ![Above max flow — rough under-extrusion](images/05-maxflow-too-high.jpg) |

**Where to set it in Orca:** **Filament settings** → **Filament** tab → **Max volumetric
speed** (mm³/s). Save the profile.

---

## Step 6 — Bridging

**What it fixes:** Spans printed across a gap with no support underneath (the underside of
holes, overhangs, ceilings). Poorly tuned bridges sag and droop.

**How to run it (Orca):** There's no one-click test — print a **bridge test model** (any
"bridging torture test" from MakerWorld/Thingiverse). Then adjust
*Quality → Bridging → Bridge flow ratio* (default `1.0`) and *bridge speed*. Lower the flow
slightly and/or increase bridge speed if it sags; reprint.

**How to read it:**
- ❌ *Too low flow / too slow:* saggy, drooping, hairy strands under the bridge.
- ✅ *Correct:* flat, taut strands spanning the gap cleanly.
- ❌ *Too high flow:* lumpy, bulging underside.

| Result | Photo |
|--------|-------|
| ❌ Sagging | ![Bridge sagging — flow too low or too slow](images/06-bridge-sagging.jpg) |
| ✅ Correct | ![Bridge correct — flat taut strands](images/06-bridge-correct.jpg) |
| ❌ Lumpy | ![Bridge lumpy — flow too high](images/06-bridge-lumpy.jpg) |

**Where to set it in Orca:** **Process settings** (the print/quality profile, *not* the
filament) → **Quality** → **Bridging** → **Bridge flow ratio**; bridge speed is under
**Speed → Others → Bridge**. Save the process profile.

---

## Step 7 — Overhang

**What it fixes:** Steep unsupported walls (angles leaning outward) printing cleanly instead
of curling, drooping, or going rough on the underside. Closely related to bridging — both
are unsupported material, controlled mainly by **cooling and speed** rather than extrusion.

**How to run it (Orca):** No one-click test — print an **overhang test model** (a stepped
"overhang tower" with increasing angles, e.g. 30°–70° from vertical, from
MakerWorld/Thingiverse). Find the steepest angle that still prints cleanly. Improve poor
overhangs by **more cooling** on the overhang, **slowing** the overhang moves, and/or
**thinner layers**.

**How to read it:**
- ❌ *Failing:* edges curl up, underside droops/rough, corners lift → too little cooling or too fast.
- ✅ *Correct:* clean, consistent surface down to steep angles.
- ⚖️ *PETG trade-off:* more cooling improves overhangs but **weakens layer bonding** — balance this against your Step 1 temperature/strength choice rather than maxing cooling.

| Result | Photo |
|--------|-------|
| ❌ Poor (curling/droop) | ![Overhang poor — curling and droop](images/07-overhang-poor.jpg) |
| ✅ Correct | ![Overhang correct — clean steep angles](images/07-overhang-correct.jpg) |

**Where to set it in Orca:** **Process settings** → **Quality** → *Force cooling for
overhangs and bridges*, *Cooling overhang threshold*, *Fan speed for overhangs*; and
**Speed** → *overhang speeds / "Slow down for overhangs"* to slow steep overhangs. Save the
process profile.

---

## Step 8 — Ironing (top surface)

**What it fixes:** Makes flat top surfaces smooth and even by re-passing them with a hot
nozzle and a trickle of plastic. Optional, but great for lids, plates, and logos.

**How to run it (Orca):** Enable *Quality → Ironing → Ironing type = Top surfaces*. Tune
*Ironing flow* (start ~**10–15%**) and *Ironing line spacing* (start ~**0.1 mm**). Print a
flat-topped test cube and adjust.

**How to read it:**
- ❌ *Too little flow / too wide spacing:* visible lines/gaps remain, patchy shine.
- ✅ *Correct:* uniform, smooth, evenly glossy top.
- ❌ *Too much flow / too tight spacing:* plastic builds up, ripples, or scars the surface.

| Result | Photo |
|--------|-------|
| ❌ Under-ironed | ![Ironing too little — lines remain](images/08-ironing-under.jpg) |
| ✅ Correct | ![Ironing correct — smooth even top](images/08-ironing-correct.jpg) |
| ❌ Over-ironed | ![Ironing too much — buildup and ripples](images/08-ironing-over.jpg) |

**Where to set it in Orca:** **Process settings** (the print/quality profile) → **Quality**
→ **Ironing** → set **Ironing type = Top surfaces**, plus **Ironing flow** and **Ironing
line spacing**. Save the process profile.

---

## Recorded values per filament

Fill one row per spool you calibrate. The **generic PETG** row below shows *example*
starting ranges — replace with **your** measured values. See a real worked run in the
[Generic PETG calibration log](logs/petg-generic.md). Add a new row for each new
filament (PLA, ABS, etc.).

| Filament | Nozzle °C | Bed °C | Flow ratio | Pressure advance | Retraction (mm) | Max vol. speed (mm³/s) | Bridge flow | Ironing flow / spacing | Notes |
|----------|-----------|--------|------------|------------------|-----------------|------------------------|-------------|------------------------|-------|
| Generic PETG *(example — replace)* | 230–250 | 70–80 | ~0.95–1.0 | *from test* | 1–2 | *from test* | ~0.9–1.0 | 10–15% / 0.1 mm | Dry before printing; strings easily |
|  |  |  |  |  |  |  |  |  |  |

---

## Machine calibration (hardware setup) — *coming later*

This guide covers **filament** tuning. The one-time **machine-level** setup — mechanical
checks, belt tension, first-layer / Z-offset — is deferred and will be documented
separately. On printers with auto bed leveling and input shaping (like the author's K2)
most of this is automated, but it's worth a manual verification pass.
_TODO: add `docs/calibration/machine-setup.md`._

---

## Adding your photos

Drop your images in `docs/calibration/images/` using the filenames referenced above
(e.g. `01-temp-correct.jpg`). See `images/README.md` for the naming list. Until you add
them, the image links above will show as broken — that's expected.
