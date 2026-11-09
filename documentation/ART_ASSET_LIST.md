# SANTA DASH — Art Asset List

**Document version:** 1.0  
**Status:** Initial production inventory  
**Art pipeline:** Blender → GLB → Godot  
**Visual style:** Low Poly Cartoon / Polished 3D Cartoon  
**Target platform:** Android and iOS  
**Renderer:** Godot Mobile Renderer

---

# 1. Production Guidelines

All artistic assets will be created by the project artist.

No production asset should be considered complete until it has been imported into Godot and visually validated.

## 1.1 Technical Pipeline

- 3D modeling: Blender 4.5.3 LTS.
- 3D export: GLB.
- Engine: Godot 4.7.2.
- Textures: PNG or WebP.
- Music: OGG.
- Sound effects: WAV or OGG.
- UI graphics: SVG or PNG where appropriate.

## 1.2 Naming Convention

Use lowercase `snake_case` for filenames.

Examples:

- `santa_character.glb`
- `christmas_village_segment_01.glb`
- `gold_coin.glb`
- `magic_magnet.glb`
- `santa_run.glb`

Avoid spaces, accents and special characters.

## 1.3 General Asset Requirements

All assets must:

- Follow the approved art direction.
- Use optimized geometry.
- Have appropriate pivots and origins.
- Use consistent scale.
- Use reusable materials where possible.
- Be tested in Godot.
- Be optimized for mobile hardware.

---

# 2. Characters

## 2.1 Playable Characters

| Character | Model | Rig | Priority |
|---|---|---|---|
| Santa Claus | Required | Humanoid | Critical |
| Elf | Required | Humanoid | High |
| Snowman | Required | Humanoid-compatible | High |
| Rudolph | Required | Quadruped | Medium |
| Krampus | Required | Humanoid-compatible | Medium |
| Gingerbread Man | Required | Humanoid | Medium |

## 2.2 Santa Claus — Detailed Requirements

Santa is the initial playable character.

Visual features:

- Rounded body proportions.
- Large head.
- Red Christmas suit.
- White beard.
- Santa hat.
- Black belt.
- Golden buckle.
- Black boots.
- Gloves.
- Friendly cartoon appearance.

Initial geometry budget: approximately 8,000–15,000 triangles.

This is an initial target, not a mandatory limit. Final complexity must be validated on target devices.

## 2.3 Character Rigging

The humanoid characters should share a compatible skeleton structure where practical.

Required rig features:

- Root.
- Hips.
- Spine.
- Chest.
- Neck.
- Head.
- Arms.
- Hands.
- Legs.
- Feet.

Secondary bones may be added for:

- Beard.
- Hat.
- Clothing accessories.
- Decorative elements.

Rudolph requires a dedicated quadruped rig.

---

# 3. Character Animations

## 3.1 Santa — Required Animation Set

| Animation | Priority |
|---|---|
| Idle | Critical |
| Run | Critical |
| Jump | Critical |
| Fall | Critical |
| Land | High |
| Slide | Critical |
| Hit | Critical |
| Death | Critical |
| Victory | Medium |
| Celebration | Medium |
| Turn_Left | Medium |
| Turn_Right | Medium |
| Select | Medium |

Gameplay timing must not depend on animation duration.

Animation state and gameplay state must remain independent.

## 3.2 Additional Characters

Additional characters may reuse the same animation structure when their skeletons are compatible.

Character-specific animations may be introduced when their proportions or rig requirements demand them.

Not every character requires every animation clip.

---

# 4. Worlds and Environments

Four independent environments are required.

Each world contains reusable track segments, decorations, obstacle placement areas and background elements.

## 4.1 Christmas Village

Visual theme:

- Festive village.
- Snow-covered buildings.
- Christmas trees.
- Warm windows.
- Decorations.
- Snowfall.

Required asset groups:

- Ground and track.
- Buildings.
- Christmas trees.
- Street decorations.
- Lamps.
- Snow elements.
- Background structures.
- Environmental details.

## 4.2 Toy Factory

Visual theme:

- Colorful toy factory.
- Machinery.
- Production equipment.
- Toy decorations.
- Magical industrial atmosphere.

Required asset groups:

- Factory buildings.
- Production machinery.
- Conveyor systems.
- Toy decorations.
- Pipes.
- Steam sources.
- Background structures.

## 4.3 Frozen Forest

Visual theme:

- Frozen woodland.
- Snow-covered vegetation.
- Ice formations.
- Blue atmospheric lighting.

Required asset groups:

- Frozen trees.
- Snow-covered rocks.
- Ice formations.
- Frozen vegetation.
- Snow decorations.
- Background mountains.

## 4.4 Candy Kingdom

Visual theme:

- Colorful candy environment.
- Magical fantasy structures.
- Sweet-themed decorations.
- Bright atmosphere.

Required asset groups:

- Candy buildings.
- Candy trees.
- Lollipop structures.
- Sweet decorations.
- Candy formations.
- Background elements.

---

# 5. Track Segments

Track segments are modular and reusable.

Initial design dimensions:

- Width: 6 m.
- Length: 30 m.
- Three lanes.
- Lane width: 2 m.

Each segment must support defined gameplay placement areas.

Conceptual segment structure:

```text
TrackSegment
├── Track
├── Environment
├── DecorationPoints
├── ObstacleSpawnPoints
├── CollectibleSpawnPoints
├── PowerUpSpawnPoints
├── EntryPoint
└── ExitPoint
```

The final implementation may use different node types or resource references depending on the generation system.

