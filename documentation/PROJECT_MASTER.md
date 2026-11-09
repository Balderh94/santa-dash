# SANTA DASH — Project Master

**Document version:** 1.0  
**Project status:** Foundation and architecture phase  
**Engine:** Godot 4.7.2-stable  
**Language:** Typed GDScript  
**Renderer:** Mobile Renderer  
**Target platforms:** Android and iOS  
**Orientation:** Portrait  
**Repository:** santa-dash  
**Shared Core:** Endless Runner Core

---

# 1. Project Identity

## 1.1 Name

SANTA DASH

## 1.2 Genre

3D Endless Runner.

## 1.3 Business Model

Free-to-play with optional advertising and in-app purchases.

## 1.4 Visual Identity

Low Poly Cartoon with polished 3D cartoon presentation.

## 1.5 Core Concept

Santa Claus must recover the Christmas presents stolen by Krampus.

The player runs through different magical Christmas environments, avoids obstacles, collects rewards and unlocks characters and worlds.

---

# 2. Project Vision

Develop a polished, accessible and entertaining mobile endless runner.

The game must provide:

- Responsive three-lane movement.
- Jumping and sliding.
- Procedural track generation.
- Multiple environments.
- Unlockable characters.
- Collectibles and power-ups.
- Missions and progression.
- A balanced virtual economy.
- Optional monetization.
- Stable mobile performance.

---

# 3. Technical Foundation

| Component | Specification |
|---|---|
| Engine | Godot 4.7.2-stable |
| Language | Typed GDScript |
| Renderer | Mobile |
| Platforms | Android / iOS |
| Orientation | Portrait |
| Reference resolution | 1080 × 1920 |
| Window override | 540 × 960 |
| Stretch Mode | canvas_items |
| Stretch Aspect | expand |
| Physics engine | Jolt Physics |
| Physics ticks | 60 |
| Gravity | 9.8 m/s² |
| Asset pipeline | Blender → GLB → Godot |
| Version control | Git |
| Shared Core | Git Submodule |

---

# 4. Repository Architecture

The project uses the following structure:

```text
santa-dash/
├── addons/
│   └── endless_runner_core/
├── scenes/
├── scripts/
├── assets/
├── resources/
├── monetization/
├── localization/
├── documentation/
└── project.godot
```

The Core is maintained independently in its own repository.

Game-specific resources and logic must remain in SANTA DASH.

---

# 5. Shared Core

Repository:

`endless-runner-core`

Initial integrated version:

`v0.1.0`

Integration method:

Git Submodule.

The Core provides reusable functionality such as:

- Player movement.
- Lane management.
- Track generation.
- Object pooling.
- Obstacle spawning.
- Collectible spawning.
- Power-up spawning.
- Difficulty progression.
- Score calculation.
- Shared service interfaces.

The Core must remain independent of Christmas-specific content.

---

# 6. Gameplay Summary

## 6.1 Movement

- Automatic forward running.
- Three lanes.
- Lateral movement.
- Jump.
- Slide.
- Swipe-based mobile controls.

## 6.2 World Movement

The environment moves toward the player.

The player maintains a fixed forward gameplay position.

## 6.3 Track Dimensions

- Total width: 6 m.
- Lane width: 2 m.
- Segment length: 30 m.
- Lane centers: -2 m, 0 m, +2 m.

These values remain provisional until validated with final assets.

## 6.4 Camera

Third-person elevated camera.

Initial provisional settings:

- X = 0 m.
- Y = 5.5 m.
- Z = 8 m.
- FOV = 65 degrees.
- Smoothed following.

---

# 7. Characters

Initial playable roster:

| Character | Unlock method |
|---|---|
| Santa | Available initially |
| Elf | Gold coins |
| Snowman | Gold coins |
| Rudolph | Missions or challenges |
| Krampus | Special challenge |
| Gingerbread Man | Gold coins or optional pack |

Characters may have modest collectible appearance affinities.

No significant pay-to-win advantages are permitted.

---

# 8. Worlds

| World | Initial status |
|---|---|
| Christmas Village | Starting world |
| Toy Factory | Unlockable |
| Frozen Forest | Unlockable |
| Candy Kingdom | Unlockable |

Only one world is active during a run.

Unlocked worlds remain available.

---

# 9. Collectibles and Power-ups

## Currency

- Gold coins.
- Premium gems.

## Power-ups

- Magic Magnet.
- Shield.
- Magic Boots.
- Santa's Sleigh.
- Score Multiplier.

Power-ups activate automatically and have limited durations.

---

# 10. Progression

