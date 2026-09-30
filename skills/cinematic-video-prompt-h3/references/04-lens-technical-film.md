# Lens, Technical & Film Quality

> **H3 mapping note (read first).** Technical keywords in H3 are **trailing tags** at the end of the shot description, not standalone blocks. Group 1–3 of them in one comma-separated clause:
>
> `… shallow depth of field, 35mm film grain, 2.35:1 aspect.`
>
> Specific H3 grammar:
>
> - **Focal length / aperture / depth of field** → `shallow depth of field,` / `deep focus,` / `macro focus on …`
> - **Bokeh** → `oval bokeh in the background,` / `swirly Petzval bokeh,`
> - **Flares / halation** → `anamorphic lens flare,` / `cinematic halation,`
> - **Shutter / motion blur** → `shutter angle 180 degrees,` / `motion blur on the wheels,` / `frozen action at 1/8000s,`
> - **Film stock / grading** → `Kodak Portra 400 color,` / `CineStill 800T color shift,` / `bleach bypass,` / `teal and orange grading,` / `muted warm palette with lifted blacks,`
> - **Resolution / sharpness** → `hyperdetailed,` / `photorealistic,` / `sharp focus on the face,`
> - **Sensor / camera look** → `shot on Arri Alexa look,` / `authentic mobile phone photography style,` / `medium-format film quality,`
> - **Aspect ratio** → trailing tag is fine (`2.35:1 aspect,`) but most H3 model APIs expose aspect as a separate parameter; prefer setting it on the model side. If you write it in the description, pick one route only — do not set it on both sides.
> - **Negative prompt** → not supported. Rewrite exclusions affirmatively: `clean frame with no on-screen text, no watermark, no subtitles,`.
> - **Model flags (`--ar`, `--style raw`, etc.)** → not supported in H3 grammar. Translate the intent into natural language or use the model's parameter UI.

> **What this reference covers, and what it doesn't.**
>
> - **In scope** — terms that have an *observable* visual result in the rendered frame: lens choice, depth of field, focus behavior, bokeh, flares, halation, shutter / motion blur, sensor look, aspect ratio, film stock, color grading, white balance, grain, vintage / analog aesthetics, in-frame VFX.
> - **Out of scope (delivery parameters)** — production / delivery terms that don't translate into a visible frame property: `ProRes 4444`, `Rec. 709`, `DaVinci Resolve Color Grade`, `Photogrammetry Scan Quality`, `8K / 4K`, `IMAX Quality`, `Pristine 70mm Quality`, `High Bit Depth Color`. These describe codecs, color spaces, resolution, or capture pipelines that the model cannot reproduce directly. If you want the *look* they imply, use the observable phrasing shown next to each entry below. If you want the actual delivery format, set it on the model side or in post.

The full vocabulary for lenses, technical parameters, and film-quality cues.

## A. Lenses & Effects

### A1. Camera / medium / format — the *texture* of the image

> **Documented** (industry-standard categories) and **heuristic** (which cues current H3-class models reproduce reliably). The category sets the *texture and tonal character*; the lens and aperture control everything else.

| Category | What to describe in the frame | H3 phrasing example |
|---|---|---|
| **Digital cinema** | Clean image, natural skin, smooth highlight roll-off | `a clean digital-cinema image, natural skin tones, smooth highlight roll-off,` |
| **Super 35 digital** | Format-as-reference for field of view and depth of field | `Super 35 framing, moderate depth of field, a clean digital image,` |
| **Large-format digital** | Bigger format; with chosen optics and distance — subject separation from background | `large-format digital-cinema aesthetic, gentle background separation,` |
| **35mm motion-picture film** | Grain, emulsion texture, highlight behavior | `35mm motion-picture film texture, fine moving grain, restrained halation,` |
| **Super 16 film** | More visible grain, less smooth texture | `Super 16 film texture, visible grain, slightly softened fine detail,` |
| **Super 8 film** | Strong grain, possible frame instability, home-movie feel | `Super 8 home-movie texture, coarse grain, subtle gate weave,` |
| **65mm negative / 70mm presentation aesthetic** | Fine film texture, high detail, large-format feel | `65mm film aesthetic, fine grain, richly resolved landscape detail,` |
| **Consumer camcorder** | The look of domestic video of a specific era | `early-2000s consumer-camcorder footage, clipped highlights, modest dynamic range,` |
| **Mobile phone** | Wide field of view, usually deep DoF, computational processing | `mobile-phone footage, wide field of view, deep depth of field, mild computational sharpening,` |

