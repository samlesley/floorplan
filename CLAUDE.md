# Flat 3D model

A 3D model of my flat, built from my own measurements, floorplans and photos, used to plan furniture and interior design with real products at their real sizes.

## How it works

The whole flat is described in one data file, `flat.json`. `index.html` is a three.js viewer that reads it and builds the model: walls with door and window openings, floors, and furniture. Nothing is drawn by hand; to change the model, change `flat.json`.

The viewer has:
- a 3D view (orbit, pan, zoom) and a plan view that shows each wall's number and internal length
- a wall height slider for cutaway views
- furniture you can click for size, price and link; pieces marked `candidate` can be hidden
- a "Checks" panel listing data problems (an opening past the end of its wall, a missing wall, a piece with no size)
- a "Preview a different flat.json" button for trying a version without saving it

## Running it

`index.html` loads `flat.json` with fetch, so it needs a local web server rather than opening the file directly:

```
python3 -m http.server 8000
```

Then open http://localhost:8000. three.js loads from cdn.jsdelivr.net (version 0.170.0, pinned in the import map). GitHub Pages also works if I want a link.

## Repo layout

```
CLAUDE.md
index.html            viewer
flat.json             the model data
reference/
  floorplans/         scans or photos of plans
  photos/<room-id>/   room and furniture photos
  measurements.md     my raw measurements, as I gave them
models/               .glb furniture models (optional, see below)
products/             candidate product data (later)
```

Create folders as they are needed.

## Data format (`flat.json`)

All sizes in millimetres. Coordinates follow a printed floorplan: x runs left to right, y runs top to bottom, origin at the top left.

```jsonc
{
  "name": "My flat",
  "note": "Shown under the title in the viewer",
  "defaults": { "ceilingHeight": 2800, "wallThickness": 100, "doorHeight": 2000 },
  "rooms": [ ... ],
  "openings": [ ... ],
  "furniture": [ ... ]
}
```

### Rooms

```jsonc
{
  "id": "living",                 // short id used by openings and furniture
  "name": "Living room",
  "floor": "timber",              // timber | tile | carpet | concrete, or set "floorColour": "#hex"
  "ceilingHeight": 3100,          // optional, overrides the default
  "corners": [[0,0],[4800,0],[4800,4200],[0,4200]],
  "wallThickness": [450,100,100,450]   // optional, one per wall, else the default
}
```

- `corners` are the room's **internal** corners in flat-wide coordinates. Rooms do not share corners: two rooms either side of a 100 mm partition have corners 100 mm apart.
- Wall `i` runs from corner `i` to corner `i+1` (the last wall closes back to corner 0). Wall numbering therefore follows the order the corners are listed. List corners clockwise as seen on the plan, starting top left, so numbering is predictable.
- Walls are drawn on the outside of each room's outline, `wallThickness[i]` thick. Where two rooms' walls overlap in a shared partition, that is expected.
- Any shape works: an L-shaped room, a bay window or a chimney breast is just more corners. A chimney breast is modelled as the room outline stepping round it.

### Openings (doors and windows)

```jsonc
{ "type": "door",   "room": "living", "wall": 2, "offset": 3000, "width": 838 }
{ "type": "window", "room": "living", "wall": 0, "offset": 700, "width": 1200, "sill": 750, "height": 1700 }
```

- `offset` is measured along the wall from its start corner (corner `wall`) to the near edge of the opening.
- Doors default to `defaults.doorHeight`; set `height` to override.
- An opening is defined once, on one room. The viewer also cuts any parallel wall within that wall's thickness on the other side, so a door between two rooms appears in both.

### Furniture

```jsonc
{
  "name": "Sofa", "room": "living",
  "x": 2400, "y": 3500,           // centre of the piece on the plan
  "w": 2100, "d": 900, "h": 850,  // width along x and depth along y before rotation
  "rot": 180,                     // degrees clockwise on the plan, optional
  "colour": "#6b7a8f",
  "status": "owned",              // owned | candidate
  "price": "£599", "source": "https://...", "notes": "...",   // optional, shown in the details panel
  "model": "models/sofa.glb"      // optional, see below
}
```

Without `model` a piece is drawn as a box of its stated size. With `model` the viewer loads the GLB and scales it to exactly `w` × `d` × `h`, falling back to a box if it fails to load.

## Working rules

- **Keep the raw data.** When I give measurements, save them to `reference/measurements.md` exactly as given, with the date, before converting them. `flat.json` is derived; the notes are the source.
- **Measurements beat the floorplan.** Use plans for layout and how rooms relate, but my measured figures for sizes. Where they disagree by more than about 50 mm, tell me instead of picking one or averaging.
- **Don't invent figures.** If something needed is missing (a sill height, a wall thickness), use a sensible default, add it to a "Still to measure" list at the bottom of `reference/measurements.md`, and say so.
- **Check against photos.** Use room photos to confirm what is on each wall, the order of doors and windows, and finishes and colours. Flag anything that contradicts the measurements.
- **Check every change.** After editing `flat.json`: validate the JSON, confirm the viewer's Checks panel is empty, confirm each room's internal wall lengths in plan view match the measurements, and, if a headless browser is available, take a screenshot of both views and look at it.
- **Walls that should meet.** Rooms either side of a partition should be exactly one wall thickness apart. Work out room positions from shared walls and measured thicknesses (measure in a door frame for internal walls, in a window reveal for external ones) rather than assuming.
- Writing for me: British spelling, plain wording, no em dashes.

## Roadmap

1. **Real layout:** replace the placeholder rooms, doors and windows with my measurements and plans.
2. **Existing furniture:** add the pieces I own, with sizes and positions from my notes and photos.
3. **Candidate products:** search for pieces against a brief (type, maximum size, budget, style), saving each to `products/<slug>.json` with name, retailer, URL, price, dimensions and image URLs, then adding it to `flat.json` as `status: "candidate"`. Bright Data's MCP server is an option for scraping UK retailers at volume; plain web fetch is fine for a handful of products. Respect each site's terms.
4. **Real 3D models:** for shortlisted pieces, use the manufacturer's own model where one exists; otherwise generate one from product photos (Meshy, Tripo, Hunyuan3D or similar), export as GLB to `models/`, and let the viewer scale it to the stated dimensions.
5. **Possible later:** dragging furniture in the plan view with a way to copy the updated positions back into `flat.json`; per-room wall colours; materials from photos.

## Current state

`flat.json` holds a made-up five-room placeholder that shows the format. None of it is my flat. Start with roadmap step 1.
