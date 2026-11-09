# SANTA DASH — Game Design Document

**Document version:** 1.0  
**Status:** Initial approved game design  
**Genre:** 3D Endless Runner  
**Platform:** Android and iOS  
**Orientation:** Portrait  
**Business model:** Free-to-play  
**Visual style:** Low Poly Cartoon / Polished 3D Cartoon

---

# 1. Game Overview

## 1.1 Concept

SANTA DASH is a 3D endless runner in which Santa Claus must recover the Christmas presents stolen by Krampus.

The player controls Santa as he runs through different Christmas-themed environments, avoiding obstacles, collecting coins, activating power-ups and recovering stolen presents.

The game combines endless runner mechanics with missions, character collection, world progression and a lightweight economy.

## 1.2 Game Vision

Create an accessible, visually appealing and entertaining mobile endless runner suitable for short play sessions.

The game should offer:

- Simple controls.
- Responsive movement.
- Increasing difficulty.
- Varied environments.
- Collectible characters.
- Progression and unlockable content.
- Replayability.
- Optional monetization.

## 1.3 Core Experience

The player should feel:

- Fast and responsive movement.
- Clear anticipation of obstacles.
- Satisfaction when collecting rewards.
- Excitement from narrowly avoiding obstacles.
- Motivation to improve personal records.
- Progression through characters and worlds.

# 2. Story and Theme

## 2.1 Story

Krampus has stolen Christmas presents and scattered them throughout several magical environments.

Santa must recover them before Christmas is ruined.

During his journey, Santa encounters obstacles, collects coins and discovers magical power-ups.

The narrative provides context and personality without interrupting the endless runner gameplay.

## 2.2 Tone

The game uses a family-friendly tone.

Krampus is mischievous and intimidating but not excessively frightening.

Characters use expressive cartoon animations and humorous visual reactions.

# 3. Target Audience

The intended audience includes:

- Children.
- Teenagers.
- Adults.
- Casual mobile players.
- Fans of Christmas-themed games.

The experience must remain accessible to players with different levels of gaming experience.

Controls must be simple and gameplay sessions must be suitable for mobile use.

# 4. Core Gameplay Loop

The main gameplay loop is:

1. Select a character and world.
2. Start a run.
3. Avoid obstacles.
4. Collect coins and other rewards.
5. Activate power-ups.
6. Complete mission objectives.
7. Reach the end of the run through collision or voluntary abandonment.
8. Review score and rewards.
9. Improve progression.
10. Start another run.

The gameplay must encourage replayability through score improvement, missions and unlockable content.

# 5. Game Controls

## 5.1 Movement

Santa runs automatically.

The player does not control forward movement directly.

The world moves toward the player.

## 5.2 Lane System

The track contains three lanes:

- Left.
- Center.
- Right.

Initial provisional lane centers:

- X = -2 m.
- X = 0 m.
- X = 2 m.

Lane changes use responsive interpolation.

Initial transition duration: 0.18 seconds.

Consecutive lane changes are permitted when gameplay conditions allow them.

## 5.3 Jump

The player performs a jump using an upward swipe.

Jumping is used to avoid ground obstacles and interact with gameplay patterns.

## 5.4 Slide

The player performs a slide using a downward swipe.

Sliding is used to avoid elevated obstacles.

## 5.5 Input Mapping

Initial development keyboard controls:

| Action | Keyboard |
|---|---|
| Move left | Left Arrow / A |
| Move right | Right Arrow / D |
| Jump | Up Arrow / W |
| Slide | Down Arrow / S |

The production mobile controls use touch gestures.

# 6. Player Characters

The game includes six playable characters.

## 6.1 Santa Claus

<badge color="success">Initial character</badge>

The default playable character.

Visual identity:

- Red Christmas suit.
- White beard.
- Santa hat.
- Black belt with golden buckle.
- Black boots.
- Gloves.
- Rounded body proportions.
- Friendly appearance.

Santa is the initial character available to all players.

## 6.2 Elf

A Christmas elf with a playful appearance.

Unlock method: Gold coins.

## 6.3 Snowman

A friendly snowman character.

Unlock method: Gold coins.

## 6.4 Rudolph

A quadrupedal reindeer character.

Unlock method: Missions or special challenges.

## 6.5 Krampus

A larger and more imposing character with stylized dark fur and large horns.

Unlock method: Special challenge.

## 6.6 Gingerbread Man

A stylized gingerbread character.

Unlock method: Gold coins or optional purchase pack.

## 6.7 Character Affinities

