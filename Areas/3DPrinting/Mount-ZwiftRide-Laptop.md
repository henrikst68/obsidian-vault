---
type: project
status: design
printer: Prusa Core One
interface: Zwift Ride stem end-cap dovetail
device: laptop
created: '2026-05-30'
---
# Mount: Zwift Ride Laptop Arm

Replace the paint-spattered easel currently propping a laptop in front of the Zwift Ride with a printed arm that fixes to the Zwift Ride cockpit and holds the laptop screen ~100mm up and ~150mm forward of the mount, tilted slightly back for rider viewing angle.

## Hardware context
- Trainer: Zwift Ride (white frame, integrated cockpit, Z-button shifter pods).
- Printer: Prusa Core One (build vol ~250x220x270, enclosed CoreXY; ASA/ABS/PETG capable).
- Device: laptop (heavier + longer than a tablet — leverage matters).

## Mounting interface — KEY FINDING
The Zwift Ride accessory interface is the **stem end cap**, not a handlebar clamp.
- Remove existing cap with a 6mm Allen key: loosen bolt underneath, slide cap off. This exposes a **dovetail**.
- Two community approaches:
  1. Reuse the original metal dovetail block + 2 self-tapping screws (blur_457 original).
  2. Print the dovetail integrally — no metal part, no extra hardware (blur_457 v2, model 1160468; csthomas84 remix 1580623).
- Official Zwift tablet holder rated for **1kg tablet max**; community mounts warned **not load-bearing**. A laptop on a 150mm arm exceeds these assumptions — design must respect the leverage.

## Strategy (token-efficient)
- DO NOT re-model the dovetail from scratch — it is the costly fit-iteration part.
- Use a proven end-cap base (blur_457 integral-dovetail, model 1160468) as the **base component** — borrow the solved interface.
- Design ONLY the new arm: vertical riser (~100mm), forward cantilever (~150mm), cradle tilted back ~10-15deg with lower lip + upper strap slot.
- Author/iterate the Fusion script as TEXT here; run natively in Fusion (Scripts & Add-Ins) on the laptop in one pass. Bring back errors/photos to fix text. MCP is on a separate laptop and not needed for one-shot builds.

## Target geometry (parametric — confirm before scripting)
- screen_height_above_mount = 100 mm
- screen_forward_offset = 150 mm
- screen_tilt_back = ~10-15 deg (TBD)
- Cantilever needs triangulated gusset for stiffness; max walls; ASA or PETG.

## Reference designs
- blur_457 v2 (integral dovetail, no hardware): printables.com/model/1160468
- csthomas84 remix (printable dovetail): printables.com/model/1580623

## Open questions before scripting
1. Laptop exact dimensions: width, depth/thickness, weight, screen size.
2. Landscape (likely) — confirm orientation.
3. Reuse original metal dovetail block, or fully printed dovetail?
4. Filament choice: ASA vs PETG.
5. Cradle style: open lip + strap, or fuller tray?

## Changelog
- 2026-05-30: Project created. Interface identified as stem end-cap dovetail. Strategy set: remix proven base, design arm only.


## Final design decisions (2026-05-30)
- Device baseline: Lenovo Yoga 7i 14" — 316.7 x 220.3 x 17.4 mm, ~1.45 kg, 360deg convertible.
- Cradle adjustment RANGE (not Yoga-specific): device width ~250-360mm, thickness ~7mm (tablet) to ~22mm (large laptop).
- REUSE existing aluminium dovetail block (bolted to console alu frame). Console proven to hold 15kg+ on front — leverage NOT a constraint.
- Height adjustment: discrete holes + pin/thumbscrew (rigid). Steps ~15-20mm.
- Retention: lower lip + sliding top retainer in a channel (NO strap).
- Tilt: ADJUSTABLE via toothed/notched hinge locking at discrete angles with thumbscrew (not friction pivot — avoids creep under laptop weight).
- Filament: TBD ASA vs PETG (both fine in Core One enclosure).

