# Digital Portfolio — Version History

Backups are saved as `index_v[N].html` in this folder. Open any version directly in Chrome to preview it.

---

## v2 — (current) Three.js Wireframe 3D Viewers
**Date:** 2026-05-01
**File:** `index.html`

**Changes:**
- Replaced `<model-viewer>` web components with Three.js canvas-based wireframe viewers
- Models render in cyan wireframe (`#4cc9f0`) matching the blueprint aesthetic
- OrbitControls: drag to rotate, scroll to zoom, auto-rotate enabled
- Fallback: shows CAD poster image with "Host on GitHub Pages" overlay when running locally (file:// restriction blocks GLB loading)
- Once hosted on GitHub Pages, both GLBs (Pedal_Box_v9.glb, diff-bar-assembly.glb) load as interactive wireframe models

---

## v1 — Tab Layout + Build Photo Galleries + model-viewer
**Date:** 2026-04-30 / 2026-05-01
**File:** `index_v1.html`

**Changes from original:**
- Restructured site from single vertical scroll to 3-tab layout (Resume / Projects / Photos)
- Added MRover build photo gallery (5 photos, base64-encoded inline)
- Added DER (Dearborn Electric Racing) build photo gallery (5 photos, base64-encoded inline)
- Fixed EXIF rotation on 4 sideways photos (ImageOps.exif_transpose)
- Redesigned Capabilities section: removed boxed tiles, replaced with 2-col resume-style list
- Contact section: added second email (goellner@umich.edu), updated top-right label
- Hero H1: "Design." made orange and italic to match "Engineering"
- Added `<model-viewer>` web components for Pedal Box GLB and Diff Bar GLB (poster images as fallback)
- Added JS error detection overlay directing user to GitHub Pages for 3D viewing
- Converted diff-bar STL → GLB via trimesh

---

## v0 — Original single-scroll portfolio
**Date:** Pre-2026-04-30
**File:** *(no backup — this was the starting state)*

**Known state:**
- Single vertical scroll: Nav → Hero → About → FSAE scrollytelling → FSAE renders → MRover scrollytelling → Capabilities → Contact → Footer
- SVG schematics in both scrollytelling sections
- 5 CAD render images (external files, not base64)
- model-viewer not yet added
- Capabilities as boxed 8-tile grid
- Contact had phone number removed, single email only
