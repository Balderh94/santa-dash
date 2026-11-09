# SANTA DASH — Art Direction Guide

**Document version:** 1.0  
**Status:** Initial art direction specification  
**3D software:** Blender 4.5.3 LTS  
**Game engine:** Godot 4.7.2  
**Asset format:** GLB  
**Target platforms:** Android and iOS  
**Visual style:** Low Poly Cartoon / Polished 3D Cartoon

---

# 1. Art Direction Overview

## 1.1 Visual Identity

SANTA DASH uses a polished Low Poly Cartoon visual style.

The artistic direction combines:

- Simplified geometry.
- Rounded silhouettes.
- Exaggerated proportions.
- Expressive characters.
- Vibrant colors.
- Soft lighting.
- Carefully controlled materials.
- Readable environments.
- Cartoon-inspired visual effects.

The objective is to achieve a polished 3D appearance without unnecessarily expensive geometry, materials or shaders.

The visual identity must remain consistent across all four worlds and playable characters.

## 1.2 Artistic Priorities

The following priorities apply to all assets:

1. Gameplay readability.
2. Strong silhouettes.
3. Consistent proportions.
4. Clear color separation.
5. Visual appeal.
6. Mobile performance.
7. Reusability.

Gameplay objects must always remain visually distinguishable from decorative elements.

---

# 2. Modeling Style

## 2.1 Geometry

Models should use simplified, clean geometry.

Preferred characteristics:

- Rounded forms.
- Controlled bevels.
- Smooth silhouettes.
- Selective low-poly faceting.
- Minimal unnecessary details.
- Clean topology.
- Efficient polygon distribution.

Avoid:

- Excessive small details.
- Dense geometry without visual benefit.
- Extremely thin surfaces.
- Unnecessary internal geometry.
- Excessive overlapping surfaces.

## 2.2 Polygon Budgets

Initial production targets:

| Asset category | Initial target |
|---|---:|
| Main playable character | 8,000–15,000 triangles |
| Secondary character | 6,000–12,000 triangles |
| Small collectible | 100–1,000 triangles |
| Power-up | 500–3,000 triangles |
| Small obstacle | 300–2,000 triangles |
| Large obstacle | 1,000–5,000 triangles |
| Decorative prop | 100–3,000 triangles |

These values are starting guidelines, not strict engine limits.

Final budgets must be validated using representative mobile hardware.

## 2.3 Silhouette

Every important gameplay object must have a recognizable silhouette.

Characters must remain identifiable at gameplay camera distance.

Obstacles must communicate their collision and movement requirements clearly.

Decorative objects should not resemble dangerous obstacles unless they actually participate in gameplay.

---

# 3. Character Art Direction

## 3.1 Character Proportions

Characters use exaggerated cartoon proportions.

General characteristics:

- Relatively large heads.
- Compact bodies.
- Rounded limbs.
- Readable hands and feet.
- Expressive faces.
- Simplified anatomy.

Santa is the reference character for the overall visual style.

## 3.2 Santa Claus

### Visual Identity

- Large rounded body.
- Friendly face.
- White beard and moustache.
- Red suit.
- White clothing details.
- Santa hat.
- Black belt.
- Golden buckle.
- Black boots.
- Gloves.

### Material Direction

- Red fabric with moderate roughness.
- White beard with readable volume.
- Black leather-like accessories.
- Golden metallic details with controlled reflections.
- Skin materials with soft color transitions.

Avoid excessive metallic reflections and highly realistic skin shading.

## 3.3 Krampus

Krampus must appear more imposing than Santa.

Visual characteristics:

- Taller proportions.
- Larger silhouette.
- Stylized dark fur.
- Large horns.
- Strong facial expression.
- Cartoon-inspired threatening appearance.

The design must remain suitable for a family-friendly game.

## 3.4 Character Consistency

All characters must share:

- Consistent world scale.
- Compatible material quality.
- Similar visual detail density.
- Consistent color saturation.
- Matching artistic finish.

