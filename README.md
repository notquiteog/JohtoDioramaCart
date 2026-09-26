## 1.21.4 — 2026-09-26

Pins Battle Art 1.28.4.

FireRed/LeafGreen builds moving scenery windows cooperatively while continuing to draw the last complete window. Reversals, warps and invalidation cancel unfinished work and release its GPU resources. Model generation and shared uploads gain budget checkpoints; Crystal/FRLG reuse tree source pixels and Gen3 furniture matching skips unrelated recipes.

Raised first-person framing in all three generations: native GB height 12 world pixels, FRLG 13.5, retaining sprite foot anchors and authored provider overrides.

In one isolated 2560×1440 LeafGreen forest benchmark on Gen1Recomp 0.3.20 / RTX 5060 Ti, maximum traversal frame time fell from 53.28 ms to 10.57 ms. Mean was similar (4.56 → 4.61 ms); p95 increased (5.20 → 7.03 ms) as work was spread across frames. Both replacement windows completed. This is a targeted hitch reduction, not an all-game FPS claim. Cold map loads and individual GPU calls remain synchronous.

Native Yellow, Crystal, FireRed and LeafGreen checks covered forest/lab rendering, first-person height, and house exits. Focused scheduler, resource, geometry and furniture regressions pass. Full all-map quality and companion feature parity remain unfinished. Evidence: docs/STREAMING_QA_2026-09-26.md.

All other mod pins and cart options are unchanged.

## 1.21.3 — 2026-09-26

Pins Battle Art 1.28.3.

Fixes FireRed/LeafGreen losing the selected 3D camera when leaving the player’s house with FAR/FULL render distance: connected tilesets with no ground triangles are valid empty batches. Genuine upload failures retain actionable diagnostics and bounded recovery.

Rebuilds complete FireRed/LeafGreen house staircases with separate treads, risers, stringers, handrails and recessed descending flights. Restores the bedroom dresser with two drawers and handles. Mom sits at the dining chair’s cushion, with the chair backs facing away from the table; scripted movement remains native.

Crystal house stairs retain their native four-step footprint. Stair warps are protected from door folding; north wall framing and wallpaper recess behind the flights, and shared Gen 1/2 room foundations leave descending stairwells open.

First-person eyes now follow native sprite eye rows and visible-foot anchors across all three generations. FireRed/LeafGreen first person also disables world curvature and uses the shared close-wall focus distance. Mesh revision 76 refreshes stored geometry.

Checked on Gen1Recomp 0.3.20 with isolated native fixtures and focused regressions. See docs/HOUSE_CAMERA_QA_2026-09-26.md for evidence and limits. Full all-map scenery and cross-generation feature parity remain unfinished.

All other mod pins and cart options are unchanged.

## 1.21.2 — 2026-09-26

Pins Battle Art 1.28.2. Native tree models now preserve distinct source-art families and correct footprints. Crystal and FireRed/LeafGreen share GPU tree models instead of copying every placement. All generations reuse unchanged scalar draw state and avoid repeated shadow-camera setup; Shadows OFF skips the shadow pass. Gen 1 keeps its authored models and existing map/chunk cache.

In a short 2560×1440 LeafGreen Viridian Forest traversal on RTX 5060 Ti, the largest scenery-rebuild frame dropped from about 1,300 ms to 64 ms. Steady frame time was similar; residual rebuilding remains synchronous. This is a measured scene-specific hitch improvement, not a general FPS multiplier.

Native GPU comparisons matched instanced/merged geometry and shadow pixels at four angles. Native smoke/scenery checks cover Yellow, Crystal, FireRed and LeafGreen. Full all-map scenery and cross-generation gameplay/settings parity remain unfinished.

All other mod pins and cart options are unchanged.

## 1.21.1 — 2026-09-26

Pins Battle Art 1.28.1, Online 0.8.1 and Double Battles 0.12.1. Adds Crystal house/traditional-house furniture and wall/floor fixes, FireRed/LeafGreen office and ship furniture, and reworked potted plants with solid curved leaves. The 3D/2.5D scenery option remains available. Removes the optional asset startup dialogue and strengthens Gen1 online-doubles state checks.

