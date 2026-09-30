# Camera Angles & Camera Movement

> **H3 mapping note (read first).** H3 does not accept comma-separated keyword tags. Camera angle + size become part of the opening shot sentence (`a medium close-up from a low angle frames …`), and camera motion becomes a natural-language **clause** with the exact triplet `motion type + (amplitude) + (speed)` from the H3 grammar (see `SKILL.md` section 3).
>
> - Pick one motion type from: `Zoom In / Zoom Out · Push In / Pull Out · Pan Left / Pan Right · Truck Left / Truck Right · Tilt Up / Tilt Down · Pedestal Up / Pedestal Down · Arc Shot · Tracking Shot · Static Shot · Shake Slightly / Shake Strongly · POV · Roll Clockwise / Roll Counterclockwise`.
> - Add amplitude (`with small amplitude` / `with large amplitude`) only when it differs from medium.
> - Add speed (`at slow speed` / `at fast speed`) only when it differs from normal.
> - Start with one dominant motion; combine a second axis only when the move naturally implies it (a crane that rises while tilting down to keep the subject framed). Test on a 4-second clip.
>
> Example clause: `The camera pushes in with small amplitude at slow speed toward her face.`

> **Evidence status:** **Documented** for the motion-type vocabulary (H3 grammar). **Heuristic** for "one dominant motion per shot" — current H3-class models mix stacked moves; combined moves may work in simple cases. **Documented** for the formal shot-size labels (industry-standard nomenclature). The function labels (Reaction Shot, Insert, Establish, Reveal) are *cinematographic purposes*, not camera moves — they describe what the shot *does* in the edit, not how the camera *moves*.

Full reference. `SKILL.md` keeps the condensed tables; load this file when you need a specific shot size, an exotic angle, or a verified motion phrasing. Terms are organized by category so the table is easier to scan than a flat alphabetical list.

## A. Shot size (how much of the subject fills the frame)

| Term | Visible result | H3 phrasing |
|---|---|---|
| Extreme Long Shot (ELS) / Distant View | Subject tiny in vast environment | `an extreme long shot frames her as a small figure in the vast desert, …` |
| Long Shot (LS) / Full Shot | Full body visible with environment | `a long shot frames the full figure of the protagonist, …` |
| Wide Shot | Substantial environment, character(s) established | `a wide shot captures the full scene, the character small within it, …` |
| Cowboy Shot (a.k.a. American Shot) | Mid-thigh up — holstered guns visible | `a cowboy shot frames her from mid-thigh up, the holster at her hip, …` |
| Medium Long Shot | Same frame as cowboy, no genre constraint | `a medium-long shot frames her from mid-thigh up, …` |
| Medium Shot (MS) | Waist up | `a medium shot frames her from the waist up, …` |
| Medium Close-Up (MCU) | Mid-chest up, tighter than MS | `a medium close-up frames her from mid-chest up, …` |
| Choker Shot | Just below lips to just above eyebrows (term is used loosely; describe the framing) | `a choker shot frames her face from just below the lips to just above the eyebrows, …` |
| Close-Up (CU) | Full face or object detail | `a close-up frames her full face, …` |
| Extreme Close-Up (ECU) | Eyes, lips, hands, fine detail | `an extreme close-up frames only her eyes, …` |
| Italian Shot | ECU on the eyes only (Sergio Leone) | `an Italian shot — an extreme close-up of her eyes alone, …` |
| Macro Shot (Macro Cinematography) | Tiny detail fills the frame | `a macro shot of the watch face — the second hand fills the frame, …` |
| Head Shot | Shoulders up, portrait-style framing | `a head shot frames her shoulders up, the face dominant in the frame, …` |
| Two-Shot | Two subjects in frame | `a two-shot frames the man and woman together at the table, …` |
| Three-Shot | Three subjects in frame | `a three-shot frames the three friends standing together, …` |
| Profile Shot | Pure side profile | `a profile shot captures her face in pure side view, …` |

## B. Camera height and angle (the camera's vertical position and tilt)

