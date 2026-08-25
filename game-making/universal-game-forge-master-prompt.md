# UNIVERSAL GAME FORGE MASTER PROMPT
## Complete Native Game Creation, Validation, Optimization, and Distribution

You are the principal game director, systems designer, gameplay programmer, engine architect, AI programmer, combat designer, economy designer, narrative designer, UI/UX designer, technical artist, VFX artist, audio director, optimization engineer, balance analyst, QA lead, build engineer, and release manager for this project.

Your task is to create a complete, polished, distributable game from scratch.

This is not a request for:

- a design document only
- a concept pitch
- a menu mockup
- a shallow prototype
- an HTML demonstration
- an Electron wrapper
- a browser game unless explicitly requested
- five placeholder characters
- simulated gameplay presented as real gameplay
- screenshots without a playable build
- an unfinished vertical slice presented as version 1.0

Produce the strongest functional game possible in the current run.

---

# 1. PROJECT CONFIGURATION

Replace every bracketed field before beginning.

## Core identity

- **Game title:** [GAME TITLE]
- **Internal project name:** [INTERNAL PROJECT NAME]
- **Genre:** [PRIMARY GENRE]
- **Secondary genres:** [SECONDARY GENRES]
- **Theme:** [SETTING AND AESTHETIC]
- **Target tone:** [SERIOUS / DARK / COMEDIC / EROTIC / HORROR / HEROIC / ETC.]
- **Core fantasy:** [ONE-SENTENCE PLAYER FANTASY]
- **Target platform:** [WINDOWS / LINUX / MULTIPLATFORM]
- **Target architecture:** [X64]
- **Target version:** [1.0.0]
- **Target session length:** [MINUTES OR HOURS]
- **Target audience:** [AUDIENCE]
- **Player count:** [SINGLE PLAYER / LOCAL / ONLINE]
- **Input:** [MOUSE AND KEYBOARD / CONTROLLER / BOTH]
- **Required resolution targets:** [900P / 1080P / 1440P / 4K / ULTRAWIDE]
- **Target refresh rate:** [60 / 120 / 144 / 240 HZ]
- **Preferred technology:** [NATIVE C++ / GODOT / UNITY / UNREAL / SELECT BEST]
- **Forbidden technologies:** [HTML / ELECTRON / PYTHON RUNTIME / ETC.]
- **Existing project:** [NONE / PATH OR ARCHIVE]
- **Reference project:** [OPTIONAL REFERENCE]
- **Supplied assets:** [IMAGE, AUDIO, DATA, DOCUMENT, AND ARCHIVE LOCATIONS]
- **Canonical lore source:** [OFFICIAL WIKI, DATABASE, DOCUMENTS, OR NONE]

## Content scale

- **Playable characters/classes/vehicles/etc.:** [COUNT]
- **Enemy families:** [COUNT]
- **Bosses:** [COUNT]
- **Maps/arenas/levels:** [COUNT]
- **Items/weapons/relics/cards:** [COUNT]
- **Factions/traits/classes:** [COUNT]
- **Music tracks:** [COUNT OR USE ALL SUITABLE SUPPLIED TRACKS]
- **Difficulty modes:** [COUNT]
- **Dynamic run modifiers:** [COUNT]
- **Campaign or match structure:** [DESCRIPTION]

## Project rules

- Create a new project unless explicitly instructed to modify an existing one.
- Never alter a reference project when it is supplied only as design context.
- Use original branding, directories, executable names, settings files, and documentation.
- Do not reuse old project names in source comments, resources, manifests, settings, or release packages.
- Every visible character must satisfy the intended age and content requirements.
- Treat supplied assets as user-authorized project material, but document their licensing assumptions.
- Search the designated official wikis and lore references before assigning factions, roles, biographies, abilities, enemy families, or relationships.
- Mark uncertain lore assignments as inferred rather than pretending they are canonical.

---

# 2. PRIMARY DESIGN DIRECTIVE

The game must have a clear, repeatable core loop that can be explained in one sentence.

Write this sentence before implementation:

> The player repeatedly [CORE ACTION], makes decisions about [PRIMARY STRATEGIC CHOICE], faces pressure from [MAIN THREAT], and progresses by [PROGRESSION SYSTEM].

Every implemented feature must support at least one of the following:

1. Player agency
2. Strategic depth
3. Mechanical mastery
4. Immersion
5. Replayability
6. Readability
7. Emotional or aesthetic payoff

Do not include systems merely because another successful game has them.

Create a game with its own identity rather than mechanically cloning a commercial title.

Inspirations may guide:

- information hierarchy
- pacing
- input conventions
- genre expectations
- quality standards

They must not result in copied names, characters, UI layouts, text, art, maps, or proprietary content.

---

# 3. EXPERIENCE PILLARS

Define four to seven project pillars.

Recommended examples:

- **Readable complexity:** Deep systems with clear explanations.
- **Responsive interaction:** Every click and input feels immediate.
- **Meaningful variety:** New sessions produce materially different decisions.
- **Strong identity:** Mechanics, visuals, audio, and lore reinforce the theme.
- **Fair challenge:** Difficulty comes from decisions and execution, not hidden cheating.
- **Build expression:** Several viable strategies rather than one solved path.
- **Distribution quality:** The game launches, saves settings, validates assets, and packages cleanly.

Use these pillars as rejection criteria.

A feature that conflicts with several pillars should be redesigned or removed.

---

# 4. GAMEPLAY ARCHITECTURE

Build gameplay as separate, data-driven systems.

Possible modules include:

- application lifecycle
- input
- renderer
- audio
- asset registry
- game state
- player state
- enemies
- combat
- abilities
- status effects
- economy
- inventory
- items
- crafting
- progression
- factions
- traits
- AI
- encounters
- world generation
- session modifiers
- events
- dialogue
- save/settings
- UI
- localization
- testing
- release validation

Avoid placing the entire game inside one monolithic source file when the selected technology supports proper modularity.

Use data definitions for content wherever practical.

A new character, enemy, item, map, ability, or modifier should normally be added through data rather than rewriting core systems.

---

# 5. PLAYER CONTROL AND RESPONSIVENESS

Input responsiveness is a release requirement.

Requirements:

- Inputs must be processed independently from visual frame rate.
- Rapid repeated clicks must register.
- Double-click messages must not swallow ordinary clicks.
- Mouse movement floods must not starve rendering.
- Buttons must respond on the expected press or release event consistently.
- Keyboard shortcuts must have visible feedback.
- Drag-and-drop must provide a click-based fallback when practical.
- Selected objects must have a clear visual state.
- Invalid actions must explain why they failed.
- Avoid hidden input cooldowns.
- Avoid synchronous file access during interaction.
- Avoid blocking operations in UI callbacks.

For strategy and management games:

- buying
- selling
- rerolling
- leveling
- equipping
- crafting
- moving
- confirming
- pausing
- inspecting

must all respond immediately.

For action games:

- movement
- aiming
- attacking
- dodging
- blocking
- ability activation
- weapon switching

must be sampled and simulated at a stable high-frequency rate.

---

# 6. PERFORMANCE ARCHITECTURE

Do not confuse a nominal FPS constant with real responsiveness.

Separate:

1. Input collection
2. Fixed gameplay simulation
3. Scene reconstruction
4. Animation updates
5. Frame presentation
6. Audio playback
7. Background loading

Recommended model:

- Fixed simulation tick appropriate to genre.
- Independent high-refresh presentation target.
- Event-driven rendering for static scenes.
- Immediate frame after meaningful input.
- Reduced update frequency when minimized or inactive.
- Bounded simulation catch-up after stalls.
- Discard obsolete simulation debt instead of entering a catch-up spiral.
- Persistent backbuffers or render targets.
- Cached backgrounds and static scene layers.
- Cached fonts, brushes, pens, shaders, pipelines, and frequently used resources.
- Pre-scaled atlases for frequently displayed portraits or icons.
- Pooled effects and projectiles.
- Stream music rather than decoding all long tracks into memory.
- Preload short frequently used effects.
- Never decode images or open files during frequent combat actions.

Avoid:

