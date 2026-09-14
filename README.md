# Johto Diorama

A version-pinned Gen1Recomp cart for **Pokémon Crystal**, with layered
**HD-2D DEPTH** scenery by default, battles staged in the world, mounts,
modern menus, PC storage, running shoes and a party follower.

## Install

Download the `johto_diorama-<version>.g1rcart` asset from the
[latest release](https://github.com/notquiteog/JohtoDioramaCart/releases/latest)
and drop it into your save directory's `carts/` folder (or import it from the
launcher's Custom Carts panel). The first boot of the cart resolves and
installs the thirteen pinned mods itself; each is fetched at the exact build
pinned in `cart.json` and verified against its published sha256.

This bundle ships no code. It is a pin list — every mod on it is published
separately and fetched at its exact build.

## What's on it

| mod | build | what it does here |
| --- | --- | --- |
| [Gen1Online+](https://github.com/notquiteog/gen1online-plus) | 0.5.5 | Crystal trading/PVP integration; Casino Lounge map scripts remain Gen 1-only |
| [Kanto Gear](https://github.com/AverageConsumer/kanto-gear) | 3.2.9 | companion UI host for the single-screen window |
| [Wilds of Kanto](https://github.com/YoDrehDenSwagAuf/overworld-spawn-mod) | 2.1.9 | wild Pokémon visible in the overworld, **and the party follower** |
| [Battle Art Voxel Fork](https://github.com/notquiteog/DramaticShapeVoxelMod) | 1.19.1 | the diorama, 3D-BTL staged on it, Johto's tiles classified, round scenery, furniture, ledges and rock models, HD-2D scenery by default |
| [Dramatic Sky Ride](https://github.com/notquiteog/dramatic-sky-ride) | 0.2.22 | land, water and air mounts with Suicune's traversal; a FLY user carries you over the map |
| [Gen 2 Modern UI](https://github.com/notquiteog/gen2recomp) | 1.0.15 | modern menus for the start and PC screens |
| [Gen 3 Boxes](https://github.com/MadeinTaly/gen1recomp-gen3-boxes) | 1.24.0 | Gen 3-style PC boxes and box back sprites |
| [Modern Johto](https://github.com/MadeinTaly/gen1recomp-modern-johto) | 0.2.0 | optional texture modernisation, off by default |
| [NPC Bubbles](https://github.com/notquiteog/gen1recomp-npc-bubbles) | 2.3.13 | speech bubbles over NPCs |
| [Double Battles](https://github.com/notquiteog/double-battles-gen2) | 0.9.3 | Crystal wild/trainer doubles with opponent selection; paired ally commands and multiplayer doubles remain unfinished |
| [Running Shoes](https://github.com/MadeinTaly/gen1recomp-running-shoes) | 1.10.0 | hold to run |
| [Wild Skies](https://github.com/notquiteog/wild_skies) | 1.12.2 | flocks of local flying Pokémon crossing the sky, perching on rooftops |
| [Crystal Animated Sprites with Shiny Visuals](https://github.com/notquiteog/crystal_animated_sprites_with_shiny_visuals) | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order this cart was verified
in. It matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and the one that loads last has the outermost say on
which art a battle draws.

`seal` is `sealed+`: the list is fixed, but you can switch any of the thirteen
off. Modern Johto ships with its balance switches at the author's off
defaults, and Double Battles' WILD DOUBLES ships at SOMETIMES.

## Why these mods are forks

These forks carry Crystal compatibility and presentation work; the original
mods and their authors are credited upstream.

- **Battle Art Voxel Fork** is the Gen 2 port itself. 1.12.0 added the tile
  classifier: before it, nothing on a Johto map was classified at all —
  `TileShape` keys its authored groups on tileset id and every id in its
  8,284-line profile is a Gen 1 one, so trees, buildings, fences and ledges
  were all the same 16px box wearing their own facade art on the roof.
  1.12.1 then made them *build* right: buildings take their height from
  their drawing instead of a 16px slab, doors sit in their own facades, and
  characters stand on the ground — `groundAt` had been answering 16px for
  every cell of every map, so everyone in Johto floated a block in the air.
  1.12.2 was the height pass: trees and bushes are one cell again instead of
  leaning two into the path, interiors keep the class height, and each town
  wears its own roofs. 1.13.0 is the Crystal scenery pass: Mom's kitchen and
  Elm's lab furniture modelled as whole drawings at furniture height with the
  starter balls ON the table, two-cell border trees carved into round
  canopies, three-pixel retaining lips with joined corners, coastal and
  ocean rock models, and live Strength/Rock Smash boulders that move and
  break with the engine instead of leaving static copies. It also keeps the
  diorama visible around the Gen 2 battle panels and through attack
  animations, and carries the applicable DRAMALESS_SHAPE mouse-release and
  menu-click fixes. 1.14.0 adds the HD-2D reading behind a CRYSTAL SCENERY
  options row: compact broadleaf crowns for Crystal's dense borders,
  whole-drawing furniture for the common house, Mart, Center and bedroom
  tilesets, wood-grain fences with beveled caps, and shoreline rocks — with
  SOURCE ART keeping the previous reading. It also supports Modern Johto's
  retiled ledges.
- **Dramatic Sky Ride** is burgerslayer7's mount system — land, water and
  air, Suicune's amphibious traversal — forked for one fix: the Crystal
  rider crashed the draw because the mod's crop file landed where the
  engine's sprite renderer cannot read it (mod filesystem writes are
  sandbox-rerouted on this host). The fork verifies the crop through the
  engine's own asset reader and falls back to the live player renderer
  when it cannot be opened. Generation 1 is untouched, and the declared
  Free Fly conflict is now free to be honest — Free Fly left the cart in
  the same release.
- **Gen 2 Modern UI** is Modern UI (FAFF0x/gen2recomp) re-published
  unmodified at notquiteog/gen2recomp: the upstream archive had no
  installable release build for a digest pin, so the fork publishes the
  byte-identical archive as v1.0.15. No code changes.
- **NPC Bubbles** declared no `games` key, which means Gen 1 only, so a
  Crystal boot skipped it outright.
- **Crystal Animated Sprites** wrapped Gold's `drawSceneBody` without its
  `panelFn` argument and forwarded none, silently discarding whatever the
  caller asked to be drawn.

- **Double Battles** is the Crystal 2v2 fork: the stock mod's Gen 1 half
  unchanged, plus a Gen 2 layer that runs real two-a-side rounds on the
  engine's own battle sim (`useMove`, priority, speed, experience), stages
  both foes on the diorama through Battle Art's staged textures, and draws
  the second foe's HP plate on the engine screen. Wild doubles roll the
  second foe from the map's own table; roamers stay strictly 1v1. WILD
  DOUBLES defaults to SOMETIMES and TRAINER 2V2 to on.
- **Gen1Online+** re-publishes Gen1Online+ (gamecorner-033/Gen1Online
  v0.5.0) at notquiteog/gen1online-plus with three online fixes: the server
  address is always asked for on connect (nothing connects silently to the
  shipped default), every sync stamps the sealed cart's own fingerprint so
  future quest mods change the online room automatically instead of
  desyncing players, and a self-hostable cart-aware server ships in the
  fork's `tools/`. No gameplay edits; the official server's version
  handshake still accepts it.

**Kanto Gear, Wilds of Kanto, Gen 3 Boxes, Modern Johto, Running Shoes and
Wild Skies are pinned upstream unchanged** — all six already declare Gen 2
and load clean.

## Followers are already here

There is no separate follower mod on this cart, and that is deliberate.
Wilds of Kanto absorbed the two that people usually reach for. From its own
source: *"Wilds unified follower system (standalone). Owns: selection,
persistence, control modes, trailers, talk, sprite refresh. **No Followers
EX / PokéPC runtime dependency.** Concepts adapted from PokéPC Followers
(gamecorner-033) and Followers EX (masterwebx). Assets: Wilds HGSS/PokeMMO
runtime sheets (no external sprite pack required)."*

It ships all 251 follower sprites, its settings page explicitly replaces
Followers EX's rows and migrates its save keys, and it is live on Crystal —
the `DISMISS` row in the party submenu is it.

Adding either upstream mod would be strictly worse. **PokéPC Followers**
cannot be installed at all: it has no releases, it hard-returns on anything
but Red/Blue/Yellow, and the `assets/sprites/` directory it reads went with
a deleted `mod.zip`. **Followers EX** hard-depends on it and raises
`"cannot find PokePC follower sprites"` without it.

## Not on it

Three mods were considered and left off. Each for a measured reason.

### Gen2-3D-Sprites / Stadium 2 Overworld Models

It cannot coexist with a voxel renderer, in **either** position of its own
switch, and that is by design rather than by accident:

- `3D VOXEL WORLD = ON` — it renders its own 3D world through
  `render.compose`, which runs after the world pipeline. On this cart it
  burned 24 frames of 3D per 42 attempted and the screen still showed
  Battle Art's diorama.
- `3D VOXEL WORLD = OFF` — it forces flat 2D and the diorama disappears
  outright. Its own source says why: *"Gen1Recomp permits one active
  drawWorld pipeline, and optional companion mods may still have theirs
  enabled even when THIS mod's 3D VOXEL WORLD switch is OFF. World:draw()
  would otherwise invoke that external pipeline and the user would still see
  3D."* It zeroes every other world pipeline for the duration of the frame.

It is also not a sprite pack. It is a total conversion that wants to own the
renderer, the camera, live battles, wild spawns, followers, the pause menu,
the Pokédex and the weather — its embedded copy of Wilds of Kanto already
fails on this cart with `screens already registered: OverworldSpawnPreview`,
because the real Wilds got there first. And its 3D models come from a
Pokémon Stadium 2 ROM the player supplies; with no ROM there are no models
either way.

It is an excellent mod and the right centre of a *different* cart — one
where Battle Art and Wilds come off and it owns everything.

### Double Battles

`shanehudson-gen1recomp-mods/double_battles` 0.6.1 declares no Gen 2 game,
and forcing it on with the engine's own TRY HERE ANYWAY toggle shows why
that is honest rather than an oversight: it loads with **zero errors** and
then does nothing. A real wild battle came back `battle.__double = nil`.

Its interception seam is `OverworldController.pushBattle`, which Gold does
not have — `World:startBattle` constructs and pushes in one call — and its
machinery wraps about fifteen Gen 1 `BattleState` instance methods
(`syncSides`, `resolveSwitch`, the draw path) over a `player`/`player2`/
`enemy`/`enemy2` model. Gold's battle engine is a separate implementation
with its own turn loop. Porting it is a battle-mechanics rewrite, not a
compatibility fix, and shipping the one-line `games` edit would give you a
cart that lists double battles and does not have them.

The only working Gen 2 doubles in this ecosystem today are inside Stadium 2
Overworld Models, which is the mod above.

### Crystal 251

A Gen 1 overhaul: it imports a Crystal ROM as a *data source* to bring 251
Pokémon, Gen 2 battles and breeding to Red/Blue/Yellow. On Crystal every one
of those is already native. Forced there it fails outright at
`battle/crystal_presentation.lua:124`, asserting a `BLIZZARD` battle-anim
that does not exist in Gold's differently-keyed registry.

### And the flying mod that left

[Free Fly](https://github.com/notquiteog/free_fly) held the mount slot
through 1.4.0 and flew on evidence: it offered `FREEFLY` through the
party-submenu row while Dramatic Sky Ride raised a missing rider sheet on
Crystal (`rider_SPRITE_CHRIS`). That crash is now fixed in the
[Dramatic Sky Ride fork](https://github.com/notquiteog/dramatic-sky-ride)
— the crop file is verified through the engine's own asset reader, with
the live player renderer as the fallback — and DSR brings the bigger
system: land, water and air mounts, Suicune's amphibious traversal, badge
progression. Free Fly left the cart in the same release its rival's crash
was fixed, which is the fairest rematch either of them will get. Its
declared conflict with Free Fly stays: run both and both want the mount.

## Verified in the 1.6.0 companion set

Desktop Crystal testing on gen1recomp 0.2.59 with software OpenGL:

- All thirteen companions load. Online+ 0.5.2 still reports an unsupported
  Gen 2 map_scripts registration; online/casino features are not claimed tested.
- Battle Art's 16-map scenery check passes, including its 19 captured views:
  distinct tree families, shallow ledges, natural rocks, low furniture, Elm's
  horizontal healing bed/open bin, and four-pixel starter balls.
- Native imported water frames reach the actual drawn water geometry; imported
  flower/other animation programs are supported without substituting Gen 1 art.
- Both 1ST and 3RD use camera-relative native Crystal grid steps. Sky Ride
  0.2.20 preserves the camera owner's input predicate during those steps.
- Existing staged battle HUD backplates remain included. Optional depth-based
  focus is available through DEPTH OF FIELD; OFF remains its default.

## Known gaps

- Crystal doubles still commands one player-side active Pokémon. Selecting
  both allies' commands, full doubles mechanical parity and multiplayer doubles
  remain unfinished. Online+/native link stay singles; only a local mirrored
  session simulation has been checked, not Internet multiplayer.
- **Resolved in 1.11.0:** the darting town Pokémon came from Online+'s second
  offline spawner, malformed rare slots and per-frame roster rerolls. Native
  tests with the real update hooks now pass in New Bark, Cherrygrove and Violet;
  the normal ambient Pokémon and one party follower remain.
- Wilds still logs occasional sprite presentation fallbacks. Neither this release
  nor the map audit claims that every prop across all 35 tilesets has bespoke art.
- These checks are desktop tests, not Android hardware validation.

Historical beta notes (superseded by the later release entries below):

- **Double Battles on Crystal** is you against two, for now: the player-side
  partner, the aim menu and the shared 2v2 HUD are the fork's next chunk.
  The sim, both foes, their plates and the collapse to 1v1 are all live.
- **Dramatic Sky Ride on Crystal** carries the fork's rider-crash fix, but
  the mount system itself remains what upstream ships: an author-declared
  Gen 2 beta. Ground Ride and the FLY progression are the exercised paths.

## Licensing

Wilds of Kanto, NPC Bubbles, Crystal Animated Sprites and Modern UI declare
no licence upstream, so no redistribution terms are granted anywhere in that
chain; each fork or re-publish states its provenance and claims nothing.
Kanto Gear, Wild Skies, Gen 3 Boxes, Modern Johto and Running Shoes are
MIT. Free Fly left the cart in 1.5.0 and is no longer pinned.

No mod here distributes ROMs, extracted game data, or Pokémon-copyrighted
art, audio or text. Game data comes from your own cartridge dump. Battle Art also supplies original
procedural models and generated foliage artwork; CG3 remains the cart label.

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

## 1.10.0

Restores the **3** camera key on Crystal, including first person and third
person, while respecting menus and cutscenes. Battle Art1.18.0 also repairs
native scenery caching, adds open Park benches/bins, corrects two unused prop
recipes, and improves crown tops and Dark Cave surfaces. Wild Skies1.12.2 fixes
connected-map collision calls; Online+0.5.3 skips unsupported map-script hooks.
The reported bouncing Pokémon remains unresolved. This is an incremental
HD-2D update; exact Gamma Emerald parity and hardware testing remain open.

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
