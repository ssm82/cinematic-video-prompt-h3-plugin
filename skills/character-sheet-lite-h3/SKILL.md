---
name: character-sheet-lite-h3
description: Use when you need a character reference-sheet prompt (three full-body views + one close-up in a single image) for H3 video generation. The sheet's output image feeds into H3 as <Picture 1> for I2VA mode or as the source defining <Subject 1> for Ref2VA mode, so the same character stays consistent across shots. Lite version.
---

# Character Sheet Lite — H3 Edition

Produces one 16:9 image: three full-body angles on the left (front / side profile / back), one chest-up close-up on the right. The image is a **reference asset**, not a video frame — it is consumed by H3 as input.

## How to consume this sheet in H3

The sheet is an **input**, not an H3 prompt by itself. Two integration paths:

### Path A — I2VA (sheet as the first frame of `[Shot 1]`)

Use the sheet image directly as the first-frame input. Wrap with the I2VA instruction:

```
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, {style + camera setup}, the character shown in <Picture 1> … (preserve appearance, clothing, accessories) … {camera-motion clause}. {color grading + technical}.

overall_soundscape: …

non_diegetic_music: …
```

Pros: simplest, fastest. Cons: the sheet's three-quarter views and back view become "unused" once the camera starts moving — H3 only reads the first frame.

### Path B — Ref2VA (sheet defines `<Subject 1>`)

Define the character as `<Subject 1>` in `subject_definitions`, anchored to `<Picture 1>` (the sheet). Use `<Subject 1>` in every shot of `detailed_description`. This is the right path when you need the **same character across multiple shots** (the H3 cost-prototype scenario):

```
subject_definitions:
<Subject 1> is the young woman in <Picture 1>, with shoulder-length black hair, a faded indigo wrap coat, a thin silver necklace, and a small scar through the left brow.
<Picture 1> is the character reference sheet, providing full-body front / side / back views and a chest-up close-up of <Subject 1>.

summary:
[reference generation] The target video follows <Subject 1> through three connected scenes, preserving her identity, clothing, and silhouette across cuts.

retention_analysis:
<Subject 1> (appears in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - identity, garment, and key accessories are retained across all shots.
<Picture 1> (reference asset for <Subject 1>): fully_preserved - the sheet's full-body views and close-up define the visual reference for the entire video.

detailed_description:
{The target video is in a cinematic, slightly desaturated palette with soft window light.}
[Shot 1] Live-action, cinematic, {shot size + angle} frames <Subject 1> … {camera-motion clause}. {color grading + technical}.
[Shot 2] At MM:SS.mmm, the camera cuts to {next scene}. <Subject 1> continues to wear the faded indigo wrap coat with the same thin silver necklace …
…
```

Pros: identity holds across cuts because `<Subject 1>` is the same anchor in every shot. Cons: more boilerplate per prompt.

## Workflow

1. Receive a brief character description (a few lines is enough). Choose the rest yourself and note the assumptions in the response.
2. Ask one question only if you don't know: **animation style** (`cinematic 3D character,` / `live-action photoreal film still,` / `stylized animated,`) and **target H3 mode** (I2VA single-shot or Ref2VA multi-shot).
3. Build the sheet prompt using the template below.
4. Pair the sheet with a character tag — 8–10 short, specific, visible keywords — that you paste into the H3 shot description so the verbal description matches the visual reference:

   `woman early 30s, lean build, crooked nose, olive skin, scar through left brow, ash-black bob, faded indigo wrap coat, rust silk lining, scuffed leather boots, brass ring on thumb`

## Four rules so the character does not "flatten"

1. **Strong silhouette.** The outline must be recognizable (broad shoulders, oversized coat, A-line shape, deep V-neck). "A person wearing clothes" is not a silhouette.
2. **Mixed colors, not base colors.** Use `charcoal violet`, `rust brown`, `faded indigo` instead of `gray` / `brown` / `blue`. Add one high-contrast accent color at exactly one small place (lining, button, iris).
3. **Signs of life.** Pick at least two: a patch, fraying, a scar, asymmetry, dirt.
5. **No empty adjectives.** Replace `beautiful`, `handsome`, `cool`, `stylish`, `pretty` with specific, visible descriptions.

**Originals mandatory.** Do not take the face of a real actor, celebrity, or named film / game character. If the user asks for "looks like X", propose an original design instead.

## Sheet prompt template

```
character design reference sheet, single image, left: three full-body views (front, side profile, back) in a row, A-pose, evenly spaced; right: one large chest-up close-up headshot,
[gender], [age] years old, [build], [skin tone with undertone],
face: [face shape, eyes + iris color, brows, nose, lips], natural asymmetry, visible skin texture, [one mark: scar / mole / freckles], default expression [mood],
hair: [length, texture, multi-tone color, styling],
wearing: [inner layer: fabric + color], [outer layer: fabric + color + silhouette], [one sign of wear], [one accent color detail],
footwear: [style + material + wear], accessories: [1 item with a story],
[render style: cinematic 3D character / photoreal film still / stylized animated], same identity across all views, same outfit, studio lighting, neutral light gray background, no text, no labels, no watermark, ultra detailed
```

## H3 mapping notes

- H3 does not accept `--ar 16:9` flags or `--style raw` flags. Aspect ratio and style are set on the model side. The sheet image is rendered at 16:9 by the upstream image model; H3 only consumes the result.
- The sheet prompt is still a free-form image-generation prompt (no H3 fields needed). The H3 adaptation happens **after** the sheet is generated.
- When you later write the H3 shot description, repeat the character's tag (`the same young woman in the faded indigo wrap coat with the thin silver necklace, scar through the left brow`) at the start of every relevant shot. Section 8.5 in the main `SKILL.md` covers why.

## By tool

The original Lite sheet targets Midjourney / SD / Flux. For H3 the upstream image model is usually MiniMax image generation or a third-party T2I model called by the same pipeline. Translate the tool-specific rules:

- **Midjourney-style API**: add `--ar 16:9` equivalent at the API level; remove it from the prompt body.
- **SD-style API**: keep the negative prompt as a separate field on the API call. Suggested exclusions: `inconsistent face, outfit changes between views, plastic skin, airbrushed, bad anatomy, extra fingers, text, watermark, celebrity likeness, cropped`.
- **Flux-style API**: minimal negative prompt support → state exclusions affirmatively inside the prompt body: `same identity across all views, same outfit in all four, skin with visible pores and fine hair, no text anywhere, no watermark`.

---

> The full (VIP) version adds: multi-character layout rules, 6 extreme-rules tables, a 20-render-style library, 9 cut-and-sew vocabularies, a 3-layer garment guide, a 5-direction fabric guide, age and regional facial feature guides, an English vocabulary for fabric and facial features, a 4000-character budget guide, and a 17-item checklist. Contact the author on GitHub [@Rylaispirit](https://github.com/Rylaispirit).