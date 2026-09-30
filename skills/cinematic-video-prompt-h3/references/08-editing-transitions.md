# Editing — Transitions, Cuts & Rhythm

> **H3 mapping note (read first).** H3's cut timing notation is `At MM:SS.mmm, the camera cuts to …`. Editing vocabulary describes **what happens between shots** (cut type, transition, audio handling) and **the rhythm of cutting across the whole sequence**. Three rules:
>
> 1. **Always state the cut explicitly.** `the camera cuts to` / `the shot cuts to` / `the shot transitions to` / `the shot switches to` — pick one and use it on every cut. Never imply a cut with words like `then` alone; H3 reads that as continuous motion, not a cut.
> 2. **Name the transition type only when it is not a straight cut.** Straight cuts are the default; do not write `straight cut to`. If it is a cut, just say `cuts to`. For dissolves, wipes, fades, iris — name them. `the shot dissolves to a night-time version of the same corridor,` / `the frame fades to black,` / `a vertical wipe replaces the image with …`.
> 3. **Dialogue across cuts uses `<scenetrans>` placed inside the `<d>` block that crosses the cut.** `<scenetrans>` marks the join point of a dialogue line that crosses a cut. Ambient / SFX / score audio across cuts is described in prose inside the shot that produces the sound, not with a tag.
>
> Worked example — dialogue crossing a cut (mirrors upstream H3 syntax):
>
> ```
> [Shot 1] Live-action, cinematic, a medium shot at eye level frames a young woman (S1) on a train, the city sliding past the window behind her. She begins to speak.
>
> [Shot 2] At 00:04.000, the camera cuts to a reverse shot of the young woman (S1) saying, <d>[English] <scenetrans>I get off at the next station.</scenetrans></d> Her voice carries over from the previous shot; her lips begin moving in this frame.
> ```
>
> Notice: `<scenetrans>` sits **inside** the `<d>...</d>` block, at the join point of a line that crosses a cut. Carry-over for non-dialogue audio (ambient, SFX, score) is described in prose without any tag.

> **Evidence status:** **Documented** for the cut-timing format (`MM:SS.mmm`) and the `<scenetrans>` / `<cutoff>` tag positions (upstream H3 guide). **Heuristic** for whether the model renders 180° rule consistency, eyeline matches, and OTS framing correctly across multi-shot prompts — these depend on the model's spatial reasoning. Test on a short sequence before committing.

The vocabulary of how shots join, how audio behaves across cuts, and how rhythm shapes a sequence. Loads of overlap with `references/02-lighting.md` (cross-cutting builds tension), `references/03-composition.md` (rule of thirds continuity), and `references/04-lens-technical-film.md` (freeze frame, slow motion, motion blur). Combines with `references/10-storytelling-devices.md` (montage theory, parallel editing).

## A. Cuts & continuities

| Term | Definition | H3 phrasing |
|---|---|---|
| Cut / Straight Cut | Abrupt transition between two shots | `the camera cuts to …` (default; do not annotate) |
| Match Cut | Cut linking two shots by matching shape, color, motion, or composition | `the camera cuts to …, the composition matching the previous frame.` |
| Jump Cut | Abrupt cut breaking continuous action, creating discontinuity | `the camera cuts to the same subject in a noticeably later moment, the action skipping forward.` A jump cut is **not** a dissolve-like effect — it is a deliberate discontinuity. Don't use `jump cut` to mean "cut quickly". |
| Cutaway | Temporary cut to related detail (object, environment, other character) | `At MM:SS.mmm, the camera cuts away to a close-up of …, then cuts back to the main action at MM:SS.mmm.` |
| Cut-In | Cut to a tighter view of detail within the main action | `At MM:SS.mmm, the camera cuts in to a close-up of her hands.` |
| Reaction Shot | Cut to a character responding to an event | `At MM:SS.mmm, the camera cuts to the young man's face, his eyes widening.` |
| Insert Shot | Close-up of object or detail filmed separately, edited in | already covered in `01-camera-angles-and-movement.md` |
| Match on Action | Cut during continuous movement, motion masks the transition | `the camera cuts to the reverse angle mid-stride, her foot still landing.` |
| Eyeline Match | Cut from a character looking to what they see | `At MM:SS.mmm, the camera cuts to what she sees, …` — describe the gaze, then the cut, then the framed subject. **Eyeline match** is a framing-of-look relation, distinct from a **match cut** which is a shape / motion / composition match. |
| Cutting on Look | Edit based on where characters direct their gaze | describe the gaze and the next shot's framing in the same sentence |
| Invisible Cut | Edit hidden within movement, similar objects, or darkness | describe the masking element (motion, darkness, similar shape) — let the model pick the cut point |
| Continuity Editing | Seamless cuts preserving spatial/temporal coherence | not annotated; default state of a well-built sequence |
| 30-Degree Rule | Consecutive shots of same subject change angle by ≥30° to avoid jump cuts | `the camera cuts to a 45-degree closer angle on the same subject, …` |
| 180-Degree Rule | Camera stays on one side of an imaginary axis between characters | state the **screen relationship** explicitly: `the conversation sits on the woman's right side; she stays screen-left, he stays screen-right across all cuts in the dialogue.` Frame-left / frame-right is clearer than "her right". |
| Shot-Reverse-Shot | Alternating close-ups of two characters in dialogue | describe both shots in the sequence: `[Shot 2] At MM:SS.mmm, the camera cuts to a reverse close-up of the man, his eyeline matching hers from the previous frame.` |
| Reverse Angle | Cut to the opposite viewpoint in a scene | `the camera cuts to the reverse angle, …` |
| Establishing Shot | Opening shot showing where the action takes place | covered in `01-camera-angles-and-movement.md` |

