---
name: oriental-scene-lite-h3
description: Use when writing H3 prompts for Wuxia, Chinese-fantasy, period-oriental, or Eastern-aesthetic scenes (celestial palaces, sea of clouds, swordmasters, mirror lakes) — folds the 6-layer scene formula into [Shot 1] integrated_multimodal_description so the result reads like a cinematic concept-art poster. Lite version.
---

# Oriental Scene Lite — H3 Edition

Cues Wuxia / Chinese-fantasy / period-oriental scenes in H3 grammar. The 6-layer formula from the original Lite stays the same; the change is **where each layer lands in the H3 output**.

## How to fold the 6-layer formula into H3

Original 6-layer order:

1. Camera angle
2. Architecture
3. One focal element (pick one)
4. Small figure, back view
5. Environment + lighting
6. Quality (volumetric, depth of field, 8K)

H3 mapping:

| Layer | H3 slot | Phrasing pattern |
|---|---|---|
| 1. Camera angle | Opening of `[Shot 1]` | `a low-angle long-corridor depth shot,` / `a symmetrical wide composition,` / `an extreme wide establishing shot with low horizon,` |
| 2. Architecture | Subject clause (continues) | `… frames a white jade colonnade carved with dragons and clouds, a glossy stone floor reflecting the sky,` |
| 3. One focal element | New clause | `a giant moon-gate arch opening onto a sea of clouds,` |
| 4. Small figure, back view | Subject clause (continues) | `a tiny figure in a crimson hanfu standing at the far end, back view, silk fluttering in the wind.` |
| 5. Environment + lighting | New clause | `Soft cool morning light filters through atmospheric haze,` |
| 6. Quality | Trailing tag | `volumetric light, depth of field, cinematic, 8K detail.` |

Style descriptor at the top of `[Shot 1]`: pick `Live-action, cinematic,` for film-set shots, or `3D CG, cinematic,` for digital concept-art look. Wuxia scenes typically use the latter.

## Universal template

```
[Shot 1] {3D CG / Live-action}, cinematic, {camera angle from layer 1}, {architecture from layer 2}, {one focal element from layer 3}, {small figure, back view, outfit from layer 4}, {environment + lighting from layer 5}. The camera {single H3 motion clause — pick from §Camera-motion below}. Volumetric light, atmospheric haze, delicate texture, depth of field, cinematic, 8K detail.
```

## Camera-motion (H3 grammar)

Pick **one** of these clauses; do not stack.

- `The camera pushes in with small amplitude at slow speed toward the figure.`
- `The camera dollies out with small amplitude at slow speed to reveal the full palace.`
- `The camera cranes up with large amplitude at slow speed to reveal distant mountain peaks.`
- `The camera arcs 180 degrees with small amplitude at slow speed around the figure.`
- `The camera holds a static shot as clouds drift past the colonnade.`
- `The camera trucks left with small amplitude at slow speed, sliding past the foreground pillar to reveal the figure.`

Add **one** ambient motion inside the same sentence: `clouds drift slowly,` / `silk flutters in the wind,` / `cherry blossoms fall,` / `a faint mist rolls across the lake,`. The H3 model needs both the camera motion and one in-frame motion cue to avoid static-feeling renders.

## Worked examples

### Cloud corridor at dawn (serene)

```
[Shot 1] 3D CG, cinematic, a low-angle long-corridor depth shot frames a white jade colonnade carved with dragons and clouds, a glossy stone floor reflecting the pale blue sky. A giant moon-gate arch opens onto an endless sea of clouds. A tiny figure in a crimson hanfu stands at the far end, back view, silk fluttering in the wind. Soft cool morning light filters through atmospheric haze. The camera pushes in with small amplitude at slow speed toward the figure as clouds drift slowly past the colonnade. Volumetric light, atmospheric haze, delicate texture, depth of field, cinematic, 8K detail.

overall_soundscape: Wind carries through the corridor while silk flutters and a distant bell rings once from a temple below.

non_diegetic_music: A slow guqin melody at a quiet tempo, joined by sustained low strings.
```

### Swordmaster by a mirror lake (dreamy)

