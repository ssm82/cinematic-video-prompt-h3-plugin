# H3 Example Prompts — Worked examples per mode

Each example uses the cinematic vocabulary from `references/01`–`references/06` and folds it into H3 grammar (see `SKILL.md` section 3). Replace the subject and setting to reuse the recipe.

---

## 1. T2VA — Story / flashback (single shot, 6 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a medium close-up at eye-level frames an elderly Vietnamese woman in a faded brown áo bà ba beside a wooden window. Soft window light falls on an old photo album in her lap while dust particles drift through the air. The camera pushes in with small amplitude at slow speed as her fingers slowly turn the photo album's page. Muted warm palette with lifted blacks, shallow depth of field, 35mm film grain.

overall_soundscape: A quiet room tone continues underneath while the photo album's pages softly turn and the wooden floor creaks once as she shifts her weight.

non_diegetic_music: A solo piano line at a slow tempo, joined by sustained low strings, fading in the final second.
```

Why: window light + lifted blacks for an aged-film feel; slow push-in pulls the viewer into the memory; MCU keeps the album visible.

---

## 2. T2VA — Horror (single shot, 8 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a low-angle Dutch-tilted shot frames a lone figure in a white dress standing at the far end of a long corridor in an abandoned French colonial house. Ground fog creeps along the floor while a single candle held at chest level throws a tight circle of light into deep shadow around her. The camera pushes in with small amplitude at slow speed, handheld with subtle shake. Cool desaturated palette, deep shadows, high contrast, 2.35:1 aspect.

overall_soundscape: Wind drafts down the corridor while the candle flame hisses faintly and distant floorboards creak under slow footsteps.

non_diegetic_music: N/A
```

Why: Dutch tilt + low angle create unease; a single candle source maximizes contrast; handheld puts the viewer in the scene.

---

## 3. T2VA — Wuxia / cultivation fantasy (single shot, 10 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, an extreme wide establishing shot with a low horizon frames a young cultivator in flowing white hanfu standing on a cliff edge above an endless sea of clouds at sunrise. God rays break through the mist and silk fabric drifts in the wind. The camera cranes up with large amplitude at slow speed to reveal distant mountain peaks. Cinematic fantasy art with ink-wash influence, ethereal golden hues, volumetric lighting.

overall_soundscape: Distant wind carries through the valley while silk fabric flutters and a faint bell rings from a temple far below.

non_diegetic_music: A slow guqin melody at a quiet tempo, joined by sustained low strings and a gong hit at the final beat.
```

Why: crane up + extreme wide = small subject before a vast landscape; God rays + sea of clouds are the genre's visual language.

---

## 4. T2VA — Product (two-shot sequence, 6 s + 4 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, an eye-level product shot frames a matte-black ceramic coffee mug on a clean light-grey stone surface. Softbox studio lighting with a subtle rim light picks up specular highlights along the handle. The camera arcs 360 degrees with small amplitude at slow speed around the mug. Photorealistic, clean high-key look, neutral palette, 8K detail.
[Shot 2] At 00:06.000, the camera cuts to an extreme close-up of the same matte-black ceramic mug's surface, fine speckled texture visible. A soft directional light rakes across the surface as the camera pans right with small amplitude at slow speed. Hyperdetailed, neutral palette, premium mood.

overall_soundscape: A quiet room tone continues throughout while the ceramic surface softly taps against the stone base as the mug rotates.

non_diegetic_music: A soft pizzicato pattern at a moderate tempo, fading out at the end of the second shot.
```

Why: keep "matte-black ceramic mug", lighting, and palette identical across shots; only shot size and motion change so the clips cut cleanly.

---

## 5. T2VA — Food (single shot, 8 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, an overhead flat lay transitions to a 45-degree angle over a steaming bowl of phở with lime, chili, and fresh herbs on a rustic wooden table. Warm window light from the left highlights the rising steam. The camera pushes in with small amplitude at slow speed. Food-photography palette with rich reds and greens, shallow depth of field.

overall_soundscape: A quiet kitchen ambience continues underneath while broth softly simmers and chopsticks tap the rim of the bowl once.

