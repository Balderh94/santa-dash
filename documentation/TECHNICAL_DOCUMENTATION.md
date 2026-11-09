# SANTA DASH — Technical Documentation

**Document version:** 1.0  
**Project status:** Initial technical architecture  
**Engine:** Godot 4.7.2  
**Language:** Typed GDScript  
**Renderer:** Mobile Renderer  
**Target platforms:** Android and iOS  
**Orientation:** Portrait

---

## 1. Project Overview

SANTA DASH is a 3D mobile endless runner developed using Godot 4.7.2.

The project uses Endless Runner Core as its reusable gameplay foundation.

SANTA DASH is an independent game project. It contains all Christmas-specific gameplay rules, characters, environments, progression, economy, presentation and monetization configuration.

The Core is integrated through a Git Submodule.

Repository dependency:

`addons/endless_runner_core/`

## 2. Technical Objectives

The project must:

- Maintain a modular architecture.
- Reuse Endless Runner Core functionality.
- Keep game-specific systems independent of the Core implementation.
- Support Android and iOS.
- Target 60 FPS on supported mid-range devices.
- Support portrait orientation.
- Use the Godot Mobile Renderer.
- Support scalable graphics quality.
- Keep gameplay logic independent from artistic assets.
- Support future content expansion.

## 3. Project Architecture

The project is divided into the following logical areas:

### 3.1 Application Layer

Responsible for:

- Application initialization.
- Main scene management.
- Navigation between menus and gameplay.
- Global game configuration.
- Application lifecycle.

Main scene:

`SantaDash.tscn`

### 3.2 Gameplay Layer

Responsible for SANTA DASH-specific gameplay rules:

- Run initialization.
- Christmas world selection.
- Character selection.
- Game-specific rewards.
- Missions and objectives.
- Character abilities and affinities.
- Game-specific power-up configuration.
- Game over and continuation rules.

Reusable movement and generation mechanics belong to Endless Runner Core.

### 3.3 Presentation Layer

Responsible for:

- Character models.
- Character animations.
- Environments.
- Track appearance.
- Obstacles and collectibles.
- User interface.
- Visual effects.
- Audio presentation.

All artistic assets are produced and supplied separately from gameplay logic.

### 3.4 Economy and Progression Layer

Responsible for:

- Gold coins.
- Premium gems.
- Character unlocks.
- World unlocks.
- Cosmetic purchases.
- Mission rewards.
- Player progression.
- Persistent statistics.

The game economy must remain independent of the monetization provider.

### 3.5 Monetization Layer

Responsible for:

- Rewarded advertisements.
- Interstitial advertisements.
- In-app purchases.
- Remove-ads purchases.
- Premium currency packs.
- Optional commercial bundles.

Platform-specific SDK integration must remain replaceable.

## 4. Scene Architecture

The main application scene will be:

`scenes/app/SantaDash.tscn`

The gameplay scene will be:

`scenes/gameplay/SantaRun.tscn`

The main menu will be:

`scenes/menus/MainMenu.tscn`

Additional scenes will include:

- Character selection.
- Shop.
- Missions.
- Game over interface.
- Character presentation.
- World-specific gameplay environments.

### 4.1 Gameplay Scene Structure

Proposed initial structure:

```text
SantaRun
├── WorldEnvironment
├── CameraRig
│   └── Camera3D
├── WorldController
│   ├── TrackManager
│   ├── EnvironmentController
│   └── SpawnController
├── Player
│   └── SantaVisual
├── GameplayController
├── HUD
└── AudioController
```

This structure is conceptual and may be refined during implementation.

Nodes must be introduced only when their responsibilities are clearly defined.

## 5. Endless Runner Core Integration

Endless Runner Core will provide reusable functionality for:

- Player movement.
- Lane switching.
- Jumping and sliding.
- Track generation.
- Segment recycling.
- Object pooling.
- Obstacle spawning.
- Collectible spawning.
- Power-up spawning.
- Difficulty progression.
- Score calculation.

SANTA DASH will provide game-specific configuration and content.

The Core must not contain Christmas-specific references.

## 6. Player Architecture

The player will have a separation between gameplay logic and visual representation.

Gameplay logic will manage:

- Current lane.
- Movement state.
- Jump state.
- Slide state.
- Collision response.
- Temporary invulnerability.
- Power-up effects.

The visual character will manage:

- Character model.
- Skeleton.
- Animation playback.
- Visual effects.
- Character-specific presentation.

The initial player character is Santa Claus.

Additional playable characters:

- Elf.
- Snowman.
- Rudolph.
- Krampus.
- Gingerbread Man.

Character-specific gameplay affinities must be applied through configurable rules, not hardcoded movement systems.

## 7. Movement and Camera

The game uses three lanes.

Initial provisional lane centers:

- Left: X = -2 m.
- Center: X = 0 m.
- Right: X = 2 m.

Track width: 6 m.

Initial segment length: 30 m.

The world moves toward the player while the player maintains a fixed forward gameplay position.

The player can:

- Move left.
- Move right.
- Jump.
- Slide.

Initial lane transition duration: 0.18 seconds.

Camera configuration is provisional:

- Third-person elevated camera.
- Approximate position: X = 0, Y = 5.5 m, Z = 8 m.
- Initial field of view: 65 degrees.
- Smoothed follow behavior.

These values must be validated through gameplay testing.

## 8. World Architecture

