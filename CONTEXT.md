# Digital Portfolio — Project Context

This file is a handoff document for a new Cowork session. Read it, then continue the work.

## Who this is for

**Lucas Goellner** — B.S.E. Mechanical Engineering, University of Michigan-Ann Arbor (grad **Apr 2028**).
- **Chassis Engineer, Michigan Mars Rover Team (MRover)** — Sep 2025 – Present. Designing the differential bar and chassis body components in **Siemens NX**. Reducing lost motion via tighter tolerances and joint redesign. Manufactures parts in-house (mill, lathe, laser cutter, 3D printer). Works with carbon fiber and metal joining.
- **Brake System Team Lead, Dearborn Electric Racing (FSAE EV)** — Oct 2024 – Jul 2025. Owned 32-part pedal box. **2.9 factor of safety** on brake pedal (7 design iterations). $2,000 budget, in-house manufactured. Brake system performed without failure at competition. Master CAD passed FSAE pre-comp review on first attempt (1,644 parts).
- U.S. Army veteran — Bradley Crewman, M2A3 (Jul 2021 – Mar 2024)
- Email: **goellnerlucas@gmail.com** | LinkedIn: lucasgoellnerpf
- Phone number is on his resume but **must NOT be displayed on the public portfolio site** — Lucas asked it removed.
- Currently seeking a Mechanical Design internship for Spring–Summer 2026

## What's built

A single-file portfolio at `index.html` in this folder. Everything is inline (no build step, no external deps except Google Fonts).

**Stack:** Plain HTML + CSS + vanilla JS. Inter (display) + JetBrains Mono (mono) loaded from Google Fonts.

**Aesthetic:** Modern technical / engineering blueprint feel. Inspired by:
1. The Claude Design components Lucas exported (`components.jsx` in the uploads folder) — striped CAD-style placeholders with corner brackets, callout pins, mono spec tables, three-column Problem/Approach/Outcome, four-up highlight stats
2. The MRover team site (mrover.org) — starfield background, dark `oklch` navy palette, vertical left-side step rail with dashed markers, schematic ↔ blueprint mode swap

**Color tokens (in `:root`):**
- Background: `oklch(0.20 0.005 240)` (dark navy)
- Accent: `#FF6B35` (engineering orange)
- Wireframe-mode tint: `#4cc9f0` (cyan)
- Text varies from `#fff` down through several rgba alpha levels (`--fg-85`, `--fg-55`, `--fg-50`, `--fg-45`, `--fg-35`, `--fg-20`)

## Sections (in order)

1. **Nav** — sticky top, brand "LG / MECH ENG · 2026", links: About / FSAE / MRover / Capabilities / Contact
2. **Hero** — name + "designing the things that move", monospace ticker row (CAD / SIM / TEAMS / MFG / YEAR), two CTAs
3. **About** — `00 / ABOUT` — kicker + balanced h2 + spec table (grad Apr 2028), 3-col body (Background = Army; Now = MRover Chassis Engineer + FSAE history; Focus = 2026 internship)
4. **FSAE Pedal Box** (`#projects`) — `01 / FEATURED` — scroll-pinned, sticky SVG schematic with left rail + 6 scrolling steps. Spec table shows 32 parts, FoS 2.9, $2K, Competition Verified.
5. **Render Gallery** (`#pedal-renders`) — `01.5 / RENDERS` — real CAD images from the Mechanical Design Portfolio PDF: master CAD car (span-2 hero), pedal box assembly, v7 brake pedal, 7 iterations, FEA stress plot.
6. **MRover Differential Bar** (`#rover`) — `02 / FEATURED` — scroll-pinned, 6 steps (The Role, D1 Bar, D2 Pivot, E1 Joints, F1 Chassis Body, G1 In-House Build). Spec table now: Siemens NX, Carbon · Metal, In-House mfg.
7. **Capabilities** (`#capabilities`) — 8-tile skills grid (SolidWorks, Siemens NX, SW Sim, AutoCAD, Mill & Lathe, 3D Printing, Laser Cutting, Carbon & Metal Joining)
8. **Contact** (`#contact`) — 4 contact cards (Email, LinkedIn, Resume 2026 .pdf, Phone)
9. **Footer**

## Key implementation patterns

