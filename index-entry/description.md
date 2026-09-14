# Johto Diorama

Battle Art's 3D diorama of Johto, with the battles fought on it and a FLY
user to cross it — plus modern menus, PC storage, running shoes and the
party follower.

The overworld is extruded into real geometry with depth-buffered occlusion and
cast shadows — trees, roofs, ledges, fences and tall grass each built as what
they are, classified from Crystal's own collision bytes and BG palette slots.
Crystal's interiors get the same treatment: kitchen and lab furniture built as
whole drawings at table height, the starter balls sitting ON the ball table.
Johto's retaining lips are thin joined edges, the coast wears rock models, and
Strength/Rock Smash boulders are live actors that move and break with the
engine. Wild Pokémon walk around in it, a party follower walks behind you,
flocks of local flyers cross the sky, NPCs talk in speech bubbles, and a
battle is staged on the map's nearest clear ground — the diorama stays visible
in the panels' margins and through attack animations. Then a FLY user picks
you up and the camera rises with you.

For **Pokémon Crystal**. Thirteen mods, pinned by digest.

## What's on it

| mod | build | what it does here |
| --- | --- | --- |
| Gen1Online+ | 0.5.2 | online multiplayer: GTS trading, PVP battles and the Casino Lounge, server always asked for, sync scoped to the sealed cart |
| Kanto Gear | 3.2.9 | companion UI host for the single-screen window |
| Wilds of Kanto | 2.1.9 | wild Pokémon visible in the overworld, and the party follower |
| Battle Art Voxel Fork | 1.17.2 | the diorama, 3D-BTL staged on it, Johto's tiles classified, round scenery, furniture, rock models and default HD-2D scenery |
| Dramatic Sky Ride | 0.2.23 | land, water and air mounts with Suicune's traversal; a FLY user carries you over the map |
| Gen 2 Modern UI | 1.0.15 | modern menus for the start and PC screens |
| Gen 3 Boxes | 1.24.0 | Gen 3-style PC boxes and box back sprites |
| Modern Johto | 0.2.0 | optional texture modernisation, off by default |
| NPC Bubbles | 2.3.13 | speech bubbles over NPCs |
| Double Battles | 0.9.4 | wild doubles and trainer 2v2 on the engine's own battle sim, staged on the diorama |
| Running Shoes | 1.10.0 | hold to run |
| Wild Skies | 1.12.0 | flocks of local flying Pokémon, perching on rooftops |
| Crystal Animated Sprites with Shiny Visuals | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order the cart was verified
in. It matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and the one that loads last has the outermost say on
which art a battle draws.

`seal` is `sealed+`: the list is fixed, but you can switch any of the thirteen
off.

## Forks

Six of the twelve are compatibility forks. Each is a fix and nothing else;
all credit for the mods belongs upstream.

- **Battle Art Voxel Fork** is the Gen 2 port itself. Before 1.12.0 nothing on
  a Johto map was classified at all, so trees, buildings and fences were the
  same 16px box wearing their own facade art on the roof; 1.12.1 then made
  them build right — real building heights, doors in their facades, and
  characters standing on the ground rather than a block above it. 1.12.2 was
  the height pass: trees and bushes one cell instead of leaning into the
  path, interiors at class height, and each town wearing its own roofs.
  1.13.0 is the Crystal scenery pass: whole-drawing furniture at table
  height, round canopied trees, thin retaining lips, coastal and ocean rock
  models, and live Strength/Rock Smash boulders — plus battle surround and
  attack-animation visibility on Gen 2. 1.14.0 adds an HD-2D reading
  (SOURCE ART keeps the previous one): broadleaf crowns for Crystal's dense
  borders, the common interiors as whole drawings, wood-grain fences and
  shoreline rocks, and Modern Johto's retiled ledges.
- **Dramatic Sky Ride** is burgerslayer7's mount system forked for the
  Crystal rider draw crash: the crop file is verified through the engine's
  own asset reader, with the live player renderer as the fallback.
  Generation 1 untouched.
- **Gen 2 Modern UI** is Modern UI (FAFF0x/gen2recomp) re-published
  unmodified for an installable digest pin. No code changes.
- **NPC Bubbles** declared no `games` key, so a Crystal boot skipped it.
- **Crystal Animated Sprites** dropped the `panelFn` argument when wrapping
  Gold's `drawSceneBody`, discarding whatever a caller asked to be drawn.

Wilds of Kanto, Gen 3 Boxes, Modern Johto, Running Shoes and
Wild Skies are pinned upstream unchanged. Gen1Online+ is pinned from our
fork: the server address is always asked for, and sync is scoped to the
sealed cart so future quest mods never split the player base.

## No separate follower mod

Wilds of Kanto absorbed the two people usually reach for. Its own source:
*"Wilds unified follower system (standalone) … No Followers EX / PokéPC
runtime dependency."* It ships all 251 follower sprites, replaces Followers
EX's option rows and migrates its save keys.

## Verified and remaining reports

The 1.6.0 pin set contains Battle Art 1.15.0 and Sky Ride 0.2.20. Desktop
Crystal checks cover 16 maps/19 views, a horizontal healing bed and open bin
in Elm's lab, smaller item balls, distinct foliage and native animated water
textures reaching the rendered geometry. Both 1ST and 3RD support native,
camera-relative Crystal grid steps. Staged battle HUD backplates remain.

