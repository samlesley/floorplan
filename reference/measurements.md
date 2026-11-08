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
- The lounge's 4.08 is measured into the chimney recess. The main part of the room is about 3.73 deep (scaled). Width 5.10 is to the tip of the bay. Since the photos show the fireplace set flush in a flat wall, the model leaves the recess out, so the lounge reads 3730 deep in plan view rather than 4080.
- The hall's 3.07 is its left-hand part. The walk-in cupboard cuts into the hall's lower right corner, so the hall is L-shaped.
- Only permanent fixtures are modelled. No furniture, clutter or people.

## 2026-11-08: what the photos show

Source: `reference/photos/<room>/` (18 photos, uploaded 2026-11-08). They confirm the plan's layout: door order round the hall, the kitchen door into the lounge, no kitchen window, two bathroom windows, the bath against the part wall, the chimney breast in bedroom 2. Nothing contradicts the plan.

Clutter, people and movable furniture are left out. The model keeps paint, floors, woodwork and fixed fittings only. Colours are matched by eye from the photos, so they are approximate (lighting in the photos varies).

| Room | Walls | Floor | Fixed fittings modelled |
|------|-------|-------|-------------------------|
| Lounge | Dark blue below a white picture rail, white frieze above, deep ornate cornice and ceiling rose | Stripped pine boards | Burgundy fireplace surround with pale tiled slips, gas fire and raised hearth; white built-in shelving between the chimney and the bay; white column radiator by the hall door; tall column radiator by the bay; varnished timber sash windows in the bay |
| Hall | Cream, picture rail, dentil cornice | Stripped pine boards | White panelled doors with stained glass top panels; high storage shelf over the kitchen wall; white panel radiator; front door in a curtained recess |
| Kitchen | Cream | Large pale floor tiles | Dusty blue units in an L (hob and oven run on the bedroom 1 wall, sink run on the hall wall), grey stone-effect worktop, cream tiled splashback, tall fridge freezer unit, integrated dishwasher, black sink, gas hob, extractor with boxed-in chimney to the ceiling, glazed door to the lounge. Downlights suggest a lower ceiling than the lounge |
| Bathroom | Dark green tongue and groove panelling to about 1150, pale grey-green above | Black and white chequerboard tiles | Bath with glass screen and white tiling against the part wall; WC under the window nearest the outside corner; dark gloss vanity unit and basin with mirror cabinet; washing machine and cupboard under an oak worktop with a white wall cabinet; green panel radiator; cream tiled ledge under the windows; white top-hung windows |
| Bedroom 1 | Cream | Greige carpet | Dark blue panel radiator by the door; white sash windows. The mirrored wardrobe and bookcase are movable, so left out |
| Bedroom 2 | Sage green below a picture rail, white above, cornice; chimney breast in the corner | Light grey carpet | Tall timber sash window in a white surround; white panel radiator by the door |

Door swings from the photos: bedroom 1 and bathroom doors open into those rooms; lounge, bedroom 2 and kitchen doors open into the lounge or bedroom 2. All drawn open so the rooms can be seen.

## Still to measure

Defaults, plan-scaled figures or photo estimates are in use for all of these.

- Ceiling heights. Estimated from photos: lounge, hall, bedroom 2 and hall cupboard 3400; bedroom 1 2650, bathroom 2700 and kitchen 2500 (these look lowered, with downlights or a textured ceiling).
- Picture rail height (estimated 2450) and cornice depths.
- Door heights (estimated 2100) and the front door width (plan shows a 1140 opening; in the photos the door sits in a recess behind a curtain).
- Window sill heights and window heights. Estimated: lounge bay sill 600, height 1800; bedroom 2 sill 600, height 1850; bedroom 1 sill 800, height 1550; bathroom sill 950, height 1650.
- Window widths and positions, especially the four lounge bay windows (scaled from the plan). In the photos the bathroom windows look narrower than the plan, with a wider pier between them.
- Outside wall thickness, measured in a window reveal (plan draws about 150; real stone walls are likely much thicker).
- Internal wall thickness, measured in a door frame (plan draws about 100).
- Lounge: fireplace surround (1150 wide, 1180 high estimated), hearth and the position of the built-in shelving (about 900 wide, 380 deep estimated).
- Kitchen: unit runs and appliance positions (laid out from photos to fit the plan), wall unit heights, and what the two solid blocks in the lower corners are.
- Bedroom 1: the short wall by the door (about 940 long) and the cupboard marked W (about 400 x 510 inside). What is W?
- Bathroom: bath length (1440 to the part wall, from the plan), WC, vanity and utility positions; the part wall height; the cupboard marked C (about 370 x 620 inside).
- Bedroom 2: the solid block in the lower right corner (1410 x 290 scaled).
- Hall: the high shelf (depth and height) and radiator position; the hall cupboard inside size (about 1230 x 1340 scaled).
- Radiator sizes and positions in every room (estimated from photos).
