# SANTA DASH — Development Log

## Project Information

- Project: SANTA DASH
- Engine: Godot 4.7.2-stable
- Language: Typed GDScript
- Current phase: Phase 2 — Core Gameplay Systems
- Current sprint: Sprint 2.6.3.3.4 — Minimum-Count Track Maintenance

---

## Development History

### Phase 0 — Product Definition and Architecture

**Status: Completed**

Approved decisions include:

- 3D mobile endless runner.
- Godot 4.7.2.
- Mobile Renderer.
- Portrait orientation.
- Three-lane movement.
- Jump and slide mechanics.
- Hybrid procedural generation.
- Four Christmas worlds.
- Six playable characters.
- Free-to-play monetization.
- Shared reusable Core.
- Three independent repositories.

### Phase 1 — Project Foundation

**Status: In Progress**

#### Sprint 1.1 — Development Environment

**Status: Completed**

- Godot installation verified.
- Blender installation verified.
- Git installation verified.
- GitHub Desktop configured.
- Development hardware documented.

#### Sprint 1.2 — Repository Creation

**Status: Completed**

Created repositories:

- endless-runner-core
- santa-dash
- generic-runner

#### Sprint 1.3 — Core Plugin Foundation

**Status: Completed**

- Initial Godot plugin created.
- Plugin activated successfully in a test project.
- Core repository organized.
- Initial release v0.1.0 published.

#### Sprint 1.4 — Git Submodule Integration

**Status: Completed**

- Core integrated into SANTA DASH.
- Core integrated into GENERIC RUNNER.
- Both integrations use the v0.1.0 release.

#### Sprint 1.5 — Godot Project Configuration

**Status: Completed**

- Both game projects initialized.
- Mobile Renderer selected.
- Portrait orientation configured.
- Viewport configured to 1080 × 1920.
- Window override configured to 540 × 960.
- Stretch Mode set to canvas_items.
- Stretch Aspect set to expand.
- Physics settings verified.
- Jolt Physics selected.

#### Sprint 1.6 — Input Configuration

**Status: Completed**

Both games contain:

- move_left
- move_right
- jump
- slide

Keyboard mappings:

- Left Arrow / A
- Right Arrow / D
- Up Arrow / W
- Down Arrow / S

#### Sprint 1.7 — Repository Structure

**Status: Completed**

- Initial folder organization approved.
- Documentation folders created.
- SANTA DASH documentation files created.
- Core documentation files created.
- GENERIC RUNNER documentation files created.
- Repository structures visually verified.

#### Sprint 1.8 — Technical and Design Documentation

**Status: Completed**

- SANTA DASH project documentation created and reviewed.
- Core documentation created and reviewed.
- GENERIC RUNNER documentation files created.
- Core architecture, API reference, development guide and changelog reviewed for consistency.
- Initial documentation changes committed and pushed to the three GitHub repositories.
- Repository structures and documentation organization verified.


---

### Phase 1 — Project Foundation

**Status: Completed**

The SANTA DASH project foundation, repository structure, Godot configuration and initial documentation are complete and published to GitHub.

### Phase 2 — Core Gameplay Systems

**Status: In Progress**

#### Sprint 2.1 — Game Flow

**Status: Implemented, documented, tested in the temporary Godot test project, committed and pushed to the Core repository.**

Implemented in the `endless-runner-core` repository:

- `core/managers/game_flow_manager.gd`
- `GameFlowManager` states: READY, RUNNING, PAUSED and FINISHED.
- Valid transitions for starting, pausing, resuming, finishing and resetting a run.
- Rejection of invalid state transitions.
- Signals: `state_changed`, `run_started`, `run_paused`, `run_resumed` and `run_finished`.
- Core test script: `tests/test_game_flow_manager_core.gd`.

Validation performed:

- The Core test script was copied into the separate `endless-runner-core-test` Godot project and executed successfully.
- Valid and invalid transitions and signal emission counts were checked.
- Output confirmed: `PASS: GameFlowManager tests completed successfully.`

Integration status:

- GameFlowManager has not yet been integrated into the SANTA DASH gameplay scene.
- SANTA DASH still references the Core submodule release `v0.1.0`, which predates this implementation.
- No SANTA DASH gameplay scene or game-specific gameplay script was changed for Sprint 2.1.

#### Sprint 2.2 — Player Controller

**Status: Implemented, documented, tested, committed and pushed to the Core repository.**

Implemented in the `endless-runner-core` working tree:

- `player/controllers/player_controller.gd`
- Player states: IDLE, RUNNING, JUMPING, FALLING, SLIDING, HIT and DEAD.
- Logical jump and slide action requests.
- A single-slot pending-action queue for controlled jump/slide chaining.
- Impact interruption and pending-action cancellation.
- Terminal death state until the Game Flow lifecycle returns to READY.
- Synchronization with `GameFlowManager` through its `state_changed` signal.
- `tests/test_player_controller.gd`.

Validation performed:

- The implementation and test script were copied into the separate `endless-runner-core-test` Godot project.
- The test covered initial state, valid and rejected requests, jump/fall progression, action chaining, queue capacity, pause/resume, hit interruption and recovery, death, reset, and signal counts.
- Output confirmed: `PASS: PlayerController tests completed successfully.`

Scope and integration status:

- PlayerController manages logical states and action requests only.
- Physical movement, animation playback, collision detection, and action timing are not implemented by this controller.
- The exact physical compatibility and timing of jump/slide chaining remain to be validated by the Movement System.
- PlayerController has not yet been integrated into the SANTA DASH gameplay scene.
- SANTA DASH still references Core submodule release `v0.1.0`; the Sprint 2.2 implementation is not included in that pinned release.
- No SANTA DASH gameplay scene, character asset, or game-specific gameplay script was changed for Sprint 2.2.

#### Sprint 2.3 — Lane System

**Status: Implemented, tested, documented, committed and pushed to the Core repository.**

Implemented in the `endless-runner-core` working tree:

- `gameplay/lanes/lane_system.gd`
- `Lane` enum: LEFT (-1), CENTER (0) and RIGHT (+1).
- CENTER as the initial logical lane.
- Configurable `lane_width`, defaulting to 2.0 metres.
- X-coordinate calculation for each lane.
- Immediate logical lane updates for accepted requests.
- Rejection of invalid directions and requests beyond the left/right boundaries.
- Consecutive requests evaluated against the latest logical lane.
- Signals: `lane_change_requested` and `lane_changed`.
- `reset_lane()` to return to CENTER.
- `tests/test_lane_system.gd`.

Validation performed:

- The implementation and test script were copied into the separate `endless-runner-core-test` Godot project.
- The test covered initial lane, lane coordinates, configurable width, accepted and rejected requests, immediate logical updates, consecutive requests, signal counts and reset behavior.
- Output confirmed: `PASS: LaneSystem tests completed successfully (25 assertions).`

Scope and integration status:

- LaneSystem manages logical lane state only.
- It does not move a player node, interpolate transforms, read input actions, or depend on PlayerController.
- Physical lateral movement and smooth destination changes remain for the Movement System in Sprint 2.4.
- LaneSystem has not yet been integrated into the SANTA DASH gameplay scene.
- SANTA DASH still references Core submodule release `v0.1.0`; the Sprint 2.3 implementation is not included in that pinned release.
- No SANTA DASH gameplay scene, character asset, or game-specific gameplay script was changed for Sprint 2.3.

#### Sprint 2.4.1 — Input Buffer

**Status: Implemented, tested, documented, committed and pushed to the Core repository; Santa Dash development log committed and pushed.**

Updated in the `endless-runner-core` working tree:

- Replaced the Sprint 2.2 single-slot pending-action queue with a one-slot, time-limited Input Buffer in `player/controllers/player_controller.gd`.
- Added the `BufferedAction` enum: `NONE`, `JUMP` and `SLIDE`.
- Added the configurable `input_buffer_duration`, defaulting to 0.15 seconds.
- Added read-only access to `buffered_action` and `input_buffer_time_remaining`.
- The latest valid buffered input replaces the previous entry, including repeated input of the same action.
- A slide can be buffered while the player is `JUMPING` or `FALLING`; a jump can be buffered while `SLIDING`.
- The buffer lifetime is updated by `_physics_process(delta)` while the game is running and expires when the configured window elapses.
- The buffer and its remaining lifetime are preserved while the Game Flow state is `PAUSED`.
- Hit, death and player reset clear the buffer.
- Added/updated `tests/test_player_controller.gd` to cover buffer replacement, expiration, pause preservation, action chaining, interruption, death and Game Flow behavior.

Validation performed:

- The updated implementation and test script were copied into the separate `endless-runner-core-test` Godot project.
- The first test run exposed an outdated assertion that expected a repeated buffered request to be rejected. The test expectation was corrected to match the approved latest-input-replaces-previous rule.
- The updated test then completed successfully.
- Output confirmed: `PASS: PlayerController tests completed successfully.`

Scope and integration status:

- The Input Buffer manages logical input retention only. It does not implement physical jump or slide movement.
- Physical action timing, movement compatibility and execution remain responsibilities of the upcoming Movement System work.
- No SANTA DASH gameplay scene, character asset, or game-specific gameplay script was changed for Sprint 2.4.1.
- SANTA DASH continues to reference the Core submodule release `v0.1.0`; this unreleased working-tree update is not included in that pinned release.

#### Sprint 2.4.2 — Player Lateral Movement

**Status: Implemented, tested, documented, committed and pushed to the Core repository; the Santa Dash development log was committed and pushed.**

Implemented in the `endless-runner-core` working tree:

- Added `gameplay/movement/player_movement.gd`.
- `PlayerMovement` extends `CharacterBody3D` and owns physical lateral movement on the player root.
- Added `bind_dependencies(lane_system, player_controller)` to connect the movement component to the logical lane system and player-state controller.
- Added `request_lane_change(direction)` as the entry point for lane-change input. It validates dependencies and permitted player state before forwarding the request to `LaneSystem`.
- Subscribed to `LaneSystem.lane_changed`; logical lane changes update the physical X target immediately without snapping the player's current position.
- Added configurable `lane_change_duration`, defaulting to 0.18 seconds.
- Lateral speed is derived from `LaneSystem.lane_width / lane_change_duration` (approximately 11.11 m/s with the default 2.0 m lane width).
- Consecutive requests update the destination during movement. A request in the opposite direction reverses movement from the current physical position.
- The final step is limited to the remaining distance and the player's X position is corrected to the exact lane centre.
- Longitudinal Z velocity is set to zero; existing vertical Y velocity is preserved for later jump/fall integration.
- Lateral input and movement are blocked in READY, PAUSED, FINISHED, HIT and DEAD. RUNNING, JUMPING, FALLING and SLIDING are permitted when `PlayerController.control_enabled` is true.
- Added `tests/test_player_movement.gd` and the temporary test scene `tests/player_movement_test.tscn`.

Validation performed:

- The implementation and test files were copied into the separate `endless-runner-core-test` Godot project.
- The test scene executed successfully in Godot 4.7.2.
- Output confirmed: `PASS: PlayerMovement tests completed successfully (40 assertions).`

Scope and integration status:

- Sprint 2.4.2 implements physical lateral movement only. It does not implement jump, fall, landing or slide physics.
- `LaneSystem` remains responsible for logical lane selection; `PlayerController` remains responsible for player states and the input buffer.
- No SANTA DASH gameplay scene, character asset, or game-specific gameplay script was changed for Sprint 2.4.2.
- SANTA DASH continues to reference the Core submodule release `v0.1.0`; this unreleased working-tree update is not included in that pinned release.

#### Sprint 2.4.3 — Jump and Slide Movement

**Status: Implemented, functionally tested, documented, committed and pushed to the Core repository; the Santa Dash development log was committed and pushed.**

Updated in the `endless-runner-core` working tree:

- Extended `gameplay/movement/player_movement.gd`; the existing `PlayerMovement` remains the single physical movement component attached to the `CharacterBody3D` root.
- Added exported references for `LaneSystem`, `PlayerController` and the player's direct-child `CollisionShape3D`.
- Updated `bind_dependencies()` to validate all three dependencies and require a vertical `CapsuleShape3D` on a direct child collision node.
- The supplied capsule resource is duplicated into separate normal and slide capsule resources before configuration, preventing in-place modification of the original shared resource.
- Added configurable `jump_height` (default 2.0 m) and `gravity` (default 9.8 m/s²).
- Added `jump_initial_velocity`, calculated as `sqrt(2 * gravity * jump_height)`.
- Connected to `PlayerController.jump_requested` and implemented jump initiation, gravity, apex detection, falling and landing notification through `notify_jump_apex_reached()` and `notify_jump_finished()`.
- Added configurable `slide_duration` (default 0.8 seconds), `normal_capsule_height` (1.8 m), `slide_capsule_height` (0.9 m) and `capsule_radius` (0.35 m).
- Connected to `PlayerController.slide_requested`; slide action switches to the reduced capsule and starts the slide timer.
- The collision shape's local Y offset is adjusted to half the active capsule height, keeping the capsule bottom aligned with a foot-level player origin.
- When the slide timer expires, the system queries the full normal capsule at the intended standing position using `PhysicsShapeQueryParameters3D`.
- The clearance query checks physics bodies, ignores `Area3D`, uses the player's collision mask and excludes the player's own RID.
- If a physics body blocks standing clearance, the reduced capsule remains active and the query is retried every physics frame. This does not create HIT or complete the slide.
- HIT blocks lateral control but keeps gravity and floor collision active. Landing during HIT does not automatically recover the HIT state.
- PAUSED freezes physical simulation and preserves velocity. DEAD stops physical movement.
- Extended `tests/test_player_movement.gd` for jump/slide, capsule, clearance, input-buffer chaining and state validation. The test scene `player_movement_test.tscn` was temporary and remained in the separate `endless-runner-core-test` project.

Validation performed:

- The updated implementation, test script and temporary test scene were copied into the separate `endless-runner-core-test` Godot project.
- The test executed successfully in Godot 4.7.2.
- Output confirmed: `PASS: PlayerMovement jump/slide tests completed successfully (40 assertions).`

Scope and integration status:

- Sprint 2.4.3 extends the existing `PlayerMovement`; it does not add a separate movement node or controller.
- No character model, animation, production scene, or game-specific SANTA DASH gameplay script was created or changed.
- The physical player origin is expected to be at foot level, with a direct-child `CollisionShape3D` using a vertical `CapsuleShape3D`.
- SANTA DASH continues to reference the Core submodule release `v0.1.0`; this unreleased working-tree update is not included in that pinned release.

#### Sprint 2.4.4 — Animation Configuration and Controller

**Status: Implemented, functionally tested, documented, committed and pushed to the Core repository; the Santa Dash development log was committed and pushed.**

Implemented in the `endless-runner-core` working tree:

