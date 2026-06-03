# YUNG 1.21.11 Fabric Ports Case Study

This is a public case study for porting YUNG's API and multiple YUNG mods to Minecraft 1.21.11 Fabric.

The goal was to preserve existing behavior while updating dependencies, mappings, mixins, registry usage, config/data loading, worldgen hooks, and version-sensitive Minecraft internals.

This repository is an index, not an official upstream release. Use the fork branches and patches as study material for the porting process, not as an upstream distribution channel.

## Fork Branches

| Project | Fork branch | Patch |
| --- | --- | --- |
| YUNG's API | [ZECHEESELORD/YUNGs-API `1.21.11`](https://github.com/ZECHEESELORD/YUNGs-API/tree/1.21.11) | [patch](patches/yungs-api-1.21.11-fabric.patch) |
| YUNG's Better End Island | [ZECHEESELORD/YUNGs-Better-End-Island `1.21.11`](https://github.com/ZECHEESELORD/YUNGs-Better-End-Island/tree/1.21.11) | [patch](patches/better-end-island-1.21.11-fabric.patch) |
| YUNG's Better Strongholds | [ZECHEESELORD/YUNGs-Better-Strongholds `1.21.11`](https://github.com/ZECHEESELORD/YUNGs-Better-Strongholds/tree/1.21.11) | [patch](patches/better-strongholds-1.21.11-fabric.patch) |
| YUNG's Bridges | [ZECHEESELORD/YUNGs-Bridges `1.21.11`](https://github.com/ZECHEESELORD/YUNGs-Bridges/tree/1.21.11) | [patch](patches/yungs-bridges-1.21.11-fabric.patch) |

## Case Study Notes

The patches cover a practical Fabric port from Minecraft 1.21.4 to 1.21.11:

- Dependency and mapping updates: Gradle wrapper, Fabric Loom, Fabric API, loader versions, Minecraft versions, YUNG's API versions, and mapping configuration were moved to the 1.21.11 toolchain.
- Minecraft API renames and moves: call sites were updated for changed Minecraft names, codecs, registry helpers, chunk/structure APIs, and feature placement internals.
- Mixin target changes: affected mixins and accessor registrations were adjusted for 1.21.11 targets, including API accessor changes and loader-side entity/worldgen mixins.
- Registry and data loading changes: auto-registration helpers, creative tabs, entity and potion registration, structure condition/action codecs, and local sibling YUNG API dependency wiring were updated.
- Worldgen and structure behavior changes: jigsaw assembly, terrain adaptation, aquifer overrides, End island features, stronghold processors, and bridge feature codecs/placements were ported while keeping existing behavior.
- Client/server and loader compatibility notes: the case study focuses on Fabric-compatible builds and keeps optional NeoForge project inclusion configurable through `-PfabricOnly`.
- What was intentionally not rewritten: structure algorithms, mod feature design, config semantics, loot/data definitions, and unrelated local files were left out of the committed port history.

## Proof Files

- [Patch manifest](proof/patch-manifest.md)
- [Fork branch proof](proof/fork-branches.md)
- [Build verification](proof/build-verification.md)