Online+ 0.5.2 still reports an unsupported Gen 2 map_scripts registration.
A user-reported fast ground/water Pokemon on cart 1.5.0 was not reproduced in
two instrumented current boots and remains open. Wilds presentation fallbacks
and remaining bespoke prop coverage are also recorded in the repository README.
Doubles/player-side partner work and Crystal mounts remain beta. Android
hardware has not been validated in this batch.

The cart contains pins and CG3 label art, not a ROM. Game data is imported
from the user's cartridge; Battle Art also supplies original procedural models
and generated foliage artwork.

## 1.7.0 — modern doubles, 1440p framing and gameplay fixes

Battle Art **1.15.3**, Double Battles **0.9.1**, Sky Ride **0.2.21**.

- Crystal attacks selected through the normal battle screen now deal damage.
- Both foes render independently; the survivor takes over correctly at 1v1.
- Compact modern status cards, command highlights and move type/PP rows use
  sharp fonts and a capped desktop scale, with HUD cards at the window edges.
- Native back sprites face the opponents; the wider staged camera shows more
  scenery at 16:9. Verified in a real 2560x1440 two-Sentret battle.
- The temporary scientist granting level-50 test mounts is no longer loaded.
  Existing party and PC Pokemon are not deleted.
- Refined tree crowns/branches, foliage filtering, turf fringes, roof courses
  and lab wood carry over from the scenery pass.

Crystal, sealed+, the CG3 label and the other ten mod pins are preserved.
Checks: 39 native doubles assertions, staged-pair placement/facing, HUD
font/DPI/bounds, 16-map scenery review, and real battle-screen damage and
survivor handling. Native special prompts remain in use. Explicit opponent
aim and player-side pair command collection remain future work. Full Gamma
Emerald art parity and the reported fast overworld Pokemon remain ongoing.

## 1.8.0 — closed roof sides and refined HD scenery

Battle Art **1.16.0** closes open roof sides and steps between adjacent roof
sections. Johto house walls now use clean plaster, warm timber and blue-gray
windows, with proper side/rear wall materials. Original larger leaf sprays,
varied crowns, sparse meadow blades and softer Crystal HD shadows refine the
outdoor scenery. Sharp 1440p doubles UI and native battle fixes carry forward.

Validated across sixteen Crystal maps, three oblique roof views and a native
1440p double battle. This remains an incremental pass toward Gamma Emerald;
complete scenery/prop parity and hardware verification remain open. Crystal,
sealed+, CG3 artwork and the other twelve mod pins are unchanged.


## 1.9.0 — HD-2D default, low shrubs and natural terrain

**HD-2D** is the fork and cart default; the voxel/source style selector has been removed. Battle Art 1.17.2 adds curved illustrated
maple/pine/spreading canopies, matching forest fill, low bushes, retained Cut
saplings, small flowers, shallow Park beds, expanded interior furniture/floors,
irregular short reef clusters, wet-sand shore slopes and rounded ledge mounds.
The mound crest is only 2.5 pixels high; the outward face keeps its dirt texture. Optional HD-2D lighting and
Depth of Field affect the world while keeping text sharp.

The overworld Poké Ball HUD is hidden. Double Battles 0.9.2 keeps status panels
out of attack-effect zooms; Battle Art retains the stage through KO/escape
messages. Sky Ride 0.2.22 restores the requested scientist at **New Bark Town
(9,10)**. Talking to him grants missing level-50 Ho-Oh/Fly, Suicune/Surf,
Raikou and Gyarados/Surf. He grants nothing on boot or map entry.

Crystal, sealed+, CG3 cover and all thirteen companions are retained.
This is an incremental scenery release; exact Gamma Emerald parity and the
reported fast bouncing Charmander remain open. Native tests use software GPU,
including 1440p battles, style/shader switching and a 388-map rendering sweep;
the sweep does not certify that every prop has a finished custom model.

## 1.11.0

Fixes the rapidly respawning town “glitchmon” in Online+0.5.5. Invalid encounter
rows fell back to Charmander artwork while an offline spawner rerolled its
population every frame. The cart now leaves offline wilds and the local follower
to Wilds; Online+ validates encounter data and retains stable standalone rosters.

Battle Art1.19.0 lays the Center healing bed flat, repairs sign backing, adds
capped roof courses and fuller tree sides, and encloses upper interior walls for
first-person/rotating third-person views. Reviewed 40 views at 2560×1440 across
five maps and four headings per camera mode. The test launcher now exercises
the normal mod update hooks, which exposed the glitchmon missed by older probes.

Crystal, sealed+, all thirteen companions, HD-2D defaults, hidden overworld
Poké Ball HUD and CG3 cover are retained. Exact Gamma Emerald parity, exhaustive
map polish and hardware performance remain ongoing.

## 1.12.0

Choose which opponent to attack in Crystal doubles; confirm with A or return
with B without spending PP. Overworld spawn encounters retain their supplied
Pokémon, even when wild doubles is set to ALWAYS. Only ordinary random step
encounters can automatically add a second wild foe.

First-person and rotating third-person views can turn during dialogue and
world cutscenes while movement remains locked. Mouse, controller-stick and
touch look use the native input paths.

Includes Battle Art1.19.1 and Double Battles0.9.3. Target input, encounter
ownership and camera dialogue/script behavior pass in the Linux AppImage.
A local host/guest simulation verifies three mirrored Online+ singles rounds
with automatic doubles kept out of multiplayer construction. Multiplayer
doubles and player-side pair command collection are unfinished; no Internet
multiplayer playtest is claimed. Crystal, sealed+, CG3, HD-2D defaults and
all thirteen companions remain.