> **Important.** Super 35 and large-format do not, on their own, mean a particular palette, grain, or "cinematic quality". They are *formats* first; describe every other property separately. The phrase `{format} framing, {DoF}, {texture}` is the safest template.

### A2. Named cameras — optional secondary reference

These are aesthetic hints, not guarantees. Don't write `RED = aggressive contrast` or `ARRI = always warm skin` — the final image depends on light, exposure, optics, and processing.

| Camera / family | How to use | Recommended phrasing template |
|---|---|---|
| **ARRI ALEXA / ALEXA 35** | Reference for digital-cinema aesthetic; specify skin tone, contrast, and highlight behavior separately | `An ARRI ALEXA-inspired digital-cinema image, natural skin tones and smooth transitions into bright highlights,` |
| **ARRI ALEXA LF / Mini LF** | Reference for large-format digital; pick lens and DoF separately | `A large-format ARRI ALEXA LF-inspired image, gentle background separation, …` |
| **Sony VENICE / VENICE 2** | Reference for digital cinema; do not assume a cold or blue cast | `A Sony VENICE-inspired digital image, …` |
| **RED V-RAPTOR / KOMODO** | Reference for digital capture; do not assume fixed sharpness, saturation, or contrast | `A RED V-RAPTOR-inspired image, …` |
| **ARRICAM / ARRIFLEX 435** | Reference for 35mm motion-picture film capture; texture comes from the stock and processing | `35mm motion-picture film capture on an ARRIFLEX 435-inspired camera, fine grain, …` |
| **ARRIFLEX 416** | Reference for Super 16; grain and color specified separately | `Super 16 capture on an ARRIFLEX 416-inspired camera, visible grain, …` |

**Preferred template:** `{camera-family} aesthetic, {two observable image properties}.`

If the brand name doesn't help the model, drop it and keep the observable properties.

### A3. Focal length (bound to format) and aperture