## Script approach
- Single Fusion 360 Python script, all dims as parameters at top.
- Dovetail pocket params marked as PLACEHOLDERS — user fills 6 caliper numbers:
  block width, block length, block height, dovetail top width, dovetail bottom width (=> angle), screw hole centre spacing, screw hole dia.
- Everything else (arm, post, tilt hinge, cradle) is solved geometry independent of measurements.
- Run natively in Fusion Scripts & Add-Ins, one pass.

## Changelog
- 2026-05-30: Project created. Interface identified as stem end-cap dovetail.
- 2026-05-30: Decisions locked — discrete-hole height, lip+sliding retainer, adjustable toothed tilt hinge, reuse alu dovetail. Yoga 7i 14" baseline confirmed. Writing script.


## Correction (2026-05-30) — cradle orientation
- Sketch v1 drew device on FORWARD face → screen faced away from rider. WRONG.
- Correct: device + lower lip on REAR (saddle-facing) face; back plate top leans FORWARD ~12deg so rider looks slightly down onto screen.
- SCRIPT BUG to fix next pass: cradle lip currently built on `cy + cradle_lip_depth` (forward) side — must move to REAR face. Retainer rails/slider likewise. Flip when adding hinge teeth + slider piece.


## Geometry revision (2026-05-30) — arm order flipped
- NEW arm shape: horizontal 150mm forward run FIRST off the dovetail, THEN riser ~100mm angled UP & BACK toward rider (brings screen to eye-line, better looking). Aligns with dovetail slide axis.
- Riser carries tilt hinge + cradle at its top.
- Stiffening: user chose SLIM arm, accept a little flex. Expect some screen bob during hard out-of-saddle efforts; stiffen later via one parameter (arm_thick) if needed. Safe structurally (console handles 15kg+).
- Sketch updated to this geometry + rider-facing cradle. Script NOT yet rewritten.
- PENDING SCRIPT REWRITE (do all at once with caliper numbers): (1) arm = forward-then-back-angled-riser; (2) reposition hinge+cradle to riser top; (3) flip cradle lip/retainer to REAR face; (4) add hinge teeth; (5) add sliding retainer piece.

## Still needed from user
- 6 caliper numbers off alu dovetail block (block length, width top, width bottom, height, screw spacing, screw dia).


## Geometry revision 2 (2026-05-30) — height adjust moved under screen, riser leans away
- Height adjustment MOVED from low (by dovetail) to UP UNDER THE SCREEN.
- Adjustment = TELESCOPING along the riser axis (discrete holes), not vertical.
- Riser now leans FORWARD / AWAY from rider (reversed from revision 1).
- Tilt hinge brings the screen FACE back to the rider (decoupled from riser lean).
- Stack: base -> short fixed neck -> 150mm horizontal run -> forward-leaning riser -> telescoping height section (under screen) -> tilt hinge -> rider-facing cradle.
- CAVEAT (noted to user): telescoping along a leaning riser means raising screen also pushes it forward (~few cm over 100mm travel); re-tilt to keep face square. Alternative if disliked: vertical telescoping column (busier look).
- Sketch updated. Script still NOT rewritten.

## Pending script rewrite — do ALL at once with caliper numbers
1. Base + short fixed neck (no adjustment at base).
2. 150mm horizontal run off neck.
3. Forward-leaning riser.
4. Telescoping height section under screen (discrete holes along riser axis).
5. Tilt hinge (add teeth) decoupling face angle.
6. Cradle lip/retainer on REAR rider-facing face.
7. Sliding retainer piece.
8. Fold in 6 dovetail caliper numbers.


## Geometry revision 3 (2026-05-30) — SIMPLIFIED to single arm
- Removed the fixed neck entirely (was purposeless — user correctly questioned it).
- Removed the separate riser. Arm is now ONE gentle upward+forward sweep straight off the dovetail base.
- 100mm datum CORRECTED: measured to the CRADLE LIP (screen lower edge), screen extends UP from there. Eye-line now roughly level, not looking up.
- Telescoping height adjust + tilt hinge remain at the screen end.
- ~150mm forward reach, ~100mm to lip — both fine-tuned on the bike.
- Caveat: telescoping along the diagonal arm axis => raising screen drifts it up+forward; tilt squares the face. Acceptable per user.
- This is the settled geometry. Sketch updated.

