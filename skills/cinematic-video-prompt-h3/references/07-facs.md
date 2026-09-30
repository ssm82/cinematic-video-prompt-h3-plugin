# FACS — Facial Action Coding System

> **H3 mapping note (read first).** FACS (Ekman & Friesen, 1978) gives you **observable** facial-muscle actions (Action Units, AUs) instead of subjective emotion words. **For emotional close-ups, the primary method is plain-English description of the visible movements** — `her inner brows rise, then her upper lids lift, then her jaw drops`. AU codes work as auxiliary notation: the codes themselves are not guaranteed to be parsed literally by current H3-class models, but the muscle-by-muscle phrasing they imply renders more reliably than bare words like `sad face` or `angry expression` (which average into a generic grimace).
>
> Two phrasing patterns:
>
> - **Time-sequenced beats.** Describe AUs in chronological order inside the shot description. The model reads the order literally.
>
>   `At 00:03.000, her inner brows rise (AU1), then her outer brows lift (AU2), then her upper lids raise (AU5), then her jaw drops (AU26) — surprise.`
>
> - **Cluster shorthand.** Group AUs into a named emotion cluster and put the cluster inside the shot description:
>
>   `surprise on her face — inner brows raised, outer brows lifted, eyes widened, jaw dropped.`
>
>   This is shorter but less precise. Use it for casual beats; use the time-sequenced form for the central close-up of a shot.
>
> Pair FACS with `references/06-materials-weather-pose.md` for body pose, and with the lighting / palette vocabulary from `references/02-lighting.md` and `references/05-style-color-mood.md` — face AUs describe the muscles; lighting controls the read.

> **Evidence status:** **Documented** (Ekman & Friesen, 1978) for the AU catalogue and the basic emotion clusters. **Heuristic** for which AUs current H3-class video models render reliably, for the intensity adverb mapping, and for the asymmetry cap (G.3). **Experimental** for "AU6 = Duchenne marker = genuine smile" (G.4) — the muscle movement is documented; the inference from AU6 alone to *internal* genuineness is contested in the FACS literature. Treat AU6 + AU12 as a visible smile cluster, not as proof of felt happiness.
>
> FACS codes **observable actions**, not internal states. Use AUs to describe what the face *does*, not what the character *feels*. For complex states (embarrassment, concentration, confusion), describe the visible movements; the inferred emotion is a reading, not a guarantee.

Ekman & Friesen's Facial Action Coding System. **44 Action Units (AUs)** describe facial-muscle movements; recognizable emotions are clusters of AUs. Below are the ~20 AUs most useful for prompting current H3-class video models. The full 44-AU reference is in Ekman & Friesen (1978), ISBN 0-939169-01-1, with the cross-checked table at <https://www.cs.cmu.edu/~face/facs.htm>.

## A. Upper face (brows, forehead, eyes)

| AU | Muscle | Visible result | H3 phrasing |
|---|---|---|---|
| AU1 | Frontalis (medial) | Inner brows lifted | `inner brows rise,` |
| AU2 | Frontalis (lateral) | Outer brows lifted | `outer brows lift,` |
| AU4 | Corrugator + Depressor supercilii | Brows drawn together and down | `brows knit together and lower,` |
| AU5 | Levator palpebrae superioris | Upper lids raised, eyes widened | `upper lids lift, eyes widen,` |
| AU6 | Orbicularis oculi (pars orbitalis) | Cheeks raised, eye corners wrinkled (visible-smile marker) | `cheeks raise, eye corners wrinkle,` |
| AU7 | Orbicularis oculi (pars palpebralis) | Lower lids tensed, squinting | `lower lids tighten,` |
| AU43 | Orbicularis oculi (pars palpebralis) | Eyes closed | `eyes close,` |
| AU45 | Blink | Eyes briefly close and reopen | `a single blink,` |

## B. Lower face (nose, cheeks, lips, mouth)

