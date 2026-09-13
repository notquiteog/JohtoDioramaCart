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

For **Pokémon Crystal**. Twelve mods, pinned by digest.

## What's on it

| mod | build | what it does here |
| --- | --- | --- |
| Gen1Online+ | 0.5.0 | online multiplayer: GTS trading, PVP battles and the Casino Lounge |
| Kanto Gear | 3.2.9 | companion UI host for the single-screen window |
| Wilds of Kanto | 2.1.9 | wild Pokémon visible in the overworld, and the party follower |
| Battle Art Voxel Fork | 1.13.0 | the diorama, 3D-BTL staged on it, Johto's tiles classified, round scenery, furniture and rock models |
| Free Fly | 1.8.2 | a FLY user carries you over the map; land anywhere walkable |
| Gen 2 Modern UI | 1.0.15 | modern menus for the start and PC screens |
| Gen 3 Boxes | 1.24.0 | Gen 3-style PC boxes and box back sprites |
| Modern Johto | 0.2.0 | optional texture modernisation, off by default |
| NPC Bubbles | 2.3.13 | speech bubbles over NPCs |
| Running Shoes | 1.10.0 | hold to run |
| Wild Skies | 1.12.0 | flocks of local flying Pokémon, perching on rooftops |
| Crystal Animated Sprites with Shiny Visuals | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order the cart was verified
in. It matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and the one that loads last has the outermost say on
which art a battle draws.

`seal` is `sealed+`: the list is fixed, but you can switch any of the twelve
off.

## Forks

Five of the twelve are compatibility forks. Each is a fix and nothing else;
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
  attack-animation visibility on Gen 2.
- **Free Fly** flew on Crystal but the camera never lifted with the rider;
  1.8.2 also fixes the walk frame a 3D pipeline poses through. MIT upstream,
  so the fork carries that licence unchanged.
- **Gen 2 Modern UI** is Modern UI (FAFF0x/gen2recomp) re-published
  unmodified for an installable digest pin. No code changes.
- **NPC Bubbles** declared no `games` key, so a Crystal boot skipped it.
- **Crystal Animated Sprites** dropped the `panelFn` argument when wrapping
  Gold's `drawSceneBody`, discarding whatever a caller asked to be drawn.

Gen1Online+, Wilds of Kanto, Gen 3 Boxes, Modern Johto, Running Shoes and
Wild Skies are pinned upstream unchanged.

## No separate follower mod

Wilds of Kanto absorbed the two people usually reach for. Its own source:
*"Wilds unified follower system (standalone) … No Followers EX / PokéPC
runtime dependency."* It ships all 251 follower sprites, replaces Followers
EX's option rows and migrates its save keys.

## Verified

Booted on Crystal (gen1recomp 0.2.59) from exactly these pinned artifacts:
all twelve load in the pinned order with **zero loader errors**, the
overworld draws as a diorama with round scenery and furniture-height
interiors, a wild battle is staged on its ground and keeps the diorama
visible through its margins and animations, the modern start/PC menus and
Gen 3 boxes work, takeoff works through the party submenu and the camera
rises with the rider. The boot was checked a second time from the packaged
release files.

Known gaps: the 1ST and 3RD first-person rungs are Gen 1 only; Gold's battle
HUD is authored for a white field, so a name or HP box can land on busy
geometry; animated tiles are coloured but still.

No mod here distributes ROMs, extracted game data, or Pokémon-copyrighted
art, audio or text. Everything shown at runtime comes from your own cartridge
dump, imported by the engine on your machine.
