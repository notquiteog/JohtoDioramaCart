# Johto Diorama

A version-pinned Gen1Recomp cart for **Pokémon Crystal**: Johto as a 3D
diorama, with the battles fought on it.

This bundle ships no code. It is a pin list — every mod on it is published
separately and fetched at its exact build.

## What's on it

| mod | build | what it does here |
| --- | --- | --- |
| [Wilds of Kanto](https://github.com/YoDrehDenSwagAuf/overworld-spawn-mod) | 2.1.9 | wild Pokémon visible in the overworld, with idle/roam/chase behaviour |
| [Battle Art Voxel Fork](https://github.com/notquiteog/DramaticShapeVoxelMod) | 1.11.1 | the diorama, and 3D-BTL staged on it |
| [NPC Bubbles](https://github.com/notquiteog/gen1recomp-npc-bubbles) | 2.3.13 | speech bubbles over NPCs |
| [Crystal Animated Sprites with Shiny Visuals](https://github.com/notquiteog/crystal_animated_sprites_with_shiny_visuals) | 2.0.4 | animated battle sprites and shiny visuals |

The order above is the load order, and it is the order this cart was verified
in — it is priority-ascending, which is what the loader picks on its own. It
matters: Battle Art and Crystal Animated Sprites both wrap the engine's
`pokemon.sprite` hook, and the one that loads last has the outermost say on
which art a battle draws.

`seal` is `sealed+`: the list is fixed, but you can switch any of the four off.

## Why three of the four are forks

Two of them did not run on Gen 2 at all, and one broke another mod on it.
Each fork is a compatibility fix and nothing else; all credit for the mods
belongs upstream.

- **NPC Bubbles** declared no `games` key, which means Gen 1 only, so a Crystal
  boot skipped it outright. The fork declares Gen 2 and gates its Gen 1-only
  OPTIONS page, which borrows `src.ui.OptionRows` — one of the two Gen 1 names
  the engine's Gen 2 compatibility layer deliberately does not serve.
- **Crystal Animated Sprites** wrapped Gold's `drawSceneBody` without its
  `panelFn` argument and forwarded none, silently discarding whatever the
  caller asked to be drawn. That broke Battle Art's Gen 2 battle background
  and would break any other mod passing a panel through that seam.
- **Battle Art Voxel Fork** is the Gen 2 port itself.

**Wilds of Kanto is pinned upstream unchanged** — it already declares Gen 2 and
loaded clean.

## Not on it

**Crystal 251** was considered and left off deliberately. It is a Gen 1
overhaul: it imports a Crystal ROM as a *data source* to bring 251 Pokémon,
Gen 2 battles and breeding to Red/Blue/Yellow. On Crystal every one of those is
already native, and it patches Kanto move tables Gold never loads while
declaring `profile: overhaul`, `priority: 110` and `affects_link`. Forced onto
Crystal it fails outright at `battle/crystal_presentation.lua:124`, asserting a
`BLIZZARD` battle-anim that does not exist in Gold's differently-keyed anim
registry. It is the right mod for a Gen 1 cart, not this one.

## Verified

Installed from exactly these pinned artifacts and booted on Crystal
(gen1recomp 0.2.59):

- all four load, **zero loader errors**;
- all six render pipelines coexist (`voxel`, `tiltshift`, `owwild_ball_hud`,
  `owwild_catching_tick`, `owwild_behavior_tick`, `npc_bubbles_overlay`);
- New Bark Town draws as a coloured diorama;
- a wild battle is staged on its ground, mons standing on the terrain as
  billboards under Gold's HUD.

## Known gaps

Inherited from Battle Art's Gen 2 port, and documented there:

- the **1ST** and **3RD** first-person rungs are Gen 1 only;
- Gold's battle HUD is authored for a white field, so a name or HP box can land
  on busy geometry;
- animated tiles (water, flowers) are coloured but still.