Required segment categories:

- Straight segments.
- Decorative segments.
- Obstacle pattern segments.
- Collectible pattern segments.
- Mixed gameplay segments.

The initial production should focus on a limited, reusable segment library.

---

# 6. Obstacles

Obstacles must communicate their gameplay function clearly.

Initial obstacle categories:

- Ground obstacles requiring jumping.
- Elevated obstacles requiring sliding.
- Lane-blocking obstacles requiring lane changes.
- Multi-lane obstacle patterns.
- Environmental obstacles.

Each obstacle requires:

- Optimized model.
- Appropriate collision shape.
- Clear visual silhouette.
- Correct pivot.
- Mobile-friendly materials.

Collision geometry should be simpler than render geometry whenever possible.

The final obstacle inventory will be defined during world and gameplay pattern design.

---

# 7. Collectibles

## 7.1 Gold Coin

Required features:

- Readable silhouette.
- Golden material.
- Collection animation.
- Optional visual rotation.
- Collection feedback effect.

## 7.2 Premium Gem

Required features:

- Distinct silhouette.
- Recognizable premium appearance.
- Material with controlled reflections.
- Collection feedback effect.

Both collectibles should use optimized models and reusable materials.

---

# 8. Power-ups

Required models:

| Power-up | Visual identity |
|---|---|
| Magic Magnet | Magical magnet |
| Shield | Protective magical shield |
| Magic Boots | Enhanced boots |
| Santa's Sleigh | Santa-themed sleigh |
| Score Multiplier | Multiplier symbol or magical object |

Each power-up requires:

- Main 3D model.
- Readable silhouette.
- Collection effect.
- Activation effect.
- Optional idle animation.

Additional visual indicators may be required for active effects in the HUD.

---

# 9. Environmental Decoration

Decorative assets must be reusable and grouped by world.

Examples:

- Trees.
- Rocks.
- Buildings.
- Lamps.
- Signs.
- Fences.
- Christmas decorations.
- Factory equipment.
- Ice formations.
- Candy structures.

Decoration must be distributed across three visual depth layers:

1. Foreground.
2. Midground.
3. Background.

Distant geometry should use simplified models and materials.

---

# 10. User Interface Assets

Required UI resources:

- Game logo.
- Application icon.
- Buttons.
- Currency icons.
- Character portraits.
- Character selection elements.
- Shop icons.
- Mission icons.
- Power-up icons.
- Settings icons.
- Menu backgrounds.
- Game over graphics.
- Reward graphics.

Reference interface resolution: 1080 × 1920.

The interface must adapt to different screen ratios and safe areas.

Text should use Godot Control nodes rather than being embedded into decorative textures whenever possible.

---

# 11. Visual Effects

Required effects:

| Effect | Usage |
|---|---|
| Snow | Christmas Village |
| Steam | Toy Factory |
| Ice particles | Frozen Forest |
| Magical dust | Candy Kingdom |
| Coin sparkle | Collectible feedback |
| Gem sparkle | Premium collectible feedback |
| Power-up activation | Power-up feedback |
| Shield impact | Protection feedback |
| Collision effect | Impact feedback |
| Record celebration | New personal record |

Effects must be brief, readable and optimized for mobile devices.

---

# 12. Audio Assets

Audio will initially use external licensed libraries.

Required categories:

## Music

- Main menu music.
- Gameplay music loop.

## Sound Effects

- Coin collection.
- Gem collection.
- Jump.
- Landing.
- Slide.
- Collision.
- Shield activation.
- Power-up collection.
- Power-up expiration.
- Button interaction.
- Reward feedback.

## Environmental Audio

- Christmas Village ambience.
- Toy Factory ambience.
- Frozen Forest ambience.
- Candy Kingdom ambience.

All audio must have a license compatible with commercial distribution.

License records and attribution requirements must be documented.

---

# 13. Production Priorities

## Priority 1 — Initial Playable Prototype

- Santa model.
- Santa rig.
- Santa idle animation.
- Santa run animation.
- Santa jump animation.
- Santa fall animation.
- Santa slide animation.
- Christmas Village track.
- Basic track segments.
- Initial obstacles.
- Gold coin.
- Initial power-up models.

## Priority 2 — Complete Initial Gameplay

- Remaining critical Santa animations.
- Obstacle variations.
- Additional track segments.
- Collectible effects.
- Power-up effects.
- Gameplay UI assets.
- Main menu presentation.
- Game over presentation.
- Initial audio assets.

## Priority 3 — Content Expansion

- Additional characters.
- Additional character animations.
- Toy Factory.
- Frozen Forest.
- Candy Kingdom.
- Additional obstacles.
- Additional decorative assets.
- Additional effects.
- Additional UI elements.

---

# 14. Asset Validation Checklist

An asset is ready for integration when:

- [ ] Correct filename.
- [ ] Correct file format.
- [ ] Correct scale.
- [ ] Correct origin and pivot.
- [ ] Appropriate geometry complexity.
- [ ] Materials validated.
- [ ] Textures optimized.
- [ ] Animation tested where applicable.
- [ ] Exported successfully.
- [ ] Imported successfully into Godot.
- [ ] Visual appearance validated in the game.
- [ ] Performance impact reviewed.

---

# 15. Asset Status Management

Each asset should have one of the following statuses:

- NOT_STARTED
- IN_PROGRESS
- READY_FOR_IMPORT
- IMPORTED
- VALIDATED

Assets must not be considered complete merely because their Blender model or source file exists.

**End of document.**