SANTA DASH includes four independent worlds:

1. Christmas Village.
2. Toy Factory.
3. Frozen Forest.
4. Candy Kingdom.

Each world defines its own:

- Track segments.
- Obstacles.
- Decorations.
- Materials.
- Lighting.
- Environmental effects.
- Music and ambient audio.

All worlds use the same fundamental gameplay systems.

Only one world is active during a run.

World unlocking is based on player progression, distance and missions.

Previously unlocked worlds remain playable.

## 9. Procedural Generation

Generation uses a hybrid approach.

Artistic segments and gameplay patterns are authored in advance.

Runtime systems combine these segments and distribute gameplay objects according to configurable rules.

The generation system must enforce:

- Reachable obstacle patterns.
- Valid lane transitions.
- Safe jumping and sliding sequences.
- Minimum recovery distances.
- Progressive difficulty.
- Appropriate collectible distribution.

Impossible obstacle combinations must be prevented.

## 10. Collectibles and Power-ups

### Collectibles

The game includes:

- Gold coins.
- Premium gems.

Collectibles contribute to economy and progression, not directly to score unless explicitly configured.

### Power-ups

Initial power-ups:

- Magic Magnet.
- Shield.
- Magic Boots.
- Santa's Sleigh.
- Score Multiplier.

Power-ups activate automatically when collected.

Each power-up has an independent duration and effect.

Gameplay logic and visual presentation must remain separated.

## 11. Scoring System

The score combines:

- Distance traveled.
- Collected coins.
- Obstacles avoided.
- Special gameplay actions.

Currency and score are separate systems.

The game records:

- Current score.
- Best score.
- Distance.
- Collected currency.
- Run statistics.

## 12. Game Flow and Recovery

The initial run flow includes:

1. Run preparation.
2. Short character presentation.
3. Active gameplay.
4. Collision handling.
5. Game over or recovery.
6. Results presentation.

A shield can absorb one qualifying impact.

Without protection, a fatal collision ends the run.

One optional rewarded-ad continuation may be offered per run.

After a successful continuation:

- The player retains the current score and distance.
- Temporary invulnerability is applied.
- The run resumes.

Voluntarily abandoning a run must not trigger continuation offers.

## 13. User Interface

The interface uses a portrait reference resolution of 1080 × 1920.

It must adapt to different aspect ratios and mobile safe areas.

Primary screens:

- Main menu.
- Character selection.
- Shop.
- Missions.
- Gameplay HUD.
- Pause.
- Game over.
- Settings.

The main menu is integrated into a 3D world presentation.

Gameplay HUD displays relevant information without obstructing obstacle visibility.

## 14. Economy and Progression

The economy includes:

- Gold coins.
- Premium gems.
- Character unlocks.
- Cosmetic items.
- World progression.
- Mission rewards.

Characters may provide small item appearance affinities.

These bonuses must remain balanced and must not create pay-to-win mechanics.

Daily missions reset every 24 hours.

Weekly missions use cumulative progress.

## 15. Monetization

The initial monetization model includes:

- Optional rewarded advertisements.
- Controlled interstitial advertisements.
- Remove-ads purchase.
- Premium currency packs.
- Cosmetic bundles.

Monetization must not be required to complete the core game.

Purchases and advertising must be implemented through replaceable provider integrations.

All advertising and purchasing behavior must comply with applicable platform policies, privacy requirements and audience protections.

## 16. Persistence

Initial persistence uses local storage through Godot's `user://` directory.

Saved data includes:

- Currency balances.
- Best score.
- Player statistics.
- Unlocked characters.
- Unlocked worlds.
- Mission progress.
- Settings.
- Purchase entitlements where appropriate.

Save data must be versioned and validated.

Future cloud synchronization must not require rewriting gameplay systems.

## 17. Audio

Audio includes:

- Main music loop.
- Coin collection effects.
- Jump and slide effects.
- Collision effects.
- Power-up effects.
- Interface sounds.
- Optional world ambience.

Music and sound effects have independent volume settings.

Audio assets must have compatible licenses for commercial distribution.

## 18. Visual Effects

Visual effects include:

- Snow.
- Steam.
- Ice particles.
- Magical dust.
- Collection effects.
- Power-up activation effects.
- Impact effects.

Effects must be optimized for mobile hardware.

Particle counts, transparency and shader complexity must be controlled.

## 19. Localization

Initial supported languages:

- Spanish.
- English.
- Catalan.

Localization data will use CSV translation resources.

The game will detect the device language and allow manual language selection.

## 20. Performance and Quality

Target:

- 60 FPS on supported mid-range devices.
- Mobile Renderer.
- Controlled draw calls.
- Shared materials.
- Efficient object pooling.
- Limited dynamic shadows.
- Controlled particle effects.
- Scalable graphics settings.

Testing must include real Android and iOS devices.

## 21. Development Constraints

The project will use:

- Godot 4.7.2.
- Typed GDScript.
- Blender-to-GLB asset pipeline.
- Git Submodule integration.
- Independent repositories.
- Incremental implementation and testing.

No gameplay feature should be implemented without defining its responsibilities, required assets and validation criteria.

## 22. Future Extensibility

The project must support:

- Additional characters.
- Additional worlds.
- New obstacles.
- New collectibles.
- Additional power-ups.
- More missions.
- Additional languages.
- New monetization products.
- Cloud persistence.
- Additional platform integrations.

**End of document.**