# Flat 3D model

A 3D model of my flat, built from my own measurements, floorplans and photos, used to plan furniture and interior design with real products at their real sizes.

## How it works

The whole flat is described in one data file, `flat.json`. `index.html` is a three.js viewer that reads it and builds the model: walls with door and window openings, floors, and furniture. Nothing is drawn by hand; to change the model, change `flat.json`.

The viewer has:
- a 3D view (orbit, pan, zoom) and a plan view that shows each wall's number and internal length. Plan view cuts everything at 1200 mm, like an architect's plan, so doors, worktops and windows show and wall cupboards and cornices don't
- realistic finishes: textured floors, wall colours, skirting, picture rails, panelling, cornices, window frames and sills, door frames and door leaves
- a wall height slider for cutaway views (fixed fittings are cut with the walls)
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
  floorplans/         scans or photos of plans (floorplan.png is the agent's plan)
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
  "defaults": { "ceilingHeight": 3400, "wallThickness": 100, "doorHeight": 2100,
                "finish": { "trim": "#f4f2ec", "skirting": 200 } },   // finish defaults for every room
  "rooms": [ ... ],
  "walls": [ ... ],
  "openings": [ ... ],
  "furniture": [ ... ]
}
```

### Rooms

```jsonc
{
  "id": "living",                 // short id used by openings and furniture
  "name": "Living room",
  "floor": "timber",              // timber | tile | checker | carpet | concrete
  "floorColour": "#c99d68",       // base colour (boards, tiles, carpet; the light squares for checker)
  "floorColour2": "#1c1c1e",      // checker only: the dark squares
  "floorRuns": "x",               // timber only: boards run along x or y
  "tileSize": 300,                // tile and checker only
  "ceilingHeight": 3100,          // optional, overrides the default
  "finish": {                     // optional, merged over defaults.finish
    "wall": "#34495f",            // paint (below the picture rail, if there is one)
    "upper": "#f1eee7",           // paint above the picture rail
    "pictureRail": 2450,          // height of the rail
    "cornice": 260,               // depth of the cornice at the top of the wall
    "skirting": 230,              // skirting height (0 for none)
    "dado": { "height": 1150, "colour": "#1f3b32" },   // panelling from the floor up
    "trim": "#f4f2ec"             // woodwork: skirting, rails, architraves, sills
  },
  "corners": [[0,0],[4800,0],[4800,4200],[0,4200]],
  "wallThickness": [450,100,100,450]   // optional, one per wall, else the default
}
```

- `corners` are the room's **internal** corners in flat-wide coordinates. Rooms do not share corners: two rooms either side of a 100 mm partition have corners 100 mm apart.
- Wall `i` runs from corner `i` to corner `i+1` (the last wall closes back to corner 0). Wall numbering therefore follows the order the corners are listed. List corners clockwise as seen on the plan, starting top left, so numbering is predictable.
- Walls are drawn on the outside of each room's outline, `wallThickness[i]` thick. Where two rooms' walls overlap in a shared partition, that is expected.
- Any shape works: an L-shaped room, a bay window or a chimney breast is just more corners. A chimney breast is modelled as the room outline stepping round it.

### Freestanding walls

For wall pieces that are not part of a room outline: nibs, part walls, the sides of a built-in cupboard.

```jsonc
{ "name": "Bathroom part wall", "room": "bathroom", "from": [1490, 3340], "to": [1490, 4270], "thickness": 100, "height": 2000 }
```

- The wall is centred on the line from `from` to `to`. `thickness` defaults to `defaults.wallThickness`, `height` to the room's ceiling height.
- With `room`, both faces get that room's finish (paint, skirting and so on). `colour` sets the plain wall colour instead.

### Openings (doors and windows)

```jsonc
{ "type": "door",   "room": "living", "wall": 2, "offset": 3000, "width": 838 }
{ "type": "window", "room": "living", "wall": 0, "offset": 700, "width": 1200, "sill": 750, "height": 1700 }
```

- `offset` is measured along the wall from its start corner (corner `wall`) to the near edge of the opening.
- Doors default to `defaults.doorHeight`; set `height` to override.
- Door leaves are drawn only when `hinge` is set: `"hinge": "start" | "end"` (the jamb nearer the wall's start or end corner), `"swing": "in" | "out"` (into this room or the other side), `"open": 85` (degrees, 0 for closed), `"glazed": true` for a glazed door, `"leaf": "#hex"` for a colour other than the trim.
- Windows take `"frame": "#hex"` (frame colour, default the trim colour), `"transom": 0.6` (height of the meeting rail as a fraction of the window, 0 for none) and `"bars": 1` (vertical glazing bars).
- Every door and window gets an architrave in the room's trim colour; windows also get an internal sill board.
- An opening is defined once, on one room. The viewer also cuts any parallel wall within that wall's thickness on the other side, so a door between two rooms appears in both.

### Furniture

```jsonc
{
  "name": "Sofa", "room": "living",
  "x": 2400, "y": 3500,           // centre of the piece on the plan
  "w": 2100, "d": 900, "h": 850,  // width along x and depth along y before rotation
  "rot": 180,                     // degrees clockwise on the plan, optional
  "colour": "#6b7a8f",
  "status": "owned",              // owned | candidate | fixture
  "price": "£599", "source": "https://...", "notes": "...",   // optional, shown in the details panel
  "model": "models/sofa.glb"      // optional, see below
}
```

`fixture` is for permanent parts of the flat that are not walls, such as a fireplace, kitchen units, bath or radiators. They are always shown, listed under "Fixed fittings", and cut with the walls by the wall height slider. A fitted item made of several parts (worktop on units, fireplace surround and hearth) is several fixtures.

Extra fields for any piece:
- `"z": 1500`: height of its underside above the floor (wall cupboards, shelves, mirrors).
- `"kind": "radiator"` with `"style": "panel" | "column"`: drawn as a radiator rather than a plain box.
- `"opacity": 0.3`, `"metalness": 0.6`, `"roughness": 0.2`: for glass, stainless steel, gloss.

Without `model` a piece is drawn as a box of its stated size. With `model` the viewer loads the GLB and scales it to exactly `w` × `d` × `h`, falling back to a box if it fails to load.

## Working rules

- **Keep the raw data.** When I give measurements, save them to `reference/measurements.md` exactly as given, with the date, before converting them. `flat.json` is derived; the notes are the source.
- **Measurements beat the floorplan.** Use plans for layout and how rooms relate, but my measured figures for sizes. Where they disagree by more than about 50 mm, tell me instead of picking one or averaging.
- **Don't invent figures.** If something needed is missing (a sill height, a wall thickness), use a sensible default, add it to a "Still to measure" list at the bottom of `reference/measurements.md`, and say so.
- **Check against photos.** Use room photos to confirm what is on each wall, the order of doors and windows, and finishes and colours. Flag anything that contradicts the measurements.
- **Check every change.** After editing `flat.json`: validate the JSON, confirm the viewer's Checks panel is empty, confirm each room's internal wall lengths in plan view match the measurements, and, if a headless browser is available, take a screenshot of both views and look at it.
- **Permanent fixtures only, keep it clean.** In the model and in any renders or screenshots, leave out clutter, people and anything movable that appears in photos or plans. Keep only what looks permanent: walls, doors, windows, fireplaces, built-in cupboards, fitted kitchen and bathroom fittings, radiators. Furniture comes in only when I ask for it (roadmap step 2 onwards).
- **Walls that should meet.** Rooms either side of a partition should be exactly one wall thickness apart. Work out room positions from shared walls and measured thicknesses (measure in a door frame for internal walls, in a window reveal for external ones) rather than assuming.
- Writing for me: British spelling, plain wording, no em dashes.

## Roadmap

1. **Real layout:** replace the placeholder rooms, doors and windows with my measurements and plans.
2. **Existing furniture:** add the pieces I own, with sizes and positions from my notes and photos.
3. **Candidate products:** search for pieces against a brief (type, maximum size, budget, style), saving each to `products/<slug>.json` with name, retailer, URL, price, dimensions and image URLs, then adding it to `flat.json` as `status: "candidate"`. Bright Data's MCP server is an option for scraping UK retailers at volume; plain web fetch is fine for a handful of products. Respect each site's terms.
4. **Real 3D models:** for shortlisted pieces, use the manufacturer's own model where one exists; otherwise generate one from product photos (Meshy, Tripo, Hunyuan3D or similar), export as GLB to `models/`, and let the viewer scale it to the stated dimensions.
5. **Possible later:** dragging furniture in the plan view with a way to copy the updated positions back into `flat.json`; per-room wall colours; materials from photos.

## Current state

Roadmap step 1 is nearly done. `flat.json` holds the real layout traced from `reference/floorplans/floorplan.png` (seven rooms including the hall cupboard, all doors and windows, nibs and cupboard walls), dressed from the room photos in `reference/photos/`: wall colours, picture rails, cornices, floors, door leaves, window frames, and the fixed fittings (fireplace, built-in shelving, kitchen units, bathroom fittings, radiators). Room sizes are the plan's printed figures; positions are scaled from the plan; heights, fittings and colours are estimated from photos. No tape measurements yet. Next: my measurements, working through the "Still to measure" list in `reference/measurements.md`.
