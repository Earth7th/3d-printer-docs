# Topic-based documentation structure

The repo grew from a calibration-only doc into a general 3D-printing knowledge base. We
segment content **by topic** (calibration, materials, hardware, slicer, troubleshooting,
reference) rather than by printer or by material. This keeps each method written **once**
and applicable to any machine — matching the "portable, K2 as reference" goal — instead of
duplicating the same guide under every printer or filament. Printer- and material-specific
details live *inside* the relevant topic doc, with a small `printers/` area for
genuinely machine-only notes. Trade-off: some content is cross-cutting (e.g. filament
drying touches materials, troubleshooting, and calibration) and must be linked from
multiple topics rather than living in one obvious place; we keep one canonical copy in
`reference/` and link to it.
