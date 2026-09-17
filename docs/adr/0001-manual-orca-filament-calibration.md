# Manual per-filament calibration in OrcaSlicer, over trusting K2 auto-calibration

The K2's AI auto-calibration produces flow and pressure-advance values automatically, so
the obvious path is to just trust it. We instead document a **manual** calibration pass
because the auto result is frequently off for a specific spool and can't tune temperature,
retraction, max flow, bridging, or ironing at all. We target **OrcaSlicer** (not the
official Creality Print) because its built-in calibration tests are far stronger, and the
resulting method is portable to other printers — matching this archive's "readable and
reusable by others" goal. Trade-off: readers must install Orca and the doc doesn't fully
cover Creality Print.