non_diegetic_music: A light acoustic-guitar arpeggio at a moderate tempo, joined by a single flute counter-melody.
```

---

## 6. T2VA — Talking head / training (single shot, 12 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a medium shot at eye-level frames a professional in a navy blazer speaking directly to camera in a modern office with a soft bokeh background. Two-point softbox lighting with a gentle rim light keeps her face evenly lit. The camera holds a static shot with one slow zoom in at slow speed. Clean corporate look, neutral color balance, sharp focus on face. The professional with a calm, measured voice (S1) says: <d>[English] Welcome back. In this module we walk through three things: planning, execution, and review.</d>

overall_soundscape: A quiet office room tone continues throughout while the speaker's chair softly creaks once.

non_diegetic_music: N/A
```

Why: static camera + two-point lighting = interview standard; speaker ID `(S1)` set on first vocal event; dialogue inside `<d>` block.

---

## 7. T2VA — Neon night street (single shot, 8 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a low-angle medium shot frames a man in a black leather jacket walking through a rain-soaked Hanoi street at night. Neon shop signs reflect on wet asphalt while rim lighting from city lights separates him from the dark. The camera trucks right at slow speed, tracking his walk. Neon-noir aesthetic, teal and magenta palette, anamorphic lens flare.

overall_soundscape: Steady rain falls on metal awnings and distant motorbike engines hum in the alley while his boots splash through shallow puddles.

non_diegetic_music: A muted synth-bass line at a slow tempo, joined by sparse saxophone notes, fading out in the final second.
```

---

## 8. T2VA — Landscape / travel (single shot, 10 s)

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, an aerial FPV drone shot flies low over terraced rice fields in Mu Cang Chai at golden hour. Sun-kissed slopes cast long shadows and wind ripples the paddy water. The camera pushes forward at fast speed then pulls up with small amplitude to reveal the wider valley. Vibrant HDR with warm golden hues, sharp deep focus.

overall_soundscape: Wind rushes past the drone while distant water buffalo bells faintly clink and birds call once across the valley.

non_diegetic_music: A wide orchestral swell at a moderate tempo, joined by sustained low strings.
```

Note: this is two motions (`push forward` then `pull up`). On weaker renders, split into two clips.

---

## 10. T2VA — Vertical Reels / TikTok (single shot, 8 s)

```
integrated_multimodal_description: [Shot 1] Authentic mobile phone photography style, a 9:16 vertical frame captures a young woman unboxing a skincare package at a bright kitchen table. Natural window light from the right throws soft shadows. The camera holds a handheld static shot with a slight shake. Vibrant but natural colors, candid feel.

overall_soundscape: A bright kitchen ambience continues while paper crinkles as the package opens.

non_diegetic_music: A light pop melody at a moderate tempo, fading out at the end.
```

---

## 11. I2VA — Story / flashback with reference image

```
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, the young woman shown in <Picture 1> remains beside the rain-covered train window, preserving her appearance, clothing, seat position, and the carriage layout. The camera trucks right with small amplitude at slow speed as she lifts her gaze from a folded letter toward the passing city lights. Her reflection moves across the glass while the quiet, breathy young woman (S1) says: <d>[English] I get off at the next station.</d> She folds the letter along its existing crease.

overall_soundscape: The train wheels produce a steady metallic rhythm beneath a low ventilation hum while rain ticks against the window and paper rustles softly in her hands.

non_diegetic_music: Sustained cello notes at a slow tempo with widely spaced piano tones, gradually decreasing in volume.
```

---

## 12. FL2VA — Single-shot path between first and last frame (8 s)

```
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot 1) aligns with the 8.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, a rain-soaked cyclist begins in the position and framing established by Picture 1, holding a closed black umbrella beside a silver bicycle. The camera pulls out with small amplitude at slow speed as she releases the bicycle handle, raises the umbrella above her shoulder, and presses the runner upward until the canopy opens. Water rolls from the expanding fabric while she steps beneath it, rotates the handle into the final angle, and settles into the pose, spacing, and composition established by Picture 2 at the end of the shot.

overall_soundscape: Rain falls steadily on the pavement, followed by the metallic click of the umbrella runner and the soft snap of the canopy opening. Water drips from the bicycle frame as distant traffic passes.

non_diegetic_music: N/A
```

