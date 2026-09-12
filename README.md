# Johto Diorama

A version-pinned Gen1Recomp cart for **Pokémon Crystal**: Johto as a 3D
diorama, with the battles fought on it and a FLY user to cross it.

This bundle ships no code. It is a pin list — every mod on it is published
separately and fetched at its exact build.

## What's on it

| mod | build | what it does here |
| --- | --- | --- |
| [Wilds of Kanto](https://github.com/YoDrehDenSwagAuf/overworld-spawn-mod) | 2.1.9 | wild Pokémon visible in the overworld, **and the party follower** |
| [Battle Art Voxel Fork](https://github.com/notquiteog/DramaticShapeVoxelMod) | 1.12.2 | the diorama, 3D-BTL staged on it, and Johto's tiles classified |
| [Free Fly](https://github.com/notquiteog/free_fly) | 1.8.1 | a FLY user carries you over the map; land anywhere walkable |
| [NPC Bubbles](https://github.com/notquiteog/gen1recomp-npc-bubbles) | 2.3.13 | speech bubbles over NPCs |
| [Wild Skies](https://github.com/shanehudson-gen1recomp-mods/wild_skies) | 1.12.0 | flocks of local flying Pokémon crossing the sky, perching on rooftops |
| [Crystal Animated Sprites with Shiny Visuals](https://github.com/notquiteog/crystal_animated_sprites_with_shiny_visuals) | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order this cart was verified
in — it is priority-ascending, which is what the loader picks on its own. It
matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and the one that loads last has the outermost say on
which art a battle draws.

`seal` is `sealed+`: the list is fixed, but you can switch any of the six off.

## Why four of the six are forks

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
  1.12.2 is the height pass that 1.12.1's overcorrections needed: trees and
  bushes are one cell again instead of leaning two into the path, interiors
  keep the class height so Elm's Lab's tables are furniture and not 48px
  towers, and each town wears its own roofs — the palette bake had keyed on
  the tileset, so New Bark came up in Cherrygrove's pink after one visit
  there.
- **Free Fly** flew on Crystal but the camera never lifted, so the diorama
  filled with a very large trainer standing on the grass. Gold's `World`
  drives its own camera every frame, so the mod's ground-plane lift is
  skipped there by design — and the placed-camera seam that would have
  covered it was gated to the 75° rung and read a `Game.renderer` that does
  not exist on Gen 2. MIT-licensed upstream, so the fork is clean.
- **NPC Bubbles** declared no `games` key, which means Gen 1 only, so a
  Crystal boot skipped it outright.
- **Crystal Animated Sprites** wrapped Gold's `drawSceneBody` without its
  `panelFn` argument and forwarded none, silently discarding whatever the
  caller asked to be drawn.

**Wilds of Kanto and Wild Skies are pinned upstream unchanged** — both
already declare Gen 2 and load clean.

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

### And the flying mod that lost

[Dramatic Sky Ride](https://github.com/burgerslayer7/dramatic-sky-ride)
0.2.18 is the bigger mount system — land, water and air, Suicune's amphibious
traversal, badge progression — and it declares a hard conflict with Free Fly,
so this was a choice between them rather than a ranking.

Free Fly won on evidence. Both load clean on Crystal, so takeoff was driven
through the real seam, the party-submenu row each one adds. Free Fly offered
`FREEFLY` and flew. Dramatic Sky Ride offered `RIDE & FLY` and raised:

```
src/render/Assets.lua:61: Could not open file
dramatic_sky_ride_runtime/rider_SPRITE_CHRIS_c13_y1.png. Does not exist.
```

Its composed rider sheet is keyed to the player sprite, and Crystal's is
`SPRITE_CHRIS`. Its own `GEN2_BETA_TESTING.md` calls Gen 2 an *"unverified
Gen1Recomp++ / Gold compatibility beta"*, and it ships no tests. Free Fly is
also the mod the rest of this family is built around: `wild_skies` and
`double_battles` share a byte-identical `lib/shared/skylib.lua` with it, and
Wild Skies reads Free Fly's exported flight state in four places to keep its
birds out of the player's lane.

## Verified

Installed from exactly these pinned artifacts and booted on Crystal
(gen1recomp 0.2.59):

- all six load, **zero loader errors**;
- six render pipelines coexist (`voxel`, `tiltshift`, `owwild_ball_hud`,
  `owwild_catching_tick`, `owwild_behavior_tick`, `npc_bubbles_overlay`);
- New Bark Town draws as a coloured diorama with real buildings, roofs and
  trees; Route 29 has ledges and tall grass as shapes;
- a wild battle is staged on the ground, mons standing on the terrain as
  billboards under Gold's HUD;
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
- Free Fly's rider wears the trainer sprite rather than trainer-on-mount
  until a sprite pack registers in-air art through its
  `registerSpriteSource` API.

## Licensing

Wilds of Kanto, NPC Bubbles and Crystal Animated Sprites declare no licence
upstream, so no redistribution terms are granted anywhere in that chain; each
fork states its provenance and claims nothing. Free Fly and Wild Skies are
MIT (© 2026 Shane Hudson), and the Free Fly fork carries that licence and its
copyright notice unchanged.

No mod here distributes ROMs, extracted game data, or Pokémon-copyrighted
art, audio or text. Everything shown at runtime comes from your own
cartridge dump, imported by the engine on your machine.
