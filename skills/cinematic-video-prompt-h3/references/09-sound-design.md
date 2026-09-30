# Sound Design — Diegetic, Non-Diegetic, Foley & Score

> **H3 mapping note (read first).** H3 has two distinct audio fields:
>
> - `overall_soundscape` — diegetic **non-musical** sound across the entire video. **1–4 English sentences** as a single paragraph. Covers ambient sound + physical action sounds + non-verbal human sound. **No dialogue. No music (diegetic or otherwise).**
> - `non_diegetic_music` — score audible only to the audience. **1–3 English sentences.** No characters can hear this music. Use `N/A` when there is no score. **This field is for score only — voiceover and audience-only sound effects belong in the shot description, not here.**
>
> Sound vocabulary from this reference fills these fields with concrete, named terms rather than vague `cinematic sound` / `dramatic music`. Diegetic dialogue goes inside `<d>...</d>` blocks in the shot description; **diegetic music (a radio playing, a character singing, a TV in the corner) also goes inside the shot description, synchronized to the shot that produces it** — not in `overall_soundscape`. Voiceover goes inside the shot description followed by `while her lips remain completely closed.`. The diegetic / non-diegetic split is the **single most important sound rule in H3** — see section A.

The vocabulary of cinematic sound: what sound is, where it lives, how it shapes the picture. Pair with `references/08-editing-transitions.md` for sound bridges, J/L-cuts, and audio transitions. Pair with `references/05-style-color-mood.md` because mood is carried by both palette and audio.

## A. The diegetic / non-diegetic split

| Type | Definition | Where in H3 |
|---|---|---|
| **Diegetic sound** (non-musical) | Sound from the story world that is not music: characters talking, cars passing, rain on a window | ambient + physical + non-verbal human → `overall_soundscape`; dialogue → `<d>...</d>` inside the shot |
| **Diegetic music** | Music from the story world — a character singing, a radio playing, a band on stage | **inside the shot description**, synchronized to the shot that produces it (e.g. `the radio on the counter plays a soft jazz instrumental, …`). NOT in `overall_soundscape`, NOT in `non_diegetic_music`. |
| **Non-diegetic music** | Music from outside the story world — the film score | `non_diegetic_music` |
| **Voiceover / off-screen narration** | Speaker's voice with closed lips; audience hears it but the diegesis is ambiguous | `<d>...</d>` inside the shot, followed by `while her lips remain completely closed.` |
| **Internal diegetic** | Character's thoughts, dream voices, hallucinatory audio | treat as voiceover (close-lipped) or as a separate audio cue depending on the source — it is diegetic from the character's perspective but inaudible to other characters |

The split is **strict**. A character listening to music on headphones is diegetic (the music is in the scene). A film score playing over the same shot is non-diegetic (the character cannot hear it). Mixing the two in one audio field confuses the model.

## B. Diegetic sound vocabulary

| Term | Definition | H3 phrasing |
|---|---|---|
| Dialogue | Speech between characters | `<d>[English] ...</d>` inside the shot body |
| Ambient Sound | Continuous environmental sound (room tone, traffic hum, wind) | named source + quality: `room tone with a low ventilation hum,` / `steady city traffic outside,` / `wind in the trees.` |
| Room Tone | The specific "silence" of an interior space (AC, electrical hum, resonance) | `room tone of a small office: air conditioning, the buzz of a fluorescent tube, the building settling.` |
| Sound Effects (SFX) | One-off physical sounds (explosions, footsteps, doors) | diegetic SFX goes in the shot that produces it; non-diegetic SFX (added for emphasis) belongs in `overall_soundscape` and must be flagged as such |
| Foley | Reproduction of everyday sounds performed in post (footsteps on different surfaces, fabric rustling) | describe the texture: `cloth shoes on polished marble, fabric brushing as she turns, the leather bag shifting against her hip.` |
| Walla | Background murmur of crowd scenes — indistinct conversation | `a low walla of indistinct voices in the corridor, suggesting a dozen people just out of sight.` |
| ADR (Automated Dialogue Replacement) | Re-recorded dialogue in post | not relevant for H3 generation; mention only when describing the source of a voice |
| Acousmatic Sound | Sound heard without seeing its source | `the voice comes from off-screen — a man with a flat mid-Atlantic accent, his origin unseen.` |
| Sonic Worldbuilding | Distinctive cohesive sound environment for a fictional setting | describe the layered mix: `a forest soundscape: leaves rustling, distant wood pigeons, the snap of twigs underfoot, a river far below.` |

## C. Non-diegetic sound vocabulary

| Term | Definition | H3 phrasing |
|---|---|---|
| Score | Original music composed for the video | describe instrumentation + tempo + dynamic arc in `non_diegetic_music` |
| Source Music | Pre-existing recorded music (used like a "needle drop") | state the title or genre if the brief is specific, e.g. `a recording of Miles Davis's "Kind of Blue" plays over the scene.` |
| Needle Drop | Use of pre-existing music, as if dropping a needle on a record | same phrasing as Source Music |
| Leitmotif | Recurring musical theme for a character, place, idea | describe the theme once; later shots reference it: `the same four-note piano phrase from the opening returns as she reaches the door.` |
| Sound Motif | Recurring non-musical audio (footsteps pattern, clock tick) | describe the sound once; reference it later: `the same clock tick returns, now doubled in tempo.` |
| Stinger | Short, sharp musical accent punctuating a moment | `a single stinger — a brass stab — punctuates the door opening.` |
| Mickey Mousing | Music precisely synchronized to on-screen action | use sparingly in H3: `a pizzicato on each blink of her eyes.` |
| Voiceover Narration | Spoken commentary over images, with closed lips | `<d>[English] ...</d> while her lips remain completely closed.` |
| Audio Ducking | Background audio auto-lowers under dialogue | describe the effect, not the tool: `the score recedes to a whisper whenever she speaks.` |