---

## 13. L2VA — Inferring the opening, landing on a supplied last frame (6 s)

```
How the reference pictures align with the target video — <Picture 1> (from [Shot 1]) aligns with the 6.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, a close shot begins with an intact drinking glass near the edge of a dark wooden table, while the same hand and sleeve visible in <Picture 1> approach from the right. The camera pushes in with small amplitude at slow speed as the fingertips strike the rim. The glass tips, falls, and hits the floor with a sharp impact; cracks spread through it as fragments slide outward. Toward the end, the moving pieces lose momentum and settle into the exact broken arrangement, hand position, camera angle, lighting, and final composition established by <Picture 1>.

overall_soundscape: Fingertips tap the glass before it scrapes across the tabletop, falls, and breaks with a sharp crash. Small fragments scatter and gradually stop sliding across the floor.

non_diegetic_music: A low electronic pulse at a slow tempo, ending immediately after the glass breaks.
```

---

## 14. Ref2VA — Character continuity across shots, voice-timbre reference

```
subject_definitions:
<Subject 1> is the young woman in <Picture 1>, with shoulder-length black hair, a faded indigo wrap coat, and a thin silver necklace.
<Subject 2> is the young man in <Picture 2>, with short wavy brown hair and a dark-grey hoodie with drawstrings.
<Subject 3> is the coffee-shop environment in <Picture 3>, featuring an exposed brick wall, an orange tufted sofa with patterned pillows, a neon sign, and a wooden coffee table.
<Audio 1> is the voice-timbre reference for <Subject 1> (S1), containing a spoken English vocal layer.

summary:
[reference generation + audio reference] The target video shows <Subject 1> and <Subject 2> having a short conversation in <Subject 3>. The three-shot exchange uses <Audio 1> as the voice-timbre reference for <Subject 1> and ends on <Subject 2> looking down at his empty cup.

retention_analysis:
<Subject 1> (appears in [Shot 1], [Shot 3]): fully_preserved - the young woman's identity, shoulder-length black hair, faded indigo wrap coat, and thin silver necklace are retained.
<Subject 2> (appears in [Shot 2], [Shot 3]): fully_preserved - the young man's short wavy brown hair and dark-grey hoodie with drawstrings are retained.
<Subject 3> (appears in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - the exposed brick wall, orange tufted sofa, patterned pillows, neon sign, and wooden coffee table are retained.
<Audio 1>: reference - its vocal timbre guides the dialogue delivery of <Subject 1> without copying the original signal.

detailed_description:
The target video is in a cinematic, warm-light style with a slightly desaturated palette and a steady 24-frame-per-second feel.
[Shot 1] Live-action, cinematic, a medium close-up frames <Subject 1> seated against the orange tufted sofa in <Subject 3>, the neon sign glowing softly in the background. Soft window light falls across her face as the camera holds a static shot. The quiet young woman with a measured, breathy voice (S1) says: <d>[English] You said you'd be here twenty minutes ago.</d>
[Shot 2] At 00:04.000, the camera cuts to a reverse medium close-up of <Subject 2> seated across the table, his dark-grey hoodie lit by the same soft window light. The camera pushes in with small amplitude at slow speed as the young man (S2) replies: <d>[English] The train was late. I'm here now.</d>
[Shot 3] At 00:08.000, the camera cuts to a wide two-shot showing both <Subject 1> and <Subject 2> at the wooden coffee table in <Subject 3>. The camera dollies out with small amplitude at slow speed to reveal the full sofa and the neon sign. <Subject 1> lifts her cup while <Subject 2> looks down at his empty cup.

overall_soundscape: Quiet indoor room tone and a low ventilation hum continue throughout while cups softly clink against the wooden coffee table and the neon sign hums faintly.

non_diegetic_music: A restrained solo-piano line at a slow tempo with sustained low cello underneath and no swell.
```

Why each piece:

- `subject_definitions` declares every visual reference before it is used, with provenance.
- `summary` carries the `[reference generation + audio reference]` task-type prefix and uses the same labels.
- `retention_analysis` lists one line per reference with a fixed relationship marker (`fully_preserved`, `reference`).
- `detailed_description` opens with the style **outside** `[Shot 1]`.
- Speakers are `<Subject N> (Sx)`; dialogue is `<d>[English] ...</d>`.

---

## 15. Negative / exclusion phrasing (positive restatement)

H3 does not accept negative prompts. Rewrite exclusions as affirmative clauses inside the shot description:

| Instead of | Write (inside the shot) |
|---|---|
| `no subtitles` | `clean frame with no on-screen text` |
| `no watermark` | `clean frame with no watermark or logo` |
| `no extra fingers` | `hands with five fingers each, anatomically correct` |
| `no blurry face` | `sharp focus on the subject's face, hyperdetailed features` |
| `not anime` | `cinematic live-action, photorealistic, no stylization` |
| `no modern buildings` | `period setting with traditional wooden buildings, no contemporary architecture, no neon, no vehicles` |

---

## 16. FACS-driven emotional close-up — single shot, 6 s

Uses Action Units from `references/07-facs.md` instead of bare emotion words. Sequence the AUs in time, name the peak cluster, and describe the release.

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, an extreme close-up frames the young woman's face, eyes to chin visible. Soft window light from the left throws a gentle shadow along the right side of her nose. The camera holds a static shot. At 00:01.000, her inner brows rise (AU1), then her outer brows lift (AU2), then her upper lids raise (AU5), then her jaw drops (AU26) — surprise. At 00:03.000, the expression shifts: brows knit together and pull down (AU4), lip corners pull down (AU15), chin raises (AU17) — grief replacing surprise. At 00:05.000, her face relaxes back to neutral, her jaw closing, brows returning to baseline. Her eyes stay dry; no tears fall; she does not smile. Muted warm palette with lifted blacks, 35mm film grain.

overall_soundscape: A quiet room tone continues underneath while her breath catches once at 00:01.000 and a soft exhale follows at 00:05.000.

non_diegetic_music: A solo piano line at a slow tempo, joined by sustained low strings, fading out in the final second.
```

Why each piece:

- **Time-sequenced AUs** — H3 reads the order literally; `then` is the connective. Surprise first (1.0–2.5 s), grief (3.0–4.5 s), release (5.0 s).
- **3–5 AUs per cluster, not all 12** — surprise cluster is `AU1 + AU2 + AU5 + AU26`; grief cluster is `AU4 + AU15 + AU17`. Anything more blurs.
- **Intensity is left at default** — for a 6 s shot with two peaks, full-strength AUs read fine. For a longer sustained close-up, fold in `slightly` / `sharply` from section D of the FACS reference.
- **Affirmative exclusions at the end** — `eyes stay dry, no tears fall, does not smile` — these prevent the model from overshooting into melodrama, the most common H3 failure for emotional close-ups (see `SKILL.md` 8.6).
- **Lighting + palette consistent** — soft window light + muted warm palette already imply an intimate interior. The AUs complete the emotional read; without them the same lighting reads as "contemplative quiet", not "shock then grief".

---

## 17. FACS + body pose combination — medium shot, 5 s

Pairs face AUs with body pose (`references/06-materials-weather-pose.md`).

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a medium shot at eye-level frames a young woman in a charcoal-grey hoodie standing in a dim corridor. Cool window light from behind throws her face into partial shadow. The camera holds a static shot with a single slow push in at slow speed. Her head tilts down (head-down pose), shoulders hunched, hands clasped at her waist. At 00:02.000, her inner brows rise (AU1), then her brows knit together and pull down (AU4), then her lip corners pull down (AU15), then her chin raises (AU17) — restrained grief. She does not cry, she does not speak, her eyes stay dry. Cinematic color grading, muted cool palette, shallow depth of field.

overall_soundscape: A quiet corridor ambience continues while her breath steadies once and her hoodie fabric rustles as she shifts her weight.

non_diegetic_music: N/A
```

Why each piece:

- **Face AUs match body pose** — AU1 + AU4 + AU15 + AU17 is the sadness cluster. `head-down pose + shoulders hunched + hands clasped` is the containment/sadness body pose from `references/06`. They reinforce each other; using AUs with the wrong body pose (e.g., AU6 + AU12 happy-smile AUs + hunched posture) reads as off-key.
- **Affirmative exclusions** — `does not cry, does not speak, eyes stay dry` — three constraints prevent the model from escalating the emotion past the intended level.
- **Static camera + slow push in** — the push-in creates tension without requiring the model to manage multiple camera moves in a 5 s shot.
- **`overall_soundscape` carries the breath + fabric rustle** — these are diegetic physical sounds. They belong in the description, not in `overall_soundscape`. (Oops — for H3 they should move into `integrated_multimodal_description`. The example shows them in `overall_soundscape` to demonstrate the difference between the two fields; in production put diegetic sounds where the action happens.)

---

## 18. FACS — short reference card

Quick lookup for the 10 most reliable emotion clusters (full list in `references/07-facs.md` section C).

| Emotion | AUs |
|---|---|
| Surprise | `AU1 + AU2 + AU5` (+ `AU26` for jaw drop) |
| Fear | `AU1 + AU2 + AU4 + AU5 + AU20 + AU26` |
| Sadness | `AU1 + AU4 + AU15 + AU17` |
| Anger | `AU4 + AU5 + AU7 + AU23 + AU24` |
| Happiness (Duchenne) | `AU6 + AU12 + AU7 + AU25` |
| Disgust | `AU9 + AU10 + AU17 + AU4` |
| Contempt | `AU12L` (one-sided) + `AU14` |
| Embarrassment | `AU6 + AU12 + AU51` (head turn) |
| Pain | `AU4 + AU7 + AU9 + AU10 + AU20 + AU43` |
| Confusion | `AU1L + AU4R` (asymmetric) |

---

## 19. Editing — multi-shot with cut rhythm and audio carry-over (Ref2VA, 12 s)

Demonstrates `references/08-editing-transitions.md` vocabulary: shot-reverse-shot, audio-across-cuts, dialogue continuity with `<scenetrans>`, and a final dissolve.

```
subject_definitions:
<Subject 1> is the young woman in <Picture 1>, with shoulder-length black hair, a faded indigo wrap coat, and a thin silver necklace.
<Subject 2> is the young man in <Picture 2>, with short wavy brown hair and a charcoal-grey hoodie.

summary:
[reference generation] The target video is a 12-second conversation between <Subject 1> and <Subject 2> on a rain-soaked bridge at night. Shot-reverse-shot builds the dialogue; a dissolve on the final beat releases into a wide shot of the empty bridge.

retention_analysis:
<Subject 1> (appears in [Shot 1], [Shot 3], [Shot 4]): fully_preserved - identity, garment, and accessories retained.
<Subject 2> (appears in [Shot 2], [Shot 3]): fully_preserved - identity and garment retained.

detailed_description:
[Shot 1] Live-action, cinematic, a medium close-up at eye-level frames <Subject 1> on a rain-soaked bridge at night, neon shop signs from across the river reflecting on wet metal. Rim lighting from a distant streetlamp separates her from the dark. The camera holds a static shot. <Subject 1> (S1) says: <d>[English] I didn't think you'd come.</d>
[Shot 2] At 00:03.500, the camera cuts to a reverse medium close-up of <Subject 2>, his eyeline matching hers from the previous frame, the same neon reflections visible across the river behind him. The camera holds a static shot. <Subject 2> (S2) says, <scenetrans>[English] I didn't think you wanted me to.</scenetrans> Her voice from the previous shot carries over for the first half-second of this frame before his voice begins.
[Shot 3] At 00:07.000, the camera cuts to a wider two-shot of both figures standing three meters apart on the bridge, the city skyline behind them. The camera pushes in with small amplitude at slow speed. <Subject 1> (S1) exhales; <Subject 2> (S2) steps one pace closer. They do not speak.
[Shot 4] At 00:10.500, the shot dissolves to an extreme wide establishing shot of the empty bridge, the figures gone, the neon reflections continuing on the wet metal, the rain still falling. The shot holds until the end of the video.

overall_soundscape: Steady rain falls on metal railings throughout, mixed with distant traffic hum from across the river. Footsteps squelch on wet asphalt in Shot 3. A long exhale at 00:07.500.

non_diegetic_music: A solo cello line at a slow tempo, joined at Shot 3 by sustained low strings, fading out as the empty bridge dissolves in.
```