- Added `player/resources/animation_config.gd` with the `AnimationConfig` Resource.
- Added optional `StringName` clip properties for `running_animation`, `jumping_animation`, `falling_animation`, `sliding_animation`, `hit_animation`, `death_animation`, `land_animation`, `idle_animation` and `victory_animation`.
- Added configurable `crossfade_duration`, defaulting to 0.15 seconds.
- Added `player/controllers/animation_controller.gd` with the `AnimationController` Node.
- Added `setup()` to validate and bind `PlayerController`, `AnimationPlayer` and `AnimationConfig`, connect state and animation-finished signals, and start the animation associated with the current logical state when a valid clip is available.
- Added `bind_player_movement()` to connect `PlayerMovement.player_landed` to the configured `land_animation`.
- Added `play_animation_event()` for existing non-looping event clips and `clear_setup()` for disconnecting signals and clearing dependencies.
- Added state-to-clip mapping for `IDLE`, `RUNNING`, `JUMPING`, `FALLING`, `SLIDING`, `HIT` and `DEAD`.
- Added configurable crossfade playback, missing/empty clip handling, loop-configuration warnings, one-shot event completion through `AnimationPlayer.animation_finished`, and restoration of the animation for the current logical state after an event.
- Event playback is rejected while the logical player state is `HIT` or `DEAD`. A logical state change interrupts an active event.
- Extended `gameplay/movement/player_movement.gd` with the parameterless `player_landed` signal. It is emitted after `notify_jump_finished()` when a confirmed landing occurs in `JUMPING` or `FALLING`; it is not emitted for landing while in `HIT`.
- Added `tests/test_animation_controller.gd`.

Validation performed:

- `AnimationConfig` and `AnimationController` were copied into the separate `endless-runner-core-test` Godot project and recognized by Godot.
- The AnimationController test used a technical `AnimationPlayer` with generated test clips; no production character model or artistic animation assets were required.
- The test covered valid/invalid setup, state mapping, jump/fall/slide transitions, direct LAND playback, automatic LAND playback from `player_landed`, event completion and restoration, event interruption, HIT/DEAD priority, missing event clips and cleanup.
- Output confirmed: `PASS: AnimationController tests completed successfully.` with 31 assertions and 0 failures.
- The updated `PlayerMovement` test passed with 40 assertions after its test setup was updated to provide the required `CollisionShape3D` dependency.

Scope and integration status:

- `AnimationController` is a presentation component. It does not control movement, physics, collision handling or logical player states.
- `LAND` is an animation event, not a new `PlayerController` state.
- The landing-signal integration test emits `player_landed` directly to verify the connection and animation response. Physical landing detection remains covered separately by the PlayerMovement test.
- No production player scene, character model, skeleton, or artistic animation clips have been created or integrated.
- The Core repository does not contain a `project.godot` test project; tests run in the separate `endless-runner-core-test` project using copies of the Core scripts.
- SANTA DASH continues to reference the Core submodule release `v0.1.0`; these working-tree changes are not included in that pinned release.

#### Sprint 2.5.1 — World Movement

**Status: Implemented, tested, documented, committed and pushed to Core and Santa Dash.**

Implemented in the `endless-runner-core` working tree:

- Added `gameplay/movement/world_movement.gd` with the `WorldMovement` Node.
- Added exported `world_root` and configurable `initial_speed` (default 10.0 m/s).
- Added read-only `current_speed`, `movement_active` and `registered_segment_count` properties.
- Added `bind_world_root()` to validate and bind a `WorldRoot` that is a direct sibling of `WorldMovement` in the scene tree.
- Added `register_segment()` and `unregister_segment()`; only live, in-tree, non-queued direct children of the bound `WorldRoot` are accepted, and duplicate registrations are rejected.
- Added `start_movement()`, `stop_movement()`, `set_speed()` and `get_speed()`.
- Added `movement_started`, `movement_stopped` and `speed_changed(previous_speed, new_speed)` signals.
- Implemented local positive-Z translation in `_physics_process(delta)` using `current_speed * delta`, preserving each segment's local X and Y coordinates.
- Speed changes reject negative and non-finite values. Stopping preserves the current speed; no automatic acceleration is implemented.
- Registered segments are removed automatically when they leave the scene tree. If `WorldRoot` exits the tree, movement stops and registrations are cleared.
- Rebinding to a different `WorldRoot` stops movement and clears prior registrations.
- Added `tests/test_world_movement.gd`. The technical scene `world_movement_test.tscn` remains exclusively in the temporary `endless-runner-core-test` project and is not copied into Core.

Validation performed:

- The implementation and test script were copied into the separate `endless-runner-core-test` Godot project.
- The test suite covered registration, movement, speed validation, unregistering, rebinding and deferred cleanup.
- The final diagnostic run completed all test groups and confirmed: `PASS: WorldMovement tests completed successfully (67 assertions).`
- The technical test scene used `Node3D` nodes only; no production models, materials, textures or other art assets were required.

Scope and integration status:

- `WorldMovement` moves only explicitly registered segment roots. It does not create, recycle or pool segments.
- `WorldMovement` does not move the player, change lanes, jump, slide, spawn obstacles, detect collisions or calculate difficulty.
- `WorldMovement` and `WorldRoot` must be direct siblings; registered segment roots must be direct children of `WorldRoot`. `WorldRoot` should keep an identity transform so its local positive Z axis matches the intended longitudinal direction.
- No production gameplay scene or game-specific SANTA DASH script was changed.
- Core v0.2.0 is published. Santa Dash and Generic Runner submodules have both been updated to the `v0.2.0` tag. Sprint 2.5.1 is a subsequent Core working-tree change and is not included in that release.



#### Sprint 2.5.2 — Game Flow and World Movement Integration

**Objective**

Validate the host-side coordination of the reusable `GameFlowManager` and `WorldMovement` systems without introducing a direct dependency between them.

**Implementation and test scope**

- Added `tests/test_world_movement_integration.gd` to the Core repository test suite.
- The temporary `endless-runner-core-test` project contains the technical test scene `world_movement_integration_test.tscn`; this scene is test-only and must not be copied into the Core repository or either game project.
- The test harness acts as the host layer: it connects `GameFlowManager.state_changed` and starts world movement only for `RUNNING`; it stops world movement for `READY`, `PAUSED` and `FINISHED`.
- Verified that pausing and finishing preserve the configured movement speed, and that resuming starts movement again at that speed.
- No production gameplay scene, game-specific integration script, generation system, pooling system or difficulty system was added in this sprint.

**Validation**

- Executed the integration suite in `endless-runner-core-test`.
- All test groups passed: initial `READY`, `READY → RUNNING`, `RUNNING → PAUSED`, `PAUSED → RUNNING`, `RUNNING → FINISHED → READY`, and `FINISHED` from `PAUSED`.
- Result: `PASS: GameFlowManager + WorldMovement integration tests completed successfully (52 assertions).`
- Godot Debugger reported zero errors.

**Architectural result**

- `GameFlowManager` and `WorldMovement` remain independent Core systems. The host game owns the signal connection and lifecycle mapping.
- The integration test validates the connection pattern only. Production scene integration remains future work.
- The Core test and documentation commits, and the SANTA DASH development-log commit, were pushed successfully.
- Sprint 2.5.2 does not change the published Core release `v0.2.0`; the integration test and documentation are committed working-tree additions but remain outside the published release.

#### Sprint 2.5.3 — Multi-segment World Movement Validation

**Status: Completed, documented, committed and pushed. Both repositories were subsequently confirmed published and clean.**

**Objective**

Validate that `WorldMovement` moves multiple explicitly registered segment roots consistently, without changing the production implementation or adding generation/pooling behavior.

**Test implementation**

- Added `tests/test_world_movement_segments.gd` to the Core working tree.
- The test scene `world_movement_segments_test.tscn` remains exclusively in the temporary `endless-runner-core-test` project and must not be copied into Core or either game project.
- The test uses four registered `Node3D` segment roots, an initial speed of 10 m/s, and a controlled 0.1-second simulation interval.
- Verified simultaneous movement, 1.0 m positive-Z displacement per interval, preservation of local X/Y, cumulative displacement over three intervals, stop/resume speed preservation, runtime registration, runtime unregistration and immobility of a direct child that is never registered.
- The test script was updated to leave the test window open after completion so Output and Debugger can be inspected.

**Validation**

- Executed the suite in `endless-runner-core-test`.
- Result: `PASS: WorldMovement multi-segment tests completed successfully (37 assertions).`
- The final output also confirmed that the test window remains open for manual inspection.

