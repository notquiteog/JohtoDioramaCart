# Johto Diorama

Johto as a 3D diorama, with the battles fought on it and a FLY user to cross it.

The overworld is extruded into real geometry with depth-buffered occlusion and
cast shadows — trees, roofs, ledges, fences and tall grass each built as what
they are, classified from Crystal's own collision bytes and BG palette slots.
Wild Pokémon walk around in it, a party follower walks behind you, flocks of
local flyers cross the sky, NPCs talk in speech bubbles, and a battle is staged
on the map's nearest clear ground — over-the-shoulder camera, the mons standing
on that ground, depth of field behind them. Then a FLY user picks you up and
the camera rises with you.

For **Pokémon Crystal**. Six mods, pinned by digest.

## What's on it

| mod | build | what it does here |
| --- | --- | --- |
| Wilds of Kanto | 2.1.9 | wild Pokémon visible in the overworld, and the party follower |
| Battle Art Voxel Fork | 1.12.1 | the diorama, 3D-BTL staged on it, Johto's tiles classified |
| Free Fly | 1.8.1 | a FLY user carries you over the map; land anywhere walkable |
| NPC Bubbles | 2.3.13 | speech bubbles over NPCs |
| Wild Skies | 1.12.0 | flocks of local flying Pokémon, perching on rooftops |
| Crystal Animated Sprites with Shiny Visuals | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order the cart was verified
in. It matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and the one that loads last has the outermost say on
which art a battle draws.

`seal` is `sealed+`: the list is fixed, but you can switch any of the six off.

## Forks

Four of the six are compatibility forks. Each is a fix and nothing else; all
credit for the mods belongs upstream.

- **Battle Art Voxel Fork** is the Gen 2 port itself. Before 1.12.0 nothing on
  a Johto map was classified at all, so trees, buildings and fences were the
  same 16px box wearing their own facade art on the roof; 1.12.1 then made
  them build right — real building heights, doors in their facades, and
  characters standing on the ground rather than a block above it.
- **Free Fly** flew on Crystal but the camera never lifted with the rider.
  MIT upstream, so the fork carries that licence unchanged.
- **NPC Bubbles** declared no `games` key, so a Crystal boot skipped it.
- **Crystal Animated Sprites** dropped the `panelFn` argument when wrapping
  Gold's `drawSceneBody`, discarding whatever a caller asked to be drawn.

Wilds of Kanto and Wild Skies are pinned upstream unchanged.

## No separate follower mod

Wilds of Kanto absorbed the two people usually reach for. Its own source:
*"Wilds unified follower system (standalone) … No Followers EX / PokéPC
runtime dependency."* It ships all 251 follower sprites, replaces Followers
EX's option rows and migrates its save keys.

## Verified

Booted on Crystal (gen1recomp 0.2.59) from exactly these pinned artifacts:
all six load with **zero loader errors**, six render pipelines coexist, the
overworld draws as a diorama, a wild battle is staged on its ground, takeoff
works through the party submenu and the camera rises with the rider.

Known gaps: the 1ST and 3RD first-person rungs are Gen 1 only; Gold's battle
HUD is authored for a white field, so a name or HP box can land on busy
geometry; animated tiles are coloured but still.

No mod here distributes ROMs, extracted game data, or Pokémon-copyrighted
art, audio or text. Everything shown at runtime comes from your own cartridge
dump, imported by the engine on your machine.
