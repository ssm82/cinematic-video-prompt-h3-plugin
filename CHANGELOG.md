# Changelog

All notable changes to this plugin are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] — 2026-09-30

Initial release of the **Agent Plugins v1.0.0 conformant package** for the MiniMax H3 cinematography vocabulary.

This package is a structural re-packaging of [`ssm82/cinematic-video-prompt-skill-h3`](https://github.com/ssm82/cinematic-video-prompt-skill-h3) — the prompt content (vocabulary, grammar, recipes, mood lookup, failure modes, references, examples) is byte-identical across the two repos. The differences are structural.

### Added

- **`plugin.json`** — Agent Plugins v1.0.0 manifest at the plugin root. Required `$schema` (`https://agent-plugins.org/schemas/1.0.0/plugin.schema.json`) and `name` (`cinematic-video-prompt-h3`) fields, plus optional `version`, `description`, `author`, `homepage`, `repository`, `license`, `keywords`. Plugin name satisfies the Agent Plugins naming constraints (lowercase alphanumeric + hyphens; alphanumeric start and end; no consecutive hyphens or periods).
- **`mcp.json`** — empty `mcpServers` object with the required `$schema` (`https://agent-plugins.org/schemas/1.0.0/mcp.schema.json`). No MCP servers are registered; the file exists to satisfy the Agent Plugins v1 fixed-location requirement (§6.1, §7.2).
- **`skills/`** directory — three skills in fixed-location layout:
  - `skills/cinematic-video-prompt-h3/SKILL.md` — main prompt-writing skill (entry point).
  - `skills/cinematic-video-prompt-h3/references/` — ten reference files covering camera, lighting, composition, lens / format, style, materials, FACS, editing, sound design, storytelling.
  - `skills/cinematic-video-prompt-h3/examples/example-prompts-h3.md` — twenty worked examples across all five H3 modes.
  - `skills/character-sheet-lite-h3/SKILL.md` — bonus skill: character reference sheet for I2VA / Ref2VA consistency.
  - `skills/oriental-scene-lite-h3/SKILL.md` — bonus skill: Wuxia / Eastern-aesthetic scenes.
- **Agent Skills YAML frontmatter** on every `SKILL.md`:
  - `name` field matches the parent directory name (Agent Skills spec requirement).
  - `description` field is ≤1024 characters and includes "Use when…" trigger phrases.
  - `name: cinematic-video-prompt-h3`, `name: character-sheet-lite-h3`, `name: oriental-scene-lite-h3`.
- **README.md** — rewritten for Agent Plugins format: skill discovery flow (`skills/` location), MCP server discovery flow (`mcp.json`), installation instructions, structural overview, three-repo provenance table (upstream + this fork + older Claude-style fork).

### Changed

- **`bonus-skills/character-sheet-lite/SKILL.md`** → `skills/character-sheet-lite-h3/SKILL.md` (renamed directory so the `name` field matches the parent dir, per Agent Skills spec).
- **`bonus-skills/oriental-scene-lite/SKILL.md`** → `skills/oriental-scene-lite-h3/SKILL.md` (same reason).
- **`references/`** (root) → `skills/cinematic-video-prompt-h3/references/` (Agent Skills spec puts references next to the skill's `SKILL.md`).
- **`examples/example-prompts.md`** (redirect file) → removed (the redirect was redundant once both `examples/` files live in the same folder).
- **`examples/example-prompts-h3.md`** → `skills/cinematic-video-prompt-h3/examples/example-prompts-h3.md` (moved alongside the skill).

### Provenance

This work is a derivative of [`Rylaispirit/cinematic-video-prompt-skill`](https://github.com/Rylaispirit/cinematic-video-prompt-skill), which provided the original 700+ term Vietnamese-language cinematography vocabulary. The upstream copyright notice and MIT license are preserved unchanged in [`LICENSE`](./LICENSE).

The H3 adaptation — structured-prompt grammar, mode templates, vocabulary mapping, recipes, mood lookup, pre-flight checklist, failure modes, references, and examples — is original work by Serge (`ssm82`).

## [0.x] — pre-release (in `ssm82/cinematic-video-prompt-skill-h3`)

The `ssm82/cinematic-video-prompt-skill-h3` repo carries the prior history of the H3 adaptation in the original (Claude-style) layout. See that repo's CHANGELOG for the full pre-1.0.0 history:

- Initial H3 adapter fork (commit `7048cfa`) — restructured 700+ cinematography terms into H3's structured-prompt grammar; added 4 new reference files (`07-facs`, `08-editing-transitions`, `09-sound-design`, `10-storytelling-devices`); created `bonus-skills/character-sheet-lite` and `bonus-skills/oriental-scene-lite`; all in English.
- Review pass (commit `baf2f8a`) — resolved internal contradictions; corrected FACS AU codes (AU13, AU14, AU43, AU45, AU51–58, AU64–67); softened absolutist claims ("one motion per shot", "FACS is the most reliable"); added blocking / screen direction / eyeline / OTS / master shot / coverage vocabulary in `references/03`; added a full focus section in `references/04`; added master shot / coverage / OTS matching / neutral shot vocabulary in `references/08`; demoted delivery-parameter terms (ProRes 4444, Rec. 709, etc.) to "set on model side"; softened categorical contrasts (warm + grief, golden hour + rain) — kept the underlying concern, reframed as "avoid unmotivated contradictions".
- Camera + lens pass (commit `113a4da`) — restructured `references/04` to format-first vocabulary (Digital cinema / Super 35 / Super 16 / Super 8 / 65mm / camcorder / mobile) with named cameras (ARRI ALEXA / VENICE / RED / ARRICAM) as optional secondary reference; added lens types (spherical / anamorphic / macro / probe / tilt / shift / fisheye / Petzval / vintage); added the "H3 Integration Sequence" (shot size + position → FoV bound to format → sharp / blurred → one optical effect → texture → brand as optional reference) with worked examples for emotional portrait, hero in environment, and product macro; added the "What NOT to make mandatory rules" section rejecting six folk-wisdom claims (85mm always portrait, large-format always shallow DoF, anamorphic always blue flares, vintage always soft, ARRI automatically cinematic, camera name guarantees resolution).