**Scope and limitations**

- This sprint adds test coverage only; no production `WorldMovement` behavior or public API was changed.
- No segment generation, recycling, object pooling, difficulty integration or production gameplay scene integration was added.
- The test uses technical `Node3D` nodes only; no artistic assets are required.


#### Sprint 2.5.4 — World Movement Lifecycle Validation

**Status: Completed, documented, committed and pushed. Both repositories were subsequently confirmed published and clean.**

**Objective**

Validate the lifecycle and cleanup behavior of `WorldMovement` without changing its production implementation or public API.

**Test implementation**

- Added `tests/test_world_movement_lifecycle.gd` to the Core working tree.
- The technical test scene remains exclusively in the temporary `endless-runner-core-test` project and must not be copied into Core or either game project.
- The suite exercises cleanup when registered segments or the bound `WorldRoot` leave the scene tree, WorldRoot changes/removal, signal-connection cleanup, and safe release of the `WorldMovement` node.
- The test adds automated coverage for lifecycle edge cases; it does not add new production behavior.

**Validation**

- Executed the lifecycle suite in `endless-runner-core-test`.
- Result: `PASS: WorldMovement lifecycle tests completed successfully (76 assertions).`
- Godot reported 0 errors and 0 warnings.
- The test script was copied into `endless-runner-core/tests/`.

**Scope and limitations**

- Sprint 2.5.4 adds test coverage only; no production `WorldMovement` code or public API was changed.
- No segment generation, recycling, object pooling, difficulty integration or production gameplay scene integration was added.
- The technical test scene remains in the temporary test project; only the test script belongs in Core.
- The test uses technical nodes and requires no artistic assets.
- Core v0.2.0 remains the published release; this test and its documentation are unreleased working-tree changes.


#### Sprint 2.6.1 — SegmentDefinition

**Status: Completed, documented, committed and pushed to the Core repository and SANTA DASH repository. Both repositories were confirmed published and clean.**

**Objective**

Create a reusable resource that describes a world segment and validates its resource-level configuration without introducing scene instantiation, pooling or spawning responsibilities.

**Implementation**

- Prepared `generation/segments/segment_definition.gd` with the `SegmentDefinition` class extending `Resource`.
- Exported properties: `segment_id` (`StringName`), `is_enabled` (`bool`), `segment_scene` (`PackedScene`) and `segment_length` (`float`, default 30.0).
- Implemented `get_validation_errors()` to report an empty identifier, missing scene reference and non-finite or non-positive length.
- Implemented `is_valid()` as a convenience validation method.
- `is_enabled` controls availability and does not determine whether the resource configuration is valid.
- The resource does not instantiate scenes, modify the scene tree or depend on `SegmentPool`, `SegmentSpawner` or `WorldMovement`.
- Prepared `tests/test_segment_definition.gd`. Its technical scene remains exclusively in `endless-runner-core-test`.

**Validation**

- Executed the suite in `endless-runner-core-test`.
- Result: `PASS: SegmentDefinition tests completed successfully (24 assertions).`
- Test groups covered valid definition, empty identifier, missing scene, invalid lengths, disabled definition and multiple validation errors.

**Scope and limitations**

- This subphase implements the segment data resource and its resource-level validation only.
- Runtime validation of the instantiated scene root type is reserved for `SegmentPool`.
- No segment pooling, spawning, procedural selection, track assembly or production-scene integration was implemented.
- No production artistic assets were required.
- The implementation, test script and updated documentation were committed and pushed. The user confirmed both repositories were published and clean.

#### Sprint 2.6.2 — SegmentPool

**Status: Completed, documented, committed and pushed. Both repositories were confirmed published and clean.**

**Objective**

Implement a reusable pool that owns instances created from registered `SegmentDefinition` resources. The pool is independent of segment placement, sequence selection and world movement.

**Implementation**

- Prepared `generation/pooling/segment_pool.gd` with the `SegmentPool` class extending `Node`.
- Each registered `segment_id` has an independent pool entry.
- Default prewarming is two instances per definition; default maximum capacity is eight instances per definition. Both values are configurable in `register_definition()`.
- `register_definition()` validates the resource, identifier, limits and duplicate registrations. Valid disabled definitions may be registered without prewarming.
- `acquire()` returns an unparented `Node3D`, reuses an available instance first, and creates instances on demand up to the configured maximum.
- `release()` requires the caller to detach the node from its parent first. Invalid, foreign, duplicate, queued-for-deletion and still-parented instances are rejected.
- Returned instances remain available for reuse. The pool does not shrink automatically.
- Count and registration queries are provided. `clear()` frees available and acquired instances and removes all registrations. `_exit_tree()` invokes `clear()`.
- The instantiated scene root must inherit `Node3D`.
- Signals: `segment_acquired`, `segment_released` and `pool_error`.
- The pool does not place segments, select their order, create sequences or register them with `WorldMovement`.
- Prepared `tests/test_segment_pool.gd`. The technical test scene remains exclusively in `endless-runner-core-test`.

**Validation**

- Executed the suite in `endless-runner-core-test`.
- Result: `PASS: SegmentPool tests completed successfully (81 assertions).`
- No errors were reported.
- Test groups covered registration and prewarming, acquisition and capacity, release and reuse, registration validation, disabled definitions, independent definition pools, invalid scene roots, and clear/cleanup.

**Scope and limitations**

- This subphase implements instance pooling and reuse only.
- `SegmentSpawner`, explicit segment sequencing, track assembly, procedural selection and production-scene integration remain unimplemented.
- No production artistic assets were required.
- The implementation, test script and updated documentation were committed and pushed. Both repositories were confirmed published and clean.
- Core `v0.2.0` remains the published release; `SegmentPool` is unreleased functionality.

#### Sprint 2.6.3.1 — SegmentSpawner Configuration and Sequence

**Status: Configuration and sequence implementation passed the temporary Godot test project with 53 assertions. Documentation has been updated; repository publication remains pending confirmation.**

**Objective**

Implement the first SegmentSpawner increment: validate its host dependencies and an explicit ordered sequence of `SegmentDefinition` resources, then expose controlled cyclic sequence access. Active segment instantiation, placement and recycling are deliberately deferred.

**Implementation**

- Prepared `generation/spawning/segment_spawner.gd` with `SegmentSpawner` extending `Node`.
- Added `configure(world_root, segment_pool, world_movement, sequence)`.
- Configuration requires valid dependencies inside the scene tree.
- `WorldMovement` must already be bound to the supplied `WorldRoot`; both must be direct siblings.
- Every sequence entry must be a valid, enabled `SegmentDefinition` already registered in the supplied `SegmentPool`.
- Empty sequences, invalid definitions, disabled definitions, unregistered definitions and invalid dependencies are rejected through the `spawning_error` signal.
- Configuration is transactional: a failed reconfiguration preserves the previous valid configuration and current sequence index.
- Added `get_next_definition()` to read the current entry without advancing.
- Added `advance_sequence()` to advance and wrap cyclically.
- Added `reset_sequence()` to return the index to zero.
- Added read-only `is_configured`, `sequence_index` and `sequence_length` properties.
- Repeated definitions are permitted and retain their explicit positions in the sequence.
- Prepared `tests/test_segment_spawner.gd`. The technical test scene remains exclusively in `endless-runner-core-test`.

**Validation**

- Executed the suite in `endless-runner-core-test`.
- Result: `PASS: SegmentSpawner tests completed successfully (53 assertions).`
- The user reported no errors.
- Test groups covered valid configuration, cyclic sequence, reset, empty sequence, invalid and disabled definitions, unregistered definitions, invalid dependencies, transactional reconfiguration and repeated definitions.

**Scope and limitations**

