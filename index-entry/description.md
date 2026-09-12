# Johto Diorama

Johto as a 3D diorama, with the battles fought on it.

The overworld is extruded into real geometry with depth-buffered occlusion and
cast shadows, wild Pokémon walk around in it, NPCs talk in speech bubbles, and
a battle is staged on the map's nearest clear ground — over-the-shoulder
camera, the mons standing on that ground, depth of field behind them.

For **Pokémon Crystal**. Four mods, pinned by digest.

## What's on it

| mod | build | what it does here |
| --- | --- | --- |
| Wilds of Kanto | 2.1.9 | wild Pokémon visible in the overworld, with idle/roam/chase behaviour |
| Battle Art Voxel Fork | 1.11.1 | the diorama, and 3D-BTL staged on it |
| NPC Bubbles | 2.3.13 | speech bubbles over NPCs |
| Crystal Animated Sprites with Shiny Visuals | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order the cart was verified
in. It matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and whichever loads last has the outermost say on the
art a battle draws.

`sealed+`, so the list is fixed but any of the four can be switched off.

## Three of the four are compatibility forks

Two of these did not run on Gen 2 at all and one broke another mod there. Each
fork is a compatibility fix and nothing else; all credit belongs upstream.

- **NPC Bubbles** declared no `games` key — Gen 1 only — so a Crystal boot
  skipped it. The fork declares Gen 2 and gates its Gen 1-only OPTIONS page,
  which borrows `src.ui.OptionRows`, one of the two Gen 1 names the Gen 2
  compatibility layer deliberately does not serve.
- **Crystal Animated Sprites** wrapped Gold's `drawSceneBody` without its
  `panelFn` argument and forwarded none, silently discarding whatever the
  caller asked to be drawn.
- **Battle Art Voxel Fork** is the Gen 2 port itself.

**Wilds of Kanto is pinned upstream unchanged** — it already declared Gen 2 and
loaded clean.

## Verified

Installed from exactly these pinned artifacts and booted on Crystal
(gen1recomp 0.2.59): all four load with zero loader errors, all six render
pipelines coexist, New Bark Town draws as a coloured diorama, and a wild battle
is staged on its ground.

## Known gaps

Inherited from Battle Art's Gen 2 port, and documented there: the **1ST** and
**3RD** first-person rungs are Gen 1 only, Gold's battle HUD is authored for a
white field so a name box can land on busy geometry, and animated tiles (water,
flowers) are coloured but still.