## SETTLED DESIGN SUMMARY (for script)
Stack: Base (dovetail pocket + 2 screws, reuse alu block) -> single arm (gentle up+forward sweep, slim, accepts flex) -> telescoping height section at screen end (discrete holes along arm axis) -> toothed tilt hinge (15deg steps) -> cradle (lower lip = 100mm datum, device extends up, lip+retainer on REAR rider-facing face, sliding top retainer between 2 rails). Cradle width ~330mm (fits 250-360 wide, 7-22 thick). Print ASA or PETG.

## ONLY remaining input before full script
6 caliper numbers off alu dovetail block: block length, width top (wide), width bottom (narrow), height, screw centre spacing, screw dia.


## Geometry revision 4 (2026-05-30) — arm must be HORIZONTAL (corrected)
- Arm is TRULY HORIZONTAL/level off the dovetail at console height, ~150mm forward. NOT a sweep, NOT angled up.
- At the far end: telescoping height element rises and LEANS FORWARD/AWAY from rider (discrete holes).
- Tilt hinge squares screen face back to rider.
- Cradle lip = 100mm datum; screen extends up; faces rider.
- This supersedes the "single gentle sweep" of revision 3. Revisions went: rise-first L -> forward-first L -> back-angled riser -> away-angled riser w/ height under screen -> single sweep -> THIS (horizontal arm + forward-leaning telescoping element). Settled here.

## SETTLED GEOMETRY (final, for script)
Base (dovetail pocket + 2 screws, reuse alu block) -> HORIZONTAL level arm ~150mm -> forward-leaning telescoping height element at far end (discrete holes) -> toothed tilt hinge (15deg steps, squares face to rider) -> cradle (lower lip = 100mm datum, device extends up, lip+sliding retainer on REAR rider-facing face, 2 rails). Cradle width ~330mm (fits 250-360 wide, 7-22 thick). ASA/PETG.

## ONLY remaining input: 6 caliper numbers off alu dovetail block
block length, width top (wide), width bottom (narrow), height, screw centre spacing, screw dia.


## Geometry revision 5 (2026-05-30) — steepened height element
- Forward-leaning element was too long (~300mm) because a shallow lean covers vertical distance inefficiently.
- FIX (option 1): near-vertical element with only a SLIGHT forward tip. ~110mm to reach the 100mm lip datum. Tilt hinge still squares face to rider.
- Settled. Final geometry = horizontal level arm ~150mm + near-vertical (slight forward tip) telescoping height element + toothed tilt hinge + rider-facing cradle (lip = 100mm datum).

## Suggested concrete params for script (from this geometry)
- arm horizontal length ~150mm, arm_thick ~12mm, arm_width ~24mm
- height element near-vertical, ~10deg forward tip, length ~120mm travel, discrete holes ~18mm pitch
- tilt hinge 15deg steps
- cradle width ~330mm, lip = 100mm datum, fits 250-360 wide / 7-22 thick


## Geometry revision 6 (2026-05-30) — cradle tilt direction corrected
- Rider sits HIGHER than the screen and looks slightly DOWN at it.
- Therefore screen TOP tips AWAY (forward), face angles UP toward rider. (Previous draw had it backwards — top toward rider.)
- Tilt hinge default should reflect this: screen face up toward a higher eye point.
- Cradle/sketch updated. Eye-line now angled down to screen.

## FINAL SETTLED GEOMETRY
Base (dovetail pocket + 2 screws, reuse alu block) -> horizontal level arm ~150mm -> near-vertical telescoping height element w/ slight forward tip (~110-120mm, discrete holes) -> toothed tilt hinge (15deg steps) -> cradle: lower lip = 100mm datum, screen extends up, screen TOP tips away / face angles UP toward higher rider, lip+sliding retainer on rider-facing side, 2 rails. Width ~330mm (250-360 wide, 7-22 thick). ASA/PETG.