Differences in body proportions are allowed when required by character identity.

---

# 4. Rigging and Skeletons

## 4.1 Humanoid Skeleton

Humanoid characters should share a compatible skeleton structure whenever practical.

Recommended main bones:

- `root`
- `hips`
- `spine`
- `chest`
- `neck`
- `head`
- `shoulder_l`
- `upper_arm_l`
- `lower_arm_l`
- `hand_l`
- `shoulder_r`
- `upper_arm_r`
- `lower_arm_r`
- `hand_r`
- `upper_leg_l`
- `lower_leg_l`
- `foot_l`
- `upper_leg_r`
- `lower_leg_r`
- `foot_r`

Secondary bones may include:

- Beard bones.
- Hat bones.
- Accessory bones.
- Clothing bones.

Use a clean hierarchy without unnecessary bones.

## 4.2 Quadruped Skeleton

Rudolph requires a separate quadruped skeleton.

The rig must support:

- Four-legged running.
- Jumping.
- Landing.
- Turning.
- Hit reactions.
- Idle animation.

## 4.3 Skinning

Skin weights must be checked for:

- Shoulder deformation.
- Elbow deformation.
- Knee deformation.
- Hip deformation.
- Neck deformation.

Avoid excessive deformation and mesh intersections.

## 4.4 Animation Compatibility

Gameplay animations must be compatible with the movement system.

Animation playback must not determine actual gameplay physics.

The gameplay controller controls movement while animation communicates the visual state.

---

# 5. Animation Production

## 5.1 Animation Style

Animations should be:

- Expressive.
- Readable.
- Responsive.
- Slightly exaggerated.
- Consistent with cartoon proportions.

Avoid unnecessary motion that reduces gameplay readability.

## 5.2 Santa Animation Set

Required clips:

- `idle`
- `run`
- `jump`
- `fall`
- `land`
- `slide`
- `hit`
- `death`
- `victory`
- `celebration`
- `turn_left`
- `turn_right`
- `select`

## 5.3 Animation Requirements

Run:

- Seamless looping.
- Stable forward-facing orientation.
- Consistent stride.

Jump:

- Clear anticipation.
- Strong takeoff.
- Readable airborne pose.
- Controlled landing transition.

Fall:

- Clear airborne or descending pose.
- Compatible with gameplay jump timing.

Slide:

- Clear lowered body position.
- Readable profile.
- Safe visual clearance.

Hit:

- Immediate and recognizable reaction.

Death:

- Clear final reaction.
- No unnecessary prolonged animation.

## 5.4 Animation Export

Export animations using GLB.

Animations may be exported separately when this improves reuse or reduces unnecessary asset duplication.

Skeleton compatibility must be preserved.

Animation names must remain consistent across compatible characters.

---

# 6. Materials and Textures

## 6.1 Material Style

Use a hybrid material workflow.

Preferred materials:

- Principled materials.
- Solid base colors.
- Selective texture usage.
- Controlled roughness.
- Limited metallic effects.
- Selective normal maps.

Avoid complex materials without clear visual benefits.

## 6.2 Texture Resolution

Initial guidelines:

| Asset type | Recommended resolution |
|---|---|
| Main character | 512 × 512 or 1024 × 1024 |
| Large environment texture | 512 × 512 or 1024 × 1024 |
| Small prop | 256 × 256 or 512 × 512 |
| UI icon | Depends on display size |

These are starting points.

Use texture atlases and shared materials when practical.

## 6.3 Texture Optimization

- Avoid unnecessarily large textures.
- Use appropriate compression.
- Reuse materials.
- Minimize unnecessary texture variations.
- Avoid excessive transparent materials.
- Check mipmap behavior.

## 6.4 Color Palette

Colors should be vibrant but controlled.

Avoid excessive saturation across every object.

Important gameplay elements must stand out from the environment.

---

# 7. Lighting and Rendering

## 7.1 Lighting Style

The visual style uses a combination of ambient and selective dynamic lighting.

Characteristics:

