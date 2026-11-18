# Emberdeep

A pixel-art, turn-based, permadeath roguelike designed for Android. Descend floor by floor, die, and spend the soul shards you carried out on cosmetics only.

## Features

- Full-screen 1080p-adaptive Android layout with enlarged buttons, controls, and UI for easy viewing on a phone.
- Viewport-fitted main menu and screens that scale to the device and avoid outer-page scrolling.
- Battle sequence centered on screen and sized to fit the available height, with compact move-set bars and short move descriptions.
- Map pinned in the upper right below the SOUND and MENU buttons, with FORGE, TREE, and GEAR controls grouped in the lower middle.
- Zoomed character-centered view that explores the dungeon one labeled section at a time.
- On-screen map overview with explored tiles, section grid, current section highlight, viewport, foes, loot, stairs, and player marker.
- Translucent MOBA-style control overlay with a large left analog joystick for smooth, omnidirectional Zelda-style exploration.
- Touch battle panel with enlarged command choices, a class move-set picker, and an item picker for Pokemon-style encounters.
- Large right-side interaction button and quick bag wheel for pickups, potions, forge, passive tree, character, and cosmetics.
- Pokemon-inspired encounter flow: bumping a foe starts a large-sprite battle sequence with intro, command, action, retaliation, and victory phases, and looping CC0 battle BGM.
- CC0 pixel art from Kenney's Tiny Dungeon and Clint Bellanger's Tiny Creatures packs for heroes, monsters, and battle backdrops, with a brightened lively color grade.
- Turn-based pacing: every tile crossed during free movement, battle command, skill, guard, potion, or wait advances one turn.
- Three free classes (Warden, Ranger, Arcanist) with distinct skills. No class is locked or paid.
- Procedural dungeons, fog of war, scaling enemies, loot, leveling, and a boss every fifth floor.
- Two modes: a 100-chapter campaign across ten acts with story panels, objectives, and checkpoints every five chapters, and an endless descent with no floor cap.
- Procedural map modifiers (Swarm Warrens, Lost Vault, Endless Labyrinth, Open Cavern, Cursed Depths, Mirror Halls) reroll on every floor.
- Gear in five slots (weapon, armor, helm, boots, trinket) across seven rarities from Common to Ultimate. Ultimate has a tiny drop weight that rises slightly with depth and never becomes common.
- Randomized equipment bonuses reroll alongside enchantments, with extra bonus rolls in endless mode.
- Unlimited enhancement: every successful forge step raises a piece by +1, with a chance that approaches zero as the level grows but never reaches it.
- Enchantments with elemental synergies when matching elements are equipped together.
- Five equipment sets whose bonuses scale with the rarity of the equipped pieces.
- A 24-node passive tree in four branches, two points per level, with prerequisites and a shard-cost respec.
- Five class evolutions gated by level, passive-tree build, and kills, with distinct promotion names per class.
- Permadeath runs with persistent soul shards. Only appearance unlocks survive death; gear does not.
- Cosmetic vault for hero skins, dungeon tile themes, hit effects, and crests.
- Currency packs are demo-only and grant gems that can buy cosmetics exclusively. No stat, gear, or power purchase exists anywhere in the game.
- Large analog joystick, overlay touch controls, plus keyboard controls, responsive pixel-perfect canvas up to 1080p, on-screen minimap, local save of meta progress and active run.

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

In Android Studio, choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**. For later changes run `npm run android:sync` again.

Capacitor loads the contents of `www/`, so any browser change is picked up by a sync.

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

The title screen lets you choose CAMPAIGN or ENDLESS before starting. The FORGE, TREE, and GEAR buttons in the lower middle open the gear, passive-tree, and evolution screens. Campaign objectives must be completed before the stairs will open.

The camera stays zoomed in on your character and the current labeled section of the whole map. The on-screen minimap shows explored tiles, nearby foes and loot, stairs, the current viewport, and a gold outline around the active section. Push the joystick in any direction to move freely, including diagonals. Bumping an enemy starts a Pokemon-style battle with a large sprite sequence. Use the touch panel to choose an action, open your class move set, or open items. Stand near an item and press A to pick it up; BAG opens the right-side quick wheel. Stepping on `>` descends.

## Asset credits

- Hero and monster sprites: **Tiny Creatures** by Clint Bellanger, CC0, https://opengameart.org/content/tiny-creatures
- Dungeon tiles and battle backdrops: **Tiny Dungeon** by Kenney, CC0, https://opengameart.org/content/tiny-dungeon
- Battle loop: **Chiptune Battle Music** by Alex Jaffe, CC0, https://opengameart.org/content/chiptune-battle-music

## Monetization notes

`showGemModal()` in `www/js/ui.js` is an offline demonstration of a currency purchase. Replace it with a real billing plugin (for example `@capacitor-community/in-app-purchases`) and grant gems from your server-verified purchase callback. All shop entries come from `COSMETICS` in `www/js/data.js` and only change `palette`, `theme`, `fx`, or `badge`. There is no code path that sells attack, defense, health, gear, xp, or floor skips.

## Project layout

- `www/index.html` - screens, HUD, full-screen stage, minimap, overlaid touch controls, battle overlay
- `www/style.css` - enlarged responsive glass UI with translucent joystick, action button, bag wheel, minimap, and battle layouts
- `www/js/data.js` - sprites, classes, enemies, cosmetics, themes, battle skies
- `www/js/assets.js` - CC0 sprite sheet loading and frame mapping
- `www/js/audio.js` - looping battle music controller
- `www/js/story.js` - campaign acts, 100 chapter beats, objectives, checkpoint level scaling
- `www/js/progression.js` - rarities, bonuses, sets, enchantments, passive tree, evolutions, derived stats
- `www/js/dungeon.js` - generation, map modifiers, scaling, field of view, line of sight
- `www/js/game.js` - run state, combat, battle sequence, progression, persistence
- `www/js/render.js` - adaptive zoomed section camera, minimap, and large-sprite battle rendering
- `www/js/ui.js` - screens, HUD, joystick, interaction prompt, bag wheel, battle controls, shop
- `www/js/main.js` - bootstrap, resize handling, and battle animation loop
- `www/assets/art/` - CC0 sprite sheets
- `www/assets/audio/` - CC0 battle loop

## APK checksum

v0.2.4.1 debug SHA-256: `422d1d5dd1d93606a963f1aff9781459da13741914848451d1600fb8835b4167`

## Checks

```bash
npm run check
node /tmp/opencode/smoke.js
```
