Create a complete, polished, playable browser game using Three.js: a short side-scrolling arcade brawler about a homeless man who searches dumpsters, collects bottles and trash, throws them at rival homeless characters, and fights with his fists.

Deliver the entire project as a single `index.html` file containing all HTML, CSS, and JavaScript. Use a CDN for Three.js. Generate all graphics procedurally: no external models, textures, images, audio files, or additional local files.

IMPORTANT SCOPE: Create exactly ONE short, carefully designed level lasting approximately 2–4 minutes. Focus on responsive controls, satisfying combat, readable graphics, and a complete gameplay loop. Do not create multiple levels, an open world, crafting, shops, or complicated progression systems.

GAME CONCEPT

The player controls a scruffy adult homeless man making his way through a neglected city alley toward a recycling collection point.

Along the way, the player must:
- Search dumpsters and garbage piles.
- Collect empty bottles and throwable trash.
- Fight hostile adult homeless rivals.
- Throw collected objects at enemies.
- Find alcoholic drinks that restore health.
- Defeat one tougher opponent near the exit.
- Reach the recycling point to complete the level.

Use a playful, exaggerated arcade tone with non-graphic combat. The game should feel like a compact, finished street brawler.

Use Russian for all visible interface text. The game title is “Помойный замес”.

VISUAL STYLE AND CAMERA

Create a 2D gameplay experience rendered with low-poly 3D geometry:
- Use an orthographic camera viewing the scene from the side.
- Movement and combat take place on a single horizontal gameplay plane.
- The player can move left and right and jump.
- Use depth only for visual layering, scenery, and the thickness of characters and props.
- Do not allow movement toward or away from the camera.
- Do not use OrbitControls or camera rotation.
- Let the camera smoothly follow the player horizontally, clamped to the level boundaries.

Use flat-shaded surfaces, angular silhouettes, solid colors, and a cohesive low-poly style. This must not look like pixel art or a collection of unconnected cubes.

Use muted brick red, dirty ochre, faded olive, charcoal, and concrete gray, with brighter accents for pickups and interactive objects.

Keep foreground characters clearly separated from the quieter background.

PLAYER CHARACTER

Create a recognizable full-body homeless man:
- A relatively large angular head.
- A protruding nose, visible eyes, heavy eyebrows, and an untidy gray-brown beard.
- A faded burgundy beanie.
- A worn brown jacket over a mustard sweater.
- Dark patched trousers.
- Large scuffed boots.
- Fingerless gloves.
- A small battered backpack.

Make the clothing visibly worn using geometric patches, uneven hems, contrasting scuffed areas, and broad angular folds.

Give the character connected shoulders, elbows, wrists, hips, and knees. Use logical joint pivots for animation.

Include distinct animations for:
- Idle breathing.
- Walking or running.
- Jumping and landing.
- Punching.
- Throwing.
- Searching a dumpster.
- Drinking a healing item.
- Taking damage.
- Defeat and victory.

The player must turn to face the direction of movement. Keep the face and held objects readable from the side.

CONTROLS

Use a simple keyboard layout:
- A / D or Left / Right arrows: move.
- Space: jump.
- J: punch.
- K: throw the currently selected object.
- Tab: switch between bottles and trash.
- E: search a nearby dumpster or garbage pile.
- Q: consume one alcoholic drink to restore health.
- R: restart after victory or defeat.

Prevent the browser’s default scrolling and focus behavior for game controls.

Display a compact Russian control hint at the beginning. Keep essential controls available in a small, unobtrusive help strip.

MOVEMENT AND PHYSICS

Make movement responsive, with modest acceleration and quick stopping.

Implement:
- Gravity and reliable ground collision.
- A short, controllable jump.
- Small jump buffering and coyote time.
- Solid level boundaries.
- A few low obstacles that can be jumped over.
- Stable collision against curbs, crates, and pavement.

Keep the level easy to navigate. Do not include pits, precision platforming, ladders, or complicated terrain.

COMBAT

The player has 100 maximum health.

