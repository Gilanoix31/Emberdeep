# Emberdeep

Emberdeep is a complete, free, offline pixel-art roguelike for Android. It is a turn-based, permadeath dungeon crawler with a 100-chapter campaign, endless mode, large-sprite battles, gear progression, passive builds, class evolutions, and cosmetic-only shard unlocks.

## Features

- Full 1.0.0 single-player release. No ads, no purchases, no account, and no online permission.
- Full-screen 1080p-adaptive Android layout with enlarged buttons, controls, and UI.
- Viewport-fitted menus and screens that avoid outer-page scrolling.
- Centered, height-fitted battle sequence with compact three-column move-set bars and short descriptions.
- Zoomed character-centered exploration with section labels and a full-floor minimap showing explored tiles, foes, loot, stairs, viewport, and current section.
- Translucent MOBA-style overlay with a large left analog joystick for smooth omnidirectional movement.
- Pokemon-inspired encounters: bumping a foe starts a large-sprite battle with intro, command, action, retaliation, victory, and defeat phases.
- Battle polish with class-specific skills, damage numbers, screen shake, animated backgrounds, and looping CC0 battle music.
- Music state persists between sessions and pauses/resumes correctly with app visibility.
- Three free classes: Warden, Ranger, and Arcanist, each with a distinct skill and five evolutions.
- Turn-based pacing: exploration tiles, attacks, skills, guard, potions, and waiting advance turns.
- Procedural dungeons, fog of war, scaling enemies, map modifiers, loot, leveling, and bosses every fifth floor.
- Named act guardians, boss heavy attacks, guaranteed boss gear, and relics that grant lasting run bonuses.
- Two modes: a 100-chapter story campaign across ten acts with objectives and checkpoints every five chapters, and an endless descent with no floor cap and deeper late-game scaling.
- Gear in five slots across seven rarities from Common to Ultimate, with equipment bonuses, enchantments, elemental synergies, and five scalable equipment sets.
- Unlimited forge enhancement with a chance that approaches zero but never reaches it, plus enchant rerolls that scale with item depth.
- A 24-node passive tree in four branches, two points per level, prerequisites, and shard-cost respec.
- Campaign checkpoints grant era-appropriate gear and previously earned act relics so late chapters remain viable.
- Permadeath runs with persistent shards. Shards buy cosmetics only; gear, XP, health, and floor skips are never sold.
- Cosmetic vault for hero skins, dungeon tile themes, hit effects, and crests. Every cosmetic costs shards.
- Local saves are normalized and versioned. Active battles resume with their current enemy state, and corruption is recovered safely.
- Hardware Back and Escape dismiss overlays, return from menus, and back out of battle submenus without softlocking.
- Keyboard and touch controls, focus-visible keyboard styling, potion and inventory caps, and storage-failure notices.

## Download

Sideload the v1.0.0 debug APK from https://github.com/Gilanoix31/Emberdeep/releases/tag/v1.0.0

## Run in a browser

```bash
npm start
```

Open `http://localhost:8080`. No build step is needed for the web assets.

## Build for Android

Requires Node 22+, JDK 17, Android SDK platform 34, and Android Studio.

```bash
npm install
npm run android:add
npm run android:sync
npm run android:open
```

For release APKs from the command line:

```bash
cd android
npm run android:sync
ANDROID_HOME=/opt/android-sdk ANDROID_SDK_ROOT=/opt/android-sdk ./gradlew assembleDebug --no-daemon
cp app/build/outputs/apk/debug/app-debug.apk /emberdeep-debug.apk
sha256sum /emberdeep-debug.apk
```

Capacitor loads the contents of `www/`, so any browser change requires a sync before building.

## Controls

| Action | Touch | Keyboard |
| --- | --- | --- |
| Explore current section | Large left-side analog joystick | Arrows or WASD |
| View whole floor | On-screen minimap | - |
| Pick up nearby item | A button | E |
| Quick bag | BAG button | - |
| Battle choice | Tap FIGHT / MOVES / GUARD / ITEM | Arrows plus Space or Enter |
| Class skill | Tap MOVES, then the skill | K |
| Guard | Tap GUARD | G |
| Drink potion | Tap BAG, then POTION, or ITEM in battle | P |
| Toggle sound | SOUND button | - |
| Menu | MENU | Escape |
| Back / close overlay | Device Back | Escape |

Campaign objectives must be completed before the stairs will open. Potions cap at nine. The cosmetic vault is always free and shard-only.

## Asset credits

- Hero and monster sprites: **Tiny Creatures** by Clint Bellanger, CC0, https://opengameart.org/content/tiny-creatures
- Dungeon tiles and battle backdrops: **Tiny Dungeon** by Kenney, CC0, https://opengameart.org/content/tiny-dungeon
- Battle loop: **Chiptune Battle Music** by Alex Jaffe, CC0, https://opengameart.org/content/chiptune-battle-music

## Project layout

- `www/index.html` - screens, HUD, full-screen stage, minimap, overlaid touch controls, battle overlay
- `www/style.css` - responsive glass UI, joystick, action button, bag wheel, minimap, battle layouts
- `www/js/data.js` - sprites, classes, enemies, relic effects, cosmetics, themes, battle skies
- `www/js/assets.js` - CC0 sprite sheet loading and frame mapping
- `www/js/audio.js` - looping battle music controller with persistence and visibility handling
- `www/js/story.js` - campaign acts, 100 chapter beats, objectives, checkpoint scaling
- `www/js/progression.js` - rarities, bonuses, sets, enchantments, passive tree, evolutions, derived stats
- `www/js/dungeon.js` - generation, map modifiers, scaling, field of view, line of sight
- `www/js/game.js` - run state, combat, battle sequence, progression, persistence
- `www/js/render.js` - zoomed section camera, minimap, and large-sprite battle rendering
- `www/js/ui.js` - screens, HUD, joystick, interaction prompt, bag wheel, battle controls, shop
- `www/js/main.js` - bootstrap, resize handling, and animation frame loop
- `tests/smoke.js` - 147-check headless smoke suite

## Checks

```bash
npm run verify
```

`npm run verify` runs syntax checks and the headless smoke suite.

## APK checksum

v1.0.0 debug SHA-256: `f8a3de690b8fe71accfa02abc317dff01c50873a0b5fba1a3317327b2c9760b4`