## B. Scene coverage and the master-shot toolkit

> **Documented** (industry-standard terms). **Heuristic** for whether H3-class models keep spatial relationships consistent across coverage shots — describe positions in screen-space coordinates and the model reads them more reliably than abstract "he is on her right" phrasings.

| Term | Definition | H3 phrasing |
|---|---|---|
| Master Shot | A wide shot containing the whole scene's action from one camera position | `a master shot — a wide frames both characters and the room, the whole scene visible from the doorway, …` |
| Coverage | The set of additional shots (mediums, close-ups, inserts, reverses) the editor uses to break up the master | describe the coverage list: `coverage follows: a medium of him, a close-up of her, an insert of the letter, a reverse angle from the window, …` |
| Clean Single | A single on a character with no other person in frame | `a clean single on him, no part of her visible, …` |
| Dirty Single | A single with part of another character in the foreground | `a dirty single on her, his shoulder in soft focus in the foreground, …` |
| Over-the-Shoulder (OTS) | A shot taken over one character's shoulder, looking at the other | `an over-the-shoulder shot from his shoulder, framing her face, …` |
| OTS Matching | The foreground shoulder and the framed face mirror each other across the two OTS shots | describe both halves explicitly: `her shoulder fills the foreground left; he faces screen right. Reverse: his shoulder fills the foreground right; she faces screen left. …` |
| Neutral Shot / On-axis Shot | A shot taken directly on the action axis — used to re-orient the audience | `a neutral on-axis shot re-establishes the geography: both characters at frame center, equal weight, …` |
| Spatial Re-establishment | A new wide or master shot inserted after cuts have tightened in | `a spatial re-establishment — at MM:SS.mmm, the camera cuts back to the wide shot, the geography refreshed, …` |
| Action Axis / Line of Action | The imaginary line between two subjects; the camera stays on one side to keep screen direction consistent | state the axis at the start of the dialogue: `the conversation sits on the woman's right side; both shots keep the camera on her right, …` (the 180° rule expressed as a screen relationship) |
| Screen Direction | Which side of the frame a character enters from / exits to / faces | state explicitly: `she enters from screen right and exits screen left, …` / `he faces screen left, his eyeline aimed off-frame, …` |

## C. Transitions (non-cut)

| Term | Definition | H3 phrasing |
|---|---|---|
| Dissolve | One image fades out as the next fades in | `the shot dissolves to …` |
| Crossfade | Same as dissolve | `the shot crossfades to …` |
| Fade In / Fade Out | Gradual transition to or from a solid color (usually black) | `the frame fades to black.` / `from black, the frame fades in to …` |
| Wipe | One image replaced by another via a visible moving line/shape | `a horizontal wipe replaces the image with …` / `a vertical wipe slides the new frame in from the left.` |
| Iris In / Iris Out | Circular (or shaped) mask opening/closing the frame | `an iris-in opens on …` / `an iris-out closes the frame to a dot.` |
| Match Dissolve | Two shots overlap and share a visual element (e.g., a face becomes a landscape) | `the shot dissolves from her face to the moon, both round and pale.` |

H3 supports only basic transitions (cut, dissolve, fade, wipe, iris). For complex match dissolves or shape wipes, describe both endpoints and the bridging motion explicitly:

```
At 00:08.000, the shot dissolves from the white moon to her pale face, the same circle and glow carrying across the transition.
```

## D. Audio across edits

| Term | Definition | H3 phrasing |
|---|---|---|
| L-Cut | Audio from outgoing shot extends under incoming picture | `the sound of the previous shot continues into this frame.` |
| J-Cut | Audio from incoming shot begins before its picture | `from this frame, we hear the next scene's traffic before seeing the street.` |
| Sound Bridge | Audio connecting two scenes (either direction) | describe the audio once and explicitly mark it as bridging; e.g. `the woman's voiceover carries into the next shot over black screen.` |
| Dialogue continuity (scenetrans) | Speech that crosses a cut | use `<scenetrans>` **inside the `<d>...</d>` block** at the join point, then state `carries over from the previous shot` / `continues uninterrupted into the next shot` / `remains audible across the transition` |
| Dialogue cutoff | Speech truncated by end of video | use `<cutoff>` tag at the last `<d>` block |
| Voiceover / Off-screen narration | Speaker's voice with closed lips | `says in an off-screen voiceover: <d>[English] …</d> while her lips remain completely closed.` |