| AU | Muscle | Visible result | H3 phrasing |
|---|---|---|---|
| AU9 | Levator labii superioris (alaeque nasi) | Nose wrinkled | `nose wrinkles,` |
| AU10 | Levator labii superioris | Upper lip raised, exposing upper teeth | `upper lip lifts,` |
| AU12 | Zygomaticus major | Lip corners pulled up (smile) | `lip corners pull up,` |
| AU13 | Caninus (modern nomenclature: *sharp lip puller*) | Upper lip pulled sharply upward; corners tightened | `upper lip pulls sharply upward,` |
| AU14 | Buccinator (dimpler) | Lip corners tightened, dimples form | `lip corners tighten, dimples form,` |
| AU15 | Depressor anguli oris | Lip corners pulled down (frown) | `lip corners pull down,` |
| AU16 | Depressor labii inferioris | Lower lip lowered | `lower lip drops,` |
| AU17 | Mentalis | Chin raised, lower lip pushed up | `chin raises,` |
| AU18 | Incisivii labii + Buccinator | Lips pursed forward (kiss / pout) | `lips push forward,` |
| AU20 | Risorius + Platysma | Lips stretched horizontally | `lips stretch sideways,` |
| AU22 | Orbicularis oris (pars marginalis) | Lips funneled | `lips funnel,` |
| AU23 | Orbicularis oris (pars peripheralis) | Lips tightened, pressed | `lips tighten,` |
| AU24 | Orbicularis oris (press) | Lips pressed together firmly | `lips press together,` |
| AU25 | Depressor labii + Mentalis relax | Lips part | `lips part,` |
| AU26 | Masseter + Temporalis relax | Jaw drops, mouth opens | `jaw drops,` |
| AU27 | Pterygoids + Digastric | Mouth stretched open (wide) | `mouth stretches open,` |

## C. Head and eye gaze (head AUs and gaze AUs)

These are AUs 50s and 60s. They govern head position and gaze direction, not facial muscle action — useful when an emotion needs a head turn or downcast eyes.

| AU | Movement | H3 phrasing |
|---|---|---|
| AU51 | Head turn to the left | `head turns left,` |
| AU52 | Head turn to the right | `head turns right,` |
| AU53 | Head up (chin lifts, eyes look up) | `chin lifts, eyes look up,` |
| AU54 | Head down (chin drops, eyes lower) | `chin drops, eyes lower,` |
| AU55 | Head tilt left | `head tilts left,` |
| AU56 | Head tilt right | `head tilts right,` |
| AU57 | Head forward (juts toward camera) | `head pushes forward,` |
| AU58 | Head back (pulls away from camera) | `head pulls back,` |
| AU64 | Eyes look down | `eyes look down,` |
| AU65 | Eyes look up | `eyes look up,` |
| AU66 | Eyes look left | `eyes look left,` |
| AU67 | Eyes look right | `eyes look right,` |

## D. Combinations → recognizable emotions

These clusters come from Ekman & Friesen's basic-emotion taxonomy (1978, ch. 16). **They describe visible movements**, not internal states — FACS does not say a person is *feeling* sad because their face shows AU1+AU4. Use the cluster as a shorthand for what the face *does*; the character's internal state is your narrative choice.

| Emotion | Core AUs | Common extras | Plain-English shorthand |
|---|---|---|---|
| Surprise | AU1 + AU2 + AU5 | AU26 (jaw), AU27 (mouth stretch) | `brows rise together, eyes widen, jaw drops,` |
| Fear | AU1 + AU2 + AU4 | AU5, AU20, AU26 (the "fear brow") | `brows rise and pull together, eyes widen, lips stretch sideways, jaw drops,` |
| Sadness | AU1 + AU4 | AU15 (frown), AU17 (chin raise) | `inner brows rise, brows knit together, lip corners pull down, chin raises,` |
| Anger | AU4 + AU5 + AU7 | AU23, AU24 (tight lips), AU9 (nose wrinkle) | `brows knit together and lower, eyes harden, lower lids tighten, lips press together,` |
| Happiness (visible smile) | AU6 + AU12 | AU25 (lips part), AU7 (lower lid crinkle) | `cheeks raise, eye corners wrinkle, lip corners pull up, lips part,` |
| Disgust | AU9 + AU10 + AU17 | AU4 (brow lower), AU25 (lips part) | `nose wrinkles, upper lip lifts, chin raises, lips part,` |
| Contempt | AU12 (one-sided) + AU14 (slight) | AU52 (head turn) | `one lip corner pulls up asymmetrically, head turns slightly,` |
| Embarrassment | AU6 + AU12 (often downcast) | AU51/AU52 (head turn away), AU64 (eyes look down) | `cheeks raise, lip corners pull up, head turns away, eyes look down,` |
| Pain | AU4 + AU7 + AU9 + AU10 + AU20 + AU43 | AU25 (lips part), AU26 (jaw) | `brows knit, eyes close tightly, nose wrinkles, upper lip lifts, lips stretch, jaw clenches,` |
| Concentration | AU4 + AU7 | AU51/AU52 (head turn), AU17 (chin raise), AU64 (eyes lower) | `brows knit together, lower lids tighten, chin raises slightly, eyes lower,` |
| Confusion | AU1 + AU4 (asymmetric) | AU5 (one side only), AU55/AU56 (head tilt) | `one inner brow rises, one brow lowers, head tilts slightly,` |

