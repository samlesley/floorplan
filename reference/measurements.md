# Measurements

All sizes in millimetres unless stated. Raw figures are kept exactly as given; `flat.json` is derived from them.

## 2026-11-08: floorplan figures (not yet measured by me)

Source: `reference/floorplans/floorplan.png` (estate agent style plan, no scale bar). These are the plan's figures, copied as printed. No tape measurements yet.

| Room      | Imperial          | Metric          |
|-----------|-------------------|-----------------|
| Bedroom 1 | 13'6" x 10'8"     | 4.12 m x 3.24 m |
| Kitchen   | 9'1" x 6'6"       | 2.78 m x 1.98 m |
| Lounge    | 16'9" x 13'5"     | 5.10 m x 4.08 m |
| Hall      | 9'1" x 10'1"      | 2.78 m x 3.07 m |
| Bathroom  | 13'7" x 5'11"     | 4.13 m x 1.81 m |
| Bedroom 2 | 11'8" x 8'1"      | 3.57 m x 2.46 m |

Also on the plan: a chimney breast with fireplace in the lounge's top wall, a four-sided bay window in the lounge, a cupboard marked W in bedroom 1, a cupboard marked C in the bathroom, a walk-in cupboard marked C off the hall.

### How the model was built from the plan

- The plan is drawn to a consistent scale of about 12.77 mm per pixel (every room's printed size agrees with its drawn size to within about 0.5%).
- Room sizes in `flat.json` use the printed figures. Everything else (door and window positions and widths, nibs, cupboards, the bay angles, the chimney recess, the hall cupboard) is scaled off the drawing and rounded to 10 mm, so treat those as accurate to perhaps ±50 mm.
- Wall thicknesses are as drawn: about 150 for outside walls and 100 for internal partitions.
- Bedroom 1 is printed as 4.12 wide and the bathroom below it as 4.13, but they share the same side walls on the plan. I used 4120 for both (10 mm difference, within rounding).
- The lounge's 4.08 is measured into the chimney recess. The main part of the room is about 3.73 deep (scaled). Width 5.10 is to the tip of the bay.
- The hall's 3.07 is its left-hand part. The walk-in cupboard cuts into the hall's lower right corner, so the hall is L-shaped.
- Doors are drawn as plain gaps on the plan with no swing, so door hinge sides and swing directions are unknown.
- Only permanent fixtures are modelled. No furniture, clutter or people.

## Still to measure

Defaults or plan-scaled figures are in use for all of these.

- Ceiling height in every room (default 2800; tenement-style flats are often higher).
- Door heights (default 2000) and the front door width (plan shows a 1140 opening, which may include a frame or side panel).
- Window sill heights and window heights (default sill 750, height 1700) for every window.
- Window widths and positions, especially the four lounge bay windows (scaled from the plan).
- Outside wall thickness, measured in a window reveal (plan draws about 150; real stone walls are likely much thicker).
- Internal wall thickness, measured in a door frame (plan draws about 100).
- Lounge: chimney recess width and depth, fireplace surround width, depth and height (height 1200 is a placeholder).
- Kitchen: the two solid blocks in the lower corners (310 x 470 and 170 x 470 scaled). What are they (chimney breast, boxed pipes)?
- Kitchen: the plan shows no window. Confirm.
- Bedroom 1: the short wall by the door (about 940 long) and the cupboard marked W (about 400 x 510 inside). What is W?
- Bathroom: the part wall (about 930 long) and its height; the cupboard marked C (about 370 x 620 inside).
- Bedroom 2: the solid block in the lower right corner (1410 x 290 scaled).
- Hall cupboard: inside size (about 1230 x 1340 scaled).
- Floor finishes in every room (left neutral until confirmed from photos).
- Permanent fittings not shown on the plan: kitchen units and appliances, bath, WC, basin, radiators. Need photos and measurements.