Verified representative native scenes and twelve-turn local ENet doubles on Gen1Recomp 0.3.20. Complete all-map visual coverage and full cross-generation feature/network parity remain unfinished. Existing Wilds, Ride, Skies and running-shoes pins are unchanged.

## 1.21.0 — 2026-09-26

Replaces flat-looking source-column tree/rock extrusion with intersecting 3D canopy/stone masses using each game's native palette. Tree cards remain optional. Shelves now have individually projecting contents, while terminal/rack recipes get separate CRTs, keyboards and equipment modules. Six FireRed/LeafGreen Pokémon Tower grave drawings gain closed plinths and upright headstones, scoped to their original tileset.

Pins Battle Art 1.28.0: Crystal sculpture/bicycle models and timber siding; 31 additional FireRed/LeafGreen framed cabinet recipes; native forest/cave/tower atmosphere controls and optional scenery grain. Also pins Wilds 2.4.2 and Ride 0.4.1: selected-ball quick taps work with the HUD hidden, and Ride yields a rebound catch key. Other companion pins remain unchanged.

Tested on Gen1Recomp 0.3.20 with representative rendered scenes and actual native settings menus. Full all-map scenery, settings and Gen3 world-space battle-camera parity remain unfinished; see Battle Art's native scenery QA report.

Trees, rocks and bushes default to 3D models; native tree cards and rock/bush sprites remain selectable. People, Pokemon, grass and flowers stay sprites. Narrow border rows use separate trees, and broad 2x2 drawings use one tree. Optional CLEAR/AUTO/RAIN/SNOW/FOG/STORM weather is included.

## 1.20.2 — 2026-09-26

Pins Battle Art1.27.2: 36 shared Crystal furniture recipes use component models, and six native rock drawings use closed voxel volumes (2,048 placements). Includes lower grass, starting-area furniture, native voxel trees, HUD ownership and camera-recovery fixes. Companion versions remain unchanged.

All388 Crystal maps inventoried; ten representative shared-scenery maps inspected in overview and first person on Gen1Recomp0.3.20. Full scenery/settings and Gen3 battle-camera parity remain unfinished.

## 1.20.1 — 2026-09-26

Pins Battle Art 1.27.1: lower sprite grass with complete native ground coverage; corrected bedroom console ownership; modeled neighboring-house appliances, plants and framed picture; Crystal CRT, radio, shelves and legged tables. Includes the 1.27.0 HUD, camera recovery, voxel-tree and house-side fixes. Companion versions remain unchanged.

Reviewed starting-town interiors/exteriors in Crystal, FireRed and LeafGreen on official Gen1Recomp 0.3.20, plus a Yellow smoke check. Full scenery/settings and Gen3 battle-camera parity remain ongoing; see Battle Art’s starting-area QA notes.

## 1.20.0 — 2026-09-26

Pins Battle Art 1.27.0: Crystal single-battle HUD ownership fix, bounded FireRed/LeafGreen scene recovery, source-art voxel trees with selectable card/detail alternatives, closed cave boulders and clean house-side texture samples. Gen3 uses the shared 3D-BTL control. Crystal and FireRed cart defaults select ORIGINAL MODEL trees with BALANCED detail; Yellow keeps its existing Gen1 models. Companion versions remain unchanged.

Checked on official Gen1Recomp 0.3.20. The original Pallet exception was not reproduced; controlled scene-error recovery and ordinary map transitions pass. Full scenery/settings and Gen3 battle-camera parity remain unfinished. See Battle Art's 1.27.0 QA notes for scope and limitations.

## 1.17.0 — 2026-09-22

Coordinated release pinning all six active mods: Battle Art 1.23.0, Online 0.8.0, Wilds 2.4.0, Ride 0.4.0, Double Battles 0.12.0 and Wild Skies 1.13.0. Yellow and Crystal also retain Running Shoes.