- This subphase implements dependency/sequence configuration only.
- It does not acquire instances from `SegmentPool`, add segments to `WorldRoot`, align `EntryPoint` and `ExitPoint`, register spawned nodes with `WorldMovement`, or recycle segments.
- Marker-based placement and active segment lifecycle are reserved for subsequent Sprint 2.6.3 subphases.
- No production artistic assets were required.
- Core `v0.2.0` remains the published release; this implementation is unreleased.

#### Sprint 2.6.3.2.1 — First Segment and Initial Anchor

**Status: Completed, documented, committed and pushed. Both repositories were confirmed published.**

**Objective**

Extend `SegmentSpawner` to acquire and place the first segment from the configured sequence, aligning its `EntryPoint` with the approved initial anchor: the identity local transform of `WorldRoot`.

**Implementation**

- Extended `generation/spawning/segment_spawner.gd` while preserving the configuration and cyclic-sequence API from Sprint 2.6.3.1.
- Added `spawn_first_segment()`.
- The method requires a valid configuration, an empty active-segment list, a valid `WorldRoot` inside the scene tree and an identity local transform on `WorldRoot`.
- Acquires the current definition's scene from `SegmentPool` using `SegmentPool.acquire(definition.segment_id)`.
- Validates that the acquired `Node3D` root contains direct-child nodes named `EntryPoint` and `ExitPoint`, both of type `Marker3D`.
- Calculates the segment root's local transform as the affine inverse of the `EntryPoint` local transform. With the approved identity `WorldRoot` anchor, this places the marker at the `WorldRoot` global transform.
- Adds the segment as a direct child of `WorldRoot`, verifies the marker alignment, tracks the active segment and advances the sequence only after successful placement.
- Added the `segment_spawned(segment, definition)` signal.
- Added `get_active_segment_count()` and `get_active_segments()`; the latter returns a copy of the ordered active references.
- Failed placement emits `spawning_error`, does not advance the sequence and attempts to detach and return the acquired instance to `SegmentPool`.
- A duplicate first-segment request is rejected while an active segment is tracked.
- Expanded `tests/test_segment_spawner.gd`. The technical test scene remains exclusively in `endless-runner-core-test`.

**Validation**

- Executed the suite in `endless-runner-core-test`.
- Result: `PASS: SegmentSpawner tests completed successfully (117 assertions).`
- The user reported no errors.
- Coverage includes prior configuration and sequence tests, first-segment placement at the origin, required marker presence and type checks, rejection of a non-invertible EntryPoint transform, rejection of a non-identity WorldRoot anchor, duplicate first-segment request rejection, pool rollback and sequence preservation after failure.

**Scope and limitations**

- This subphase places only the first segment at the initial anchor.
- It does not yet place a second or third segment or align a new `EntryPoint` with the previous segment's `ExitPoint`.
- It does not validate `segment_length` against marker spacing.
- It does not register the placed segment with `WorldMovement`, recycle segments or integrate with a production game scene.
- No production artistic assets were required.
- Core `v0.2.0` remains the published release; this implementation is unreleased.

#### Sprint 2.6.3.2.2.1 — Consecutive Segment Placement

**Status: Implementation passed the temporary Godot test project with 145 assertions. Documentation has been updated; repository publication remains pending confirmation.**

**Objective**

Extend `SegmentSpawner` with `spawn_next_segment()` so each subsequent segment is placed by aligning its `EntryPoint` global transform with the last active segment's `ExitPoint` global transform.

**Implementation**

- Extended `generation/spawning/segment_spawner.gd`, preserving the configuration, cyclic sequence and first-segment placement behavior.
- Added `spawn_next_segment()`, which requires an existing active segment before acquiring the next definition.
- Acquires the next segment instance from `SegmentPool` using the current definition's `segment_id`.
- Validates that the acquired root contains direct-child `Marker3D` nodes named `EntryPoint` and `ExitPoint`.
- Calculates the new root transform from the previous active segment's global `ExitPoint` transform and the new segment's local `EntryPoint` transform.
- Adds the segment to `WorldRoot`, verifies marker-transform coincidence, records it in the ordered active-segment list, advances the sequence and emits `segment_spawned` only after successful placement.
- Failed placement emits `spawning_error`, preserves the sequence and attempts to detach and return the acquired instance to `SegmentPool`.
- Expanded `tests/test_segment_spawner.gd`. The technical test scene remains exclusively in `endless-runner-core-test`.

**Validation**

- Executed the suite in `endless-runner-core-test`.
- Result: `PASS: SegmentSpawner tests completed successfully (145 assertions).`
- The user reported no errors.
- Coverage includes the prior configuration/sequence and first-segment tests, rejection when no first segment exists, second-segment alignment, third-segment alignment with an offset and locally rotated `EntryPoint`, marker validation, non-invertible entry transform rejection, initial-anchor validation, duplicate first-spawn rejection, pool rollback and sequence preservation on failed placement.

**Scope and limitations**

- This increment implements transform-based placement and marker coincidence checks for subsequent segments.
- It does not yet enforce the approved convention that `EntryPoint` and `ExitPoint` have the same local orientation aligned with `+Z`.
- It does not validate `segment_length` against marker spacing or non-uniform scale.
- It does not register placed segments with `WorldMovement`, recycle segments or integrate with a production game scene.
- No production artistic assets were required.
- Core `v0.2.0` remains the published release; this implementation is unreleased.

#### Sprint 2.6.3.2.2.1 — Consecutive Segment Placement

**Status: Implementation passed the temporary Godot test project with 145 assertions. Documentation has been updated; repository publication remains pending confirmation.**

**Objective**

Extend `SegmentSpawner` with `spawn_next_segment()` so each subsequent segment is placed by aligning its `EntryPoint` global transform with the last active segment's `ExitPoint` global transform.

**Implementation**

- Extended `generation/spawning/segment_spawner.gd`, preserving the configuration, cyclic sequence and first-segment placement behavior.
- Added `spawn_next_segment()`, which requires an existing active segment before acquiring the next definition.
- Acquires the next segment instance from `SegmentPool` using the current definition's `segment_id`.
- Validates that the acquired root contains direct-child `Marker3D` nodes named `EntryPoint` and `ExitPoint`.
- Calculates the new root transform from the previous active segment's global `ExitPoint` transform and the new segment's local `EntryPoint` transform.
- Adds the segment to `WorldRoot`, verifies marker-transform coincidence, records it in the ordered active-segment list, advances the sequence and emits `segment_spawned` only after successful placement.
- Failed placement emits `spawning_error`, preserves the sequence and attempts to detach and return the acquired instance to `SegmentPool`.
- Expanded `tests/test_segment_spawner.gd`. The technical test scene remains exclusively in `endless-runner-core-test`.

**Validation**

- Executed the suite in `endless-runner-core-test`.
- Result: `PASS: SegmentSpawner tests completed successfully (145 assertions).`
- The user reported no errors.
- Coverage includes the prior configuration/sequence and first-segment tests, rejection when no first segment exists, second-segment alignment, third-segment alignment with an offset and locally rotated `EntryPoint`, marker validation, non-invertible entry transform rejection, initial-anchor validation, duplicate first-spawn rejection, pool rollback and sequence preservation on failed placement.

**Scope and limitations**

- This increment implements transform-based placement and marker coincidence checks for subsequent segments.
- It does not yet enforce the approved convention that `EntryPoint` and `ExitPoint` have the same local orientation aligned with `+Z`.
- It does not validate `segment_length` against marker spacing or non-uniform scale.
- It does not register placed segments with `WorldMovement`, recycle segments or integrate with a production game scene.
- No production artistic assets were required.
- Core `v0.2.0` remains the published release; this implementation is unreleased.

#### Sprint 2.6.3.2.2.2 — Segment Geometry Validation

**Status: Implementation and automated validation completed. The user reported 221/221 assertions passed with no errors. Documentation is being prepared; repository publication is pending.**