| Term | Visible result | H3 phrasing |
|---|---|---|
| Eye-Level Shot | Camera at the subject's eyes — neutral perspective | `an eye-level shot frames her face, the camera aligned with her eyes, …` |
| Shoulder-Level Shot | Camera at the subject's shoulders | `a shoulder-level shot frames her from the chest up, the camera just below eye-level, …` |
| Hip-Level Shot | Camera at the subject's hips | `a hip-level shot frames her from the waist down, …` |
| High Angle | Camera above, looking down — subject reads smaller | `a high angle looks down on her, …` |
| Elevated Shot | Camera lifted (table-top, balcony), looking down | `an elevated shot from the balcony looks down on the courtyard, …` |
| Low Angle | Camera below, looking up — subject reads larger | `a low angle looks up at her, …` |
| Worm's-Eye View | Camera at ground level | `a worm's-eye view from the ground looks straight up, …` |
| Subjective Low Angle | Camera at the subject's own low angle (a child, a fallen figure) | `a subjective low angle as if seen from the child's height, …` |
| Bird's-Eye View | Camera directly overhead | `a bird's-eye view looks straight down on the rooftop, …` |
| Overhead Flat Lay | Looking straight down at a surface (food, objects) | `an overhead flat lay frames the ingredients on the table, …` |
| Overhead Group Shot | Looking straight down at a group | `an overhead group shot looks down on the cluster of figures, …` |
| Ceiling Angle | High angle that emphasizes the ceiling | `a ceiling angle looks up at the vaulted arches above her, …` |
| Drone View (Low Altitude) | Drone at rooftop-to-tree height | `a low-altitude drone view flies through the alley at roof level, …` |
| Aerial View | Drone or aircraft at altitude | `an aerial view surveys the coastline from above, …` |
| Canted Angle / Dutch Tilt | Camera tilted on the roll axis (frame skewed) | `a Dutch-tilted shot frames the corridor, the verticals leaning, …` |
| Oblique Angle | Camera placed at an angle to the subject (less extreme than Dutch) | `an oblique angle frames her from the corner of the table, …` |
| Three-Quarter View | Subject turned about 30° off full front | `a three-quarter view shows the line of her jaw, …` |
| Side Profile Shot (90°) | Subject in pure side view | `a side profile shot captures her face in pure 90° view, …` |

## C. Camera orientation (the camera's placement in 3D space, not its height)

| Term | Visible result | H3 phrasing |
|---|---|---|
| Centered Composition | Subject at the exact center | `centered in the frame, …` |
| Off-Center / Rule of Thirds | Subject at a thirds intersection | `framed at the rule-of-thirds intersection on the left, …` |
| Low Horizon Line | More sky than ground | `a low horizon line emphasizes the sky above the dunes, …` |
| High Horizon Line | More ground than sky | `a high horizon line emphasizes the ground beneath the figures, …` |
| Verticality Emphasis | Frame emphasizes height (tall verticals) | `vertical lines dominate the frame, the figure stretched between floor and ceiling, …` |
| Horizontality Emphasis | Frame emphasizes horizontal stretch | `horizontal lines pull the eye across the long flat landscape, …` |
| Foreground View | Camera placed deep into foreground elements | `the camera is in the foreground, looking past the leaves to the figure beyond, …` |
| Near-Far Juxtaposition | Two subjects at very different distances | `near-far juxtaposition — the bowl in sharp focus at the front, the woman small and soft at the back, …` |

## D. Viewpoint / POV (whose eyes the camera represents)

| Term | Visible result | H3 phrasing |
|---|---|---|
| P.O.V. (Point of View) | Camera shows what a character sees | `a POV shot — what she sees from her hiding place behind the door, …` |
| Subjective Camera | Camera's position is the character's body | `a subjective camera at her eye-level, looking where she looks, …` |
| Counter-Angle | The opposite viewpoint from a previous shot | `the counter-angle frames him from her side, his eyeline matched, …` |
| Reverse Angle | Opposite side of the scene (dialogue context) | `the reverse angle shows him across the table, …` |
| Object Perspective | Camera placed on/in an object | `a low perspective from inside the toy box, looking up at her face, …` |
| Looking Down Through Glass | Subject seen through a transparent surface | `the camera looks down through the glass tabletop at the keys, …` |
| Through the Keyhole / Peephole | Subject seen through a small framed opening | `a peephole view — the camera framed by the small circular opening, …` |
| Trunk Shot | Camera inside a car trunk looking up | `a trunk shot from inside the boot, looking up at the two figures, …` |
| Shelf Angle | Camera placed at the level of a shelf/counter, looking across | `a shelf angle from the pharmacy counter, looking across at her face, …` |
| Cross-Section Angle | Camera positioned to reveal interior structure | `a cross-section view of the engine bay, the parts laid out for inspection, …` |

> **POV is a viewpoint, not a movement.** H3's motion list includes `POV` as a recognized label, but the cinematic meaning is "the camera represents a character's eyes" — not a specific motion. In H3 you can write `POV` as a motion label and the model treats it as a hand-held, body-mounted, or eye-level feel; pair it with a body mount or action for a stronger read.

## E. Camera translation and rotation (motion in space and around axes)

These are the verbs from H3's motion-type list. Use them as a single English clause (see H3 mapping note above).

### E1. Depth moves (toward / away from subject)

| Motion | Visible result | H3 phrasing |
|---|---|---|
| Push In / Pull Out | Camera physically moves toward / away | `the camera pushes in with small amplitude at slow speed toward her face, …` / `the camera pulls out at slow speed, revealing the room, …` |
| Zoom In / Zoom Out | Focal length changes (no camera move) | `a slow zoom in tightens on the photograph, …` |
| Dolly Zoom (Vertigo effect) | Push + zoom in opposite directions | `a dolly zoom — the camera pulls back while the lens zooms in, the background warping around her, …` |
| Crash Zoom / Snap Zoom | Fast zoom for emphasis | `a snap zoom crashes onto her face, …` |
| Z-axis rotation / Corkscrew shot | Camera rotates around the depth axis | `the camera corkscrews around the figure, the depth rolling, …` |

### E2. Lateral and orbital moves (around the subject)

| Motion | Visible result | H3 phrasing |
|---|---|---|
| Pan Left / Pan Right | Camera rotates left/right on a fixed point | `the camera pans left, following her gesture, …` |
| Truck Left / Truck Right | Camera moves laterally, parallel to the action | `the camera trucks right at slow speed alongside the train, …` |
| Arc Shot | Camera orbits the subject | `an arc shot orbits her at slow speed, the background revolving, …` |
| Tracking Shot | Camera follows the subject | `a tracking shot follows her through the market at slow speed, …` |
| Following Shot | Camera behind the subject | `a following shot from behind keeps her centered as she walks, …` |
| Leading Shot | Camera in front of the subject (subject walking toward camera) | `a leading shot — the camera pulls back at slow speed as she walks toward it, …` |
| Sweeping Shot | Long, complex move through space | `a sweeping shot crosses the hall from the fireplace to the door, …` |
| Whip Pan / Swish Pan | Fast pan, blur on the transition | `a whip pan blurs from her face to the window, …` |

### E3. Vertical moves (up / down)

| Motion | Visible result | H3 phrasing |
|---|---|---|
| Tilt Up / Tilt Down | Camera rotates up/down on a fixed point | `the camera tilts up from her feet to her face, …` |
| Pedestal Up / Pedestal Down | Camera physically moves straight up/down (no tilt) | `the camera pedestals up with small amplitude at slow speed, …` |
| Boom Shot (Jib up) | Vertical lift/drop on a boom arm, less sweeping than crane | `the camera booms straight up, revealing the ceiling, …` |
| Crane Shot (Jib up) | Mechanical arm lift/drop, vertical and arc | `the camera cranes up with large amplitude at slow speed, …` |
| Jib Shot | Arm-mounted, combines vertical and horizontal arc | `the camera sweeps in a jib arc, rising and tracking left at slow speed, …` |

### E4. Camera-mounted rotation and stabilization

| Motion | Visible result | H3 phrasing |
|---|---|---|
| Static Shot / Locked-off | Camera does not move | `the camera holds a static shot, …` |
| Roll Clockwise / Roll Counterclockwise | Camera rotates around the lens axis | `the camera rolls clockwise, the horizon tilting into a vertical, …` |
| Barrel Roll / 360° Roll | Full rotation around the lens axis | `a 360° barrel roll spins the frame, …` |
| Shake Slightly / Shake Strongly | Visible handheld tremor | `the camera shakes slightly, handheld, …` / `the camera shakes strongly, the frame trembling, …` |
| Handheld (Subtle) | Slight handheld instability | `a handheld shot, slight shake, intimate and rough, …` |
| Shaky Cam | Aggressive handheld shake | `shaky cam — the frame jolts with every step, …` |
| Steadicam / Gimbal Smooth | Stable motion despite movement | `a steadicam shot — the camera glides smoothly down the corridor, …` |
| SnorriCam / Body Mount | Camera mounted on the actor | `a body-mounted shot, the frame moving with her body as she walks, …` |
| Camera Roll / Rolling Shot | Continuous roll across a moving subject | `a rolling shot — the camera rolls across the foreground as she passes, …` |

## F. Shot function (what the shot *does* in the edit)

These are not camera moves — they describe **the purpose of the shot in the sequence**. The camera work still needs a separate motion clause.

| Term | Function | Where it usually lives |
|---|---|---|
| Establishing Shot | Opens a scene, shows the location | first shot of a scene or sequence |
| Reaction Shot | Shows a character responding to an event | after the event shot |
| Insert Shot | Tight shot on a prop or detail | covered in `references/08-editing-transitions.md` |
| Cutaway | Quick cut to related detail (not the main action) | between two shots of the main action |
| Master Shot | Wide shot containing the whole scene | rehearsal / first reference for coverage |
| Coverage | Set of additional shots (mediums, close-ups) for the editor | after the master shot is locked |
| The Reveal | Frame that exposes information previously hidden | at the moment of revelation |
| Point-of-Interest Angle | Frame built around a specific object | when the object is the story |
| The Spielberg Face | Tight CU on a character's reaction to off-screen stimulus | reaction beat, often AU-driven |

## G. Special optical and temporal effects (camera tricks that alter the image itself)

| Effect | Visible result | H3 phrasing |
|---|---|---|
| Bullet Time | Frozen action with rotating camera around subject | `bullet time — the action frozen mid-flight while the camera arcs around her, …` |
| Dolly Zoom (Vertigo) | Background warps while subject size holds | covered in E1 |
| Whip Pan as Transition | A whip pan that doubles as a cut point | `a whip pan transition blurs from the killer to the door, …` |
| Reveal Shot (sliding past foreground) | Sliding past a foreground object reveals what was hidden | `a sliding reveal — the camera tracks past the foreground column, uncovering her face, …` |
| Continuous Long Take / One-shot | The entire clip is one unbroken shot | `a continuous long take — no cuts, the camera moves through the whole scene, …` |
| Stop Motion Style Camera | Frame-by-frame aesthetic | `stop-motion style — the figure advances one held pose at a time, …` |
| Through the Keyhole | Subject framed through a small opening | covered in D |
| Focus Magnification View | Push-in plus focus pull to emphasize a small detail | `a focus magnification — the camera pushes in as the focus shifts to the locket, …` |
| Barrel Roll / 360° Roll | covered in E4 |
| Forced Perspective | Subject size manipulated through placement | `forced perspective — she appears giant compared to the miniature town behind her, …` |
| Whip Around Angle | Camera whips around to face the opposite direction | `a whip around — the camera whips from the speaker to the door, …` |
| Reverse-Dolly Angle | A dolly move that reverses direction mid-shot | `a reverse dolly — the camera pushes in then pulls out, …` |
| Trinity Angle | A vertical-roll camera position used in action cinema (author/genre term; describe the framing if you want it) | `a vertical-roll camera — the frame rotates 90° as she fires, …` |
| Hyperlapse / Moving Time-lapse | Compressed time with continuous camera motion | `a moving time-lapse — the camera advances through the city as clouds race and crowds blur, …` |
| God's Eye Spiral | Drone shot spiraling down toward a subject | `a god's-eye spiral — the drone spirals down from above to her face, …` |
| Underwater Drift | Slow, weightless camera move underwater | `an underwater drift, the camera floating weightlessly, …` |

