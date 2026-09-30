---
name: cinematic-video-prompt-h3
description: Use when writing or fixing prompts for MiniMax H3 video generation (T2VA, I2VA, FL2VA, L2VA, Ref2VA) — cinematic camera angles, camera movement, lighting, composition, style, color grading, mood, and a H3-aware prompt template that produces the three required fields (integrated_multimodal_description, overall_soundscape, non_diegetic_music) or the six required Ref2VA sections. Translates free-form cinematic vocabulary into H3's natural-language shot-description grammar.
---

# Cinematic Video Prompt — H3 Adapter

A cinematography vocabulary pack that teaches the AI how to write **MiniMax H3** video-generation prompts. The vocabulary is camera-craft language (angles, movement, lighting, composition, style, color, mood); the **container** is H3's structured output: a `[Shot 1] … [Shot N]` timeline plus `overall_soundscape` and `non_diegetic_music`. For reference-driven work (Ref2VA), the container becomes six sections (`subject_definitions`, `summary`, `retention_analysis`, `detailed_description`, `overall_soundscape`, `non_diegetic_music`).

This skill is a **front-end**: it owns the prompt-building grammar (which lens, which key, which motion vocabulary). It is paired with the upstream H3 prompt-writing guide (`minimax-h3-skills:h3-prompt-writing`) which owns the field schema, label conventions, and shot-timing format. Always load both.

## 1. Workflow

1. **Pick the H3 mode** based on the input you have:
   - **T2VA** — text only. Build the full timeline from the brief.
   - **I2VA** — one reference image = first frame of `[Shot 1]`.
   - **FL2VA** — first frame + last frame. Describe the path between them, single shot preferred.
   - **L2VA** — only a last frame. Infer a compatible opening and converge to the supplied image.
   - **Ref2VA** — one or more reference images / videos / audio tracks. Define subjects, retain identity, write a detailed shot-by-shot description.
2. **Collect three things** (or infer them):
   - **Subject + action** — who/what and what are they doing.
   - **Target mood** — drives lighting + color + style trio.
   - **Target video type** — story, product, food, talking-head, night street, landscape, action, vertical Reels/TikTok. This selects the recipe combo.
3. **Pick 1–2 keywords per block** from the vocabulary tables (`references/01` … `references/10`). For emotional close-ups, also load `references/07-facs.md` and use Action Units (AUs) instead of bare emotion words. For multi-shot sequences, load `references/08-editing-transitions.md` (cuts, transitions, audio across edits) and `references/10-storytelling-devices.md` (structure, foreshadowing, frame narrative). For any audio-heavy brief, load `references/09-sound-design.md` (diegetic vs non-diegetic, Foley, leitmotif). Do not stack.
4. **Fold each keyword into H3's natural-language shot grammar.** H3 does **not** accept comma-separated keyword strings. Camera motion becomes an English clause (`the camera pushes in with small amplitude at slow speed toward …`), style and lighting become adjective phrases inside the shot, color becomes a grading clause. Use the mapping table in section 3 as a translator.
5. **Compose the H3 output** using the template for the chosen mode (section 4).
6. **Run the H3 checklist** (section 7) before submitting.
7. **If the prompt is complex** (multiple beats, rare subjects, strong emotions, custom events) re-read section 8 — H3's own failure modes.

Prompt output is always in **English**. Preserve the original language only for dialogue and lyrics inside `<d>…</d>` and for visible on-screen text in double quotes.

## 2. The Prompt Formula, Adapted for H3

> **Evidence status of this skill's recommendations**
>
> - **Documented** — directly supported by the upstream H3 prompt-writing guide (`minimax-h3-skills:h3-prompt-writing`).
> - **Heuristic** — based on observed behavior of current H3-class video models; specific limits (drift, hold time, action complexity) depend on model version and mode.
> - **Experimental** — the term/cluster/format has been promoted as worth trying but not yet validated across model versions.
>
> Where this document says "always" or "never", check the upstream guide first. Cinematography vocabulary (lens choice, lighting setup, blocking) is a heuristic that improves with testing; the field schema and shot-timing format are documented.

The original free-form formula was:

```
[Shot size + Angle], [Subject + appearance], [Specific action], [Setting + weather],
[Lighting], [Camera movement], [Style + color], [Mood], [Technical]
```

In H3, every keyword from that formula must be **woven into a natural-language shot description**, in this order, inside `[Shot 1] Live-action, cinematic, …`:

```
[Shot 1] {Style descriptor}, {camera setup + angle}, {subject + appearance + action + setting},
{lighting}, {camera motion clause (motion type + amplitude + speed)},
{color grading clause}, {technical: depth of field, lens, frame rate, grain}.
```

Worked example — the original Vietnamese example, rewritten for H3:

> `Medium close-up, low angle, a young woman in a red áo dài walks slowly through a rainy Saigon alley at night, neon signs reflecting on wet asphalt, rim lighting from city lights, slow dolly in, cinematic, teal and orange grading, melancholic mood, shallow depth of field, 35mm film grain`

becomes (T2VA, 6-second single shot):

```
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a medium close-up from a low angle frames a young Vietnamese woman in a long red áo dài, slow walk through a narrow rain-soaked Saigon alley at night. Neon shop signs reflect in the wet asphalt while rim lighting from city lights separates her hair from the dark background. The camera pushes in with small amplitude at slow speed toward her face as her expression shifts from composed to melancholic. Teal and orange color grading, shallow depth of field, 35mm film grain, 2.35:1 aspect.

overall_soundscape: Steady rain patters on metal awnings and distant motorbike engines hum in the alley while the woman's sandals splash through shallow puddles.

non_diegetic_music: A slow solo-cello line joined by sparse piano notes, sustained and quiet, fading in the final second.
```

Five things changed vs. the original free-form prompt:

1. **Shot `[Shot 1]` wrapper** and a comma-separated H3 style tag (`Live-action, cinematic,`).
2. **Camera motion is a clause**, not a tag: `The camera pushes in with small amplitude at slow speed toward …`. H3 understands the explicit `(motion type + amplitude + speed)` triplet; pick amplitude and speed only when they matter.
3. **Color grading is a clause**, not a tag: `Teal and orange color grading, …`.
4. **Mood is implied**, not declared. Melancholy is signaled by lighting (low key, desaturated), color (muted warm), and subject expression. Saying `melancholic mood` is redundant once the lighting and palette already carry that signal.
5. **Two new fields appear**: `overall_soundscape` (ambient and physical sounds across the whole video) and `non_diegetic_music` (score audible only to the audience).

## 3. Vocabulary → H3 Grammar Mapping

The 11 free-form keyword blocks from the original skill map onto H3 grammar like this:

| Original block | H3 grammar slot | Phrasing pattern |
|---|---|---|
| Shot size + angle | After `[Shot 1] {style},` | `a {close-up/medium shot/wide} from a {low/eye-level/high} angle frames …` |
| Subject + appearance | Subject clause | `a young woman in {garment}, {hair/skin/build} …` |
| Specific action | Subject clause (continues) | `who {walks slowly through / reaches for / lifts …}` |
| Setting + weather | Subject clause (continues) | `… in / at {place}, {weather/lighting-condition}.` |
| Lighting | New sentence in shot | `Lighting comes from {source}; {quality} light falls on {subject/area}.` or inline adjectives: `rim-lit, soft window light, low-key chiaroscuro.` |
| Camera movement | New sentence in shot | `The camera {pushes in / dollies out / arcs / pans / holds} {with small/large amplitude} {at slow/fast speed} {toward / past / around} {subject}.` |
| Style + color | New sentence in shot, or grading tag at end | `Teal and orange color grading,` / `Film-noir aesthetic, deep shadows,` |
| Mood | (Drop or signal via lighting/palette/expression) | Show, don't tell — set palette and expression, no `mood:` tag. |
| Technical | Last clause(s) in shot | `shallow depth of field, 35mm film grain, 2.35:1 aspect,` |
| Aspect ratio | Trailing tag in shot or set on model side | H3 has model-side aspect control; setting AR there is usually cleaner. Writing `2.35:1 aspect,` or `9:16 vertical frame,` inside the description is allowed when you want the model itself to bias the framing — pick one route, not both. |
| Negative prompt | **Not used** in H3. | H3 follows positive description. Phrase exclusions as affirmative opposites: `clean frame, no on-screen text, no watermark, no subtitles,` |