**Objective**

Enforce the approved geometric conventions for segment roots and their `EntryPoint` / `ExitPoint` markers before `SegmentSpawner` places either the first segment or a consecutive segment.

**Implementation**

- Extended `generation/spawning/segment_spawner.gd` while preserving the existing dependency configuration, cyclic sequence, first-segment placement and consecutive-segment placement APIs.
- Added validation requiring the acquired `SegmentRoot` to have an identity local transform before the spawner applies its placement transform.
- Added validation requiring direct-child `EntryPoint` and `ExitPoint` markers to be `Marker3D` nodes with unit scale and local orientation aligned with the segment's positive local Z axis.
- Added validation requiring the markers to have matching local orientation within 0.1 degrees.
- Added lateral and vertical marker-offset validation with a tolerance of 0.001 m.
- Added positive longitudinal marker-spacing validation and comparison against `SegmentDefinition.segment_length` with a tolerance of 0.01 m.
- Kept root-transform validation before placement so the spawner's intentional root transform does not cause false rejection. Marker-local geometry checks remain valid after placement.
- Improved singular-transform diagnostics by checking the marker basis determinant before scale validation, ensuring a non-invertible `EntryPoint` is reported as such.
- Applied geometric validation to both `spawn_first_segment()` and `spawn_next_segment()`.
- Preserved transactional failure behavior: a rejected segment does not advance the sequence or modify the active-segment list, emits `spawning_error`, and attempts to restore and return the acquired instance to `SegmentPool`.
- Expanded `tests/test_segment_spawner.gd`. Its technical test scene remains exclusively in `endless-runner-core-test`.

**Validation**

- Executed the updated suite in `endless-runner-core-test` using the Core implementation copied into the temporary test project.
- Result: `PASS: SegmentSpawner tests completed successfully (221 assertions).`
- The user explicitly reported no errors.
- Coverage includes all previous configuration, sequence and placement cases plus invalid root transforms, marker orientation, marker scale, lateral/vertical offsets, longitudinal spacing, `segment_length` mismatch, singular transform diagnostics and rollback behavior.

**Scope and limitations**

- This subphase implements geometric validation only; it does not register placed segments with `WorldMovement`, recycle segments, perform procedural selection, assemble production tracks or integrate a production game scene.
- The Core repository does not contain a `project.godot` test project. The suite runs in `endless-runner-core-test`; only the test script is maintained in Core, while the technical test scene remains in the temporary project.
- No production artistic assets were required.
- Core `v0.2.0` remains the published release; this implementation is unreleased.


### Sprint 2.6.3.3.1 — SegmentSpawner / WorldMovement Registration

**Status: Implemented, tested and published**

**Objective**

Integrate `SegmentSpawner` with the existing `WorldMovement` registration API so every successfully placed segment is registered for longitudinal movement, regardless of whether world movement is currently active or stopped.

**Implementation**

- Updated `generation/spawning/segment_spawner.gd`.
- After a segment has been acquired, geometrically validated, placed under `WorldRoot` and its placement transform verified, `SegmentSpawner` registers it through `WorldMovement.register_segment()`.
- The registration step is applied to both `spawn_first_segment()` and `spawn_next_segment()`.
- Registration occurs before the segment is committed to the active-segment list, before the sequence advances and before `segment_spawned` is emitted.
- Registration is independent of the current movement-active state. A segment registered while movement is stopped is ready to move when the host starts `WorldMovement`; a segment registered while movement is active joins the existing movement set.
- If registration fails, the spawn operation is rolled back. The spawner checks whether registration took effect, unregisters when necessary, detaches the instance from `WorldRoot`, restores its pre-placement identity local transform and attempts to return it to `SegmentPool`.
- A failed registration does not advance the sequence, does not add the segment to the active list and does not emit `segment_spawned`.
- The existing `WorldMovement` implementation and public API were not modified. `SegmentPool` was not modified.
- Host ownership of `WorldMovement.start_movement()` and `stop_movement()` remains unchanged. `SegmentSpawner` does not start or stop world movement.

**Validation**

- Updated `tests/test_segment_spawner.gd` and executed it in the separate `endless-runner-core-test` Godot project using the Core implementation copied into that project.
- The complete suite passed: `PASS: SegmentSpawner tests completed successfully (256 assertions).`
- The user reported no errors in the Godot Output / Debugger result.
- The suite retained the previous 221 assertions and added 35 assertions for WorldMovement registration, movement-active and movement-stopped cases, movement of registered segments, registration during active movement, forced registration failure, rollback, sequence preservation, pool state and signal behavior.

**Scope and limitations**

- This subphase implements registration of successfully placed segments with `WorldMovement`.
- Segment removal, normal unregistration during recycling, returning active segments to the pool, automatic recycling and procedural segment selection remain future work.
- Rollback of a failed spawn includes unregistering a segment if registration was partially or fully applied.
- The Core repository does not contain a `project.godot` test project. The automated suite runs in `endless-runner-core-test`; the technical test scene remains in that temporary project.
- No production artistic assets or production game-scene integration were required for this technical validation.
- Core `v0.2.0` remains the published release. This implementation is unreleased until a later Core release is prepared.

### Sprint 2.6.3.3.2.1 — Individual Segment Despawn

**Status: Implemented, tested and published**

**Objective**

Implement the inverse lifecycle operation for one active segment: unregister it from `WorldMovement`, detach it from `WorldRoot`, restore its identity local transform and return it to `SegmentPool`.

**Implementation**

- Updated `generation/spawning/segment_spawner.gd` with `despawn_segment(segment: Node3D) -> bool`.
- Added `segment_despawned(segment: Node3D, definition: SegmentDefinition)`.
- The method rejects invalid, foreign or already-despawned segment references without changing the active state.
- A valid active segment is unregistered from `WorldMovement`, detached from its parent, reset to `Transform3D.IDENTITY` and passed to `SegmentPool.release()`.
- Active segment and definition tracking is removed only after the pool accepts the instance.
- The signal is emitted only after successful release.
- Despawn does not advance, rewind or reset `sequence_index`.
- If `SegmentPool.release()` fails, the spawner attempts rollback by restoring the original parent and transform and registering the segment again. Active tracking references are retained for the failed operation.
- The operation does not start or stop `WorldMovement` and is tested with the movement system active and stopped.
- `WorldMovement` and `SegmentPool` production implementations were not changed for this subphase.

**Validation**

- Expanded `tests/test_segment_spawner.gd` in the separate `endless-runner-core-test` project.
- Result: `PASS: SegmentSpawner tests completed successfully (317 assertions).`
- The user reported no errors.
- New test groups: individual segment despawn and pool return; `SegmentPool.release()` failure rollback during despawn.
- The complete suite includes all previous configuration, sequence, placement, geometry and WorldMovement registration tests.

**Scope and limitations**

- This subphase implements individual segment despawn. Bulk cleanup is implemented and validated in the following Sprint 2.6.3.3.2.2 entry.
- Automatic distance-based recycling, procedural segment selection and production-scene integration remain future work.
- The Core repository does not contain a `project.godot` test project. The suite runs in `endless-runner-core-test`; its technical test scene remains outside Core.
- No production artistic assets were required.
- Core `v0.2.0` remains the published release; this implementation is unreleased until a later Core release is prepared.

### Sprint 2.6.3.3.2.2 — Bulk Active-Segment Cleanup

**Status: Implemented and validated in the temporary Godot test project. Core and SANTA DASH repository publication is pending.**

**Objective**

Add `clear_active_segments() -> bool` to `SegmentSpawner` so the host can attempt to despawn every currently active segment through the established individual-despawn lifecycle.

**Implementation**