Includes the verified sprite grounding and animated enemy battle fixes, four visible native double battlers, and the latest scenery corrections. Runtime and assets match the tested builds except version metadata. Official Gen1Recomp 0.3.1 validation and known limitations are retained; full scenery/settings and multiplayer edge-case parity remain unfinished.

## 1.17.0-test.11

Post-publication checks passed on official Gen1Recomp 0.3.1: all three carts load exact mod pins and defaults; FireRed/LeafGreen single and double battles show animated enemies and four visible double battlers; native trainer doubles remain visible. The museum correction was inspected from both previous viewpoints. Earlier actor/lab/rock checks remain valid. These are test releases; full scenery, settings and multiplayer edge-case parity is unfinished.

Includes the FireRed/LeafGreen sprite-grounding and shadow-contact corrections, plus real animated BW front sprites for all 386 normal and shiny species. This follow-up corrects native wild-double introductions leaving the second pair hidden, and a museum counter corner incorrectly raised into a wall.

Six independent core mods: Battle Art, Online, Wilds, Ride, Double Battles and Wild Skies. Yellow and Crystal also include Running Shoes. Host-owned ground and sky encounters, riding, multiplayer battles, chat and trading remain included.

Exact test.10 packages passed three-cart boot/settings/room-transition checks, FireRed/LeafGreen enemy animation in single battles, and inspected actor, lab, gym and cave captures on official Gen1Recomp 0.3.1. Earlier exact packages passed two-endpoint riding, trading, doubles and shared aerial encounters. This follow-up is published before its final native checks as requested. Full tile, option and multiplayer edge-case parity remains unfinished. Gen3 public music registration remains blocked by the current engine; Ride's local music catalog is available.

## 1.17.0-test.10

Fixes the FireRed floating-actor presentation with stable sprite foot anchors and matching character-shadow contact. Includes 772 real animated Gen5 front atlases for all 386 species (normal/shiny), preserving selected custom art precedence and Crystal defaults. Corrects lab ball padding and disconnected floor marks accidentally included in boulder models.

Also fixes shared aerial Ride claim completion and caught sky-flockmate restoration. Six independent core mods integrate when present; Yellow and Crystal also include Running Shoes. Gen3 public music remains gated by official 0.3.1; custom local Ride music catalogs remain available.

Previous exact archives passed three cart boots/settings, native Wilds capture/followers, two-endpoint FireRed/Crystal doubles, FireRed trade and FireRed/LeafGreen riding. Published Ride.test3 plus Skies.test2 also passed shared aerial guest battle and host consumption. All eight lab approach views show the original table-through-character clipping resolved. Full inventories cover 388 Crystal and 425 FireRed maps; this is not visual certification of every tile. New grounding/front-animation patches receive final exact archive gameplay checks after publication, as requested. Full option and visual parity remain unfinished.

## 1.17.0-test.9

Adds Wild Skies, including its native FireRed/LeafGreen port, to the shared mod set. Six independent core mods support optional integrations: Battle Art, Online, Wilds, Ride, Double Battles and Wild Skies. Yellow/Crystal also include Running Shoes. Both ground and sky encounter ownership belongs to the online host when supported by both peers.

This batch adds native generation options/consumers, native wild doubles/catching/trainer pairs, shared ball throwing, ride controls and matching mount visuals, selected battle/interface art, new Crystal/FireRed interior recipes and cave surfaces. Fixes Oak's starter table extending into the walkable player/rival approach row.

TEST PRERELEASE: published before native gameplay and screenshot verification at the user's request. Compile and focused contract checks passed; exact packaged gameplay checks follow. Complete visual coverage of every tile and complete option parity remain unfinished. Battle Art includes a generation-specific support inventory that distinguishes implemented, partial and unavailable controls. Shared-sky coverage outside provider-supported host fields and exhaustive battle/disconnect combinations need further work. This release does not claim universal parity or visual perfection.

## 1.17.0-test.8