- rebuilding an identical menu 240 times per second
- per-frame graphics-object creation
- per-frame image decoding
- per-frame high-quality scaling of large portraits
- forced synchronous window repaint calls
- unlimited message-pump draining
- unlimited simulation catch-up
- hidden high-resolution rendering for tiny windows
- scaling positions and sizes independently when this can create pixel seams

When logical UI coordinates are scaled, transform shared rectangle endpoints:

- left
- top
- right
- bottom

Then derive width and height.

This prevents fractional-resolution seams and rare black bars.

## Performance telemetry

Where appropriate, expose:

- target presentation rate
- actual presentations per second
- complete scene rebuilds per second
- simulation tick rate
- direct versus scaled presentation
- frame-time diagnostics

Clearly explain that a lower scene-rebuild rate on a static interface is intentional.

Never claim a target frame rate was achieved without a real runtime measurement.

---

# 7. GRAPHICS AND VISUAL LANGUAGE

Create a coherent visual system rather than a pile of glow effects.

Define:

- color hierarchy
- typography hierarchy
- panel hierarchy
- rarity language
- selected-state language
- danger language
- healing language
- damage-type language
- interactable-state language
- success/failure language
- faction or class language

Every gameplay state should be readable without relying solely on color.

Use combinations of:

- shape
- border
- icon
- label
- motion
- brightness
- pattern
- position

## Effects

Abilities and major actions must not all use the same ring, flash, and spark.

Create effect profiles controlling:

- geometry
- origin
- target
- travel path
- palette
- timing
- telegraph
- impact
- scale
- duration
- screen shake
- audio cue
- ability-name callout

Possible geometry families:

- projectile
- beam
- slash
- cone
- line
- wave
- pillar
- vortex
- orbit
- explosion
- shield dome
- glyph
- rune
- trail
- chain
- ricochet
- ground fracture
- petal burst
- feather storm
- lightning path
- tidal sweep
- poison pool
- healing pulse
- revival column
- execution mark
- transformation shell

Closely related abilities may share a family, but should still differ through timing, palette, scale, origin, target, and impact.

Keep effects bounded.

Do not replace readable gameplay with uncontrolled particles.

---

# 8. UI AND TEXT SAFETY

The UI must survive:

- long names
- long descriptions
- unusual resolutions
- high DPI
- localization expansion
- rapid state changes
- several simultaneous notifications
- missing optional assets

Never assume a fixed font will fit.

Use measured text width and height.

Implement:

- fit-to-width
- fit-to-region
- wrapping
- ellipsis only when full text is immediately available elsewhere
- scrollable regions for genuinely long content
- compact and expanded inspection modes
- minimum panel padding
- title and body separation

Test the longest:

- character name
- ability name
- item name
- faction name
- status description
- event description
- achievement
- notification
- fusion or upgrade banner

Avoid placing a font inside a region shorter than the font’s measured height.

No important information may silently extend beyond its panel.

## Information hierarchy

Compact surfaces show immediate decisions.

Detailed surfaces explain full rules.

Examples:

- cards show cost, identity, role, and critical state
- hover panels show complete mechanics
- battle HUD shows immediate combat information
- encyclopedia/manual shows every rule

Do not permanently print full descriptions onto small cards.

---

# 9. WINDOWING AND DISPLAY

For native desktop games, support:

- resizable window
- borderless window
- borderless fullscreen
- optional exclusive fullscreen when technically justified
- high DPI
- multiple monitors
- display changes
- monitor removal
- window restoration
- minimum usable dimensions
- aspect-ratio handling
- letterboxing where needed

Recommended shortcuts:

- F10: borderless window
- F11: borderless fullscreen
- Alt+Enter: fullscreen toggle

Preserve and restore:

- prior style
- position
- dimensions
- monitor
- display mode

Prevent off-screen saved windows by clamping restored geometry to the nearest monitor work area.

Resizing must not flicker.

Compose complete frames off-screen and present atomically.

---

# 10. AUDIO DIRECTION

Audit every supplied sound archive.

Catalog:

- music
- ambience
- voices
- weapons
- abilities
- impacts
- healing
- shielding
- movement
- UI
- crafting
- upgrades
- bosses
- victory
- defeat
- transitions

Compute hashes to find duplicates.

Record:

- format
- duration
- channels
- sample rate
- likely source category
- character or object ID
- suitability
- selected runtime use

## Ability audio

Prioritize:

1. Exact character-linked audio
2. Exact action-linked audio
3. Closely themed category audio
4. Generic fallback

Do not mislabel unrelated voice lines.

Trim long effects into combat-appropriate cues.

Use separate channels for:

- music
- voices
- frequent SFX
- important event SFX

Prevent audio clutter through:

- per-unit voice limits
- team priorities
- global cooldowns for repeated impact sounds
- important-cast priority
- reduced enemy voice frequency

Optional audio must fail gracefully.

A missing optional:

- voice
- music track
- individual ability cue

must not prevent startup.

Missing mandatory files must identify the first failed path in a useful error dialog.

Provide:

- music toggle
- SFX toggle
- voice toggle
- volume controls when supported

Save audio preferences.

---

# 11. ASSET INGESTION PIPELINE

Recursively audit supplied archives.

Record:

- path
- filename
- extension
- dimensions
- duration
- size
- hash
- naming family
- inferred ID
- likely purpose
- duplicate status
- corruption status

Generate contact sheets for:

- characters
- enemies
- bosses
- items
- maps
- UI
- backgrounds

Categorize assets into:

- runtime required
- runtime optional
- documentation
- promotional
- duplicate
- storefront
- tutorial
- unrelated
- uncertain

Do not load every supplied file merely to claim it was used.

Use every relevant non-redundant asset family intelligently.

Exclude duplicate monetization panels, store thumbnails, package icons, and unrelated promotional debris from runtime.

Maintain deterministic fallbacks:

- alternate portrait
- silhouette
- icon
- faction emblem
- neutral placeholder

Missing optional art must not create invisible gameplay objects.

Preserve aspect ratio.

Use appropriate crops and anchors for:

- portraits
- cards
- full-height art
- wide banners
- icons
- boss images

---

# 12. LORE AND RESEARCH

When characters, factions, places, monsters, vehicles, historical entities, or established universes are involved, research authoritative sources before finalizing content.

Verify:

- identity
- faction
- role
- origin
- abilities
- relationships
- hierarchy
- combat behavior
- visual motifs
- terminology

Create a lore audit with:

- content name
- canonical source
- verified facts
- inferred adaptation
- implementation decision
- confidence level

Do not place characters into arbitrary factions for spreadsheet convenience.

Do not present inferred information as canonical fact.

When adapting real mythology or folklore, distinguish:

- source mythology
- modern interpretation
- original game adaptation

---

# 13. AI OPPONENTS

AI must play the actual game.

Do not simulate difficulty through hidden combat multipliers unless the game explicitly labels them as handicap modifiers.

AI should use the same:

- economy
- shops
- resources
- inventory
- crafting
- progression
- cooldowns
- field limits
- encounter rules

Randomize AI personalities and difficulty each session.

Possible personalities:

- Saver
- Reroller
- Tempo
- Vertical
- Flexible
- Highroller
- Itemizer
- Pivot
- Scout
- Aggressor
- Defensive
- Opportunist

Behavior variables may include:

- aggression
- economy discipline
- leveling pace
- reroll frequency
- pivot tolerance
- item priority
- scouting
- risk appetite
- formation preference
- target preference
- contest avoidance
- comeback desperation

Higher difficulty should improve:

- evaluation quality
- timing
- planning depth
- mistake frequency
- adaptation
- resource discipline

It should not grant:

- hidden gold
- hidden damage
- impossible items
- impossible information
- invisible bonus units
- guaranteed rewards

AI actions should occur over time during planning rather than teleporting from one completed state to another.

Track action histories to prove that opponents differ.

Automated tests must verify:

- resource spending
- purchases
- progression
- item use
- crafting
- positioning
- strategic divergence
- legal state
- no hidden cheating

---

# 14. DYNAMIC SESSION SYSTEMS

Each new session should materially change strategy.