Why each piece:

- **180-degree rule stated once.** Both `[Shot 1]` and `[Shot 2]` keep the same eyeline direction (subjects face each other across the axis).
- **`<scenetrans>` for dialogue crossing a cut.** The line `I didn't think you wanted me to.` begins in the audio sense before S2's lips start — the carry-over phrase `Her voice from the previous shot carries over for the first half-second` makes the audio behavior explicit.
- **Dissolve only when it's not a straight cut.** Shots 1→2 and 2→3 use `cuts to`. Shot 3→4 uses `dissolves to` because the empty bridge is a deliberate stylistic release, not a continuity cut.
- **`overall_soundscape` carries ambient + physical + non-verbal human** (rain, traffic, footsteps, exhale) across all four shots — not separated per shot. The dialogue goes in the shot that produces it; ambient sound is summarized in the single paragraph.

---

## 20. Sound design — leitmotif across shots, scene with recurring motif (12 s)

Demonstrates `references/09-sound-design.md` vocabulary: a recurring leitmotif, voiceover narration, and the strict diegetic / non-diegetic split.

```
subject_definitions:
<Subject 1> is the old woman in <Picture 1>, in her late seventies, with white hair, a worn brown shawl, and weathered hands.

summary:
[reference generation + audio reference] The target video is a 12-second sequence following <Subject 1> through a winter morning in her small house. A piano leitmotif returns three times; her voiceover narration frames the sequence.

retention_analysis:
<Subject 1> (appears in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - identity, white hair, brown shawl, weathered hands retained.

detailed_description:
[Shot 1] Live-action, cinematic, a medium shot frames <Subject 1> standing at the kitchen window of a small wooden house at dawn, the first pale light on the snow outside. Soft window light from the left, cool blue palette, breath visible in the cold air. The camera holds a static shot. <Subject 1> says in an off-screen voiceover: <d>[English] When I was a girl, the snow used to come up to the windowsill.</d> while her lips remain completely closed.
[Shot 2] At 00:04.500, the camera cuts to a close-up of her weathered hands turning the pages of an old photograph album. Warm window light from the left, shallow depth of field, the same four-note piano phrase from Shot 1's score returning as a leitmotif. <Subject 1> says in an off-screen voiceover: <d>[English] And we'd stay inside for days, watching the world disappear.</d> while her lips remain completely closed.
[Shot 3] At 00:09.000, the camera cuts to a wide shot of <Subject 1> in profile, standing at the window again, the snow piled higher outside than the windowsill. The same four-note piano phrase returns, now joined by sustained low strings. <Subject 1> does not speak. The camera holds a static shot as her breath fogs the glass.

overall_soundscape: A quiet house tone continues throughout — the wood floor settling, the radiator ticking softly, wind moving past the window. Her breath fogs the glass once at 00:10.500.

non_diegetic_music: A solo piano phrase at a slow tempo — four rising notes — appears three times: as the opening score in Shot 1, returning as a leitmotif in Shot 2, and joined by sustained low strings in Shot 3 as the four-note phrase is heard for the final time before fading out.
```

Why each piece:

- **Strict diegetic / non-diegetic split.** Voiceover goes in `[Shot N]` with the lips-closed note. Ambient sound (house tone, floor settling, radiator, wind) goes in `overall_soundscape`. Score goes in `non_diegetic_music`. Nothing is mixed across the three fields.
- **Leitmotif returns with explicit reference.** `the same four-note piano phrase from Shot 1's score returning as a leitmotif` and `the same four-note piano phrase returns, now joined by sustained low strings`. H3 reads the cross-shot reference literally.
- **Voiceover text is verbatim.** Both `<d>` blocks quote real text from the brief, in English, with the lips-closed note following each.
- **Leitmotif documented in both places.** It's named in the shot description (so the model places it in the audio) AND summarized in `non_diegetic_music` (so the field is well-formed as one paragraph).