Progression includes:

- Character unlocking.
- World unlocking.
- Daily missions.
- Weekly missions.
- Personal records.
- Player statistics.
- Cosmetic content.

Achievements are planned for a future phase.

---

# 11. Monetization

Initial monetization model:

- Rewarded advertisements.
- Controlled interstitial advertisements.
- Remove-ads purchase.
- Premium currency packs.
- Cosmetic bundles.

The game must remain playable without purchases.

Advertising and purchasing integrations must comply with applicable privacy and platform policies.

---

# 12. Audio and Visual Effects

## Audio

- Main menu music.
- Gameplay music.
- Gameplay sound effects.
- Interface sounds.
- Optional world ambience.

## Visual Effects

- Snow.
- Steam.
- Ice particles.
- Magical dust.
- Collection effects.
- Power-up effects.
- Collision effects.

All effects must be optimized for mobile hardware.

---

# 13. Localization

Initial languages:

- Spanish.
- English.
- Catalan.

Translation resources use CSV.

Automatic device language detection and manual selection are required.

---

# 14. Performance Targets

Primary target:

60 FPS on supported mid-range mobile devices.

Optimization priorities:

- Object pooling.
- Shared materials.
- Controlled geometry.
- Texture optimization.
- Limited dynamic shadows.
- Controlled particles.
- Efficient collision geometry.

Real-device testing is mandatory.

---

# 15. Development Principles

1. Implement incrementally.
2. Validate every subsystem before continuing.
3. Keep gameplay logic independent from artistic assets.
4. Keep Core and game-specific functionality separate.
5. Do not introduce unnecessary dependencies.
6. Use typed GDScript.
7. Test on real mobile hardware.
8. Document significant technical decisions.
9. Avoid unapproved architectural changes.
10. Do not treat untested features as completed.

---

# 16. Current Development Status

## Completed Foundation Tasks

- [x] Godot 4.7.2 installed and verified.
- [x] Blender 4.5.3 LTS installed and verified.
- [x] GitHub repositories created.
- [x] Endless Runner Core repository created.
- [x] SANTA DASH repository created.
- [x] GENERIC RUNNER repository created.
- [x] Core Git Submodule integrated into SANTA DASH.
- [x] Core Git Submodule integrated into GENERIC RUNNER.
- [x] Initial Core plugin created and activated.
- [x] Core v0.1.0 release published.
- [x] SANTA DASH Godot project initialized.
- [x] GENERIC RUNNER Godot project initialized.
- [x] Portrait display configuration completed.
- [x] Initial viewport and stretch settings configured.
- [x] Physics settings verified.
- [x] Input Map configured in both games.
- [x] Initial repository folder structures prepared.
- [x] Documentation files created.

## Current Phase

Phase 1 — Project Foundation.

Current sprint:

Sprint 1.8 — Technical and Design Documentation.

## Pending Documentation

- [ ] Complete and validate all project documentation.
- [ ] Complete Core documentation.
- [ ] Complete Generic Runner documentation.
- [ ] Review consistency between documents.
- [ ] Commit and push documentation changes.

## Pending Development

- [ ] Implement reusable Core systems.
- [ ] Create initial gameplay scenes.
- [ ] Establish player integration.
- [ ] Implement track generation.
- [ ] Implement obstacles and collectibles.
- [ ] Import initial artistic assets.
- [ ] Build first playable prototype.

No gameplay systems have been implemented yet.

---

# 17. Main Development Roadmap

| Phase | Objective |
|---|---|
| Phase 0 | Product and architecture decisions |
| Phase 1 | Project foundation |
| Phase 2 | Core gameplay architecture |
| Phase 3 | Player movement |
| Phase 4 | Track and procedural generation |
| Phase 5 | Obstacles and collectibles |
| Phase 6 | Scoring and difficulty |
| Phase 7 | First playable prototype |
| Phase 8 | Worlds and content |
| Phase 9 | Menus and progression |
| Phase 10 | Economy and monetization |
| Phase 11 | Optimization and testing |
| Phase 12 | Publishing and release |

The roadmap may be refined as technical requirements become clearer.

---

# 18. Project Documentation

The following documents are maintained:

- `PROJECT_MASTER.md`
- `GAME_DESIGN_DOCUMENT.md`
- `TECHNICAL_DOCUMENTATION.md`
- `ART_ASSET_LIST.md`
- `ART_DIRECTION_GUIDE.md`
- `DEVELOPMENT_LOG.md`
- `DECISIONS.md`
- `BUG_TRACKER.md`

This document is the central project reference.

**End of document.**