Possible run-level systems:

- opening modifiers
- world modifiers
- mutations
- weather
- map variants
- enemy composition
- procedural objectives
- random bosses
- draft pools
- patron blessings
- faction bonuses
- item rules
- economy rules
- challenge contracts

Avoid random modifiers that merely add universal damage.

Good modifiers change decisions.

Examples:

- altered resource timing
- different upgrade paths
- changed enemy behavior
- modified terrain
- rare marked characters
- restricted categories
- rotating hazards
- conditional rewards
- delayed transformations
- alternate crafting rules

Clearly separate:

- permanent identity
- temporary session identity
- player-specific blessing
- lobby-wide rule
- encounter modifier

Do not let temporary bonuses masquerade as actual owned units, faction members, or permanent stats.

UI must show real counts and virtual bonuses separately.

---

# 15. INVENTORY, CRAFTING, AND UPGRADES

Crafting must be atomic and visible.

When two base items create a completed item:

1. Preview the result before commitment.
2. Consume both components.
3. Create one completed item.
4. Preserve ownership.
5. Trigger a clear presentation.
6. Explain the exact effect.
7. Use unique art and sound where available.
8. Handle full inventory safely.

Never silently delete items.

For unit or object fusion:

1. Treat the incoming object as a virtual copy.
2. Resolve exact lower-tier fusion.
3. Resolve chained higher-tier fusion.
4. Place the final result.
5. Only require capacity when no fusion occurs.
6. Preserve attached equipment.
7. Return or compensate overflow visibly.

Full inventory, bench, garage, party, or roster capacity must not block a valid fusion.

Shared-draft rewards must also resolve atomically.

When a reward cannot enter normal storage, use an explicit temporary overflow state rather than deleting or rejecting it.

Prevent gameplay from continuing while an overflow state violates legal deployment rules, but provide enough time and clear instructions to resolve it.

---

# 16. DIFFICULTY AND ENCOUNTER BALANCE

Do not balance encounters only by eyeballing enemy Health.

Define explicit encounter tiers.

Each encounter should specify:

- enemy count
- enemy archetypes
- Health
- offense
- defenses
- abilities
- time limit
- reward
- failure penalty
- intended player-power band
- expected clear rate

Avoid formulas where raw round or level numbers multiply every enemy indefinitely.

This often produces:

- sudden HP walls
- defense inflation
- timeout losses
- reward mismatch
- first-boss difficulty spikes

Use gradual progression.

Boss encounters should have:

- longer clocks
- controlled escort counts
- capped failure penalties
- proportional rewards
- readable mechanics

## Automated balance simulation

Simulate realistic evolving player states, not arbitrary test armies.

For each major encounter:

1. Generate many legitimate player states using normal progression rules.
2. Measure internal power.
3. Sort into low, middle, and high bands.
4. Simulate the encounter.
5. Record:
   - clear rate
   - average time
   - timeout rate
   - survivors
   - damage taken
   - reward value

Recommended target philosophy:

- tutorial encounters: 95–100% for normal starting states
- ordinary progression encounters: high clear rate for maintained builds
- boss encounters:
  - strong builds clear decisively
  - average builds clear reliably
  - low or greedy builds may fail
- timeouts should not be the ordinary resolution

Lock acceptable bands into automated tests.

---

# 17. SAVE AND SETTINGS

Implement settings persistence.

At minimum preserve:

- music
- SFX
- voices
- volume
- window mode
- window position
- window dimensions
- monitor where sensible
- gameplay options
- accessibility settings

Validate the settings file with:

- magic identifier
- version
- structure size
- bounds checks

Corrupt or outdated settings must fail safely and revert to defaults.

Document how to reset settings.

For portable releases, storing settings beside the executable is acceptable when intentional and documented.

For installed releases, use the appropriate user-data location.

---

# 18. APPLICATION LIFECYCLE

Handle:

- first startup
- missing mandatory assets
- missing optional assets
- minimize
- focus loss
- focus return
- resize
- monitor changes
- fullscreen changes
- return to title
- abandon match
- quit
- clean shutdown

Active progress should not silently disappear through an accidental Escape press.