> **Internal diegetic sound (a character's thoughts, dream voices, hallucinatory audio)** is not automatically non-diegetic. It's diegetic from the character's perspective but inaudible to other characters; treat it as voiceover (close-lipped) or as a separate audio cue depending on the source.

## E. Rhythm & montage

| Term | Definition | H3 phrasing |
|---|---|---|
| Montage | Brief shots edited together to compress time or build meaning | describe the montage as a single shot with rapid beats: `[Shot 1] a montage of …, the camera cutting rapidly between …, …, and … within the 6-second duration.` |
| Soviet Montage | Meaning emerges from collision of images (Eisenstein) | describe the two images and their juxtaposition: `a cut from the marching soldiers to the slaughterhouse — the rhythm of boots meeting the rhythm of the conveyor.` |
| Intellectual Montage | Juxtaposition creating abstract ideas not present in either shot alone | describe both shots and the implicit connection |
| Metric Montage | Cuts at fixed intervals | state the beat interval: `the sequence cuts every two seconds between the clock, the hands, and the door.` |
| Rhythmic Montage | Cuts follow internal motion rather than fixed time | describe the trigger for each cut: `the cut happens on the downbeat of her stride, then on the wave's break, then on the drum hit.` |
| Parallel Editing | Intercutting between two simultaneous storylines | label the two storylines and their cut times |
| Cross-Cutting | Same as parallel editing (US term) | same phrasing as Parallel Editing |
| Long Take | Extended continuous shot | covered in `01-camera-angles-and-movement.md` as `Continuous long take / One-shot` |
| Fast Motion | Action sped up by under-cranking or digital acceleration | `shot in fast motion, the action appearing accelerated, …` |
| Slow Motion | Action slowed by over-cranking or digital interpolation | covered in `04-lens-technical-film.md` |
| Reverse Motion | Footage played backward | `playback in reverse, water flowing upward, fragments reassembling.` |
| Freeze Frame | Hold on a single frame | `at the climax, the frame freezes; time continues outside the image.` |
| Speed Ramp | Variable fast/slow within the same shot | `the sequence begins at normal speed, accelerates through the turn, then slows as she falls — a continuous speed ramp.` |

## F. Failure modes for H3

- **F.1 — Cuts without "cuts to".** Writing `[Shot 2] At MM:SS.mmm, the same corridor.` reads as a single continuous shot. H3 will not insert the cut. Always begin a new `[Shot N]` with a transition verb.
- **F.2 — Stacking transitions.** `cuts and dissolves to` is a contradiction. Pick one transition type per cut.
- **F.3 — `<scenetrans>` outside `<d>`.** `<scenetrans>` is dialogue-specific and lives inside the `<d>...</d>` block. It marks the join point of a line that crosses a cut. Ambient / SFX carry-over uses prose, no tag.
- **F.4 — Wipes and iris as default.** These are stylized choices. Use them only when the brief calls for a period look (silent film iris, 1970s TV wipe, etc.). Default to a straight cut.
- **F.5 — Montage beats over 5.** A montage of 7 distinct subjects in 6 seconds reads as chaos. Cap at 4 subjects per montage shot. Distribute the rest across multiple montage shots.
- **F.6 — 180° drift across cuts.** A conversation that drifts across the axis reads as the characters switching seats. State the screen relationship once at the start of the dialogue sequence: `she stays screen-left, he stays screen-right across all cuts.`
- **F.7 — Jump cut where you meant a match cut.** A match cut connects two shots; a jump cut is a deliberate discontinuity. Don't use `jump cut` to mean `cut quickly` — H3 may render an actual jump.
- **F.8 — Stacked motion inside `[Shot 1]`.** H3's shot list is meant for **cuts**, not internal edits. If you need managed transitions inside what would otherwise be one shot, use additional `[Shot N]` lines instead.
- **F.9 — Coverage without character anchors.** Coverage shots that don't repeat the character tag (`the same young woman in the red áo dài`) drift in identity. Repeat the anchor at the start of each coverage shot.

## G. Pairing with other references

- **With camera angles (`references/01`)** — match cuts work best when the next shot echoes the previous shot's framing (rule of thirds → rule of thirds, eye-level → eye-level). State both.
- **With composition (`references/03`)** — a wipe follows a strong diagonal or horizontal line; an iris closes on a circular subject. Pair the transition shape with the composition. Blocking (screen direction, eyeline, off-screen space) lives in `03` and feeds the OTS / reverse / master-shot vocabulary here.
- **With sound design (`references/09`)** — sound bridges, J-cuts, and L-cuts are all sound-led transitions. State the audio before the cut in the shot description.
- **With storytelling (`references/10`)** — parallel editing carries the structure of cross-cutting narratives. Montage compresses time; cross-cutting juxtaposes space.