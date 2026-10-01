# 3D Vehicle Damage Log

Mark and document vehicle damage on an interactive 3D model of the van. Built as a lightweight tool for documenting damage on rental transporters for insurance claims.

### Live Demo: https://damage-log.wbr.one/

## Features

- Rotate and zoom a 3D model of the vehicle and click directly on the spot of the damage
- Automatic location labels from the model's parts (e.g. "Right sliding door", "Front bumper, left corner")
- Per damage: type, severity, status (open / repaired), date, reporter, description and photos
- Numbered pins coloured by severity, filter by status, click a pin or list entry to fly to it
- Download a report (HTML with rendered views, table and photos) or a CSV
- Load your own vehicle as a `.glb` model, falls back to a built-in schematic van
- Responsive, works on phones for documenting damage on site

## Tech stack

- Vanilla JavaScript, single HTML file, no build step
- [Three.js](https://threejs.org/) (WebGLRenderer, OrbitControls, GLTFLoader, raycasting)
- Blender + Python for preparing the vehicle models (cleanup, part naming, materials, polygon reduction)

## Run locally

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

To show a specific vehicle, put a model at `models/default.glb`. Part labels work best when mesh objects are named like `Body`, `FrontDoor_L`, `SlidingDoor_R`, `RearDoor_L`, `Bumper_Front`, `Wheel_FL` and materials like `Glass`, `Plastic_Dark`.

## Demo mode

This version stores everything in the browser tab (`sessionStorage`), so every visitor works on their own copy and nothing is shared or saved on a server.

## Roadmap

- Backend with Laravel 12 + MySQL (vehicles, damages, photos, audit log)
- Vue 3 component for the 3D viewer
- PDF reports generated on the server