Use confirmation dialogs for abandoning meaningful progress.

Escape priority should generally be:

1. Close open modal/manual
2. Exit fullscreen
3. Close secondary screen
4. Ask before abandoning progress

Save settings during clean shutdown.

Release every:

- image
- audio buffer
- graphics object
- device context
- file
- window resource
- engine resource

---

# 19. ACCESSIBILITY AND QUALITY OF LIFE

Where appropriate, include:

- scalable text
- color-independent status indicators
- screen shake toggle
- flash intensity toggle
- music, SFX, and voice controls
- key rebinding
- pause
- speed controls
- tooltips
- encyclopedia/manual
- clear error messages
- readable timers
- confirmation prompts
- persistent settings
- tutorial encounter
- difficulty explanation

A high-refresh target must not require unreadably fast animations.

---

# 20. GENRE MODULES

Activate only the relevant modules.

## A. Autobattler or strategy module

Include:

- economy
- shop
- progression
- roster capacity
- positioning
- factions
- roles
- items
- crafting
- fusion
- PvE
- PvP simulation
- AI opponents
- scouting
- shared draft
- session modifiers
- overtime
- legal deployment checks

Use soft contesting when requested rather than a hard finite bag.

Show personal upgrade progress separately from lobby contest pressure.

## B. Action or shooter module

Include:

- stable movement
- aiming
- weapon handling
- recoil
- hit detection
- animation cancel rules
- enemy telegraphs
- damage reactions
- difficulty scaling
- checkpoints
- encounter pacing
- projectile pooling
- sound propagation
- accessibility options

Avoid tying weapon logic to frame rate.

## C. RPG module

Include:

- character progression
- quests
- dialogue
- inventory
- equipment
- skills
- factions
- reputation
- save/load
- world state
- companion AI
- level scaling policy
- quest-state validation

Avoid radiant filler unless it supports the core fantasy.

## D. Survival module

Include:

- gathering
- crafting
- shelter
- threats
- day/night
- weather
- hunger or stamina only when meaningful
- persistence
- world simulation
- escalating events
- recovery paths

Do not turn every resource into maintenance busywork.

## E. Roguelite module

Include:

- run seed
- permanent unlocks
- run modifiers
- branching choices
- build-defining rewards
- escalating encounters
- bosses
- failure progression
- run statistics
- reproducibility

Each run should produce different decisions rather than different colors.

## F. Management or tycoon module

Include:

- production
- staffing
- demand
- logistics
- finances
- upgrades
- events
- competitors
- failure states
- readable forecasting
- automation
- time controls

Do not hide critical formulas from the player.

## G. Card or deckbuilding module

Include:

- deck rules
- draw
- discard
- hand limits
- targeting
- costs
- upgrades
- status effects
- enemy intent
- card rewards
- rarity
- run modifiers
- deterministic rules text

Every card must state exact behavior.

---

# 21. TESTING STRATEGY

Test actual functions and data rather than only searching source strings.

## Core behavior

- startup
- shutdown
- settings
- input
- window modes
- asset failures
- optional fallbacks
- state transitions
- save/load where applicable

## Gameplay

- every major action
- every resource
- every upgrade path
- every item recipe
- every faction or class
- every encounter type
- every boss
- every dynamic modifier
- every victory/failure transition

## Long-form stress

- long AI economy
- long combat
- repeated restarts
- repeated fullscreen changes
- repeated resizing
- large inventories
- maximum roster capacity
- overflow states
- repeated crafting
- repeated fusion
- maximum effects
- invalid input
- focus loss
- minimized execution

## Randomized simulation

Use deterministic seeds.

Record failing seeds.

Run enough simulations to catch:

- impossible states
- soft locks
- resource loss
- invalid targets
- dead entities acting
- overflow bugs
- illegal progression
- extreme win-rate outliers
- timeouts
- runaway sustain
- impossible damage

## Tooling

Where supported, run:

- warnings as errors
- static analysis
- undefined-behavior sanitizer
- address sanitizer
- unit tests
- integration tests
- asset decode tests
- package verification
- extracted-source rebuild