Melee:
- Press J for a short forward punch.
- Deal approximately 18 damage.
- Use a brief wind-up, active hit window, and recovery.
- Check a directional hitbox in front of the player.
- Allow each attack to damage a particular enemy only once.
- Add a small amount of knockback and a clear hit reaction.
- Do not allow attacks to hit enemies behind the player.

Throwing:
- Press K to throw one item from the selected ammunition type.
- Empty bottles deal approximately 30 damage.
- Trash objects deal approximately 15 damage.
- Bottles travel farther; trash travels in a shorter, heavier arc.
- Spawn each projectile at the throwing hand during the release frame.
- Launch it in the direction the player is facing.
- Use gravity and a predictable trajectory.
- Remove the item from inventory only when it is actually released.
- Projectiles must collide with enemies and the ground.
- Prevent projectiles from hitting their owner.
- Use swept collision checks or sufficiently small physics steps to prevent tunneling.

On impact:
- Bottles break into a few short-lived angular fragments.
- Trash tumbles or produces a small dust puff.
- Add brief, restrained hit-stop and camera shake.
- Avoid blood, gore, and excessive flashing.

Give the player approximately 0.7 seconds of damage invulnerability after being hit. Communicate this with a subtle visual effect.

COLLECTING AND SEARCHING

Place five searchable objects across the level: a mixture of dumpsters, trash cans, and garbage piles.

When the player is within range:
- Show a small “E — Обыскать” prompt.
- Holding E fills a short search progress indicator over approximately one second.
- Releasing E, moving away, or taking damage cancels the search.
- Completing the search grants a small predetermined bundle of loot.
- Each container can be searched only once.
- Visually change searched containers and remove their interaction prompts.

Loot includes:
- Empty glass bottles used as stronger ammunition.
- Crushed cans or compact trash bundles used as weaker ammunition.
- Alcoholic drinks used as healing items.

Make loot briefly appear above the container before entering the inventory.

Use guaranteed loot distribution. The player must receive useful ammunition from the first dumpster and at least two healing drinks across the level.

Start the player with two bottles and three trash items so combat is immediately available.

Distinguish empty throwable bottles from healing drinks through color, shape, and interface icons.

ALCOHOL AND HEALTH

Alcoholic drinks are collectible arcade healing items.

Press Q to:
- Consume one drink from inventory.
- Play a brief drinking animation.
- Restore 30 health, capped at 100.
- Display a small green “+30” indicator, or the actual amount restored.

Do not consume a drink if health is already full.

Prevent the player from punching, throwing, or searching during the brief drinking animation.

Keep healing simple. Do not add intoxication systems, screen distortion, addiction mechanics, or other survival meters.

ENEMIES

Create four ordinary adult homeless rivals and one tougher final rival.

Give enemies distinct silhouettes and clothing colors:
- One thin rival in a faded blue coat.
- One stocky rival in an olive jacket.
- Other variations using different hats, beards, and clothing proportions.
- A larger final rival in a dark red coat.

Use two basic enemy behaviors:
- Brawlers approach the player and perform telegraphed melee attacks.
- Throwers maintain some distance and occasionally throw cans or bottles.

Implement simple, readable AI states:
- Idle or patrol.
- Notice the player.
- Approach or reposition.
- Wind up an attack.
- Attack.
- Recover.
- React to damage.
- Defeated.

Enemies should activate only when the player approaches their section of the level. Avoid overwhelming the player with every enemy at once.

Give ordinary enemies approximately 45–60 health and the final rival approximately 110 health.

Make enemy attacks visibly telegraphed and avoid unavoidable damage chains. Allow the player to interrupt ordinary attacks with a successful hit.

Defeated enemies should perform a short exaggerated fall or seated collapse, stop blocking movement, and drop a small amount of ammunition.

ONE SHORT LEVEL

Build one continuous alley approximately 45–55 world units long, divided into three connected areas:

1. Starting corner:
- A safe space to learn movement.
- The first searchable dumpster.
- One easy melee rival.
- Clear control hints.