Camera-motion vocabulary (H3's exact allowed set):

| Motion type | Amplitude | Speed |
|---|---|---|
| Zoom In / Zoom Out | with small amplitude | at slow speed |
| Push In / Pull Out | with large amplitude | at fast speed |
| Pan Left / Pan Right | (omit if medium) | (omit if normal) |
| Truck Left / Truck Right | | |
| Tilt Up / Tilt Down | | |
| Pedestal Up / Pedestal Down | | |
| Arc Shot | | |
| Tracking Shot | | |
| Static Shot | | |
| Shake Slightly / Shake Strongly | | |
| POV | | |
| Roll Clockwise / Roll Counterclockwise | | |

Always write the triplet inline as one action clause, not as three stacked labels.

## 4. Output Templates per Mode

### 4.1 T2VA template (text only, no reference)

```
integrated_multimodal_description: [Shot 1] {Style descriptor, e.g. Live-action, cinematic,}, {shot size + angle}, {subject + appearance + action + setting + lighting}. {Camera-motion clause}. {Color grading + technical closing clause.}
[Shot 2] At MM:SS.mmm, the camera cuts to {new shot description}. {continuity note}.

overall_soundscape: {1–4 sentences covering ambient + physical + non-verbal human sound across the whole video. No dialogue. No music.}

non_diegetic_music: {1–3 sentences of score audible only to the audience. Use N/A if none. This field is for music only — voiceover and audience-only sound effects belong in the shot description.}
```

Replace `[Shot 1]` with the chosen style tag (`Live-action, cinematic,`, `2D-animated,`, `3D CG,`, `claymation,`, `watercolor,`, `vintage film,` …). Always state the overall style and initial composition at the start of `[Shot 1]`.

> **Ref2VA differs in one place:** style and initial composition live in one or two English sentences **before** `[Shot 1]` inside `detailed_description`, not inside the first shot. See section 4.5.

### 4.2 I2VA template (one reference image as `[Shot 1]` first frame)

First line (instruction, mandatory):

```
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.
```

Then the three core fields. The description must preserve the appearance, clothing, seat position, and spatial layout established by `<Picture 1>` and develop forward from it (anchor → action → continuous development → result/reaction).

### 4.3 FL2VA template (first frame + last frame, single shot preferred)

```
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot N) aligns with the S.SS-second mark of the target video.
```

Body describes the **path** between the frames: first-frame state → observable intermediate changes → progressively narrowing differences → last-frame state. Do not repeat two static image descriptions; describe the motion that connects them.

### 4.4 L2VA template (only a last frame)

```
How the reference pictures align with the target video — <Picture 1> (from [Shot N]) aligns with the S.SS-second mark of the target video.
```

Body establishes a compatible earlier state, then describes the action and transition path that **converges** to the supplied image in the final shot (plausible preceding state → explicit action → gradual convergence → last-frame landing).

### 4.5 Ref2VA template (full-reference mode)

Six sections in this order:

```
subject_definitions:
<Subject N> is {content definition with reference role and key visual features}.
<Picture N> is {role: first frame / keyframe / last frame / storyboard anchor / …}.
<Video N> is {role: source for edit, continuation source, reference for camera/cut pattern}.
<Audio N> is {role: voice-timbre reference, copied BGM, sound-effect layer}; cite speaker (S#) when bound to a target speaker.

summary:
[{task-type prefix, e.g. reference generation, video editing + audio reuse, keyframe completion}] {One short English paragraph summarizing target video + reference relationships.}

retention_analysis:
<Subject N> (appears in [Shot K], …): fully_preserved | partially_preserved | attribute_transfer | weak_reference - {brief reason}.
<Picture N> ([Shot K] role): {marker} - {reason}.
<Video N> ({structural role}): {marker} - {reason}.
<Audio N>: fully_copy | partially_copy | reference | weak_reference - {reason}.

detailed_description:
{Style + initial composition sentence(s) — established BEFORE [Shot 1].}
[Shot 1] {Style + camera + subject + action + setting + lighting + camera-motion clause + color grading + technical.}
[Shot 2] At MM:SS.mmm, the camera cuts to {…}. {continuity.}

overall_soundscape: {1–4 sentences.}

non_diegetic_music: {1–3 sentences. N/A if none.}
```

Key Ref2VA rules:

- **Style is established one or two English sentences before `[Shot 1]`**, not inside the first shot.
- **Reference labels stay consistent** across all six sections: once `<Subject 1>` is assigned, never redefine.
- **`<Subject N>` carries the visual identity; `(S1)` carries the speaker ID.** When a referenced subject speaks, write `<Subject 1> (S1)`.
- **`<Video N>` and `<Audio N>` are numbered independently.** The same source video may be `<Video 1>` and `<Audio 2>`.
- **`<d>[Language] text</d>`** for dialogue and lyrics inside the shot body. Preserve original language and punctuation verbatim.

## 5. Recipe Combos by Video Type

These are the original skill's 11 type-specific combos, rewritten as **H3-ready shots** (style + camera + lighting + palette + motion in one English sentence). Swap the subject and the setting to fit the brief.

### 5.1 Story / flashback
```
[Shot 1] Live-action, cinematic, a medium close-up at eye-level frames an elderly woman in a faded brown áo bà ba beside a wooden window. Soft window light falls on the photo album in her lap while dust particles drift in the air. The camera pushes in with small amplitude at slow speed as her fingers turn the pages. Muted warm palette with lifted blacks, shallow depth of field, 35mm film grain.
```

### 5.2 Horror / supernatural
```
[Shot 1] Live-action, cinematic, a low-angle Dutch-tilted shot frames a lone figure in a white dress at the far end of an abandoned French colonial corridor. Ground fog creeps along the floor while a single candle at her chest throws a tight circle of light into deep shadow. The handheld camera pushes in with small amplitude at slow speed. Cool desaturated palette with deep shadows, high contrast, 2.35:1 aspect.
```

### 5.3 Wuxia / cultivation fantasy
```
[Shot 1] Live-action, cinematic, an extreme wide establishing shot with a low horizon frames a young cultivator in flowing white hanfu on a cliff edge above an endless sea of clouds at sunrise. God rays break through the mist. The camera cranes up with large amplitude at slow speed to reveal distant mountain peaks. Cinematic fantasy art with ink-wash influence, ethereal golden hues, volumetric lighting.
```

### 5.4 Product (e-commerce)
```
[Shot 1] Live-action, cinematic, an eye-level product shot frames a matte-black ceramic coffee mug on a clean light-grey stone surface. Softbox studio lighting with a subtle rim light picks up specular highlights along the handle. The camera arcs 360 degrees with small amplitude at slow speed around the mug. Photorealistic, clean high-key look, neutral palette, 8K detail, 1:1 framing.
```

### 5.5 Food
```
[Shot 1] Live-action, cinematic, an overhead flat lay transitions to a 45-degree angle over a steaming bowl of phở on a rustic wooden table with lime, chili, and fresh herbs. Warm window light from the left highlights the rising steam. The camera pushes in with small amplitude at slow speed. Food-photography palette with rich reds and greens, shallow depth of field.
```

### 5.6 Talking head / training
```
[Shot 1] Live-action, cinematic, a medium shot at eye-level frames a professional in a navy blazer speaking directly to camera in a modern office with a soft bokeh background. Two-point softbox lighting with a gentle rim light. The camera holds a static shot with a single slow zoom in at slow speed over the duration. Clean corporate look, neutral color balance, sharp focus on face.
```

### 5.7 Neon night street
```
[Shot 1] Live-action, cinematic, a low-angle medium shot frames a man in a black leather jacket walking through a rain-soaked Hanoi street at night. Neon shop signs reflect on wet asphalt while rim lighting from city lights separates him from the dark. The camera trucks right at slow speed, tracking his walk. Neon-noir aesthetic, teal and magenta palette, anamorphic lens flare.
```

### 5.8 Landscape / travel
```
[Shot 1] Live-action, cinematic, an aerial FPV drone shot flies low over terraced rice fields at golden hour. Sun-kissed slopes cast long shadows. The camera pushes forward at fast speed then pulls up with small amplitude to reveal the wider valley. Vibrant HDR with warm golden hues, sharp deep focus.
```

### 5.9 Action
```
[Shot 1] Live-action, cinematic, a wide shot frames a motorbike racer leaning hard into a corner on a sunlit mountain road. Hard midday sunlight throws sharp shadows. The camera tracks right at fast speed with slight motion blur. Cinematic action grade, teal and orange, shutter angle 180 degrees.
```

### 5.10 Vertical Reels / TikTok
```
[Shot 1] Authentic mobile phone photography style, a 9:16 vertical frame captures a young woman unboxing a skincare package at a bright kitchen table. Natural window light from the right. The camera holds a handheld static shot with a slight shake. Vibrant but natural colors, candid feel.
```

### 5.11 Emotional close-up — FACS-driven
```
[Shot 1] Live-action, cinematic, an extreme close-up frames the young woman's face, eyes to chin visible. Soft window light from the left. The camera holds a static shot. At 00:01.500, her inner brows rise (AU1), then her outer brows lift (AU2), then her upper lids raise (AU5), then her jaw drops (AU26) — surprise. At 00:03.500, the expression shifts: brows knit together and pull down (AU4), lip corners pull down (AU15), chin raises (AU17) — grief replacing surprise. Her eyes stay dry, no tears fall. Muted warm palette, 35mm film grain.
```

## 6. Mood → Combo Quick Lookup

| Want | Angle + size | Lighting | Motion | Color |
|---|---|---|---|---|
| Sad, lonely | High angle, wide, small subject | Overcast, blue hour | Slow dolly out | Cool, desaturated |
| Powerful, dominant | Low angle, hero shot | Rim light, hard light | Slow push in or arc shot | High contrast |
| Warm, nostalgic | Medium shot | Golden hour, dappled light | Static or slow pan | Warm, faded film |
| Mysterious, eerie | Dutch tilt, low angle | Low-key, single source, fog | Handheld, slow push in | Cool, deep shadows |
| Epic, awe | Worm's-eye, extreme wide | God rays, volumetric | Crane up, drone flyover | Vibrant HDR |
| Intimate, romantic | Close-up, over-the-shoulder | Soft light, candle, bokeh | Slow push in | Warm pastel |
| Energetic, joyful | Eye-level, medium | Sun-drenched, high-key | Tracking, whip pan | Vibrant, saturated |
| Dreamy, surreal | Any + soft focus | Backlit, haze | Floating drift, slow | Pastel, dreamy glow |

## 7. H3 Pre-flight Checklist

- [ ] Mode picked (T2VA / I2VA / FL2VA / L2VA / Ref2VA) and the right template used. Ref2VA puts style and initial composition **before** `[Shot 1]`, not inside it.
- [ ] `[Shot 1]` opens with the style descriptor and the initial composition in one sentence.
- [ ] Every camera motion is an English clause with motion type + (optional) amplitude + (optional) speed.
- [ ] Style, lighting, and palette generally point the same way. Mismatches (`Ghibli` + `hyperrealistic`) read as mush; deliberate counterpoint (warm interior + grief scene, sunlight + downpour) is fine when you explain it (`the warm afternoon light makes the cold news feel more cruel,` `the rain catches the late sun and breaks it into a thousand glints,`).
- [ ] Emotional close-ups describe visible facial-muscle movements. FACS Action Units (see `references/07-facs.md`) work as auxiliary notation — describing the visible movements in plain English is the primary method; AU codes help disambiguate but are not guaranteed to be parsed literally by the model.
- [ ] **Multiple beats in one shot are fine** — a character can notice a letter, pick it up, read it, and lower her hand inside a single shot. Use a new `[Shot N]` when you want to change **place, angle, or time**, not for every action beat.
- [ ] Subject description (age, hair, garment, key colors) is **identical across shots** of the same story — characters do not change outfits between cuts.
- [ ] Duration matches the requested video length (H3 typically 4–15 s); cut times are formatted `MM:SS.mmm` (e.g., `At 00:03.500,`).
- [ ] Cuts always carry a transition verb (`the camera cuts to` / `dissolves to` / `fades to`). Audio across cuts uses `<scenetrans>` for dialogue and prose carry-over for ambient/SFX.
- [ ] Multi-shot sequences: structure (flashback, parallel editing, frame narrative) is stated once at `[Shot 1]` or in `summary` (Ref2VA). Plant-and-payoff objects recur by the same name across shots.
- [ ] Sound design: `overall_soundscape` covers ambient + physical + non-verbal human sound (no dialogue, no music). `non_diegetic_music` is score only — instrumentation + tempo + dynamic arc, not abstract mood words. Voiceover and audience-only sound effects belong in the shot description, not in `non_diegetic_music`. See `references/09-sound-design.md`.
- [ ] No unresolved reference labels (`<Picture 2>` mentioned but never defined) and no timing that exceeds the requested duration.
- [ ] Dialogue and lyrics are inside `<d>[Language] …</d>`, original language preserved verbatim. Voiceover is followed by `while his/her/their lips remain completely closed.`
- [ ] Visible on-screen text appears in English double quotes (`"营业中"`), original preserved.
- [ ] No `mood:` tag, no `cinematic:` keyword string. Aspect ratio: prefer setting on the model side; if you write it in the description, pick one route only.
- [ ] No negative-prompt block — exclusions are phrased affirmatively inside the shot description (`clean frame with no on-screen text, no watermark, no subtitles`).
- [ ] For I2VA / FL2VA / L2VA / Ref2VA: the instruction line is **the first line of the final prompt**, with one blank line before the core fields.
- [ ] For Ref2VA: `subject_definitions` defines every referenced subject before it is used in `detailed_description`; reference labels stay consistent across all sections; `<Video N>` and `<Audio N>` numbered independently.

## 8. H3 Failure Modes (real-world lessons)

Distilled from running prompts on H3-class video models. Severity varies by model, but most apply generally. Generate a 4-second test clip first before committing to a batch.

### Structure

- **8.1 — Cut timing tolerates ~1–3 s of drift.** A model that drifts 1.5 s on a 6 s clip is normal. Use H3's `At MM:SS.mmm,` format and keep beats tight, but do not over-specify exact frame numbers.
- **8.2 — Start with one dominant motion per shot (heuristic).** Stacking `push in + pan right + tilt up` in the same shot is a recipe for muddy motion on current H3-class models. Pick one dominant move; *combine only when the move naturally implies a second axis* (e.g., a crane that rises while tilting down to keep the subject framed). Test on a 4-second clip before committing.
- **8.3 — Avoid keyword stuffing.** A long comma-separated list works in free-form mode, but in H3 grammar it becomes a long run-on sentence that the model reads literally. Pick 1–2 keywords per block.
- **8.4 — Do not pin numeric duration inside the description.** H3 has model-side duration control. Writing `exactly 6 seconds` inside the shot description is ignored or, worse, fights the model-side setting.

### Characters and emotion

- **8.5 — Identity drifts across shots.** This is the #1 H3 failure mode. Mitigations: (a) keep the same context (lighting, palette, garment) across shots of the same character; (b) repeat the character tag (e.g., `the same young woman in the red áo dài`) at the start of every relevant shot, not just once at the top; (c) for Ref2VA, anchor identity through `<Subject N>` and use it in every shot.
- **8.6 — Emotional close-ups overshoot.** Sequence emotion beats explicitly. **Plain-English visible descriptions are the primary tool** — `her inner brows rise, then her upper lids lift, then her jaw drops` is what the model reads. **FACS Action Units** (see `references/07-facs.md`) work as auxiliary notation: the codes themselves are not guaranteed to be parsed literally, but the muscle-by-muscle phrasing they imply (visible movements in time order, with intensity) renders more reliably than bare words like `surprised face`. Cap at 3–5 visible movements per cluster; intensity matters (`slightly` / `sharply` / `fully`); describe the peak and the release. Affirmative exclusions still help: `the tear stays in her eye and does not fall; she does not smile, does not clap.`
- **8.7 — Named exotic subjects fail.** A bare noun (`gecko`, `black dragon`) tends to render as a generic lizard / snake. Describe the parts: `a small lizard with adhesive toe pads, vertical pupils, and a tapering prehensile tail`. Same applies to fantasy creatures, fashion silhouettes, and rare plant species.

### Style, text, events

- **8.8 — Style drifts when the subject is unfamiliar.** A modern character appearing in a period setting can pull the render toward generic realism. Repeat the style tag (`Live-action, cinematic, period drama,`) in every shot, and add affirmative exclusions if needed (`no modern buildings, no neon, no contemporary vehicles`).
- **8.9 — On-screen text is unreliable.** Short quoted strings in CJK or Latin (`"营业中"`, `"SALE"`) usually render; full slogans, neon Chinese signage, Japanese kanji often produce illegible glyphs. Title cards, subtitles, and karaoke are best done in post. For clean frames, state `clean frame with no on-screen text, no watermark, no subtitles`.
- **8.10 — State events with position + moment + visible result.** `the door swings open` reads weak; `at 00:03.500, the second door on the left swings fully open, revealing a pitch-dark interior` reads strong. Always describe what you want to see, not what you want to avoid.
- **8.11 — Long continuous shots work when path is described step by step.** FPV drone opens, MV establishing moves, dream sequences — all read better with explicit legs: `Route: fly over the ridge → bank left past the temple → descend into the valley.`

### Audio

- **8.12 — H3 distinguishes diegetic vs non-diegetic strictly.** Anything a character can hear belongs in `integrated_multimodal_description` / `detailed_description` (synchronized with the shot that produces the sound). The two audio fields have narrow roles:
  - `overall_soundscape` — ambient + physical + non-verbal human sound (diegetic, no dialogue, no music).
  - `non_diegetic_music` — score audible only to the audience (non-diegetic music).
  - Voiceover and audience-only sound effects do **not** belong in `non_diegetic_music` — that field is music only. Put voiceover inside the shot description as `<d>…</d> while her lips remain completely closed.`. See `references/09-sound-design.md` for the full diegetic / non-diegetic split, Foley vocabulary, and the field-filling patterns.
- **8.13 — `overall_soundscape` is one paragraph.** Do not bullet it. Summarize the ambient + physical + non-verbal human sound across the full video in 1–4 English sentences. Use named sources (`kettle whistles once`, `rain taps against metal awnings`), not abstract mood phrases (`cinematic background noise`).
- **8.14 — Voiceover requires the lips-closed note.** Every voiceover `<d>` block must be followed by `while his/her/their lips remain completely closed.`

### Editing & Transitions

- **8.16 — Cuts need a transition verb.** `[Shot 2] At MM:SS.mmm, the camera cuts to …` — without `cuts to`, H3 reads the new line as a continuation of the same shot, not a cut. For non-cut transitions (dissolve, fade, wipe, iris), name the transition type explicitly. See `references/08-editing-transitions.md` for cut types, audio-across-cuts (J-cut / L-cut / sound bridge), and rhythm patterns (montage / parallel editing).
- **8.17 — Audio-across-cuts uses `<scenetrans>`.** When dialogue continues across a cut, use the `<scenetrans>` tag inside `<d>` and state the carry-over (`carries over from the previous shot`, `continues uninterrupted into the next shot`, `remains audible across the transition`). Audio cues that are not dialogue just describe the carry-over in prose, no tag needed.
- **8.18 — Match cuts work best with echoed framing.** State the matching element explicitly: `the camera cuts to a reverse close-up of him, his eyeline matching hers from the previous frame, …`. Implicit match cuts rarely fire.

### Storytelling & Structure

- **8.19 — State the structure once at the start.** A flashback that does not signal when it lives reads as present. Use explicit markers: `the shot cuts to a flashback — twenty years earlier, …` or `at MM:SS.mmm, the shot cuts to a flashforward —`. For multi-shot H3 sequences, the structure lives in `summary` (Ref2VA) or in the first shot of `[Shot 1]`.
- **8.20 — Plant-and-payoff needs both halves.** A foreshadowed object must return in the payoff shot. `the red thread` in Shot 1 must become `the same red thread` in Shot 5 — by the same name, in the same form. See `references/10-storytelling-devices.md` for the full device list (MacGuffin, red herring, Chekhov's gun, cliffhanger, dramatic irony, unreliable narrator, breaking fourth wall).
- **8.21 — Cliffhangers belong at the end of the last shot.** If the brief calls for a cliffhanger, end on the unresolved moment — `the door opens; the shot ends on her reaction, just as the figure is revealed.` Do not cut to resolution.

### Licensing

- **8.15 — Do not name films, games, studios, or copyrighted characters.** The model may drift toward an IP-shaped render and there is a legal risk. Describe the design of your own.

## 9. Response Format

When asked to write a prompt, return:

1. The H3 prompt (one or more paragraphs, paste-ready). Use the template for the chosen mode.
2. One short English sentence explaining the dominant cinematic choices (which shot size, which lighting, which motion → which feeling).
3. For a sequence of clips: number each clip, note which blocks stay constant (character, style, palette) and which change (action, camera).

## 10. Pairing With the Upstream Skill

This skill owns the **prompt content** (cinematic vocabulary → H3 grammar). For field schema, label conventions, and shot-timing format, always cross-check the upstream:

- `minimax-h3-skills:h3-prompt-writing` and its `references/base-en.txt` (T2VA / I2VA / FL2VA / L2VA) and `references/ref-en.txt` (Ref2VA).

When the two skills conflict, the upstream guide wins on field schema and label format; this skill wins on camera / lighting / composition / style vocabulary and on the recipe combos.

## 11. Deep-Dive References

The full 700+ term vocabulary lives under `references/`. Each file opens with an H3 mapping note explaining how to fold its terms into H3 grammar:

- `references/01-camera-angles-and-movement.md` — shot sizes, camera angles, camera-motion golden prompts, and the H3 motion-type vocabulary.
- `references/02-lighting.md` — natural light, dramatic light, studio light, urban / artificial light, material-aware light.
- `references/03-composition.md` — foundational rules, leading lines, balance and symmetry, depth and space, rhythm and contrast.
- `references/04-lens-technical-film.md` — focal length, aperture and depth of field, bokeh, flares, shutter and motion, film stocks and grading.
- `references/05-style-color-mood.md` — artistic style, color palette and grading, mood and emotion.
- `references/06-materials-weather-pose.md` — materials and textures, weather and atmosphere, character pose.
- `references/07-facs.md` — Ekman & Friesen's Facial Action Coding System. Action Units (AUs) for emotional close-ups, validated emotion clusters (surprise / fear / sadness / anger / happiness / disgust / contempt / pain), intensity vocabulary, asymmetry, and the H3 phrasing patterns for time-sequenced beats.
- `references/08-editing-transitions.md` — cuts, transitions, audio across edits (J-cut / L-cut / sound bridge), rhythm (montage / parallel editing / cross-cutting), and the cut-timing patterns that drive multi-shot H3 sequences.
- `references/09-sound-design.md` — diegetic vs non-diegetic split (the foundation of H3's two audio fields), Foley, leitmotif, sound motif, stinger, voiceover narration, sonic worldbuilding, and the recipes for filling `overall_soundscape` and `non_diegetic_music`.
- `references/10-storytelling-devices.md` — three-act structure, in medias res, flashback / flashforward, frame narrative, parallel storylines, foreshadowing, plant-and-payoff, MacGuffin, red herring, cliffhanger, dramatic irony, unreliable narrator, breaking fourth wall, voiceover narration.

Worked H3-formatted examples live in `examples/example-prompts-h3.md`.

Bonus skills for H3:

- `bonus-skills/character-sheet-lite/SKILL.md` — character reference sheets. The sheet's output image feeds into H3 as `<Picture 1>` for I2VA or as the source image defining `<Subject 1>` for Ref2VA.
- `bonus-skills/oriental-scene-lite/SKILL.md` — Wuxia / Chinese-fantasy scene vocabulary. The 6-layer formula folds into `[Shot 1] integrated_multimodal_description`.

## License

MIT — free to use, modify, and share.