Characters provide small bonuses affecting the appearance probability of certain items.

The bonuses must remain modest.

Initial example:

- Base appearance probability: 20%.
- Character affinity: 25%.

The probability distribution must be normalized to prevent bonuses from unintentionally increasing the total probability of all items.

Character selection must not create significant competitive advantages or pay-to-win mechanics.

# 7. Worlds and Environments

The game contains four worlds.

Only one world is active during a run.

## 7.1 Christmas Village

<badge color="success">Starting world</badge>

A festive Christmas village with warm lighting and seasonal decorations.

Visual characteristics:

- Snow-covered buildings.
- Christmas decorations.
- Warm festive colors.
- Snowfall.
- Christmas atmosphere.

## 7.2 Toy Factory

A magical toy production environment.

Visual characteristics:

- Colorful machinery.
- Toy production areas.
- Bright magical lighting.
- Steam effects.
- Playful industrial decorations.

## 7.3 Frozen Forest

A cold winter forest.

Visual characteristics:

- Frozen trees.
- Snow and ice.
- Blue-toned lighting.
- Ice particles.
- Cold atmospheric effects.

## 7.4 Candy Kingdom

A colorful magical candy environment.

Visual characteristics:

- Candy structures.
- Sweet-themed decorations.
- Warm and bright colors.
- Magical dust.
- Fantasy atmosphere.

## 7.5 World Progression

Worlds unlock progressively through distance, missions and player progression.

Previously unlocked worlds remain available.

# 8. Obstacles and Procedural Generation

## 8.1 Generation Model

The game uses hybrid procedural generation.

Artist-created track segments and obstacle patterns are combined at runtime.

The system controls:

- Segment selection.
- Obstacle distribution.
- Collectible placement.
- Power-up placement.
- Difficulty progression.

## 8.2 Obstacle Rules

Obstacle patterns must always be fair and avoid impossible combinations.

Generation must consider:

- Available lanes.
- Jump requirements.
- Slide requirements.
- Player movement time.
- Recovery distances.
- Current gameplay speed.
- Difficulty level.

The player must always have a valid route through the generated track.

## 8.3 Track Dimensions

Initial design values:

- Total track width: 6 m.
- Lane width: 2 m.
- Segment length: 30 m.

These values are provisional and must be validated with the final character and environment models.

# 9. Collectibles

The game uses two currencies.

## 9.1 Gold Coins

The primary free currency.

Used for:

- Character unlocks.
- Cosmetic items.
- Other progression rewards.

## 9.2 Premium Gems

The premium currency.

Used for optional premium content and purchases.

Premium currency must not be mandatory to complete the main gameplay progression.

# 10. Power-ups

Power-ups activate automatically when collected.

Each power-up has a limited duration.

## 10.1 Magic Magnet

Attracts nearby collectibles toward the player.

## 10.2 Shield

Protects the player against one qualifying collision.

## 10.3 Magic Boots

Enhance jumping capabilities.

## 10.4 Santa's Sleigh

Activates a temporary protected gameplay mode.

## 10.5 Score Multiplier

Increases score accumulation for a limited period.

Power-ups must have independent gameplay logic and configurable durations.

The HUD must communicate active effects and remaining duration.

# 11. Scoring System

Score is calculated using multiple gameplay factors:

- Distance traveled.
- Coins collected.
- Obstacles avoided.
- Special gameplay actions.

Score and currency are separate systems.

The game records:

- Current score.
- Best score.
- Distance traveled.
- Currency collected.
- Run statistics.

# 12. Difficulty Progression

Difficulty increases progressively throughout a run.

The system may adjust:

- World movement speed.
- Obstacle frequency.
- Obstacle complexity.
- Pattern combinations.
- Recovery distances.
- Collectible distribution.

Difficulty must remain fair.

The generation system must never create unavoidable obstacle combinations.

# 13. Missions and Objectives

## 13.1 Daily Missions

Daily missions reset every 24 hours.

They provide objectives and rewards that encourage regular play.

## 13.2 Weekly Missions

Weekly missions accumulate progress over multiple sessions.

They provide longer-term objectives.

## 13.3 Achievements

Achievements are planned for a future development phase.

They are not part of the initial implementation scope.

# 14. Character and World Progression

Character unlocking uses a combination of:

- Gold coins.
- Missions.
- Special challenges.
- Optional purchase packs.

World unlocking uses:

- Distance progression.
- Mission completion.
- General player progression.

Progression must remain accessible without mandatory purchases.

# 15. Economy