- Soft illumination.
- Controlled shadows.
- Moderate contrast.
- Readable character silhouettes.
- Limited emissive materials.
- Atmospheric depth.

## 7.2 World Lighting

### Christmas Village

- Warm festive illumination.
- Soft golden highlights.
- Snow contrast.
- Moderate snowfall visibility.

### Toy Factory

- Colorful illumination.
- Magical accents.
- Controlled metallic reflections.
- Readable industrial silhouettes.

### Frozen Forest

- Cool blue lighting.
- Cold atmospheric appearance.
- Strong contrast between ice and vegetation.

### Candy Kingdom

- Warm and bright illumination.
- Colorful environmental accents.
- Controlled emissive details.

## 7.3 Mobile Rendering

The project uses Godot Mobile Renderer.

Avoid unnecessary:

- Real-time shadow casters.
- Transparent layers.
- Expensive shaders.
- Excessive particle effects.
- High-overdraw materials.
- Large numbers of unique materials.

Performance must be evaluated on physical devices.

---

# 8. Environment Art Direction

## 8.1 Environmental Depth

Each environment uses three visual depth layers.

### Foreground

- Track.
- Obstacles.
- Collectibles.
- Power-ups.
- Nearby decorations.

This layer requires the highest gameplay readability.

### Midground

- Trees.
- Buildings.
- Machinery.
- Environmental structures.
- Large decorative objects.

### Background

- Mountains.
- Distant buildings.
- Forest silhouettes.
- Large environmental forms.

Background geometry should be simplified.

## 8.2 Track Design

Initial track dimensions:

- Width: 6 m.
- Length: 30 m.
- Three lanes.
- Lane width: 2 m.

The track center is X = 0.

Track segments must have consistent entry and exit positions.

Seams between consecutive segments must not produce visible gaps or geometry intersections.

## 8.3 Modular Environment Production

Environment assets should be created as reusable components.

Separate:

- Track geometry.
- Decorative geometry.
- Obstacle geometry.
- Background geometry.
- Placement points.

Decorative elements should not require modifications to gameplay collision logic.

---

# 9. Obstacle Art Direction

Obstacles must be visually readable.

Every obstacle should communicate its gameplay requirement.

Design considerations:

- Recognizable silhouette.
- Clear collision boundaries.
- Appropriate scale.
- Strong contrast with track.
- Consistent world styling.

Avoid decorative details that obscure the obstacle's actual shape.

Render geometry and collision geometry should be treated separately.

---

# 10. Collectibles and Power-ups

## 10.1 Gold Coin

- Strong golden appearance.
- Simple readable shape.
- Distinct silhouette.
- Optional rotation.
- Collection animation.

## 10.2 Premium Gem

- Distinct shape.
- Clear premium identity.
- Controlled reflections.
- Visible collection feedback.

## 10.3 Power-ups

Power-ups must be identifiable at a glance.

Each power-up should use:

- A recognizable central object.
- Consistent visual framing.
- Clear color identity.
- Collection feedback.
- Activation feedback.

Active effects should have corresponding HUD indicators.

---

# 11. Visual Effects

Effects use a polished cartoon style.

Required categories:

- Snow particles.
- Steam.
- Ice particles.
- Magical dust.
- Collection sparkles.
- Shield effects.
- Power-up activation.
- Collision effects.

Effects must:

- Be short and readable.
- Avoid obscuring gameplay.
- Use controlled particle counts.
- Avoid unnecessary transparency.
- Support object pooling where appropriate.
- Have a reduced-quality or disabled option when necessary.

---

# 12. User Interface Art Direction

## 12.1 Interface Style

The interface should match the cartoon 3D identity.

Characteristics:

- Rounded shapes.
- Clear hierarchy.
- Strong contrast.
- Readable typography.
- Consistent icon style.
- Simple interactions.

## 12.2 Resolution

Reference resolution:

1080 × 1920 pixels.

Aspect ratio:

9:16.

The interface must adapt to different screen dimensions and safe areas.