## Script v2 written (2026-05-30)
- File: zwift_ride_laptop_mount.py (presented to user). Syntax-checked OK (py_compile).
- Built to settled geometry. 6 components: Base, Arm, HeightElement, TiltHinge, Cradle, TopRetainer.
- All float dims published as Fusion user parameters (live-editable in Change Parameters).
- Dovetail values STILL placeholders — Base not printable until 6 caliper numbers entered.

### Known-fragile spots (wrapped in try/except, may need a tweak on first run)
1. Hinge teeth via circularPatternFeatures — axis/quantity API varies by Fusion version. If teeth missing, get user's Fusion version + adjust.
2. hole_y cuts use SymmetricExtentDirection enum — may differ by version.
3. moveFeatures rotation for tel forward-tip and cradle tilt — verify bodies actually rotate; if not, check Matrix3D/moveFeatures signature.
- Strategy honest-flagged to user: strong first pass, NOT guaranteed flawless one-shot (written without live Fusion execution). User rationing live round-trips deliberately.

### Next session pickup
- User runs v2 in Fusion, reports message-box text / any error.
- Then: fix fragile spots if needed + fold in 6 dovetail caliper numbers.
- Geometry is DONE — do not re-litigate the concept (took 6 sketch revisions to settle; see above).


## Live MCP debug session (2026-05-30) — geometry corrected in Fusion
- Fusion MCP IS available this session (fusion_mcp_read/execute/update). Note: deferred tools don't persist across turns; re-search to load. Ranking often returns Chrome tools first — search "fusion_mcp_read screenshot" etc. and act in same turn.
- First run (script v2) had 3 bugs, all confirmed via screenshot + bounding-box query:
  1. Height element tipped wrong way (toward rider) — rotation sign inverted.
  2. Hinge + cradle + lip scattered/floating — separate transforms instead of one; disc built on XZ plane rotated differently than XY boxes; tip-rotation about world origin flung far-from-origin bodies (hinge landed z -92).
  3. Holes not cut (cut couldn't find target body).
- FIXES applied live: build whole screen assembly in local frame; tilt cradle bodies about their own base; tip whole assembly about ELEMENT BASE (not world origin) then translate; build hinge as cylinder on XY plane (shares frame with boxes).
- RESULT: clean continuous Z-stack, no floating parts. Verified by screenshot + bbox:
  Base z0-18, Arm 18-32, Element 30-142, Hinge 128-143, Cradle 139-240. Good.
- Document NOT saved (per user). Geometry will regenerate from script; script is source of truth.

## STILL TODO (next session, with measurements)
1. Cut the 5 height-adjust holes into the element properly (cut-target issue — target the element body explicitly / use participantBodies).
2. Add dovetail pocket + 2 screw holes to Base using 6 caliper numbers.
3. Re-verify on side view that forward tip (~10deg) reads right.
4. Working corrected build script lives in this session's history; consolidate into the .py file when finalising.

## STILL NEEDED FROM USER
6 caliper numbers off alu dovetail block: length, width top (wide), width bottom (narrow), height, screw centre spacing, screw dia.


## Correction (2026-05-30) — geometry NOT signed off
- Previous note said geometry "corrected/clean" — that overstates it. What was fixed: the scattered/floating-pieces bug (parts now form one connected continuous-Z assembly). That is NOT the same as the design being right.
- User does NOT agree the geometry is fixed. There are remaining issues (TBD — user to specify when resuming). Do not treat the design as approved.
- Next session: ask user what still looks wrong before making changes; don't assume.


## Block measurements + interface correction (2026-06-07)
- Alu block MEASURED (caliper, 3 photos + hand checks). These are AUTHORITATIVE; mesh is visual-reference only.
  - Width (narrow, L-R as mounted): **29.5 mm**
  - Height (Z): **43.87 mm** (confirmed twice — Image 1 = 43.87, Image 3 = 43.94, same dim within tolerance)
  - Depth (front-back): **40.55 mm** (not load-critical; size Base body to clear it)
  - Screw hole dia: **4.4 mm** (M4 clearance)
  - Hole spacing horizontal: **18 mm**
  - Hole spacing vertical: **25 mm**
  - Hole pattern: 4 holes, rectangle 18 (H) x 25 (V) — PENDING user confirm both pairs share 18mm H spacing.
- INTERFACE CORRECTION: block is a RECTANGULAR 4-HOLE bracket, NOT a 2-screw dovetail with a tapered pocket.
  - Supersedes all prior "dovetail pocket + 2 screws" + "width top/width bottom => angle" language in Base spec & script.
  - Base must capture a 29.5 (W) x 43.87 (H) x 40.55 (D) rectangular block and bolt via a 4-hole 18x25 M4 pattern. No dovetail taper.
  - Script Base component needs reworking accordingly (was built around dovetail placeholders).
- Revopoint scan of block now loaded in Fusion as RAW MESH — used ONLY as visual fit check, NOT referenced for geometry (avoids fragile mesh-face refs; keeps Base fully parametric off measured values).

## Open items still standing
- Confirm 4-hole pattern is a clean 18x25 rectangle (both H pairs = 18mm).
- Confirm front face the holes sit on is FLAT (not angled) — earlier photos looked angled; resolve before Base face is modelled.
- Prior unresolved geometry issues (user never specified) still open — ask before changing.
- Height-adjust holes still not cut into HeightElement (participantBodies/cut-target issue).


## Base interface RESOLVED (2026-06-07)
- Block side-profile confirmed via Image 3 + sketch review. Interface is a STEP, not an angle.
- Two MATING FACES on the rider/screen side, parallel, offset 8mm in DEPTH:
  - Lower face (near pair) — closer to rider.
  - Upper face (far pair) — stands 8mm proud in depth.
  - Both faces parallel; all 4 holes point the same direction. No canted face → arm will not sit cocked.
- Dovetails are on the LOWER part of the block body, frame side — embedded in the Zwift Ride frame. Base does NOT engage them.
- Base design: two flat bosses 8mm apart in depth, seating against the two faces; 4x M4 clearance (4.4mm) through-holes on the 18(H)x25(V) rectangle, split across the two faces (near pair on lower, far pair on upper).
- Block envelope 29.5(W) x 43.87(H) x 40.55(D) used only to size the Base body to clear/cradle the block.
- Revopoint mesh in Fusion = visual fit check only; geometry driven entirely off these measured values.

### Base spec is now COMPLETE — no further block input needed.
### Next session: rework Base component to stepped 4-hole interface (replaces old dovetail-pocket/2-screw Base), then re-address open items (height-adjust hole cut; user's unspecified geometry concerns).


## Donor STL reviewed — TabHolderTubeBase.stl (2026-06-07)
- User supplied an existing tablet-holder STL built around the SAME alu block, asking to reuse its interface and replace the tablet-holder part with our design. Clean approach chosen: mesh = spatial reference only, NOT edited. Our parametric Base (caliper-measured stepped 4-hole interface) is authoritative for the actual mount.
- Mesh facts (binary STL, 51k tris) for spatial matching:
  - Base plate footprint ~105mm (X) x ~104mm (Y); top surface Z~8.8mm, mounting underside Z~-9mm (~18mm base stack).
  - Cradle/backrest springs off the REAR edge of the base plate (~Y180) rising forward+up.
  - Donor backrest leans back ~41 deg from vertical = tablet propped near-upright, tilted back. This is a DIFFERENT intent from ours (near-vertical height element + adjustable toothed hinge tilting screen face UP toward higher-seated rider). DO NOT copy the 41 deg cradle.
  - Donor pocket geometry NOT copied (its interface region measures differently in-mesh; our caliper interface supersedes).
- NET: little new info needed from the STL — interface already = caliper numbers; arm/height/tilt/cradle = our settled 6-revision design. STL usefully CONFIRMS base-plate envelope (~105x104, ~18mm stack) and rear-edge cradle takeoff = sane footprint for our ~150mm forward arm + ~100mm rise.

### DECISION for next session
- Keep using our own parametric design (Base + horizontal arm + near-vertical height element + toothed up-tilt hinge + rider-facing cradle). Use STL only to sanity-check the base-plate footprint and takeoff point. Do not graft mesh.


## Interface CORRECTED from STL extraction (2026-06-07)
- Earlier "two parallel faces, 8mm depth step" interpretation was WRONG. Resolved by extracting the 4 hole centres directly from TabHolderTubeBase.stl.
- The 4 mounting holes lie on a SINGLE FLAT FACE raked back ~30 deg from the depth (Y) axis.
- Refined hole centres (mesh coords, mm):
  - A-left  (118.55, 101.22, 42.38)
  - A-right (136.71, 101.21, 42.39)
  - B-left  (118.67, 123.13, 54.78)
  - B-right (136.69, 123.44, 55.49)
- Pattern in the face plane: 18mm horizontal (X) x 25mm up the raked face (pair-to-pair = 25.48mm slant). Matches caliper 18 x 25.
- The "8mm above" = the Z (height) component of the 30deg rake; "different plane" = the upper pair further along the raked face. NOT a parallel depth step.
- Hole dia ~4-5mm in mesh (facet-inflated) -> use caliper 4.4mm (M4 clearance).
- CONCLUSION: STL carries the FULL alu-block interface. Build the parametric Base by referencing these 4 hole centres + the single 30deg-raked mating face, NOT the flat caliper axes. This captures the rake the calipers flattened.
- Lower four bores near Y193/Z~0 and the Y240 hole = base-plate/holder features, NOT the block interface — ignore for Base.

### Base build (next MCP session)
- Import/keep the mesh as reference; snap 4 construction points to the hole centres above; one construction plane on the 30deg raked face.
- Build Base body to that plane, 4x M4 (4.4) clearance holes on the 18x25 pattern, counterbored for heads as needed.
- Then hand off to horizontal arm per settled geometry.
- Supersedes the "stepped 2-boss / 8mm depth" Base sketch from earlier today.


## NEXT MCP SESSION — ordered execution steps (2026-06-07)
Pure execution against fixed spec below. Geometry/interface are SETTLED — do not re-litigate. Conserve round-trips: batch reads, verify by screenshot + bbox after each major body.

### 0. Setup
- Load Fusion MCP tools (deferred; re-search each turn: "fusion_mcp_read", "fusion_mcp_execute", "fusion_mcp_update"). Ranking may surface Chrome tools first — search specifically.
- Import TabHolderTubeBase.stl as mesh body for visual reference (do NOT edit it). Confirm orientation matches extracted coords (holes near X118-137, Y101-123, Z42-55).

### 1. Interface reference geometry (from STL extraction)
- Create 4 construction points at hole centres (mm):
  A-left (118.55,101.22,42.38) A-right (136.71,101.21,42.39)
  B-left (118.67,123.13,54.78) B-right (136.69,123.44,55.49)
- Create construction plane through the 4 points = the 30deg-raked mating face. (3-point plane; verify the 4th point lies ~on it, tol <0.5mm.)
- Sanity: in-plane pattern should read 18mm (X) x 25mm (up-slope).

### 2. Base body
- Build Base as a plate on/parallel to the raked plane, thickness ~6mm, sized to cover the 18x25 pattern + ~6mm margin.
- Cut 4x M4 clearance holes dia 4.4mm at the 4 points, axis normal to the raked face.
- Counterbore heads if needed (cbore ~8mm dia x ~4mm) — confirm screw head style first.
- Use participantBodies = [Base] on the cut to avoid the prior cut-target failure.
- VERIFY: screenshot + bbox; holes present; Base hugs mesh face.

### 3. Arm handoff
- From Base, build HORIZONTAL level arm ~150mm forward (per settled geometry). Confirm takeoff point/orientation against base-plate footprint (~105x104, top Z~8.8).

### 4. Remaining (carry from prior session)
- HeightElement: near-vertical, ~10deg forward tip; CUT the discrete height-adjust holes (prior failure: target the element body explicitly / participantBodies).
- TiltHinge: toothed, 15deg steps, tilts screen face UP toward higher rider.
- Cradle + TopRetainer: lip+sliding retainer on rider-facing side.

### 5. Geometry inspection (UNRESOLVED — do FIRST before changes)
- User flagged unspecified geometry issues at end of prior session; never specified. Ask user what looks wrong on a fresh side-view screenshot BEFORE editing. Do not assume.

### Reminders
- Don't save the document unless user asks; script is source of truth.
- Fragile API spots from v2: circularPatternFeatures (hinge teeth), SymmetricExtentDirection enum, moveFeatures/Matrix3D rotations — validate live, fix per Fusion version.


## BASE BUILT IN FUSION (2026-06-09) — supersedes the 30deg-rake entry
- CORRECTION of my own earlier error: the "single flat face raked 30deg" entry (2026-06-07) was WRONG. The 4 holes are NOT coplanar. Confirmed by user (Image 3 side profile) and by the 3-point plane fit leaving the 4th hole 0.45mm off — the tell I'd ignored. Interface = TWO PARALLEL FACES, 8mm step in depth (Y). near pair on front face, far pair 8mm back. Both faces' holes point same way. This matches the long-settled spec; the 30deg detour was a mistake.

### What got built this session (Base only)
- Mesh re-imported CLEANLY: TabHolderTubeBase.stl from C:\\Users\\micro\\OneDrive\\3DPrint\\Zwift Ride PC mount, via meshBodies.add(path, MeshUnits.MillimeterMeshUnit, baseFeature). Lands at correct 1:1 mm, bbox X74.9-180.4 Y88.9-284.6 Z-9-79.7 (size 105.5x195.7x88.7). The EARLIER mesh was scaled ~4.5x and metres off origin — deleted.
- Base = stepped 2-level block, one joined BRep body, built in the MESH's own coordinate frame (so it visually mates). 4x M4 (4.4mm) holes cut at true donor hole centres. Verified: 16 faces, 4 cylindrical bores, sits at the interface end of the mesh on screen.
- Base bbox mm: X109.5-145.7, Y89.2-135.3, Z33.4-64.5.

### HARD-WON BUILD CONVENTIONS (use these to avoid repeating today's thrashing)
- DOC IS SINGLE-COMPONENT (Part Design): cannot addNewComponent. Build all parts as BREP BODIES in root, not sub-components.
- Mesh import REQUIRES explicit MeshUnits arg: meshBodies.add(path, adsk.fusion.MeshUnits.MillimeterMeshUnit, baseFeature). Wrap in baseFeature.startEdit()/finishEdit() for parametric docs.
- New sketch auto-creates an ORIGIN sketchPoint at (0,0,0). When iterating sketchPoints as hole locations, FILTER OUT the origin or it becomes a phantom 5th hole.
- On an XZ-offset construction plane: sketchX -> +worldX, plane offset -> worldY, but sketchY -> NEGATIVE worldZ. Negate Z inputs. (Verified by probe point.)
- sketch.project() needs a sketch ENTITY, not a raw Point3D (throws InternalValidationError).
- ConstructionPlane has no isVisible setter; hide via root.isConstructionFolderLightBulbOn=False / isSketchFolderLightBulbOn=False.
- Screenshots can render sketch entities over the solid and can frame empty space — call activeViewport.fit() first; hide sketches before judging hole count; verify hole count via cylindrical-face count, not by eye.
- Build coords in the MESH frame (real STL hole centres ~X118-137,Y101-123,Z42-55), NOT a recentred origin — else Base floats away from the reference mesh.

### NEXT: arm + up the stack (unchanged settled geometry)
- From Base front face, HORIZONTAL level arm ~150mm forward, then near-vertical height element (~10deg forward tip, discrete adjust holes), toothed tilt hinge (15deg steps, face UP toward higher rider), rider-facing cradle (lip=100mm datum, sliding top retainer).
- Doc NOT saved (per standing pref). Geometry not yet signed off by user — still owe a fresh side-view inspection of the full stack once arm+ is built; ask what looks wrong before changing.
