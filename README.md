# Johto Diorama

A sealed Pokémon Crystal cart for Gen1Recomp, with original-art 2.5D scenery.

## Unreleased five-mod refresh

The authoring manifest now contains only:

- Battle Art — scenery, camera and battle presentation.
- Wilds — visible wild Pokémon and followers.
- Online — overworld presence, chat, trading and battle rooms.
- Dramatic Ride — Pokémon mounts.
- Double Battles — optional doubles integration.
- Running Shoes — retained because Crystal has no native running.

Each mod remains independently usable. Online hosts own the shared wild roster;
guests see the host's Pokémon and request encounters from it. Double Battles
must preserve the exact Pokémon supplied by visible-spawn encounters.

This source update is **not yet released**. The manifest still carries previous
published version/hash pins while the new ports are verified. Do not package it
as a completed cross-generation release until those pins are replaced together.
The latest published cart still contains the earlier bundle.

## Install a published cart

Download the `.g1rcart` from the [GitHub releases](https://github.com/notquiteog/JohtoDioramaCart/releases)
and import it through Gen1Recomp's Custom Carts panel. Supply your own Crystal ROM.
The cart contains configuration and artwork, not a ROM. Each pinned mod download
is verified against its SHA-256 hash.

The current development verification baseline is Gen1Recomp 0.3.0. No player
saves are changed by preparing the next cart release.