- **Scrollytelling:** Each `.feature` section has a 2-col `.feature-grid` with a sticky `.feature-stage` on the left (the SVG schematic + left rail) and `.feature-steps` on the right (the scrolling text panels). JS uses `requestAnimationFrame` + scroll listener to find the step closest to viewport center, sets `data-active` on the matching `.feature-canvas`, and adds `.is-active` to the matching `.feature-step` and `.rail-item`.
- **Component highlighting:** Each SVG schematic has 5 `<g data-part="N">` groups. CSS rules like `.feature-canvas[data-active="1"] [data-part="1"] .part { stroke: var(--accent); }` light up the active part. Pins pulse via a CSS keyframe.
- **Wireframe mode:** When `data-active != "0"` on a canvas, all parts shift to cyan stroke; the active part overrides back to orange. Tag in top-right swaps from `SCHEMATIC · OVERVIEW` (white dot) to `BLUEPRINT · DETAIL` (cyan glowing dot).
- **Starfield:** SVG data URI background on `body::before`, fixed positioning so it parallaxes.
- **Rail:** Buttons inside `.feature-stage` positioned absolute top-left. Click jumps to the step via `scrollIntoView`.

## Files in this folder

- `index.html` — the portfolio (everything is here)
- `Lucas Goellner 2026 Resume.pdf` — **current resume** (linked from the contact section)
- `Pedal_Box_v9.zip` — full SolidWorks part files for the FSAE pedal box (linked as a download)
- **CAD renders (linked from the new "01.5 / RENDERS" gallery section):**
  - `fsae-car-master.jpg` — full FSAE EV master CAD with all subsystems integrated (1,644 parts)
  - `pedal-box-assembly.jpg` — pedal box front view with master cylinders
  - `brake-pedal-final.jpg` — v7 final brake pedal (isometric)
  - `pedal-iterations.jpg` — 6 brake pedal iterations side-by-side
  - `brake-pedal-fea.jpg` — FEA von Mises stress plot, FoS 2.9
- Older resume PDFs (no longer linked, kept for archive): `Lucas Goellner Resume 2025.docx`, `Lucas Goellner Tesla FSAE EV Resume.pdf`, `Lucas Goellner Tesla Cover Letter.pdf`
- `CONTEXT.md` — this file

## Open follow-ups (not done yet)

1. **The Pedal Box scrollytelling section still uses the SVG schematic** as the sticky visual. Now that real renders exist (`pedal-box-assembly.jpg`, `brake-pedal-final.jpg`, `brake-pedal-fea.jpg`), an upgrade is to swap the SVG out for a stack of images that swap based on `data-active`: overview shows assembly, brake-pedal step shows the v7 render, etc. Either replace the SVG entirely or layer it on top of the image to keep the callout pins.
2. **MRover renders missing** — the differential bar section still uses the SVG schematic. When Lucas exports NX renders of the chassis/diff bar, drop them in (filenames like `diff-bar-iso.jpg`, `chassis-body.jpg`) and either swap the SVG or build a second `02.5 / RENDERS` gallery section between the diff-bar feature and Capabilities, mirroring the Pedal Box gallery pattern.
3. **Photo of manufactured pedal box** — would be great as a reality-check next to the CAD renders. Add a "manufactured" card to the gallery if/when one exists.
4. **Profile photo** — optional, would warm up the hero/about.
5. **GitHub Pages deployment** — Lucas wants to potentially host this at a real URL. Push folder to a public repo, enable Pages, get `lucasgoellner.github.io/portfolio` for the resume.
6. **Custom domain** — `.com` for ~$12/year (Cloudflare/Namecheap/Porkbun) pointed at GitHub Pages would be the polished move.
7. **Dearborn Electric Racing logo** — Lucas attached the DER logo (Michigan M with car silhouette + "DEARBORN ELECTRIC RACING" text) to the chat. It wasn't saved as a file. Could be incorporated as a small inline mark in the FSAE feature section header. He'd need to re-attach as a file (PNG/SVG) for it to land in the folder.

## Design decisions to honor

- **Single-file HTML.** No build step, no React, no npm. Lucas asked for this explicitly — easy to host, easy to edit.
- **Orange accent stays.** Don't switch to MRover's yellow — the orange differentiates Lucas's portfolio from his team's brand. (MRover *inspired* the design; we don't want to copy it outright.)
- **Don't copy MRover's logo treatment or layout 1:1.** Take cues, not the whole identity.
- **Dark background only.** No light mode requested.
- **Conversational, low-formatting tone in chat replies.** Lucas prefers terse, direct answers without lots of bullet points or trailing summaries.
