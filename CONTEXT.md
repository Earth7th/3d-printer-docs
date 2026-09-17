# 3D Print Knowledge

An archive of practical 3D-printing knowledge — guides, calibration procedures, and reference notes — written to be readable by others and portable across printers where possible.

## Language

**Machine calibration**:
One-time, hardware-level setup of a printer: mechanical checks, belt tension, bed/first-layer and Z-offset. Redone only after hardware changes.
_Avoid_: printer setup, hardware tuning

**Filament calibration**:
Per-spool tuning of print parameters (temperature, flow rate, pressure advance, retraction, max volumetric speed) that must be repeated for each new filament type. This is the current focus.
_Avoid_: material profiling, per-material calibration

**Auto-calibration**:
The printer's built-in routine that self-tunes some parameters (on the K2: AI-camera-assisted flow and pressure advance, plus auto bed leveling and input shaping). Distinct from manual [[filament-calibration]], which refines or replaces its results.
_Avoid_: self-calibration, one-click calibration