> **Note on complex states.** Embarrassment, concentration, and confusion are visible clusters but are not part of Ekman's original six basic emotions (1971). They are reconstructed from the FACS literature and are **heuristic** — model response varies. Describe the visible movements; the audience reads the emotion.

## E. Intensity vocabulary

FACS codes intensity in five grades (A → E, lightest → most extreme). Current H3-class models do not parse the A–E labels reliably; fold intensity into **adverbs** in the phrasing:

| Intensity | Adverbs to use |
|---|---|
| Trace (A) | `subtly`, `slightly`, `a hint of` |
| Slight (B) | `a touch`, `mildly`, `softly` |
| Moderate (C) | `clearly`, `noticeably`, `definitely` |
| Strong (D) | `deeply`, `sharply`, `strongly` |
| Maximum (E) | `fully`, `completely`, `to the limit`, `extreme` |

Example: `her inner brows rise slightly` (B) vs `her inner brows rise sharply, the skin folding between them` (D).

## F. Asymmetry — when one side moves differently

Asymmetry is a major cinematographic tool. In FACS you mark an AU with `L` (left) or `R` (right) when only one side fires:

- `AU12L` — left lip corner pulled up (one-sided smile, contempt, smirk)
- `AU1L + AU4R` — one inner brow up, the other drawn down (confusion, skepticism)
- `AU4L + AU4R` (full) — symmetrical anger brow

Phrasing: `her left lip corner pulls up while the right stays neutral,` / `her brows knit unevenly, the left drawing down while the right rises,`.

## G. The hold-and-release pattern

For dramatic close-ups, AUs rarely fire continuously — they peak and then release. The grammar reads this as a sequence of state changes:

- **Hold** — describe the AU in the present state at the moment the camera lands.
- **Trigger** — name the event that changes the expression.
- **Peak** — describe the peak AU cluster.
- **Release** — describe how the muscles relax (return to AU0 / neutral).

Worked beat sequence (the "Spielberg Face"):

```
[Shot 1] Live-action, cinematic, an extreme close-up frames her eyes to chin.
At 00:01.500, the door opens off-screen and her upper lids lift (AU5), then
her inner brows rise (AU1), then her outer brows lift (AU2), her jaw drops
(AU26). At 00:03.000, the expression shifts: brows knit together and pull
down (AU4), lip corners pull down (AU15), chin raises (AU17) — grief
replacing surprise. Her eyes stay dry, no tears fall.
```

> **Frame the shot to what you describe.** An extreme close-up framed "eyes to chin" lets you describe brows, lids, jaw, and lips together. An ECU of the eyes alone cannot show jaw or lip movement; an ECU of the lips alone cannot show brow movement. Match the framing to the AU cluster.

## H. Failure modes for H3

- **H.1 — Bare emotion words fall back to a single mid-intensity grimace.** `surprised` / `angry` / `sad` all collapse to a generic squint-frown unless you specify the visible movements. **Use plain-English descriptions first**; AU codes are auxiliary.
- **H.2 — AUs stack into mush.** Writing all 12 fear AUs at once produces a noisy face. Pick the 3–5 most visible AUs for the emotion (brow + eyes + mouth + chin).
- **H.3 — Asymmetry over-specifies.** Two or three asymmetric AUs is convincing. Six is jitter. Cap at three asymmetric AUs per shot.
- **H.4 — `AU6 = genuine smile` is contested.** AU6 + AU12 is the visible-smile cluster; the inference that AU6 alone equals felt happiness is not supported by FACS (AU6 fires in non-smile contexts including pain). Don't combine AU6 with negative-emotion AUs for *internal* state reasons, but it's fine if your narrative calls for a conflicted smile (warm smile + grief = the bittersweet smile).
- **H.5 — Always specify duration and release.** A continuous AU peak reads as a stuck face; describe the build, the peak, and the release explicitly.
- **H.6 — Don't name the emotion after listing AUs.** Saying `… brow knit, lips press together — anger` and then writing `angry face` later in the same shot is redundant and the model may pick up on the word. Trust the visible movements.
- **H.7 — Frame the AU cluster to the visible area.** AUs described outside the framed area are wasted (an ECU of the eyes cannot show lip movement). Match the shot size to the cluster you describe.

