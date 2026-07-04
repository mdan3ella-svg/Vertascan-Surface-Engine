# VERTASCAN Surface Engine

**Version:** v0.2 — Render Pipeline Update
**Type:** Single-file, browser-based surfacing, shading & look-development tool
**License:** Proprietary — All Rights Reserved (see `LICENSE.md`)

---

## Overview

VERTASCAN Surface Engine is a self-contained HTML application for sketching curves,
generating surfaces, applying physically based materials, lighting scenes with
image-based lighting, and exporting look-development stills — all running client-side
in the browser on top of Three.js/WebGL. There is no build step, server, or install
process: open the `.html` file and the full toolset is available.

This is a surfacing and shading workbench, **not** a parametric CAD kernel. There is
no BREP/NURBS solver and no history-based dependency graph — geometry is generated
directly as triangle meshes from user-drawn curves and primitives.

## Getting Started

1. Open the `.html` file in a modern desktop browser (Chrome, Edge, or Firefox with
   WebGL2 support).
2. Use the left-hand dock to sketch curves, generate surfaces, or drop in primitives.
3. Select any object to edit its transform and material in the right-hand **Scene**
   panel's Inspector.
4. Switch the right-hand panel to **Render** to control lighting, atmosphere,
   environment (HDRI/IBL), and postprocessing, then export a still render.
5. Click **Help** in the topbar at any time for the full in-app tools manual, or
   **About** for the technical spec sheet.

No installation, package manager, or internet connection is required after the page
and its module dependencies have loaded once (Three.js is loaded via CDN import map).

## Feature Summary

**Modeling**
- Ground-plane curve sketching (Catmull-Rom)
- Revolve, Extrude (with bevel), and Loft surfacing operations
- Primitives: box, sphere, cylinder, cone, torus
- Mesh tools: flip normals/winding, mirror on X
- Transform gizmo (move/rotate/scale), undo/redo, 4 camera bookmarks

**Shading & Materials**
- Preset PBR materials (carpaint, chrome, aluminum, glass, plastic, carbon, etc.)
- Full per-object shader controls: metalness, roughness, clearcoat, clearcoat
  roughness, transmission, IOR, emissive intensity/color, opacity
- Analysis shading modes: Shaded PBR, Wireframe, Normal Map, Zebra Stripes,
  Curvature Tint

**Lighting, Atmosphere & Environment**
- Key light intensity/color/azimuth/elevation, ambient fill
- Fog (color/near/far), exposure control, backdrop color
- HDRI (`.hdr`) and equirectangular world-map (`.jpg`/`.png`) environment import for
  image-based global illumination and reflections
- Adjustable environment intensity and background blur; one-click studio reset

**Postprocessing & Export**
- Bloom, depth of field (bokeh), vignette + film grain, all via a proper
  `EffectComposer` pipeline
- Still-image export to PNG or JPG at Viewport, HD, Full HD, QHD, or 4K resolution
- Model import: `.glb`/`.gltf`, `.obj`, `.stl` (including drag-and-drop)
- Model export: `.glb`, `.stl`

## Technical Stack

| Component | Detail |
|---|---|
| Rendering | Three.js r170 (WebGL2) |
| Tone Mapping | ACES Filmic, sRGB output |
| Material Model | `MeshPhysicalMaterial` |
| Environment Lighting | PMREM-filtered HDRI / equirect maps |
| Postprocessing | `EffectComposer` (Bloom, Bokeh DOF, custom vignette/grain shader) |
| UI | Vanilla HTML/CSS/JS, no framework, no build step |

## Documentation

Full usage instructions and the technical specification are built into the
application itself:

- **Help** (topbar) — step-by-step tool manual, keyboard shortcuts, workflow guidance
- **About** (topbar) — technical spec sheet, supported formats, feature list

## Browser Support

Requires a browser with WebGL2 and ES module support. Recommended: current versions
of Chrome, Edge, or Firefox. Not tested on mobile browsers.

## License

This software is proprietary and confidential. See `LICENSE.md` for full terms.
All rights reserved.
