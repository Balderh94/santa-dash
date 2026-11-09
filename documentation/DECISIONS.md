# SANTA DASH — Decision Log

**Project:** SANTA DASH  
**Status:** Active  
**Last updated:** 2026-11-09

---

## Decision 001 — Game Engine

**Decision:** Use Godot 4.7.2-stable.

**Reason:** Provides the required 3D, mobile and scripting capabilities.

**Status:** Approved.

## Decision 002 — Programming Language

**Decision:** Use typed GDScript.

**Reason:** Maintain readable, maintainable and type-safe gameplay code.

**Status:** Approved.

## Decision 003 — Rendering

**Decision:** Use Godot Mobile Renderer.

**Reason:** Target Android and iOS devices with controlled rendering costs.

**Status:** Approved.

## Decision 004 — Gameplay Orientation

**Decision:** Portrait orientation.

**Reference resolution:** 1080 × 1920.

**Window override:** 540 × 960.

**Status:** Approved.

## Decision 005 — Movement Architecture

**Decision:** The world moves toward the player while the player maintains a fixed forward gameplay position.

**Reason:** Simplifies endless track recycling and generation.

**Status:** Approved.

## Decision 006 — Lane System

**Decision:** Three lanes.

- Left: X = -2 m.
- Center: X = 0 m.
- Right: X = 2 m.

**Initial transition duration:** 0.18 seconds.

**Status:** Approved, subject to gameplay validation.

## Decision 007 — Camera

**Decision:** Elevated third-person camera.

Initial values:

- X = 0 m.
- Y = 5.5 m.
- Z = 8 m.
- FOV = 65 degrees.

**Status:** Approved as provisional values.

## Decision 008 — Jump and Slide

**Decision:** Swipe-based jumping and sliding.

**Status:** Approved.

## Decision 009 — Procedural Generation

**Decision:** Hybrid generation using artist-authored segments and runtime combination.

**Status:** Approved.

## Decision 010 — Worlds

**Decision:** Four independent worlds.

- Christmas Village.
- Toy Factory.
- Frozen Forest.
- Candy Kingdom.

**Status:** Approved.

## Decision 011 — Visual Style

**Decision:** Low Poly Cartoon with polished 3D cartoon finishing.

**Status:** Approved.

## Decision 012 — Character Design

**Decision:** Exaggerated cartoon proportions with large heads and compact bodies.

**Status:** Approved.

## Decision 013 — Character Geometry

**Decision:** Initial playable character polygon budget of approximately 8,000–15,000 triangles.

**Status:** Approved as a target.

## Decision 014 — Materials

**Decision:** Hybrid material workflow with solid colors and selective textures.

**Status:** Approved.

## Decision 015 — Animation Architecture

**Decision:** Gameplay logic and animation playback must remain independent.

**Status:** Approved.

## Decision 016 — User Interface

**Decision:** Reference resolution of 1080 × 1920, responsive to mobile aspect ratios and safe areas.

**Status:** Approved.

## Decision 017 — Performance

**Decision:** Target 60 FPS on supported mid-range mobile hardware.

**Status:** Approved as a target.

## Decision 018 — Monetization

**Decision:** Free-to-play with optional advertising and in-app purchases.

Initial features:

- Rewarded advertisements.
- Controlled interstitial advertisements.
- Remove-ads purchase.
- Premium currency packs.
- Cosmetic packs.

**Status:** Approved.

## Decision 019 — Persistence

**Decision:** Initial local persistence using Godot user:// storage.

**Status:** Approved.

## Decision 020 — Characters

**Decision:** Six initial playable characters.

- Santa.
- Elf.
- Snowman.
- Rudolph.
- Krampus.
- Gingerbread Man.

**Status:** Approved.

## Decision 021 — Power-ups

**Decision:** Five initial power-ups.

- Magic Magnet.
- Shield.
- Magic Boots.
- Santa's Sleigh.
- Score Multiplier.

**Status:** Approved.

## Decision 022 — Mission System

**Decision:** Daily and weekly missions.

**Status:** Approved.

## Decision 023 — Localization

**Decision:** Spanish, English and Catalan.

Translation resources will use CSV.

**Status:** Approved.

## Decision 024 — Asset Pipeline

**Decision:** Blender → GLB → Godot.

**Status:** Approved.

## Decision 025 — Audio

**Decision:** Use licensed external audio libraries.

**Status:** Approved.

## Decision 026 — Visual Effects

**Decision:** Controlled cartoon visual effects optimized for mobile devices.

**Status:** Approved.

## Decision 027 — Shared Core

**Decision:** Maintain three independent repositories:

- Endless Runner Core.
- SANTA DASH.
- GENERIC RUNNER.

**Status:** Approved.

## Decision 028 — Core Distribution

**Decision:** Distribute Endless Runner Core as a Git Submodule.

The plugin root is the repository root and is integrated under:

`addons/endless_runner_core/`

**Status:** Approved.

## Decision 029 — Core Instantiation

**Decision:** Instantiate Core systems through scenes and nodes owned by the host game.

Do not use Autoload for primary gameplay systems.

**Status:** Approved.

## Decision 030 — System Communication

**Decision:** Use a hybrid communication model.

- Signals for events.
- Direct method calls for explicit operations.

**Status:** Approved.

## Decision 031 — Configuration

**Decision:** Use Godot Resource objects for gameplay configuration.

**Status:** Approved.

## Decision 032 — Naming Conventions

**Decision:** Use English for code, filenames, folders, classes, nodes, variables and functions.

Use ASCII-compatible identifiers.

Documentation and development communication remain in Spanish.

**Status:** Approved.

---

## Change Management

Significant changes must include:

- Decision identifier.
- Description.
- Reason.
- Impact.
- Approval status.

Previously approved decisions must not be silently replaced.

**End of document.**