Four Gen 1 double-battle cards follow the actual composed sprite heads, and the camera widens to keep both near-side Pokemon in view. FireRed/LeafGreen modern commands preserve full-body sprite pixels beneath the old command window; status anchors use the selected artwork. Fixes the packaged animated BW back atlas path (dex 1–251). Includes the shared modern UI toggle and functional Gen 3 shadow/world-curve/wireframe controls from test.7.

Verified using isolated scripted profiles on latest official Gen1Recomp 0.3.1: four-card Yellow online doubles, normal battle completion with matching state hashes and intact owned parties; Crystal integrated sprite/settings checks; FireRed 1440p UI toggle, native directional input, animated back frame changes, damage, attack-stage lifetime and field return. Inspected native rendered captures, including complete FireRed back sprites and all four Yellow battlers. Final archive checks follow publication.

These remain test releases. Full cross-generation feature parity, complete animation coverage, Gen 3 shiny-context handling and exhaustive multiplayer move/disconnect scenarios are unfinished. User saves and live profiles were not touched.

Pins Double Battles 0.12.0-test.3, including the Gen 1 online faint/bench replacement synchronization fix. Five core mods in FireRed/LeafGreen; Yellow and Crystal also include Running Shoes.

## 1.17.0-test.7

Gen 1 staged battles now have separate projected status cards for all four double battlers and compact commands drawn after attack effects. MODERN BATTLE UI is a live shared setting across all three generations; OFF retains native UI. Gen 3 exposes the existing shadow, world-curve and wireframe controls. The selected-art renderer can reuse the bundled animated BW back atlases for dex 1–251; missing species retain static fallback. Custom installed atlases remain first priority. Crystal remains the default Gen 1/2 sprite pack.

TEST PRERELEASE: published before gameplay testing as requested. Full cross-generation parity, Gen 3 shiny-context handling, animated front coverage and advanced multiplayer scenarios remain unfinished.

Includes Double Battles’ Gen 2 UI opt-out fix. Five core mods in FireRed/LeafGreen; Yellow and Crystal also include Running Shoes.

## 1.17.0-test.6

TEST PRERELEASE. Battle Art now includes the complete Crystal sprite pack and its normal/shiny animations, reveal effects, trainer portraits, menu/evolution presentation and optional Gen 5 full-body staged backs. Crystal is the default style for Gen 1/2; Gen 3 retains its selected BW battle art. The separate Crystal sprite dependency is removed from every cart. Yellow and Crystal now contain the five core mods plus Running Shoes; FireRed/LeafGreen contains the five core mods.

Sprite pack selection requires restarting the game. Includes test.3 camera/sprite regression corrections. Source/asset checks precede publication; new gameplay/visual checks follow publication as requested. Full cross-generation feature parity and adapter-pending settings remain unfinished.

## 1.17.0-test.5

TEST PRERELEASE. Battle Art now includes the complete Crystal sprite pack and its normal/shiny animations, reveal effects, trainer portraits, menu/evolution presentation and optional Gen 5 full-body staged backs. Crystal is the default style for Gen 1/2; Gen 3 retains its selected BW battle art. The separate Crystal sprite dependency is removed from every cart. Yellow and Crystal now contain the five core mods plus Running Shoes; FireRed/LeafGreen contains the five core mods.

Sprite pack selection requires restarting the game. Includes test.3 camera/sprite regression corrections. Source/asset checks precede publication; new gameplay/visual checks follow publication as requested. Full cross-generation feature parity and adapter-pending settings remain unfinished.

## 1.17.0-test.4

TEST PRERELEASE. Battle Art now includes the complete Crystal sprite pack and its normal/shiny animations, reveal effects, trainer portraits, menu/evolution presentation and optional Gen 5 full-body staged backs. Crystal is the default style for Gen 1/2; Gen 3 retains its selected BW battle art. The separate Crystal sprite dependency is removed from every cart. Yellow and Crystal now contain the five core mods plus Running Shoes; FireRed/LeafGreen contains the five core mods.

Sprite pack selection requires restarting the game. Includes test.3 camera/sprite regression corrections. Source/asset checks precede publication; new gameplay/visual checks follow publication as requested. Full cross-generation feature parity and adapter-pending settings remain unfinished.

