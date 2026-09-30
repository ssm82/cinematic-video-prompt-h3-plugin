# Contributing

Thanks for your interest in the **Cinematic Video Prompt — H3 Adapter** Agent Plugin. This document covers the scope, style, and review process for contributions.

## Scope

The plugin's purpose is to translate cinematography vocabulary into H3-class video generation prompts. Contributions are welcome in three areas:

1. **Vocabulary additions and corrections** — new cinematography terms in `skills/cinematic-video-prompt-h3/references/01–10.md`, or corrections to existing entries.
2. **Recipe combos and worked examples** — new entries in `skills/cinematic-video-prompt-h3/SKILL.md` (recipes), or new worked examples in `skills/cinematic-video-prompt-h3/examples/example-prompts-h3.md`.
3. **Failure modes** — observed behaviors from H3-class models that future users should know about, added to `SKILL.md §8` with a documented / heuristic / experimental evidence status.

Contributions outside scope (and likely to be declined):

- Adding new component types beyond skills and MCP servers (Agent Plugins v1 only defines these two).
- Hard-coded prompts or presets specific to a particular commercial product.
- Brand-name promotions as "the only correct choice" — the camera + lens vocabulary is format-first by design; named cameras are aesthetic hints, not guarantees.
- Negative-prompt blocks (H3 doesn't support them; describe exclusions affirmatively).
- Undocumented shot-timing formats (`At MM:SS.mmm, …` is the only portable format).
- New code, scripts, or MCP servers that aren't part of the H3 prompt-writing problem space.

## Style

### YAML frontmatter on every SKILL.md

Every skill must have Agent Skills spec YAML frontmatter at the top:

```yaml
---
name: your-skill-name
description: Use when … (≤1024 characters; describes both what and when-to-use).
license: MIT
---
```

Rules:

- `name` must match the parent directory name (Agent Skills spec §name-field).
- `name` is lowercase alphanumeric + hyphens only; must start and end alphanumeric; no consecutive hyphens.
- `description` is ≤1024 characters, non-empty.
- `description` should describe both **what** the skill does and **when** to use it; include specific trigger keywords.
- `license` is the SPDX identifier or a reference to a bundled license file.

### Markdown body

- Body has no format restrictions, but follow these conventions:
  - Reference files open with `> **H3 mapping note (read first).**` describing how the vocabulary maps to H3 grammar.
  - Tables must have header row + matching separator row (matching column counts).
  - Each term includes: visible result + H3 phrasing (and optionally Common confusion, Evidence status).
- Evidence status convention (used throughout the references):
  - **Documented** — directly supported by the upstream H3 prompt-writing guide.
  - **Heuristic** — based on observed behavior of current H3-class video models.
  - **Experimental** — promoted as worth trying but not yet validated.

### References organization

Vocabulary lives in numbered files in `skills/cinematic-video-prompt-h3/references/`:

| File | Domain |
|---|---|
| `01-camera-angles-and-movement.md` | shot size, camera height, orientation, viewpoint, translation / rotation, support, function, special effects |
| `02-lighting.md` | lighting direction, setups (key / fill / back / three-point), modifiers, source quality |
| `03-composition.md` | framing, lines, visual weight, blocking / screen direction / eyeline, staging in depth, reframing |
| `04-lens-technical-film.md` | format / medium, lens types (spherical, anamorphic, macro, …), focal length bound to format, aperture / DoF, focus moves, optical accessories |
| `05-style-color-mood.md` | artistic styles, regional / cultural genres, palette, lighting consistency |
| `06-materials-weather-pose.md` | materials, surface, weather, body pose |
| `07-facs.md` | Facial Action Coding System (Ekman & Friesen 1978) — head + gaze AUs included |
| `08-editing-transitions.md` | cuts, transitions, audio across edits, master shot / coverage / OTS |
| `09-sound-design.md` | diegetic / non-diegetic split, Foley, leitmotif, voiceover, recipes |
| `10-storytelling-devices.md` | three-act structure, flashbacks, frame narratives, foreshadowing |

New vocabulary goes into the matching file. If the new vocabulary spans multiple files, update the most relevant one and cross-link.

## Review process

1. **Open an issue first** for major changes (new vocabulary domains, new recipes, structural changes). Minor edits and typo fixes can go straight to a PR.
2. **Verify vocabulary against an H3-class model** before submitting. The vocabulary describes what the model *renders*; an entry that doesn't actually render as described is a candidate for failure-mode inclusion (§8 of `SKILL.md`) rather than a vocabulary claim.
3. **PRs should:**
   - Use a single commit when possible; multiple commits are fine if the structure requires it.
   - Have a clear title and description.
   - Update `CHANGELOG.md` `[Unreleased]` section if the change is non-trivial.
   - Maintain the MIT license and the upstream attribution in `LICENSE`.

## Anti-patterns

- **Hard-coded brand-name promotion.** Don't write "the best camera is the ARRI ALEXA 35" or "85mm is always the best portrait lens." These are folk-wisdom claims, not rules.
- **Negative prompts.** H3 doesn't support them. Describe exclusions affirmatively: `clean frame with no on-screen text, no watermark, no subtitles,`.
- **Bare emotion words for facial expressions.** Use FACS Action Units (see `references/07-facs.md`) for the visible movements, or describe the muscle actions in plain English. `surprised face` alone averages into a generic grimace.
- **Unmotivated contrasts.** `Ghibli style + hyperrealistic + neon palette` is a contradiction. Deliberate counterpoint (warm interior + grief scene, sunlight + downpour) is fine when explained.
- **Delivering delivery parameters as visible properties.** `ProRes 4444`, `Rec. 709`, `DaVinci Resolve Color Grade`, `IMAX Quality`, `8K`, `Photogrammetry Scan Quality` are not visible frame properties — set them on the model side or in post. If you want the *look* they imply, name the observable phrasing.

## Plugin structure

The plugin conforms to [Agent Plugins v1.0.0](https://agent-plugins.org/specification) and the [Agent Skills specification](https://agentskills.io/specification):

- `plugin.json` — manifest with `$schema`, `name`, `version`, `description`, `author`, `homepage`, `repository`, `license`, `keywords`.
- `mcp.json` — empty `mcpServers` map with `$schema`. The plugin is skills-only.
- `skills/<skill-name>/SKILL.md` — one skill per directory. `name` in frontmatter must match the directory name.
- `skills/<skill-name>/references/` — optional documentation per skill.
- `skills/<skill-name>/examples/` — optional worked examples per skill.
- `skills/<skill-name>/scripts/` — optional executable code per skill.
- `skills/<skill-name>/assets/` — optional static resources per skill.

Other directories (e.g. `LICENSE`, `README.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, `.gitignore`) live at the plugin root. Client-specific extensions go under top-level directories named for the client namespace (e.g. `com.example.client/hooks/`).

## License

By contributing, you agree that your contributions will be licensed under the MIT license. See [`LICENSE`](./LICENSE).