> **Documented** (optical behavior). **Heuristic** (how cleanly the model reproduces a given focal length's *look* — usually fine).

Focal-length numbers in this table assume a **full-frame / 35mm still-equivalent** field of view. On Super 35 the same lens gives a *narrower* field of view; on large-format it gives a *wider* one. Bind the number to the format in the prompt.

| Focal length (full-frame equiv.) | Practical use | What to clarify in the prompt |
|---|---|---|
| **14–20mm, ultra-wide** | Architecture, tight interiors, dynamic POV | Large share of environment; close camera exaggerates foreground objects |
| **24–28mm, wide** | Hero in space, walk-and-talk, moving alongside a character | Subject-to-environment relationship, distance to camera |
| **35mm, moderate wide** | Dialogue with the environment, observational framing | Moderate wide FoV, readable background |
| **50mm, normal** | Medium shots, neutral observation | Frame size and distance; don't promise "exactly the human eye" |
| **75–100mm, short telephoto** | Portrait, emotional close-up | Narrower FoV, the chosen amount of background blur |
| **135–200mm, telephoto** | Distant observation, layered cityscapes | Camera far from the action, visually compressed planes |
| **300mm+, long telephoto** | Sports, wildlife, very remote details | Very narrow FoV, distance, atmospheric haze if needed |

#### Aperture and depth of field

> **Important — DoF is not determined by aperture alone.** Depth of field depends on *format, focal length, subject distance, and chosen frame size*. The f-stop or T-stop number does not, on its own, guarantee a particular amount of blur. Describe the blur; let the model pick the parameters that produce it.

| Term | What to describe | H3 phrasing |
|---|---|---|
| **f-stop** | Relative aperture (still-photography convention) | use only when paired with `shallow depth of field,` or another DoF cue |
| **T-stop** | Light transmission (cinematography convention) | same as f-stop: pair with DoF |
| **Shallow depth of field** | One plane sharp; rest of frame soft | `Shallow depth of field: her eyes remain sharp, while the room behind her falls into soft blur,` |
| **Moderate depth of field** | Subject sharp, environment partly readable | `Moderate depth of field — her face and her hands are sharp; the background is recognizable but soft,` |
| **Deep depth of field** | Multiple planes sharp simultaneously | `Deep focus — the key in the foreground and the figure in the doorway both sharp,` |
| **Hyperfocal distance** | Setting that maximizes the in-focus range | use only when paired with `deep focus,` |
| **Focus distance** | The distance from the lens to the sharp plane | describe the subject's distance from camera: `shot from across the room, …` |
| **Foreground / subject / background separation** | Three depth bands with three different sharpness levels | `foreground soft, her face in sharp focus, the city skyline behind her slightly soft,` |

> **Perspective correction — important.** Perspective (the spatial relationship between near and far objects) is determined by **camera position**, not focal length. "Telephoto compresses space" is shorthand: to keep the same framing, the operator steps further back, and that new shooting point changes the foreground/background relationship. Use this phrasing:
>
> ```
> An 85mm full-frame-equivalent portrait view from several meters away, the distant background appearing closely layered behind her.
> ```
>
> instead of:
>
> ```
> 85mm lens, cinematic compression.
> ```
>
> The first names the *position* and the *result*; the second relies on a shorthand the model may not resolve correctly.

### A4. Lens types

| Type | Visible result / use | H3 phrasing |
|---|---|---|
| **Spherical lens** | Standard uncorrected projection; specific character depends on the lens | `spherical-lens rendering, round out-of-focus highlights,` |
| **Anamorphic lens** | Possible oval bokeh, directional flares, characteristic distortion | `anamorphic rendering, oval background bokeh, restrained horizontal flares,` |
| **Macro lens** | Close-up of small objects at high magnification | `a macro close-up of the watch mechanism, focus on the moving escapement,` |
| **Probe lens** | Close view inside tight spaces with wide surroundings | `a wide-angle probe-lens view moving between the miniature gears,` |
| **Tilt lens** | Focus plane tilted away from parallel-to-sensor | `a tilted focus plane keeping the tabletop objects sharp along a diagonal,` |
| **Shift lens** | Perspective correction of architecture with appropriate staging | `perspective-corrected architectural framing, vertical lines remaining parallel,` |
| **Fisheye lens** | Non-linear projection, strongly bowed lines | `fisheye projection, straight architectural lines bowing near the frame edges,` |
| **Petzval-style lens** | Possible swirly bokeh, soft periphery | `Petzval-style swirling background bokeh, the central face remaining sharp,` |
| **Vintage spherical lens** | Selected aberrations, flares, lower contrast transfer | `vintage spherical-lens rendering, gentle veiling flare and softened corners,` |

**Two clarifications:**

- **Not every anamorphic lens produces the same strong blue streak, oval bokeh, or soft edges.** Name the specific effect you want.
- **Split diopter is an accessory, not a lens type.** See section A7 below.

### A5. Named lens families (optional reference)

A short reference list — without promises of exact reproduction. Pair each name with 1–3 specific visible properties.

- **ARRI Signature Prime** — modern large-format lens reference.
- **ZEISS Supreme Prime / Master Prime** — modern spherical cinema-optics reference.
- **Cooke S4/i / Panchro** — different generations of spherical optics; don't merge them into one fixed "Cooke Look".
- **Canon K-35** — vintage cinema-optics reference.
- **Panavision C Series / other specific anamorphic families** — anamorphic-rendering reference.
- **Helios 44-2** — strong swirly bokeh reference when background and conditions support it.

Worked template:

```
Vintage K-35-inspired lens rendering, softened highlight edges,
gentle veiling flare, and restrained contrast.
```

That's the *intended* aesthetic — not a claim that every K-35 in any setup looks exactly that way.

### A6. Quick-reference legacy terms (kept for vocabulary coverage)

The following terms from upstream are kept as one-liners for parity with the source vocabulary. Where possible, prefer the format-first framing above. Each term still resolves to an *observable phrasing* — if you use one of these in a prompt, expand it into the visible result.

| Term |
| --- |
| 24mm / 35mm / 50mm / 85mm lens |
| Fast prime lens (50mm f/1.4, 85mm f/1.8) |
| Aperture f/1.2 (Extreme Shallow Depth) |
| T-Stop T1.4 |
| shallow depth of field |
| Depth of Field (Extremely Deep) |
| Hyperfocal Distance |
| Macro Photography (Extreme Detail) |
| fisheye lens |
| Lens Distortion (Pin Cushion/Barrel) |
| Distortion (Warped Perspective) |
| Tilt-Shift Lens Effect (Miniature Faking) |
| Faux Tilt-Shift (Digital Miniature) |
| Tilt-Shift (Vertical/Horizontal Focus Plane) |
| Vintage Lens Aesthetic |
| Uncoated Lens Look |
| Anamorphic Squeeze / De-Squeeze |

> **Heuristic — focus stacking.** "Telephoto Lens (Focus Stacking)" is a single term from upstream; focus stacking is not a property of telephoto lenses. If you want a deep-focus look, name it explicitly: `deep focus, both the foreground key and the background figure sharp,`.

### Bokeh
| Term |
| --- |
| bokeh |
| Anamorphic Bokeh (Oval) |
| Lens Bokeh (Swirly/Petzval) |
| Lens Bokeh (Lemon/Cat's Eye) |

### Flare & Light Leaks
| Term |
| --- |
| lens flare |
| anamorphic lens flare |
| Blue Streak Filter / Vertical Flare |
| Anamorphic Glare (Red/Orange Streak) |
| Lens Flare (Multiple Rings) |
| Ghosting Effect (Flare) |
| Flare (Dusty/Dirty Lens) |
| Lens Whacking (Light Leak) |
| Sun Star Effect (Sharp Aperture) |
| Diffraction Spike Filter |
| Cinematic Halation |

### Shutter & Motion
| Term |
| --- |
| motion blur |
| Motion Blur (Radial) |
| Shutter Speed 1/8000s (Freezing Action) |
| Shutter Speed 1/30s (Subtle Motion Blur) |
| Shutter Speed 1/2s (Heavy Motion Blur) |
| Shutter Angle 180 Degrees |
| long exposure / Long exposure for light trails |
| Variable ND Filter (Motion Blur Control) |
| time-lapse |
| High Refresh Rate (Fluid Motion) |
| Low FPS Motion Blur (Stuttering) |
| Film Stutter (Choppy Motion) |
| Camera Shake (Digital Emulation) |
| Sharp focus on subject's face |
| Hyperrealistic Sharpness |

### Focus & depth

> **Heuristic.** Rack focus and selective focus are observable moves the model can attempt; "deep focus" and "split diopter" describe the depth-of-field behavior in the frame. "Focus breathing" and "focus pull" describe focus mechanics and may or may not render literally.

| Term | Visible result | H3 phrasing |
|---|---|---|
| Rack focus (Focus Pull A → B) | Focus shifts from one subject to another mid-shot | `rack focus — the focus shifts from the key in the foreground to the woman in the doorway. The camera remains locked off, …` |
| Focus tracking | Focus follows a moving subject | `focus tracking — the camera remains still as the focus follows her across the room, …` |
| Selective focus | One subject sharp, the rest of the frame soft | `selective focus on the locket in her hand, the rest of the frame soft, …` |
| Focus plane | The depth slice that is sharp | `the focus plane sits at her eyes, the foreground railing and the back wall both soft, …` |
| Focus breathing (optional) | Subtle focal-length shift as focus racks | `a faint focus breathing as the focus pulls to the background, …` (rare in current H3-class models) |
| Deep focus | Both foreground and background sharp | `deep focus — the figure in the foreground and the building behind both sharp, …` |
| Shallow depth of field | Only one plane is sharp | `shallow depth of field, only her eyes in focus, …` |
| Split Diopter | Lens holds focus on two planes simultaneously | `a split diopter keeps both her face in the foreground and the door behind sharp at the same time, …` |
| Parallax | Foreground and background shift relative to each other as camera moves | `parallax — the foreground railing slides past faster than the background as the camera trucks right, …` |
| Perspective compression | Background appears closer to subject (long lens) | `a long-lens perspective compression — the distant skyline presses up behind her, …` |
| Perspective expansion | Background appears further from subject (wide lens) | `a wide-lens perspective expansion — the background recedes behind her, the foreground exaggerating, …` |

Worked example, focus move inside a static shot:

```
A locked-off medium shot of two figures. She stands in the foreground on
screen left, his face in the doorway behind her. At 00:01.500, the focus
pulls from him to her. Her face sharpens as his softens. The camera does
not move.
```

> **A focus shift is not a camera move.** It can combine with a static camera, a slow pan, or a dolly. State the camera move and the focus move separately.

### Filters & Soft Processing
| Term |
| --- |
| ProMist Filter / Black Pro Mist |
| Soft Focus (Black Mist Filter) |
| Cinematic Diffusion (Heavy) |
| Soft Focus (Dream Glow) |
| Soft Focus (High Contrast Edges) |
| Glow Effect (Digital Post-Processing) |
| Warm Polarizer Filter |
| Circular Polarizer Filter (Max Saturation) |
| Soft Vignette (Subtle Light Falloff) |
| Vignetting (Rectangular Frame) |
| Pinhole Camera Effect |
| double exposure |
| Double Exposure (Ghosting Effect) |
| infrared |
| Chromatic Aberration / Color Fringing |
| Chromatic Separation |

## B. Camera & Sensor (legacy brand-first list — superseded by section A1/A2)

> **Heuristic — format first, brand second.** Section A1 and A2 above are the *recommended* camera vocabulary: pick a **format** (digital cinema / Super 35 / large-format / 35mm film / Super 16 / Super 8 / 65mm / camcorder / mobile), then optionally add a **named camera family** as an aesthetic reference. The brand-first terms below are kept for vocabulary parity with upstream but should be rephrased into format + observable properties when used.

| Term (legacy) | Format-first rephrasing |
| --- | --- |
| Shot on Sony Alpha camera | `a clean digital-cinema image with natural skin tones,` |
| Shot on RED Gemini / Arri Alexa | `a clean digital-cinema image, smooth highlight roll-off,` (drop the brand if the model doesn't parse it) |
| Super 35 Sensor Format | `Super 35 framing, moderate depth of field, a clean digital image,` |
| Medium Format Film Quality / Medium Format Digital Look | `large-format digital-cinema aesthetic, gentle background separation,` |
| authentic mobile phone photography style (24–26mm) | `mobile-phone footage, wide field of view, deep depth of field, mild computational sharpening,` |
| ISO 100 (Clean Image) | `a clean image with no visible noise,` |
| Clean Digital Sensor Look (No Grain) | `a clean digital image, no visible grain,` |
| Digital Noise Reduction (Off) | (rarely useful — describe the *visible* noise: `visible sensor noise in the shadows,`) |
| Digital Noise (Color Noise) | `subtle color noise in the dark areas,` |
| hyperdetailed | `hyperdetailed — fine surface texture and micro-contrast,` |
| Photogrammetry Scan Quality | delivery parameter — see scope note above |

> **Heuristic — resolution claims.** `8K`, `4K`, `hyperdetailed`, `Photogrammetry Scan Quality` do not reliably produce a particular pixel count in H3-class video output. `hyperdetailed` is the most useful — it cues fine surface texture and micro-contrast.

## C. Aspect Ratio
| Term |
| --- |
| Cinemascope / 2.35:1 Aspect Ratio |
| Wide Aspect Ratio 2.76:1 (Ultra Panavision) |
| IMAX framing (large-format composition — describe the framing, not the format) |
| 16:9 / 9:16 vertical / 1:1 |

> **Documented.** Aspect ratio has a model-side parameter. Set it there when possible. Writing the ratio inside the description (e.g. `2.35:1 aspect,`) is allowed when you want the model itself to bias the framing — pick one route, not both. `IMAX framing` is best expressed as a composition cue: `a tall, edge-to-edge composition filling the large-format frame,`.

## D. H3 Integration Sequence — choosing camera, lens, and focus

When a brief calls for a specific cinematic look, work through the choices in this order. Each step depends on the previous one.

1. **Determine shot size and camera position.** `a medium shot, eye-level, frames her beside the window` — done before any optical choice.
2. **Pick field of view / focal length, bound to format.** `a 28mm full-frame-equivalent wide view` or `a 85mm full-frame-equivalent portrait view from several meters away`. The same number means different things on Super 35 or large-format — always bind to format.
3. **State what is sharp and what is blurred.** `Focus stays on her eyes as she lowers her chin; the background remains softly blurred.` Don't rely on f-stops or T-stops alone — name the blur.
4. **Add one characteristic optical effect if needed.** `oval background bokeh,` / `gentle veiling flare,` / `Petzval-style swirling bokeh at the edges,`. One effect reads; stacking two or three reads as noise.
5. **Pick the camera / film texture.** `a clean digital-cinema image, natural skin tones, smooth highlight roll-off,` or `Super 16 film texture, visible grain, slightly softened fine detail,`.
6. **Brand name — only as an optional reference.** Drop the brand if the model doesn't parse it; the observable properties carry the look.

### Compact template

```
{shot size and camera position}.
{lens / field of view bound to format}, {focus behavior}.
{camera or film texture}, {one optical characteristic}.
```

### Worked examples

**Emotional portrait** (T2VA single shot, 6 s):

```
[Shot 1] Live-action, cinematic, a close-up at eye level frames the
woman beside the window. An 85mm full-frame-equivalent portrait view
isolates her against the room. Focus stays on her eyes as she lowers
her chin; the background remains softly blurred. A clean digital-cinema
image with natural skin tones and smooth highlight roll-off.
```

**Hero in environment** (T2VA, walking shot):

```
[Shot 1] Live-action, cinematic, a medium shot frames the man walking
through a narrow workshop. A 28mm full-frame-equivalent wide view keeps
the benches and hanging tools visible around him. The camera tracks
backward, maintaining his size in the frame. Moderate depth of field,
Super 16 film texture, visible fine grain.
```

**Product macro** (T2VA single shot):

```
[Shot 1] Live-action, a macro close-up frames a drop of water on a
brushed-metal watch case. Focus holds on the drop and the engraved
lettering beneath it; the far edge of the case falls out of focus.
Clean digital rendering, controlled specular highlights.
```

### What NOT to make mandatory rules

These are common folk-wisdom claims that are not reliable as rules. State them as **heuristics** when useful; never as absolutes.

- `85mm is always the best portrait lens` — true *if* the operator also moves to the right distance; otherwise it's just a label.
- `Large-format always gives shallow depth of field` — the format affects DoF, but DoF depends on focal length, aperture, and distance too.
- `Anamorphic always means blue horizontal flares` — not all anamorphic lenses produce blue streaks or strong oval bokeh; name the effect.
- `Vintage optics are always soft` — vintage character varies; describe the specific softness you want.
- `ARRI automatically makes the image cinematic` — no camera, including an ARRI, makes an image cinematic on its own; light, lens, framing, and color carry that.
- `A camera name guarantees its resolution, dynamic range, or color` — the model cannot reproduce exact sensor specifications; describe the visible result.

> The practical conclusion: format and lens together give the most reliable control over field of view, perspective, depth of field, and optical character. Brand names are the **least** useful layer. If you have to drop one, drop the brand.

## E. Film & Quality
### Film Grain & Stock
| Term |
| --- |
| High Grain / Film Grain |
| Cinematic 35mm Film Grain (Medium) |
| Film Grain (Heavy, Colored) |
| Grain (Luminance Only) |
| Overexposed Film Grain |
| Film Stock [Kodak Portra 400] |
| Vintage Kodachrome Colors |
| CineStill 800T Color Shift |
| Slide Film Look (High Saturation, Sharp) |
| Color Negative Film (Faded Shadows) |
| Cross Processed E-6/C-41 |
| Bleach Bypass Effect |
| Technicolor Aesthetic |
| Super 8 Film Aesthetic |
| Super 16mm Film Look |
| Cinematic 35mm Film Grain |

> **Heuristic.** "Pristine 70mm Quality" is a delivery descriptor, not a visible cue. If you want the look it implies (sharpness + fine grain + clean highlights), name the visible parts: `sharp focus on her face, fine 35mm grain, clean highlights,`.

### Vintage & Analog
| Term |
| --- |
| vintage photo |
| Polaroid (Worn Edges) |
| Disposable Camera Aesthetic |
| Lomography Aesthetic |
| Daguerreotype Photo |
| Wet Plate Collodion (Ambrotype) |
| Sepia Tone (Heavy) |
| Film Scratch Overlay |
| Underexposed Film Look (Muted Colors) |
| Faded Color Grading (Low Saturation) |

> **Optional cues.** Daguerreotype, wet plate, Polaroid, Lomography, daguerreotype, sepia, and similar analog aesthetics are optional layered cues — useful when the brief is specifically vintage / archival. Use 1–2 at most per shot; they tend to read as additive effects that don't necessarily combine cleanly.

### Digital & Artifacts
| Term |
| --- |
| Lo-Fi Digital Look (JPEG Artifacts) |
| Lossy Compression Artifacts |
| VHS Tracking Error |
| Moiré Pattern Effect |
| Screen Door Effect |
| 8-Bit Color Palette |
| Anaglyph 3D Effect |
| 3D Render (Low Polygon Count) |
| Unreal Engine 5 Render (Photorealistic) |
| Photorealistic CGI (No Imperfections) |

### Color Grading & Post
| Term |
| --- |
| Vibrant HDR / HDR Tone Mapping (Artistic Look) |
| Low Contrast Grading |
| Flat Color Profile (Log) |
| Vibrance Boost (Post-Processing) |
| Hyper-Saturation Post-Processing |
| Warm White Balance / Cool White Balance |
| Cool color balance with warm neon accents |
| Underexposed / Overexposed |
| Exposure Bracketing (optional — see note) |
| black and white / Black and White (High Contrast, Ansel Adams Style) |

> **Delivery parameters — moved out.** `Rec. 709 Color Space`, `DaVinci Resolve Color Grade`, `High Bit Depth Color (Smooth Gradient)`, `ProRes 4444 Quality` are delivery / production descriptors. Set color space, codec, and bit depth on the model side or in post. If you want the *visible result* these imply, use:
>
> | Delivery term | Observable phrasing |
> |---|---|
> | `Rec. 709 Color Space` | already the default — no need to state |
> | `DaVinci Resolve Color Grade` | a specific palette / contrast / shadow tint (`high contrast with teal lifted blacks,` etc.) |
> | `High Bit Depth Color` | `smooth gradients without visible banding,` |
> | `ProRes 4444 Quality` | n/a (delivery parameter; not a visible cue) |
> | `Exposure Bracketing` | n/a for video generation — describes multi-frame capture. State the chosen exposure instead: `slightly overexposed — the highlights bright but readable,` |

## In-Frame Visual Effects (VFX vocabulary)

These effects describe things inside the rendered image, not just the camera. Fold them into the shot description as inline phrases — they tend to read as trailing adjectives after the subject or scene.

| Effect | Definition | H3 phrasing |
|---|---|---|
| Bloom Effect | Soft glow around bright areas, light bleeds beyond boundaries | `bloom effect — soft luminosity around the neon sign, light bleeding into the wet street, …` |
| Glow Effect | Soft luminosity around highlights, ethereal feel | `a glow around her hair and shoulders, the rim light spilling outward, …` |
| HDR Effect | High dynamic range — both highlights and shadows retain detail | `HDR look — expanded tonal range, both the lit windows and the shadowed faces holding detail, …` |
| Loop Animation | Seamless repeating motion, no visible start or end | `a loop animation — the figure breathing in and out, the curtains swaying, on a seamless cycle, …` |
| Motion Blur | Streaking on moving elements during exposure | `motion blur on the wheels, …` (already in section A); use as a global adjective: `heavy motion blur across the running figure, …` |
| Chromatic Aberration | Color fringing at high-contrast edges (lens imperfection) | `chromatic aberration on the corners of the frame, red-green fringes at high-contrast edges, …` |
| Particle Effects | Sparks, rain, snow, dust, embers, magical energy | `particles of ash drifting through the light beam, …` / `snow particles falling across the beam, …` |
| Reflections | Mirror-like surfaces showing the environment | `reflections in the wet asphalt — the neon signs doubled in the puddles, …` |
| Refractions | Light bending through transparent materials | `refractions in the curved glass of the bottle, the room distorted behind it, …` |
| Lens Distortion | Straight lines bowing toward frame edges (wide-angle) | `lens distortion warping the corners of the frame, …` |
| Split Diopter | Lens allowing focus on foreground and background simultaneously | already noted earlier; use as adjective: `a split diopter keeps both the face and the door sharp simultaneously, …` |
| Aspect Ratio | Width-to-height proportional relationship | set on the model side; if mentioned in description, use specific ratio: `2.35:1 aspect,` |
| Anamorphic | Squeezed wide image via special lenses, then unsqueezed | already covered in section A |
| IMAX | Large-format, very high resolution | `IMAX-quality detail, …` |
| Forced Perspective | Spatial perception manipulation via distance positioning | already covered |
| Matte Painting | Painted backdrop combined with live footage (now digital) | `matte-painted mountains extending the practical set, …` |
| Miniatures | Scaled-down models appearing full-size | `miniature city exploding, the buildings crumpling in sequence, …` |
| Virtual Production | Real-time rendering on LED walls (in-camera backgrounds) | `virtual production on LED walls — the background responds to camera parallax in real time, …` |
| Prosthetic Makeup | Sculpted pieces applied to actors for transformation | `prosthetic aging makeup on the protagonist, wrinkles and grey hair physically applied, …` |
| Squibs | Small explosive charges simulating bullet impacts | `squibs bursting against the vest, blood bags detonating, …` |
| Wire Work | Cables suspending performers for flying/floating | `wire work — she hangs suspended, defying gravity, the cables invisible, …` |
| Rotoscoping | Tracing over live-action footage frame by frame | `rotoscoped animation style — the live-action footage traced frame by frame, the lines visible, …` |
| Morphing | One image fluidly transforming into another | `morphing — the wolf's snout blends smoothly into the man's face, the features flowing into one another, …` |
| Digital De-aging | CGI making actors appear younger | `digital de-aging — the protagonist's face smoothed, the skin tightened, the jawline softened, …` |

## White Balance & Color Correction

| Term | Definition | H3 phrasing |
|---|---|---|
| White Balance | Color temperature adjustment for neutral whites | `white balance set to 3200K — the candle light reads as warm-neutral, …` |
| Color Temperature | Warm/cool hue scale (2700K warm → 6500K+ cool) | already covered |
| Color Correction | Adjustment for accurate, consistent color | `color-corrected to natural skin tones, …` |