2. Central alley:
- A few low crates and pavement obstacles.
- Three ordinary rivals spread across two small encounters.
- Additional searchable containers.
- At least one accessible healing drink.

3. Recycling point:
- The final searchable container.
- One tougher rival guarding the area.
- A simple recycling booth or machine with the sign “ПРИЁМ БУТЫЛОК”.
- A clearly marked completion zone.

Completing the level requires defeating the final rival and interacting with the recycling point.

Do not require a minimum number of remaining bottles. Spending ammunition must never make the level impossible to finish.

Award a small score bonus for unused bottles deposited at the end.

ENVIRONMENT

Create a compact, visually coherent urban setting:
- Pavement with visible thickness.
- A curb and a narrow strip of asphalt.
- Low-poly brick or concrete building facades.
- Recessed doors and a few windows.
- Dumpsters with hinged lids.
- Cardboard boxes, garbage bags, and scattered cans.
- Occasional weeds and a small puddle.

Keep scenery behind or below the gameplay plane. Avoid foreground objects that obscure attacks or pickups.

Use a few subtle ambient animations, such as a loose paper scrap moving in the breeze. Keep the background secondary.

INTERFACE AND GAME FLOW

Use a clean, minimal HUD showing:
- Health bar and numeric health.
- Empty bottle count.
- Trash ammunition count.
- Healing drink count.
- The selected ammunition type.

Show small enemy health bars only during combat or when enemies are damaged.

Include:
- A compact start overlay with the title, controls, and “Начать”.
- A defeat overlay with “Попробовать снова”.
- A victory overlay with completion time, defeated enemies, and bottles recycled.

Restart must reset the entire game state without reloading the page.

Do not add menus for levels, character selection, upgrades, or settings.

LIGHTING AND FEEDBACK

Use warm directional daylight with soft ambient fill.

Enable restrained shadows so characters and props feel grounded.

Make interactions satisfying with:
- Small pickup motions.
- Short damage flashes.
- Dust on landing.
- Bottle fragments.
- Clear attack wind-ups.
- Modest knockback.

If sound is included, generate short effects procedurally with Web Audio after the user starts the game. Do not load audio assets.

TECHNICAL REQUIREMENTS

- Everything must be contained in one `index.html`.
- Use a pinned Three.js version from a CDN.
- Use only procedural geometry and solid-color materials.
- Use an orthographic camera.
- Implement gameplay physics and collision directly in JavaScript.
- Use a fixed physics timestep with a capped frame delta.
- Keep animation frame-rate independent.
- Organize code into clear systems for input, characters, combat, projectiles, loot, level state, camera, and UI.
- Reuse geometries and materials where practical.
- Clean up projectiles, particles, and temporary objects.
- Support responsive resizing and a pixel-ratio limit of 2.
- Preserve a useful vertical gameplay view across different window sizes.
- Clear held inputs when the window loses focus.
- Avoid unbounded object creation or resource leaks.
- Render smoothly in a modern desktop browser.

IMPLEMENTATION ORDER

1. Build the single level, orthographic camera, movement, jumping, and collision.
2. Create the player model and core animations.
3. Implement melee attacks, projectiles, health, and damage feedback.
4. Add searchable containers, inventory, ammunition switching, and healing.
5. Add enemy models, AI, and the five planned opponents.
6. Implement the final objective, victory, defeat, and restart.
7. Add visual polish, ambient details, and optional procedural sounds.
8. Play through the entire level and verify all interactions.

Before finishing, verify that:
- The game has exactly one short, fully playable level.
- The player can move, jump, punch, throw, search, switch ammunition, and heal.
- Punches and projectiles hit enemies reliably.
- Enemies telegraph attacks and can be defeated.
- Loot cannot be collected repeatedly from the same container.
- Healing consumes exactly one drink and never exceeds maximum health.
- Throwable bottles and healing drinks remain separate inventory items.
- The level can still be completed after all ammunition is spent.
- The camera never reveals unfinished space outside the level.
- Victory, defeat, and restart work correctly.
- No mechanics are left as placeholders.

Return only the complete code for `index.html`, without explanations, placeholders, or omitted sections.