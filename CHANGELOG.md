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

## 1.16.0 — 2026-09-22

Updates Online 0.7.0, Wilds 2.3.1, Double Battles 0.11.0 and Dramatic Ride 0.3.0; retains Battle Art 1.22.0. Adds optional synchronized mount visuals and fixes the room menu interrupting battle setup.

Restores Crystal Animated Sprites with Shiny Visuals 2.1.0 with FULL-BODY BATTLE BACKS enabled. Adds experimental Crystal online doubles with owned party members, target selection and paired turns. Running Shoes remains included.

Verified on Gen1Recomp 0.3.1 in isolated profiles. Known limits: Gen 1 online doubles remain unavailable; Crystal doubles and advanced move combinations remain experimental; the full mixed-mod/disconnect matrix and exhaustive scenery coverage are unfinished. Gen 3 free flight remains within the current map.

Import the attached .g1rcart after importing your own base game. No ROM or save is included. Existing published carts are unchanged; this is a new version.

## 1.15.0 — 2026-09-22

Bundles Battle Art, Online+, Wilds, Double Battles and Dramatic Ride plus Running Shoes. Requires Gen1Recomp 0.3.1 or newer. Includes original-art scenery, Oak lab and settings fixes, host-owned visible encounters and updated native multiplayer integration.

Gen 1/2 online doubles and the full multiplayer disconnect/mixed-mod matrix remain unfinished.

Install the attached .g1rcart. Your own legally obtained and imported base game is required; no ROM is included.