## 12.3 UI Production

Use vector graphics where appropriate.

Use PNG for raster graphics requiring transparency.

Avoid embedding important text into decorative textures.

Text must remain localizable.

---

# 13. Audio Direction

## 13.1 Music

The musical style should be festive, energetic and suitable for an arcade endless runner.

Required music:

- Main menu.
- Gameplay loop.

## 13.2 Sound Effects

Required sound categories:

- Coins.
- Gems.
- Jump.
- Landing.
- Slide.
- Collision.
- Shield.
- Power-ups.
- Interface interactions.
- Rewards.

## 13.3 Environmental Audio

Optional ambient layers:

- Christmas Village.
- Toy Factory.
- Frozen Forest.
- Candy Kingdom.

## 13.4 Audio Sources and Licensing

Audio may be obtained from external libraries.

Every resource must have a documented license.

The license must permit commercial use and distribution.

Attribution requirements must be respected.

---

# 14. Blender Production Standards

## 14.1 Scene Organization

Organize Blender scenes into logical collections.

Suggested collections:

- `geometry`
- `rig`
- `materials`
- `lights`
- `cameras`
- `export`

Remove unnecessary objects before exporting.

## 14.2 Naming

Use lowercase `snake_case` for asset files and animation clips.

Use clear, consistent bone names.

Avoid spaces, accents and special characters.

## 14.3 Scale and Transforms

Use metric units.

Maintain consistent scale between assets.

Character and track dimensions must be validated in Godot.

Apply appropriate object transforms before export.

Check:

- Position.
- Rotation.
- Scale.
- Origin.
- Pivot.
- Bone hierarchy.

## 14.4 Origins and Pivots

Origins must be selected according to gameplay behavior.

Examples:

- Characters: ground contact near the center of the feet.
- Coins: center of rotation.
- Obstacles: logical placement origin.
- Track segments: consistent segment origin.
- Environmental props: base or attachment point.

## 14.5 Export

Use GLB for 3D assets.

Before export:

1. Remove unnecessary objects.
2. Check geometry.
3. Check materials.
4. Check texture references.
5. Check skeletons.
6. Check animation names.
7. Check object transforms.
8. Export.
9. Import into Godot.
10. Validate appearance and behavior.

The export configuration must be tested with representative assets before mass production.

---

# 15. Godot Import Validation

Every exported asset must be checked in Godot.

Validation criteria:

- Correct orientation.
- Correct scale.
- Correct materials.
- Correct textures.
- Correct animation playback.
- Correct skeleton hierarchy.
- Correct origin.
- Correct collision integration where applicable.
- Acceptable runtime performance.

Imported assets must not be considered complete until validated in their actual game context.

---

# 16. Performance Guidelines

The project targets mobile hardware.

Optimization priorities:

- Appropriate polygon counts.
- Shared materials.
- Texture reuse.
- Limited transparency.
- Controlled dynamic shadows.
- Simplified collision geometry.
- Efficient particle systems.
- Object pooling.
- Appropriate level of detail.
- Simplified distant geometry.

Optimization must be based on profiling and testing rather than assumptions.

---

# 17. Art Quality Checklist

An artistic asset is ready for production integration when:

- [ ] Approved visual design.
- [ ] Correct proportions.
- [ ] Correct scale.
- [ ] Clean geometry.
- [ ] Appropriate polygon budget.
- [ ] Correct origin and pivot.
- [ ] Correct material setup.
- [ ] Correct texture resolution.
- [ ] Correct rig, where applicable.
- [ ] Animation validation, where applicable.
- [ ] Correct GLB export.
- [ ] Successful Godot import.
- [ ] Visual validation in the game.
- [ ] Performance review.

---

# 18. Art Direction Change Management

Significant changes to the visual identity must be documented.

Changes affecting character proportions, material style, world palettes or technical asset requirements must be reviewed before large-scale production.

The Art Direction Guide is the reference document for maintaining visual consistency.

**End of document.**