- Added `clear_active_segments() -> bool` to `generation/spawning/segment_spawner.gd`.
- The method takes a snapshot of the currently active segment references before iterating. Successful removals therefore do not invalidate or alter the collection being traversed.
- Each segment in the snapshot is processed through the existing `despawn_segment()` method. The bulk method does not duplicate the individual unregister, detach, transform-reset, pool-release, rollback or signal logic.
- Processing continues after an individual despawn failure. The method returns `false` if at least one despawn fails; otherwise it returns `true`.
- An empty active list is a successful no-op. Repeated calls after a successful clear also return `true`.
- Each successful individual despawn emits its existing `segment_despawned` signal. Failed individual despawns do not emit that success signal.
- The method preserves `sequence_index`, including when the clear is only partially successful. It does not call `reset_sequence()`.
- The method does not start or stop `WorldMovement`; it supports both active and stopped movement.
- After a successful clear, `spawn_first_segment()` can be called again without reconfiguring `SegmentSpawner`.
- `SegmentPool` and `WorldMovement` production implementations were not changed for this subphase.

**Validation**

- Updated `tests/test_segment_spawner.gd` and executed the complete suite in the separate `endless-runner-core-test` Godot project.
- Result: `PASS: SegmentSpawner tests completed successfully (354 assertions).`
- The user supplied the successful Godot Output result. No test errors were reported.
- The suite includes the previous configuration, sequence, placement, geometry, WorldMovement registration and individual-despawn cases.
- Bulk-cleanup coverage includes clearing multiple active segments while movement is stopped, clearing an empty list, repeated empty clears, spawning again after a successful clear, partial failure when a pool release is rejected, continued cleanup of the remaining snapshot entries, preservation of the sequence index, preservation of active WorldMovement state, and retrying the remaining segment.

**Scope and limitations**

- This subphase implements explicit bulk cleanup only. It does not add automatic distance-based recycling or decide when the host should clear segments.
- Procedural segment selection, production track assembly and production-scene integration remain future work.
- The Core repository does not contain a `project.godot` test project. The suite runs in `endless-runner-core-test`; its technical test scene remains outside Core.
- No production artistic assets were required.
- Core `v0.2.0` remains the published release. This implementation is validated in the working development state but has not yet been published as a new Core release.

### Sprint 2.6.3.3.3.1 — Recycle Reference and Candidate Detection

**Status: Implemented, validated and published.**

**Objective**

Provide a reusable, host-independent spatial reference for detecting when an active segment has moved sufficiently far behind the player.

**Implementation**

- Added `SegmentSpawner.bind_recycle_reference(reference: Node3D) -> bool`.
- Added `set_recycle_distance(distance: float) -> bool` and read-only `recycle_distance`, defaulting to 15.0 meters.
- Added `get_recyclable_segments() -> Array[Node3D]`, returning a snapshot of active segments whose `EntryPoint` has reached or passed the host reference plus the configured distance along `WorldRoot`-local +Z.
- The host supplies an external `Node3D`; Core does not depend on `PlayerMovement`, Santa or a concrete player class.
- Global positions are converted into `WorldRoot` local space. The player is not assumed to be at Z = 0.
- Detection does not despawn, unregister, reparent or move segments. It does not alter `sequence_index` or `WorldMovement`.
- Updated Core API, architecture and changelog documentation.

**Validation**

- The user executed the complete SegmentSpawner suite in `endless-runner-core-test`.
- Result: `PASS: SegmentSpawner tests completed successfully (394 assertions).`
- No test errors were reported.
- The suite included recycle-reference binding, non-zero player Z, translated parent coordinates, threshold boundaries, active/stopped movement and non-mutating candidate detection.

**Scope and limitations**

- This subphase implements reference binding and candidate detection only. Automatic despawn and segment replenishment remain future work.
- Core remains at published version `v0.2.0`; no release or submodule update was part of this subphase.

### Sprint 2.6.3.3.3.2 — Reverse-Side Segment Extension

**Status: Implemented, validated and published.**

**Objective**

Correct segment placement direction so the active track continues to extend ahead of the player while `WorldMovement` moves existing segments toward local +Z.

**Implementation**

- Revised `SegmentSpawner.spawn_next_segment()` to use the first active segment as the leading anchor.
- The new segment's `ExitPoint` is aligned with the leading active segment's `EntryPoint`. Its placement transform is calculated from the leading EntryPoint global transform and the inverse of the new segment's local ExitPoint transform.
- The new segment extends toward `WorldRoot`-local -Z. `WorldMovement` continues moving registered segments toward +Z; its implementation is unchanged.
- After successful placement and WorldMovement registration, the new segment and matching definition are inserted at index zero of the active arrays.
- Active arrays are now ordered from leading (-Z) to trailing (+Z). The oldest segment is at the last index.
- `get_recyclable_segments()` now iterates from the end of the active arrays so candidates are returned oldest/trailing-first.
- Updated alignment tests for ordinary segments and segments with a local EntryPoint offset.
- Updated recycle-detection tests to simulate +Z world movement and verify that the trailing segments become candidates in oldest-first order.
- Updated Core API, architecture and changelog documentation.

**Validation**

- The user executed the complete SegmentSpawner suite in `endless-runner-core-test`.
- Result: `PASS: SegmentSpawner tests completed successfully (402 assertions).`
- The initial 401/402 result exposed a test-coordinate-space error: the test read a marker's local `position.z` instead of converting its global position into `WorldRoot` local space. The test was corrected; production placement code was not changed for this correction.
- The corrected suite passed all 402 assertions with no reported errors.
- The user confirmed that the Core and SANTA DASH repository changes were committed and published.
- No new Core release or submodule update was part of this subphase.

**Scope and limitations**

- This subphase corrects segment placement direction and candidate ordering only.
- Automatic invocation of `despawn_segment()` was implemented and validated in the following Sprint 2.6.3.3.3.3 entry. Automatic replenishment remains future work.
- Core remains at published version `v0.2.0`; no new release or submodule update is included.

### Sprint 2.6.3.3.3.3 — Explicit Recyclable-Segment Despawning

**Status: Implemented, validated and published.**

**Objective**

Add an explicit `recycle_segments() -> int` operation to `SegmentSpawner`. The method processes the recyclable-segment candidates detected by `get_recyclable_segments()` and delegates each removal to the existing `despawn_segment()` lifecycle.

**Implementation**

- Added `recycle_segments() -> int` to `generation/spawning/segment_spawner.gd`.
- The method obtains a snapshot of recyclable candidates through `get_recyclable_segments()`.
- Candidates are processed in the order returned by the detection method: trailing/oldest segment first.
- Each candidate is processed through `despawn_segment()`. The recycling method does not duplicate unregistration, detachment, transform reset, pool release, rollback or success-signal behavior.
- The method continues processing the remaining candidates if an individual despawn fails.
- The return value is the number of segments successfully recycled; failed despawns are not counted.
- The operation preserves `sequence_index` and does not stop or start `WorldMovement`.
- Recycling is an explicit host-invoked operation. This subphase does not add a timer, `_process()` loop, movement callback or direct `GameFlowManager` dependency.
- No replacement segments are spawned by this method. Detection, despawn and replenishment remain separate responsibilities.
- Updated `tests/test_segment_spawner.gd`, `documentation/API_REFERENCE.md`, `documentation/ARCHITECTURE.md` and `documentation/CHANGELOG.md`.

**Validation**

- The user executed the complete SegmentSpawner suite in `endless-runner-core-test`.
- Result: `PASS: SegmentSpawner tests completed successfully (467 assertions).`
- The first run passed 466/467 assertions because the existing reverse-side recycle-detection test used a marker-local coordinate where a `WorldRoot`-local coordinate was required.
- The test was corrected to convert the marker's global position using `WorldRoot.to_local()`. No production code was changed for that test correction.
- The corrected complete suite passed all 467 assertions. No test errors were reported.
- The new test group, `explicit recyclable-segment despawning`, validates the explicit recycling operation alongside the existing configuration, sequence, placement, geometry, movement-registration, despawn, bulk-clear and candidate-detection coverage.

