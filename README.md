# Fusion Furniture Lab

A static, UI-only workspace that executes the research and teaching portion of the AP Fusion 360 Parametric Furniture Builder & Configurator prompt.

- Interactive, draggable 3D cabinet view, front view and exploded view.
- Width, height, depth, independent board thickness, 0–100 shelves, clearances and custom shelf elevations.
- Independent cabinet items and four named presets.
- Current finished-panel schedule, combined project cut list, grouping and CSV export.
- Ten-section native Fusion workbook, 22 official Autodesk references and resumable checkpoints.
- JSON project export/import. No database, backend, localStorage or IndexedDB.

## Use

Website: https://fusion-furniture-lab.sergiu-chiriac732673.chatgpt.site

Run locally with any static HTTP server rooted at `dist/`, e.g. `python3 -m http.server 8080 --directory dist`. Open http://localhost:8080. ES modules and fetched workbook data require HTTP rather than opening index.html as a file.

`npm test` runs the calculation tests. `npm run build` copies the authored research/workbook from docs into dist/docs. No dependency installation is needed.

## Repository map

- `dist/index.html`, `styles.css`, `app.js`: responsive website and interaction layer.
- `dist/engine.js`: pure configuration validation, geometry, grouping, CSV and project schema.
- `dist/acceptance.js`: browser-runnable acceptance cases.
- `docs/workbook.json`: complete structured tutorial, in the prompt's requested order.
- `docs/guide.html`: standalone readable guide.
- `docs/sources.json`: official sources, checked date and claim mapping.
- `docs/make_workbook.py`: editable source that regenerates the workbook and guide.
- `docs/requirements.md`: milestone scope and requirements traceability.
- `docs/verification.md`: evidence and unverified boundaries.
- `tests/engine.test.mjs`: automated tests.

## Manufacturing and verification boundaries

This release computes its own browser model; it does not connect to Autodesk Fusion or produce a native F3D file. The Python add-in is a documented next milestone, not a delivered or validated integration. Native Fusion checkpoints remain pending until executed and checked in Fusion.

Exports describe finished rectangular panel sizes, not a nesting plan or supplier-approved blanks. Edge banding starts unspecified. No band thickness, kerf or machining allowance is silently applied. Grain is explicit metadata. All dimensions are in millimeters; display rounding does not replace the underlying formulas.

Runtime state is memory-only. Export project JSON before closing or refreshing. Import validates before replacing the active project.