## I. Pairing FACS with the rest of the skill

- **With lighting** (`references/02-lighting.md`) — a face lit from below with AU4 + AU7 reads as menacing; the same face lit from above with soft window light reads as sorrowful. Face AUs describe the muscles; lighting controls the read.
- **With color** (`references/05-style-color-mood.md`) — keep palette consistent with the AU cluster. A high-saturation warm palette + visible-smile cluster (AU6 + AU12) reads as joy. A muted cool palette + AU15 + AU17 reads as grief. Deliberate counterpoint (warm palette + grief cluster) is fine when you explain it; check `references/05` for the counterpoint rules.
- **With pose** (`references/06-materials-weather-pose.md`) — face AUs + body pose is the full emotional picture. AU1 + AU4 + AU15 (visible sadness) + `head bowed, shoulders hunched` is a complete grief pose; AU1 + AU4 + AU15 + `standing straight, fists clenched` reads as contained grief, not surrender.
- **With shot size** — AUs only read at close-up or extreme close-up. In a wide or medium shot, FACS detail is wasted; rely on body pose instead. For wide shots, describe the AU cluster once at the moment of peak emotion, not on every frame.

## J. Quick reference card (print-friendly)

```
Brows up (inner)              AU1   inner brows rise,
Brows up (outer)              AU2   outer brows lift,
Brows together + down         AU4   brows knit together and lower,
Eyes widen                    AU5   upper lids lift,
Cheeks raise (visible smile) AU6   cheeks raise, eye corners wrinkle,
Squint                        AU7   lower lids tighten,
Eyes closed                   AU43  eyes close,
Blink                         AU45  a single blink,
Nose wrinkle                  AU9   nose wrinkles,
Upper lip lift                AU10  upper lip lifts,
Sharp lip puller              AU13  upper lip pulls sharply upward,
Dimpler                       AU14  lip corners tighten, dimples form,
Smile                         AU12  lip corners pull up,
Frown                         AU15  lip corners pull down,
Lower lip drop                AU16  lower lip drops,
Chin raise                    AU17  chin raises,
Lips pucker                   AU18  lips push forward,
Lips stretch sideways         AU20  lips stretch sideways,
Lips part                     AU25  lips part,
Jaw drop                      AU26  jaw drops,
Wide mouth open               AU27  mouth stretches open,
Head turn left                AU51  head turns left,
Head turn right               AU52  head turns right,
Head up                       AU53  chin lifts, eyes look up,
Head down                     AU54  chin drops, eyes lower,
Head tilt left                AU55  head tilts left,
Head tilt right               AU56  head tilts right,
Head forward                  AU57  head pushes forward,
Head back                     AU58  head pulls back,
Eyes look down                AU64  eyes look down,
Eyes look up                  AU65  eyes look up,
Eyes look left                AU66  eyes look left,
Eyes look right               AU67  eyes look right,

Surprise:  AU1 + AU2 + AU5 (+ AU26)
Fear:      AU1 + AU2 + AU4 (+ AU5, AU20, AU26)
Sadness:   AU1 + AU4 (+ AU15, AU17)
Anger:     AU4 + AU5 + AU7 (+ AU23, AU24)
Happy:     AU6 + AU12 (+ AU25, AU7)
Disgust:   AU9 + AU10 + AU17 (+ AU4, AU25)
Pain:      AU4 + AU7 + AU9 + AU10 + AU20 + AU43
```

---

> Reference: Ekman, P., & Friesen, W. V. (1978). *Facial Action Coding System*. Consulting Psychologists Press. ISBN 0-939169-01-1.
>
> FACS is a published research methodology; AU codes and emotion combinations are widely reproduced in the affective-computing and psychology literature (Ekman, 1992; Ekman & Rosenberg, 1997; Friesen & Ekman, 1983). Cross-checked against the public FACS table at <https://www.cs.cmu.edu/~face/facs.htm>. The shorthand phrasing in the tables above is original to this skill.