The economy contains:

- Gold coins.
- Premium gems.
- Character unlock costs.
- Cosmetic items.
- Mission rewards.
- World progression rewards.

The economy must be balanced to encourage continued play without creating excessive grinding.

The game must distinguish earned rewards from purchased currency.

# 16. Main Menu

The main menu is integrated into a 3D environment.

Santa appears centrally with an animated idle presentation.

The interface includes:

- Play.
- Character selection.
- Shop.
- Missions.
- Currency balances.
- Settings.

The menu environment may use subtle camera movement and ambient character animations.

# 17. Character Selection

Characters are presented using a 3D carousel.

The player can:

- Browse available characters.
- Preview character animations.
- Inspect unlock conditions.
- Select unlocked characters.
- Access relevant purchase or progression options.

# 18. Gameplay HUD

The HUD must display relevant gameplay information:

- Current score.
- Distance.
- Gold coins.
- Active power-ups.
- Power-up duration.
- Relevant mission progress.

The interface must not obstruct obstacle visibility.

# 19. Pause and Game Over

## 19.1 Pause

The player can pause the run through the interface.

Gameplay systems must stop or suspend appropriately.

## 19.2 Game Over

The results screen displays:

- Final score.
- Distance.
- Coins collected.
- Best score status.
- Mission progress.
- Applicable bonuses.

Available actions:

- Retry.
- Return to menu.

## 19.3 Record Achievement

When a new personal record is achieved, the interface provides a special visual presentation.

# 20. Collision and Continuation

When a qualifying collision occurs:

1. Check whether a shield is active.
2. If a shield is active, consume it and protect the player.
3. Otherwise, end the run.
4. Present the results screen.

One optional rewarded-ad continuation may be offered per run.

After a successful rewarded advertisement:

- Preserve current score.
- Preserve current distance.
- Resume gameplay.
- Apply temporary invulnerability.

Voluntarily abandoning a run must not offer a continuation.

# 21. Monetization

SANTA DASH follows a free-to-play model.

Initial monetization features:

- Optional rewarded advertisements.
- Controlled interstitial advertisements.
- Remove-ads purchase.
- Premium currency packs.
- Cosmetic purchase packs.

Rewarded advertisements must be voluntary.

Interstitial advertisements must be carefully controlled and must not interrupt active gameplay.

Purchases must not be required for core progression.

Monetization must comply with applicable privacy, advertising, consumer protection and platform policies.

# 22. Audio Design

Audio uses a straightforward arcade-oriented approach.

Required audio categories:

- Main music loop.
- Coin collection.
- Jump.
- Slide.
- Collision.
- Power-up activation.
- Interface interactions.
- Optional environmental ambience.

Music and sound effects have independent volume controls.

Audio resources may be obtained from external libraries, provided their licenses permit the intended commercial use.

# 23. Visual Effects

The visual effects style is polished cartoon.

Planned effects:

- Snow.
- Steam.
- Ice particles.
- Magical dust.
- Collection sparkles.
- Power-up activation.
- Collision effects.
- Temporary protection effects.

Effects must remain visually clear and performance-conscious.

# 24. Accessibility and User Experience

The game must prioritize:

- Simple controls.
- Clear obstacle readability.
- Responsive input.
- Short gameplay sessions.
- Legible interface elements.
- Adjustable audio levels.
- Adaptation to different screen ratios.
- Mobile safe areas.

# 25. Localization

Initial languages:

- Spanish.
- English.
- Catalan.

The game detects the device language automatically.

Players may change language manually through settings.

Translation data will use CSV resources.

# 26. Initial Release Scope

The initial release should prioritize a complete and stable gameplay experience.

Core release content:

- Santa as the initial playable character.
- Christmas Village as the initial world.
- Three-lane movement.
- Jump and slide.
- Obstacles and collectibles.
- Initial power-ups.
- Procedural segment generation.
- Score and distance tracking.
- Game over and recovery.
- Local persistence.
- Basic progression.
- Main menu.
- Gameplay HUD.
- Basic audio.
- Localization framework.
- Initial monetization integration.

Additional characters, worlds, missions and commercial content will be introduced according to development priorities.

# 27. Future Expansion

Potential future additions:

- More characters.
- More worlds.
- Additional obstacles.
- Additional power-ups.
- Achievements.
- Seasonal events.
- Additional missions.
- Cosmetic collections.
- Cloud synchronization.
- Additional languages.
- Additional monetization products.

These features must not compromise the stability of the initial release.

---

**End of document.**