## D. Sound transitions

| Term | Definition | H3 phrasing |
|---|---|---|
| Sound Bridge | Audio connecting two scenes (carries over or anticipates) | describe the carry-over explicitly: `the woman's voiceover carries into the next shot over black screen.` |
| J-Cut | Audio from incoming scene begins before picture | `from this frame, we hear the next scene's traffic before seeing the street.` |
| L-Cut | Outgoing audio extends under incoming picture | `the sound of the previous shot continues into this frame.` |
| Silence | Deliberate absence of sound | `the shot is silent except for the woman's breath.` |
| Acousmatic Reveal | Source of a sound revealed later in the sequence | `the voice that has been narrating throughout is revealed, at MM:SS.mmm, to be the old man at the window.` |
| Diegetic Switch | What was diegetic (in-world) becomes non-diegetic (score), or vice versa | describe the switch: `the radio music in the car continues as she steps out — the same melody now score, no longer attached to the dashboard.` |

## E. Filling `overall_soundscape` — the recipe

A complete `overall_soundscape` paragraph covers three layers, in order:

1. **Ambient (1 sentence)** — the environmental base layer (room tone, weather, traffic, wind).
2. **Physical action (0–2 sentences)** — the sounds of objects and surfaces touched by the action (footsteps, fabric, doors, rain on metal).
3. **Non-verbal human (0–1 sentence)** — breathing, sighing, gasps, laughter (not dialogue, not singing).

Worked example, three layers explicit:

```
overall_soundscape: A quiet kitchen tone continues underneath while a kettle whistles once and a spoon clinks against ceramic. The young woman exhales softly as she sets the cup down, the wood floor creaking once under her weight.
```

Bad example (common mistakes):

```
overall_soundscape: Cinematic background sound with some music and dramatic ambient noise. (BAD: vague, no concrete sources, no temporal behavior)
```

## F. Filling `non_diegetic_music` — the recipe

A complete `non_diegetic_music` paragraph covers three elements, in order:

1. **Instrumentation** — what plays (piano, strings, synth, percussion, voice).
2. **Tempo + rhythm** — slow / moderate / fast, pulse / rubato / syncopated.
3. **Dynamic arc** — how volume and intensity develop across the video.

Worked example, three elements explicit:

```
non_diegetic_music: A solo piano line at a slow tempo, joined by sustained low strings, gradually swelling through the middle of the shot and fading to silence in the final second.
```

Bad example:

```
non_diegetic_music: Sad cinematic music in the background. (BAD: abstract mood word, no instrumentation, no behavior)
```

## G. Failure modes for H3

- **G.1 — Putting dialogue in `overall_soundscape`.** Dialogue is shot-specific; describe it in `integrated_multimodal_description` with `<d>` blocks. `overall_soundscape` is for ambient + physical + non-verbal human sound.
- **G.2 — Putting ambient sound in `non_diegetic_music`.** Ambient sound is diegetic by default. Music on a radio in the scene is diegetic; orchestral score over the scene is non-diegetic.
- **G.3 — Mood words without instrumentation.** "Sad music" / "tense score" / "happy melody" are abstract. Name the instruments (`solo cello`, `low strings`, `treble piano`) and the tempo.
- **G.4 — Same sound every shot.** H3 tends to repeat identical ambient sound. Vary: `the wind picks up at the second shot, rain begins to fall in the third, the room tone returns in the fourth.`
- **G.5 — Sound outside the diegetic / non-diegetic split.** Voiceover is allowed (and marked with closed lips). Voice without a defined source ("a narrator who may or may not exist") is ambiguous; pick one.
- **G.6 — Bullet lists in `overall_soundscape`.** It is one paragraph, not a list. Use commas, semicolons, and one final period.
- **G.7 — Score that narrates the emotion.** `the music underscores her sadness,` `the score signals the danger,` `the melody mirrors her fear` — all abstract mood descriptions. Drop them and let the score's instrumentation + tempo carry the emotional read.

## H. Pairing with other references

- **With editing (`references/08`)** — sound bridges, J-cuts, L-cuts, and audio transitions are sound-led edits. State the audio before the cut.
- **With style/color/mood (`references/05`)** — mood is carried by both palette and audio. Match them: a muted warm palette + low solo cello = nostalgia; a saturated neon palette + driving synth bass = cyberpunk intensity.
- **With FACS (`references/07`)** — emotional close-ups pair face AUs with audio cues: a sigh at the moment of `AU15` (lip corners pull down), an intake of breath at the moment of `AU1 + AU2` (inner + outer brows rise).
- **With storytelling (`references/10`)** — leitmotifs carry recurring characters and ideas across a multi-shot sequence; non-diegetic narration frames a frame narrative.