```
[Shot 1] 3D CG, cinematic, a symmetrical wide composition frames a floating palace mirrored in a still lake that merges with the clouds. A lone white-robed swordsman stands on the water's edge holding a long sword, back view, hair tied and flowing. Pale dawn sky, soft dreamy light, gentle ripples across the lake. The camera holds a static shot as gentle ripples continue across the lake. Ultra-wide lens, volumetric light, atmospheric haze, delicate texture, depth of field, cinematic, 8K detail.

overall_soundscape: A quiet wind moves across the lake while ripples softly lap the shore and a faint guqin note sustains.

non_diegetic_music: A solo guqin phrase at a slow tempo, joined by a single flute counter-melody, fading out at the end.
```

### Phoenix celestial palace (grand)

```
[Shot 1] 3D CG, cinematic, an extreme wide establishing shot with a low horizon frames an ancient Chinese palace of multi-layered upturned eaves and white jade columns, set on a clifftop above a sea of clouds. A giant phoenix perches on the highest ridge, wings half-open. A tiny swordmaster in dark hanfu stands on the foreground terrace, back view, sword at his hip. Golden dawn light breaks through the mist, Tyndall light beams slant through the columns. The camera cranes up with large amplitude at slow speed to reveal the full palace and the distant mountain peaks. Volumetric light, atmospheric haze, delicate texture, depth of field, cinematic, 8K detail.

overall_soundscape: Wind rushes across the clifftop while the phoenix's feathers rustle faintly and a distant gong rings once.

non_diegetic_music: A wide orchestral swell at a moderate tempo, joined by a slow guqin line and a gong hit at the final beat.
```

### Sword duel in bamboo forest (tense)

```
[Shot 1] Live-action, cinematic, a low-angle medium shot frames two swordmasters facing each other in a bamboo forest at sunrise. One wears flowing white hanfu, the other charcoal-grey hanfu with crimson lining. Bamboo stalks lean inward toward the clearing. Hard morning sunlight filters through the leaves, throwing sharp diagonal shadows. The camera trucks right with small amplitude at slow speed, circling the clearing. Cinematic color grading, teal and orange, motion blur on the blades, 2.35:1 aspect.

overall_soundscape: Bamboo stalks creak in the wind while the swordsmen's robes rustle and a single bamboo leaf falls.

non_diegetic_music: A driving percussion line at a moderate tempo, joined by a low string pulse and a guqin tremolo, ending abruptly.
```

## H3-specific notes

- **No `--ar 21:9` flag.** Use the model-side aspect ratio control. For Wuxia scenes the cinematic 2.35:1 or 21:9 wide look is recommended but not required.
- **No `--no text, watermark, modern buildings` flags.** Phrase exclusions affirmatively inside the shot: `period setting with traditional wooden architecture, no contemporary buildings, no neon, no modern vehicles, no on-screen text, no watermark.`
- **Tiny figure + back view is not optional.** Wuxia scenes rendered with a face-on or close-up character consistently fail the "hùng vĩ" (epic) feeling and tend to warp the face. Keep the figure small and facing away unless the brief explicitly calls for a close-up.
- **One focal element only.** Multiple focal elements (phoenix + bronze cauldron + dragon waterfall) make the frame noisy and the camera will not know where to land. Pick one.
- **Pair this skill with `character-sheet-lite-h3`.** If the Wuxia character appears across multiple clips, generate the reference sheet first and use it to define `<Subject 1>` in Ref2VA mode.

## By tool

The original Lite targets Midjourney / SD / Flux / Veo for stills. For H3 the workflow is:

- **For a still poster** — generate via the upstream image model. Pass the prompt body as the image prompt. Set aspect ratio on the model side.
- **For a short video clip (T2VA)** — paste the assembled `[Shot 1]` body into `integrated_multimodal_description`, complete `overall_soundscape` and `non_diegetic_music`.
- **For a multi-shot sequence (Ref2VA)** — define the Wuxia character as `<Subject 1>` from a character sheet, define the palace / forest / lake as `<Subject N>` if it recurs, and use the same labels in every shot.

---

> The full (VIP) version adds: the 8-layer formula with a complete keyword library, 9 worked scenes (celestial palace, Langxiao palace, dragon-head waterfall, immortal pavilion, ancient-scroll desert, …) with full Vietnamese transcripts, detailed SD parameter recommendations, a guide for converting stills to video, and a pairing guide with the character sheet skill for consistent Wuxia characters. Contact the author on GitHub [@Rylaispirit](https://github.com/Rylaispirit).