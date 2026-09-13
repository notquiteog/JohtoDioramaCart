# Johto Diorama

A version-pinned Gen1Recomp cart for **Pokémon Crystal**: Battle Art's 3D
diorama with round scenery and real furniture, the battles fought on it, a
FLY user to cross it, modern menus, PC storage, running shoes and the party
follower.

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
| [Gen1Online+](https://github.com/notquiteog/gen1online-plus) | 0.5.1 | online multiplayer for Crystal: GTS trading, PVP battles and the Casino Lounge |
| [Kanto Gear](https://github.com/AverageConsumer/kanto-gear) | 3.2.9 | companion UI host for the single-screen window |
| [Wilds of Kanto](https://github.com/YoDrehDenSwagAuf/overworld-spawn-mod) | 2.1.9 | wild Pokémon visible in the overworld, **and the party follower** |
| [Battle Art Voxel Fork](https://github.com/notquiteog/DramaticShapeVoxelMod) | 1.14.0 | the diorama, 3D-BTL staged on it, Johto's tiles classified, round scenery, furniture, ledges and rock models, HD-2D scenery row |
| [Dramatic Sky Ride](https://github.com/notquiteog/dramatic-sky-ride) | 0.2.19 | land, water and air mounts with Suicune's traversal; a FLY user carries you over the map |
| [Gen 2 Modern UI](https://github.com/notquiteog/gen2recomp) | 1.0.15 | modern menus for the start and PC screens |
| [Gen 3 Boxes](https://github.com/MadeinTaly/gen1recomp-gen3-boxes) | 1.24.0 | Gen 3-style PC boxes and box back sprites |
| [Modern Johto](https://github.com/MadeinTaly/gen1recomp-modern-johto) | 0.2.0 | optional texture modernisation, off by default |
| [NPC Bubbles](https://github.com/notquiteog/gen1recomp-npc-bubbles) | 2.3.13 | speech bubbles over NPCs |
| [Double Battles](https://github.com/notquiteog/double-battles-gen2) | 0.8.0 | wild doubles and trainer 2v2 on Crystal, run by the engine's own battle sim, staged on the diorama |
| [Running Shoes](https://github.com/MadeinTaly/gen1recomp-running-shoes) | 1.10.0 | hold to run |
| [Wild Skies](https://github.com/shanehudson-gen1recomp-mods/wild_skies) | 1.12.0 | flocks of local flying Pokémon crossing the sky, perching on rooftops |
| [Crystal Animated Sprites with Shiny Visuals](https://github.com/notquiteog/crystal_animated_sprites_with_shiny_visuals) | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order this cart was verified
in. It matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and the one that loads last has the outermost say on
which art a battle draws.

`seal` is `sealed+`: the list is fixed, but you can switch any of the thirteen
off. Modern Johto ships with its balance switches at the author's off
defaults, and Double Battles' WILD DOUBLES ships at SOMETIMES.

## Why six of the thirteen are forks

Each fork is a compatibility fix and nothing else; all credit for the mods
belongs upstream.

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

## Verified

Installed from exactly these pinned artifacts and booted on Crystal
(gen1recomp 0.2.59, software OpenGL under Xvfb):

- all twelve load in the pinned order, **zero loader errors**;
- the boot was checked a second time from the packaged files — the release
  `.g1rcart` in a clean save's `carts/` folder, the pinned Battle Art 1.14.0
  zip as the installed mod — with every pin's version loading and the game
  reaching ready;
- New Bark Town draws as a coloured diorama with real buildings, roofs and
  round canopied trees; Route 29 has six-pixel ledges with their lip; Elm's
  Lab and the player's house draw their furniture at table height with the
  starter balls ON the ball table; the coast shows its rock models;
- a wild battle is staged on the ground and the diorama stays visible in the
  panels' margins and through attack animation background clears, mons
  standing on the terrain as billboards under Gold's HUD;
- the eleven-mod driver check (Gen1Online+ adds online screens it does not
  touch) exercises Running Shoes and Free Fly walk
  phases, the modern start/PC menus, Gen 3 Boxes and box backs, the summary
  screen, and Modern Johto's optional split hook without mutating shared
  type data;
- takeoff through the party submenu works and the camera lifts with it
  (`Voxel3D.camera` goes from `nil` to a placed camera mid-flight);
- Wilds' follower engine reports `installed=true, ownerMode=wilds`.

## Known gaps

Inherited from Battle Art's Gen 2 port, and documented there:

- the **1ST** and **3RD** first-person rungs are Gen 1 only — they take the
  walk as well as the eye, and `handleInput` is not one of the three members
  Gold's compatibility facade dispatches back through;
- Gold's battle HUD is authored for a white field, so a name or HP box can
  land on busy geometry;
- animated tiles (water, flowers) are coloured but still;

## Licensing

Wilds of Kanto, NPC Bubbles, Crystal Animated Sprites and Modern UI declare
no licence upstream, so no redistribution terms are granted anywhere in that
chain; each fork or re-publish states its provenance and claims nothing.
Kanto Gear, Wild Skies, Gen 3 Boxes, Modern Johto and Running Shoes are
MIT. Free Fly left the cart in 1.5.0 and is no longer pinned.

No mod here distributes ROMs, extracted game data, or Pokémon-copyrighted
art, audio or text. Everything shown at runtime comes from your own
cartridge dump, imported by the engine on your machine.
