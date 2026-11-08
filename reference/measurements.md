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

## 2026-11-08: my measurements (first batch)

As given:

> ceiling heights about 3.2m
> slightly less in bathroom and kitchen (spotlights)
>
> the lounge is about 5.5m in total length to the longest point, the back of the sofa is 2m from the window
>
> windows in the lounge panes are 70cm wide
>
> in the bathroom, the utility counter top starts 1.6m away from the door threshold
> the counter is 88cm, the room partition is 26cm

How these were used:

- Ceilings set to 3200 everywhere except the kitchen and bathroom. "Slightly less" there is not a figure, so they use 3000 for now (see below). Bedroom 1 was 2650, a photo estimate, and is now 3200.
- Lounge length: **not applied**. The plan says 5.10 to the tip of the bay; 5.5 is about 400 more, which is more than the 50 mm I can resolve without asking. See the question under "Still to measure".
- Sofa 2 m from the window: furniture, kept for step 2.
- Lounge windows: taken as 700 of glass, so each opening is 810 including the frame, centred on its side of the bay (positions not yet measured).
- Bathroom, measured from the bathroom side of the door threshold: utility counter runs from 1600 to 2480 from the door wall (880 long, washing machine 600 plus cupboard 280), then the partition, now 260 thick (the plan drew about 110). The partition's centre is 20 mm from where the plan puts it. The bath now runs 1380 from the window wall to the partition.

## 2026-11-08: furniture seen in the photos

Added to `flat.json` as `owned` pieces. Every size and position is estimated from the photos, except the sofa, whose back is 2 m from the bay window (measured). Left out as clutter: boxes, bags, laundry, towels, ornaments, pictures, lamps, plants, the clothes airer, the leaning mirror, the step stool, cat things.

| Room | Pieces |
|------|--------|
| Lounge | Pale sage three-seat sofa facing the TV wall; walnut coffee table (two parts) on a beige rug; walnut TV unit and TV between the hall and kitchen doors; oak record cabinet left of the fireplace; wooden armchair and round side table by the radiator; oak bureau bookcase on the wall opposite the fireplace, near the bay; dining table and three chairs in the bay |
| Kitchen | Green metal shelving unit with wooden shelves and a pedal bin by the lounge door; red rug |
| Hall | Red upholstered bench and round side table on the kitchen wall; dark green patterned rug |
| Bedroom 1 | Double bed with its head on the window wall; bedside table; mirrored sliding wardrobe on the kitchen side wall; navy bookcase by the radiator |
| Bedroom 2 | Futon sofa bed on the lounge side wall; low bookshelf by the window; pine side table; cream rug; dark wood wardrobe; desk and desk chair on the hall wall |

## 2026-11-08: my corrections to the model

As given:

> the bed and wardrobe in the main bedroom are the wrong orientaiton, the photo that is based on had my back to the window
>
> the unit to the right of the fireplace is recessed into the wall, in built shelfs
>
> the spare room looks short the outside wall would be in line with the living room?
>
> the hallway rug orientation is the wrong way
>
> the 'armchair' isn't in the door in the living room, closer to the sofa and the small side table is in the gap between sofa and armchair

How these were used:

- Bedroom 1: with the photo taken from the window, the mirrored wardrobe faces the window, so it now stands in the alcove between the short wall and the corner, beside the door. The bed's head is against the kitchen side wall, near the window end, with the bedside table between it and the window wall.
- Lounge: the built-in shelving now sits in a recess in the fireplace wall, its front flush with the wall. Recess depth 380 (the shelving depth) until measured.
- Bedroom 2: the outside wall now lines up with the lounge's front wall where the bay starts, which makes the room about 4160 long against the plan's 3.57 m (about 590 more). The chimney breast stays against the outside wall, and the futon, bookshelf and side table move with it.
- Hall rug turned to run along the hall, towards the lounge and bedroom 2 doors.
- Lounge armchair moved next to the sofa's end, angled towards the TV, with the round side table between them.

## 2026-11-08: more detail from the photos

Added after a second pass over the photos, all estimated: pendant lights (lounge dome shade with ceiling rose, stained glass shade in the hall, drum shade in bedroom 1, paper globe in bedroom 2); Roman blinds half down in the bay; dark red curtains in bedroom 1; café curtains on the bathroom windows; roller blind part down in bedroom 2; curtain over the front door recess; overmantel mirror; speakers either side of the TV; wooden cube shelf in the kitchen; green border tiles round the bath; bracket shelves and the monitor in bedroom 2; picture walls in the lounge, hall and both bedrooms, and the oval mirror in the hall. Picture positions and sizes are approximate.

## Still to measure

Defaults, plan-scaled figures or photo estimates are in use for all of these.

- Bedroom 2 length, from the hall wall to the outside wall. With the outside wall in line with the lounge it is about 4160, but the plan says 3.57 m, so a tape figure would settle it. If the plan is short at that end of the flat, it may also explain the lounge length (5.5 m measured against 5.10 m).
- Lounge shelving recess: width and depth.

- Lounge length: you measured about 5.5 m to the longest point; the plan says 5.10. Was that to the glass of the middle bay windows, or to the wall face beside them? If to the glass, the gap is probably the depth of the window reveals, and the outside walls are much thicker than the plan draws.
- Kitchen and bathroom ceiling heights (3000 in use for "slightly less" than 3.2 m). In the kitchen photos the gap above the wall units looks smaller than 800, so the wall unit heights are worth measuring too (floor to top of the wall units).
- Picture rail height (estimated 2450) and cornice depths.
- Door heights (estimated 2100) and the front door width (plan shows a 1140 opening; in the photos the door sits in a recess behind a curtain).
- Window sill heights and window heights. Estimated: lounge bay sill 600, height 1800; bedroom 2 sill 600, height 1850; bedroom 1 sill 800, height 1550; bathroom sill 950, height 1650.
- Window widths and positions. The lounge bay windows are now 700 of glass each but centred by guesswork; the gap from each corner of the bay to the first frame would fix them. In the photos the bathroom windows look narrower than the plan, with a wider pier between them.
- Outside wall thickness, measured in a window reveal (plan draws about 150; real stone walls are likely much thicker).
- Internal wall thickness, measured in a door frame (plan draws about 100).
- Lounge: fireplace surround (1150 wide, 1180 high estimated), hearth and the position of the built-in shelving (about 900 wide, 380 deep estimated).
- Kitchen: unit runs and appliance positions (laid out from photos to fit the plan), wall unit heights, and what the two solid blocks in the lower corners are.
- Bedroom 1: the short wall by the door (about 940 long) and the cupboard marked W (about 400 x 510 inside). What is W?
- Bathroom: bath length (1380 if it runs from the window wall to the partition; please check), WC and vanity positions; the partition's length out from the wall and its height; the cupboard marked C (about 370 x 620 inside).
- Bedroom 2: the solid block in the lower right corner (1410 x 290 scaled).
- Hall: the high shelf (depth and height) and radiator position; the hall cupboard inside size (about 1230 x 1340 scaled).
- Radiator sizes and positions in every room (estimated from photos).
- Furniture: width, depth and height of each piece, and where it sits (distance from two walls), most usefully the sofa, coffee table, TV unit, bed, wardrobes and desk.