## H. Drone and aerial moves (specialty vocabulary)

| Term | Visible result | H3 phrasing |
|---|---|---|
| Fast FPV drone shot, aerial flyover | Low drone flythrough at speed | `a fast FPV drone shot skims the rooftops at speed, …` |
| Drone fly-through gap | Drone slips through a narrow opening | `the drone flies through the gap between the buildings, …` |
| Fly through / Pass through | Camera flies through an opening | `the camera flies through the broken window into the room, …` |
| Drone dive / Nosedive | Drone plunges downward | `a drone dive — the camera plummets from the sky to the street, …` |
| Drone nose-down to tilt-up reveal | Drone tilts up to reveal what it dove toward | `the drone noses down then tilts up, revealing the cathedral below, …` |
| Looking back drone shot | Drone reverses direction mid-shot | `a looking-back drone shot — the drone sweeps past, then banks to look back at her, …` |
| Top-down tracking shot | Drone looks straight down while moving | `a top-down tracking shot — the camera glides over her from above, …` |
| Glider shot / Cable cam | Camera on a suspended cable | `a cable-cam shot — the camera slides along the wire above the parade, …` |
| Vortex shot / Spinning tunnel | Camera spins while moving forward (often FPV) | `a vortex shot — the camera spirals down the tunnel, …` |
| Chase camera, high speed shaking | Aggressive chase framing | `a chase camera — the camera races behind her, the frame shaking violently, …` |
| Sliding shot / Slider movement | Short smooth lateral move on a slider rail | `a slider shot — the camera glides laterally across the table, …` |

## I. Pairing with other references

- **With composition (`references/03`)** — leading lines and depth cues do most of the work for a static shot; a camera move needs the same composition rules applied to its starting and ending frames.
- **With lighting (`references/02`)** — a dolly into a backlit silhouette changes the read of the lighting as the subject moves through the light. State both the move and the light.
- **With editing (`references/08`)** — the shot's function (establishing, reaction, cutaway) drives whether it's worth placing a motion on it. Reaction shots usually stay static or use a small push-in; establishing shots usually move (crane, drone, dolly).
- **With storytelling (`references/10`)** — repeated moves (the same push-in on the same character across cuts) carry meaning. State the recurring move explicitly.