**Scope and limitations**

- This subphase implements explicit recycling only. It does not automatically decide when to call `recycle_segments()` and does not replenish the track with new segments.
- Automatic recycling/replenishment orchestration, procedural segment selection and production-scene integration remain future work.
- The Core repository does not contain a `project.godot` test project. The suite runs in `endless-runner-core-test`; its technical test scene remains outside Core.
- No production artistic assets were required.
- Core remains at published version `v0.2.0`; no new release or submodule update is included in this subphase.

### Sprint 2.6.3.3.4 — Minimum-Count Track Maintenance

**Status: Implemented; Godot validation and repository publication pending.**

**Objective**

Add an explicit `maintain_track() -> bool` operation to `SegmentSpawner`. It recycles eligible trailing segments while preserving at least one active segment, then replenishes the leading end until a configurable minimum active count is reached.

**Implementation**

- Added the read-only `minimum_active_segment_count` property, defaulting to `3`.
- Added `set_minimum_active_segment_count(count: int) -> bool`; values below `2` are rejected without changing the current setting.
- Added `maintain_track() -> bool` with preconditions for valid configuration, in-tree `WorldRoot`, `SegmentPool` and `WorldMovement`, a bound recycle reference, and at least one active segment.
- The host must create the initial segment with `spawn_first_segment()`; `maintain_track()` does not initialize an empty track.
- The method obtains the existing trailing-first recyclable candidate snapshot and calls `despawn_segment()` for each candidate while more than one active segment remains.
- It never removes the final active segment. It then calls `spawn_next_segment()` until the configured minimum is reached, extending the leading (`-Z`) end through the established marker-alignment and pooling path.
- The target is a minimum, not a maximum. Non-recyclable segments are not removed merely because the active count exceeds the target.
- Individual despawn failures do not prevent later safe candidates from being attempted. A spawn failure stops replenishment for that call.
- Successful partial work is retained; no cross-operation transaction is attempted. A later explicit call can retry from the consistent active state.
- The method returns `true` only when the target is reached and all attempted recycle/spawn operations succeed. It returns `false` if an operation fails or the target remains unmet.
- `maintain_track()` does not start or stop `WorldMovement`, reset or rewind `sequence_index`, use `_process()`, create a timer, or depend directly on `GameFlowManager`.
- Updated `generation/spawning/segment_spawner.gd`, `tests/test_segment_spawner.gd`, Core `API_REFERENCE.md`, `ARCHITECTURE.md` and `CHANGELOG.md`.

**Validation**

- Added 106 assertions covering minimum-count defaults and configuration, unconfigured/missing-reference/empty-track preconditions, initial fill, no-op maintenance, recycle order, final-segment protection, pool reuse, configurable minimum targets, active/stopped `WorldMovement`, release-failure rollback, partial progress, exhausted-pool spawn failure and retry.
- Expected complete SegmentSpawner suite total: 573 assertions (467 previously passing plus 106 new assertions).
- The updated suite has not yet been executed by the user in `endless-runner-core-test`; this sprint must remain unvalidated until Godot reports a full pass.
- No production artistic assets or SANTA DASH production-scene changes are required.

**Scope and limitations**

- This increment adds explicit track maintenance only. The host must decide when to call `maintain_track()`; automatic lifecycle invocation and production-scene wiring remain future work.
- Procedural segment selection and difficulty-aware spawn patterns are not included.
- Core remains at published version `v0.2.0`; no new release or submodule update is included.

### General Implementation Status

- No production artistic assets have been imported.
- Implemented Core systems: Game Flow Manager, Player Controller (including the Sprint 2.4.1 Input Buffer), LaneSystem, PlayerMovement (lateral movement, jump/fall/landing and slide physics), AnimationConfig, AnimationController, WorldMovement, SegmentDefinition, SegmentPool and SegmentSpawner configuration/sequence/placement/geometric validation, WorldMovement registration, individual despawn, bulk active-segment cleanup, recycle-reference candidate detection, reverse-side segment extension, explicit recyclable-segment despawning and minimum-count track maintenance.
- The Lane System implementation, tests and documentation are committed and pushed to the Core repository.
- Sprint 2.4.1 implementation and documentation are committed and pushed to the Core repository; the corresponding SANTA DASH development log is also committed and pushed.
- Sprint 2.4.2 implementation, tests, documentation and repository commits are complete.
- Sprint 2.4.3 jump/slide implementation, tests, documentation and repository commits are complete.
- Sprint 2.4.4 animation configuration, controller and landing-event integration, tests, documentation and repository commits are complete.
- Core v0.2.0 is published; both SANTA DASH and GENERIC RUNNER submodules point to `v0.2.0`.
- Sprint 2.5.1 WorldMovement is implemented and passed 67 assertions in the temporary test project; its implementation and documentation were committed and pushed.
- Sprint 2.5.2 host-side GameFlowManager / WorldMovement integration test passed 52 assertions with zero Debugger errors; its Core test and documentation commits have been pushed, as has the SANTA DASH development-log update.
- Sprint 2.5.3 multi-segment WorldMovement validation passed 37 assertions; documentation and repository changes were committed and pushed.
- Sprint 2.5.4 WorldMovement lifecycle validation passed 76 assertions with zero errors and zero warnings; documentation and repository changes were committed and pushed.
- Sprint 2.6.1 SegmentDefinition passed 24 assertions; implementation, test and documentation were committed and pushed. Both repositories were confirmed published and clean.
- Sprint 2.6.2 SegmentPool passed 81 assertions with no reported errors in the temporary test project. Implementation, test and documentation were committed and pushed; both repositories were confirmed published and clean.
- Sprint 2.6.3.1 SegmentSpawner configuration and cyclic sequence passed 53 assertions in the temporary test project. Implementation and documentation were published; both repositories were confirmed clean.
- Sprint 2.6.3.2.1 SegmentSpawner first-segment placement at the WorldRoot origin passed 117 assertions with no reported errors; implementation and documentation were published.
- Sprint 2.6.3.2.2.1 SegmentSpawner consecutive-segment placement passed 145 assertions in the temporary test project. Implementation and documentation were published.
- Sprint 2.6.3.2.2.2 SegmentSpawner geometric validation passed 221 assertions with no errors in the temporary test project. Implementation and documentation were published; both repositories were confirmed published.
- Sprint 2.6.3.3.1 SegmentSpawner / WorldMovement registration passed 256 assertions with no errors. Implementation and documentation were published in Core and Santa Dash.
- Sprint 2.6.3.3.2.1 individual segment despawn passed 317 assertions with no errors in the temporary test project. Implementation and documentation were published in Core and recorded in this development log.
- Sprint 2.6.3.3.2.2 bulk active-segment cleanup passed the complete SegmentSpawner suite with 354 assertions and no reported errors. Core implementation and documentation, plus this SANTA DASH development-log entry, were published.
- Sprint 2.6.3.3.3.1 recycle-reference detection passed the complete SegmentSpawner suite with 394 assertions and no reported errors; implementation and documentation were published.
- Sprint 2.6.3.3.3.2 reverse-side segment extension passed the complete SegmentSpawner suite with 402 assertions and no reported errors; Core and SANTA DASH repository changes were committed and published.
- Sprint 2.6.3.3.3.3 explicit recyclable-segment despawning passed the complete SegmentSpawner suite with 467 assertions and no reported errors; Core implementation, tests and documentation, plus the SANTA DASH development-log update, were committed and pushed.

---

## Development Rules

- Work incrementally.
- Validate each completed task.
- Do not assume unverified functionality.
- Record important architectural decisions.
- Keep documentation synchronized with implementation.
- Test all significant systems before marking them complete.

**End of document.**
