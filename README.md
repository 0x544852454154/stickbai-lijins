# NEON STICKMAN FIGHTER — pixel edition (vertical slice)

Run: `python3 -m http.server` in this folder, open `index.html` (ES modules need http). Or open `dist/neon-stickman-fighter.html` directly.
Tests: `node tests/smoke.test.mjs` (headless: 16 matchups, hits, combos, projectiles, rebinding rules).
Rebuild sprites: `python3 tools/slice_sheets.py` · single-file build: `python3 tools/build_single_html.py`.

## Assets
Your four sheets (idle 6 / walk 8 / run 8 per fighter) were AI-generated with a *baked-in checkerboard*, uneven frame spacing and ground bars.
`tools/slice_sheets.py` keys out the checkerboard, detects frames, removes the ground bar, anchors feet, downsamples 0.4x to a ~64px sprite and packs
uniform 96x80 cells into `public/assets/characters/<id>.png` with timing metadata in `public/assets/animations/<id>.json`.

## Documented replacements (no sheets were supplied for these)
Jump/fall, crouch, block, hit, knockdown, getup, win and ALL attack poses are derived at runtime from the supplied idle/run frames
(squash, rotate, flash, run-lunge frames). Hit sparks, slash arcs, lightning, rings, ground cracks and projectiles are procedural pixel particles
(`VFXSystem`), not sprite sheets. Stages are procedural parallax layers. Audio is synthesized with Web Audio.

## Not done yet
Dedicated attack/effect sprite sheets, real jump/crouch/attack/KO animations, per-fighter counter moves (Soul Counter etc.), stage select,
hitbox editor, further automated tests, gamepad/touch.