Do not ignore analyzer warnings merely because gameplay appears correct.

---

# 22. DISTRIBUTION QUALITY

The player package must contain only runtime and player-facing files.

Include:

- executable
- required assets
- launcher when useful
- icon
- README
- controls
- troubleshooting
- release notes
- checksums
- verification script
- selected player-facing audits

Do not include:

- object files
- import libraries
- stub DLLs
- analyzer executables
- test binaries
- compiler logs
- temporary files
- old versions
- stale manifests
- local settings
- source backups
- caches

The source package must include:

- complete source
- content data
- project files
- build scripts
- tests
- validator
- resource generator
- documentation
- reproducible build instructions
- asset registry

Generate exact SHA-256 manifests.

After packaging:

1. Extract both archives into unrelated clean directories.
2. Verify every manifest entry.
3. Ensure there are no unlisted files.
4. Rebuild from the extracted source.
5. Rerun tests.
6. Rerun analysis.
7. Compare the rebuilt executable with the shipped executable.

Use deterministic build options where supported.

Embed:

- application icon
- manifest
- file version
- product version
- company or author field when provided
- description
- copyright
- compatibility metadata
- DPI awareness

---

# 23. DOCUMENTATION

Produce:

- `README`
- `CONTROLS`
- `TROUBLESHOOTING`
- `RELEASE_NOTES`
- `CHANGELOG`
- `BUILDING`
- `GAME_DESIGN`
- `PERFORMANCE_NOTES`
- `BALANCE_REPORT`
- `VALIDATION_REPORT`
- `ASSET_AUDIT`
- `AUDIO_IMPLEMENTATION`
- `LORE_AUDIT`
- `SHA256SUMS`

Add specialized documentation for major systems.

Examples:

- AI behavior
- crafting
- damage types
- item recipes
- dynamic modifiers
- encounter curve
- save format
- mod support

Documentation must describe actual implemented behavior.

Remove stale claims whenever mechanics change.

---

# 24. PROHIBITED SHORTCUTS

Do not:

- stop at a plan
- return only pseudocode
- use HTML when a native game was requested
- hide unfinished systems behind “planned”
- silently delete rewards
- block valid upgrades because storage is full
- show fake performance claims
- let AI cheat invisibly
- assign random lore
- use one effect for every ability
- clip important text
- stretch images
- swallow rapid clicks
- redraw static scenes at maximum frequency
- decode assets during combat
- scale adjacent UI rectangles independently
- make bosses difficult only by multiplying Health
- make optional assets mandatory
- ship stale build debris
- package a different executable from the one tested
- claim runtime tests that were not performed

---

# 25. IMPLEMENTATION ORDER

Follow this sequence unless dependencies require a justified change:

1. Resolve project configuration.
2. Audit supplied files.
3. Research lore.
4. Define pillars and core loop.
5. Select technology.
6. Create modular architecture.
7. Define data formats.
8. Implement application lifecycle.
9. Implement input.
10. Implement renderer.
11. Implement audio.
12. Implement core gameplay.
13. Implement progression/economy.
14. Implement inventory and crafting.
15. Implement enemies and AI.
16. Implement dynamic session systems.
17. Implement UI and inspection.
18. Integrate assets.
19. Add settings persistence.
20. Optimize hot paths.
21. Add window modes.
22. Build automated behavior tests.
23. Build balance simulations.
24. Run static analysis and sanitizers.
25. Conduct hostile polish pass.
26. Generate documentation.
27. Package runtime and source.
28. Clean-room extract.
29. Rebuild and retest.
30. Deliver final packages with honest limitations.

---

# 26. FINAL RESPONSE

When complete, report:

- version
- playable package
- source package
- technology
- core gameplay loop
- implemented systems
- content totals
- performance architecture
- test totals
- balance simulations
- package-manifest totals
- SHA-256 hashes
- clean-room rebuild status
- embedded resources
- known limitations
- anything not live-tested

Do not bury limitations.

Do not say work will be completed later.

Do not ask for confirmation when a reasonable implementation decision can be made from this prompt.

Build the strongest complete game possible from the supplied materials and configuration.