## 1.17.0-test.3

**TEST PRERELEASE — published before gameplay testing at the user’s request.** Fixes the stale indoor camera after leaving buildings and the duplicate Gen 1 battle sprite wrapper. Includes Gen 1 online doubles, HGSS overworld art (Gen 3 default; opt-in for Gen 1/2), and Battle Art right-stick/door/healing fixes.

Battle Art itself now handles front/back sprite selection across all three generations. Existing animated atlases take priority; supplied BW art is a static full-body fallback. No separate BW mod is included. Gen 1 retains ROM art by default; Crystal retains its Gen 2 animated companion and full-body backs; FireRed selects Gen 5 battle art. Change the shared Battle Art options to opt in/out.

Unsupported generation-specific settings remain visible but read-only (ADAPTER PENDING). Gen 1 doubles, new projection adapters and advanced mechanics are experimental and await gameplay verification. Gen1Recomp 0.3.1 target; no ROMs or saves.

## 1.17.0-test.2

**TEST PRERELEASE — published before gameplay testing at the user’s request.** Includes Gen 1 online doubles, HGSS overworld art (Gen 3 default; opt-in for Gen 1/2), and Battle Art right-stick/door/healing fixes.

Battle Art itself now handles front/back sprite selection across all three generations. Existing animated atlases take priority; supplied BW art is a static full-body fallback. No separate BW mod is included. Gen 1 retains ROM art by default; Crystal retains its Gen 2 animated companion and full-body backs; FireRed selects Gen 5 battle art. Change the shared Battle Art options to opt in/out.

Unsupported generation-specific settings remain visible but read-only (ADAPTER PENDING). Gen 1 doubles, new projection adapters and advanced mechanics are experimental and await gameplay verification. Gen1Recomp 0.3.1 target; no ROMs or saves.

## 1.17.0-test.1 — 2026-09-22

**TEST PRERELEASE — published before gameplay testing at the user’s request.** Build/compile validation only at publication. Includes Gen 1 online doubles, supplied HGSS overworld art (Gen 3 default; opt-in for Gen 1/2), expanded Battle Art settings visibility, and Gen 3 right-stick/door/healing presentation changes. Options lacking a generation adapter are explicitly marked unavailable.

Crystal Animated Sprites 2.1.0 and FULL-BODY BATTLE BACKS remain enabled; those are Gen 2 sprites.

Known risks: new Gen 1 doubles and door/healing projections have not yet been gameplay-tested; advanced moves and disconnect combinations may need fixes. Complete visual parity and all generation-specific settings adapters remain unfinished. Gen1Recomp 0.3.1 is the target engine. No ROM or player save is included. Stable releases remain available.

# Johto Diorama 1.16.0

Updates Online 0.7.0, Wilds 2.3.1, Double Battles 0.11.0 and Dramatic Ride 0.3.0; retains Battle Art 1.22.0. Adds optional synchronized mount visuals and fixes the room menu interrupting battle setup.

Restores Crystal Animated Sprites with Shiny Visuals 2.1.0 with FULL-BODY BATTLE BACKS enabled. Adds experimental Crystal online doubles with owned party members, target selection and paired turns. Running Shoes remains included.

Verified on Gen1Recomp 0.3.1 in isolated profiles. Known limits: Gen 1 online doubles remain unavailable; Crystal doubles and advanced move combinations remain experimental; the full mixed-mod/disconnect matrix and exhaustive scenery coverage are unfinished. Gen 3 free flight remains within the current map.

Import the attached .g1rcart after importing your own base game. No ROM or save is included. Existing published carts are unchanged; this is a new version.

## Included versions

- gen1online-plus 0.7.0
- overworld_wild_spawns 2.3.1
- BATTLE_ART_VOXEL_FORK 1.22.0
- DRAMATIC_SKY_RIDE 0.3.0
- double_battles 0.11.0
- running_shoes 1.10.0
- crystal_animated_sprites_with_shiny_visuals 2.1.0

Exact release ZIP hashes and cart defaults are pinned in cart.json.
