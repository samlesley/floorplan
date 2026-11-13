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

Source: 18 room photos shared on 2026-11-08 (since taken off GitHub; kept privately). They confirm the plan's layout: door order round the hall, the kitchen door into the lounge, no kitchen window, two bathroom windows, the bath against the part wall, the chimney breast in bedroom 2. Nothing contradicts the plan.

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

## 2026-11-08: bedroom 2 window

As given:

> the window in the bedrom is actually recessed, and the bookshelf sits inside the recess, the sofa goes up to the walll

How it was used: the window now sits at the back of a recess in the outside wall, 1150 wide and 350 deep (both estimated), starting where the futon ends, so the futon runs right up to the wall beside it. The low bookshelf sits inside the recess under the window; its height is now 600 so it fits under the sill.

## 2026-11-08: bedroom 2 window position

As given:

> the spare room window is more central

How it was used: the window recess (and the window centred in it) is now centred on the window wall, between the side wall and the chimney breast. The futon still runs up to the wall, so its end now sits partly across the recess opening, with the low bookshelf inside the recess beside it. The distance from the futon wall to the recess would confirm this.

## 2026-11-08: lamps and the cat

Lamps seen in the photos, added with estimated sizes and positions: the pleated table lamp on the lounge side table, the stained glass lamp on the dining table, the brass wall uplighter on the lounge picture wall, the green swing-arm wall lamp over the futon, the white desk lamp on the shelf above the desk, the orange wall light above the bedside table in bedroom 1, the blue clip-on lamp on top of the bookcase, and the globe lamp on the hall side table.

The calico cat (seen in the bedroom 2 photo) is modelled curled up asleep on the lounge sofa, at my choice of spot.

## 2026-11-08: bedroom 2 airer (candidate)

As given:

> can you also add a 6 lathe 1.5m long victorian style pulley air dryer to the spare room, hooked nnear to the light switch, using this winch mechanism to lower it
> put it sort of to the right and behind from the perspectic as being sat at the desk in that room, between the door and light/ sofa

How it was used: a candidate 6 lath, 1.5 m Victorian airer runs along the room between the door and the futon, behind and to the right when sat at the desk, its laths 2.3 m up when raised (Lower it in its details panel drops it to 1.15 m). The hand winch (Cast in Style A2366) is on the wall by the light switch, just round the corner from the door, at 950 to the bottom of its back board, with its rope running up and along the ceiling to the airer's pulleys. The light switch position is taken from the photo; its exact place, and the raised and lowered heights you want, are worth confirming.

## 2026-11-08: lights, layout fixes and the hi-fi

As given:

> 1. dining room table is a tiffany style lamp in the centre of the table it's also two chairs on either side none in the centre
> 2. kitchen has under cabinet strip lighting
> 3. the recessed booksehlf in the living room has 3 spotlighs on the top shelf, on the left hand side shining inwards
> 4. in the bathroom there is a strip light on the top of the mirror, and under cabinet lighting on the utility area cuppboard
> 5. there are two hubsch wally lamps in green, in the spare room this is the one on the wall by the window, also the main light in this room is slightly clsoer to the window, it hangs over the end of the sofa there. the pulley should hang so that it doesn't overlap with the open door. the over one goes between the unit in the living room and the tall radiator
> 6. in the bedroom there are two ikea donut style lamps either side of the headboard area. kind of similar to the left hand side one, but on both sides (simila bed side table on both sides as well)
>
> there's a rega p3 turntable and rega brio amp on the unit next to the fireplace

How these were used:

1. Tiffany lamp moved to the centre of the dining table. Read "two chairs on either side, none in the centre" as one chair at each end of the table, so the chair at the middle of the long side was taken out.
2. Strip lights under all three kitchen wall units.
3. Three small spotlights on the top shelf of the recessed shelving, at the left-hand end as you face it, shining in across the shelves.
4. A light bar on top of the bathroom mirror cabinet and a strip under the utility wall cabinet.
5. The green swing-arm lamp in bedroom 2 is now named as a Hübsch Wally; its pair is on the lounge wall between the bureau bookcase and the tall radiator. The paper globe pendant moved towards the window, over the end of the futon. The airer moved 430 towards the window so it clears the open door.
6. Donut wall lamps and bedside tables now on both sides of the bed in bedroom 1.

Hi-fi: Rega Planar 3 (447 W x 117 H x 360 D, lid closed, from a retailer listing; lid not modelled; colour assumed black) and Rega Brio (216 W x 78 H x 345 D, retailer listings agree) side by side on the record cabinet, which was widened from 600 to 700 (still an estimate) so they fit.

## Paint colours (2026-11-13)

> in the bathroom, the wood panelling is painted in Dark Brunswick Green from little greene. The walls are Portland Stone - Light.

> elsewhere in the house we have used china clay and stock from little greene (bedroom/hallway and kitchen respectively)

Then: "can you make the bathroom walls China Clay and also make sure the panelling is matched to dark brunswick green"

In `flat.json` the bathroom walls are now China Clay (#efe9e3) and the panelling Dark Brunswick Green (LG 88, #3f5443). The bathroom radiator was drawn in the panelling colour, so it changed too. Hex values are the ones most colour sites give for these paints; screen colour is only approximate.

## Still to measure

Defaults, plan-scaled figures or photo estimates are in use for all of these.

- Bedroom 2 length, from the hall wall to the outside wall. With the outside wall in line with the lounge it is about 4160, but the plan says 3.57 m, so a tape figure would settle it. If the plan is short at that end of the flat, it may also explain the lounge length (5.5 m measured against 5.10 m).
- Lounge shelving recess: width and depth.
- Bedroom 2 window recess: width, depth, and the distance from the futon wall to the recess; the low bookshelf's height.

- Lounge length: you measured about 5.5 m to the longest point; the plan says 5.10. Was that to the glass of the middle bay windows, or to the wall face beside them? If to the glass, the gap is probably the depth of the window reveals, and the outside walls are much thicker than the plan draws.
- Kitchen and bathroom ceiling heights (3000 in use for "slightly less" than 3.2 m). In the kitchen photos the gap above the wall units looks smaller than 800, so the wall unit heights are worth measuring too (floor to top of the wall units).
- Picture rail height (estimated 2450; the hall's looks lower in the photos, level with the tops of the door architraves, so 2250 is in use there) and cornice depths.
- Bathroom door: the height of the fanlight over it (450 estimated, so the opening is 2550 in all).
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
- Bedroom 2: light switch position (for the airer winch), and the airer's raised and lowered heights.
- Lounge: the record cabinet's real width (700 assumed so the turntable and amplifier fit side by side) and the turntable's colour.
