# 🎬 Cinematic Video Prompt — H3 Adapter (Agent Plugins)

An Agent Plugins v1.0.0 package that adapts a 700+ term cinematography vocabulary for **MiniMax H3** video generation. The vocabulary is camera-craft language (angles, movement, lighting, composition, lens / format, style, color, mood, sound design, editing, FACS, storytelling). The **container** is H3's structured output: a `[Shot 1] … [Shot N]` timeline plus `overall_soundscape` and `non_diegetic_music`; for reference-driven work (Ref2VA), the six-section layout (`subject_definitions`, `summary`, `retention_analysis`, `detailed_description`, `overall_soundscape`, `non_diegetic_music`).

> **For Agent Plugins v1.0.0 conformant clients.** This package ships as a self-contained directory. Drop it into the client's plugin path and the client discovers all three skills via the `skills/` location and (optional) MCP servers via `mcp.json`. See the [Agent Plugins Specification](https://agent-plugins.org/specification) and the [Agent Skills Specification](https://agentskills.io/specification).

---

## What this plugin contains

```
cinematic-video-prompt-h3-plugin/
├── plugin.json                          # Agent Plugins manifest
├── mcp.json                             # empty mcpServers (no MCP servers)
├── LICENSE                              # MIT
├── README.md                            # this file
├── CHANGELOG.md                         # release history
├── CONTRIBUTING.md                      # contribution guidelines
├── .gitignore
└── skills/
    ├── cinematic-video-prompt-h3/       # the main skill (entry point)
    │   ├── SKILL.md                     # H3 prompt grammar, workflow, recipes, 21 failure modes
    │   ├── references/                  # 10 vocabulary references (camera, lighting, lens, FACS, ...)
    │   │   ├── 01-camera-angles-and-movement.md
    │   │   ├── 02-lighting.md
    │   │   ├── 03-composition.md
    │   │   ├── 04-lens-technical-film.md
    │   │   ├── 05-style-color-mood.md
    │   │   ├── 06-materials-weather-pose.md
    │   │   ├── 07-facs.md
    │   │   ├── 08-editing-transitions.md
    │   │   ├── 09-sound-design.md
    │   │   └── 10-storytelling-devices.md
    │   └── examples/
    │       └── example-prompts-h3.md    # 20 worked examples across all five H3 modes
    ├── character-sheet-lite-h3/         # bonus: character reference-sheet prompt for I2VA / Ref2VA
    │   └── SKILL.md
    └── oriental-scene-lite-h3/          # bonus: Wuxia / Eastern-aesthetic scene prompt
        └── SKILL.md
```

**No MCP servers are declared.** `mcp.json` exists with an empty `mcpServers` map to satisfy the Agent Plugins v1 fixed-location requirement (§6.1, §7.2). The plugin is skills-only.

---

## Skills at a glance

### `cinematic-video-prompt-h3` (main skill)

A prompt-writing assistant that translates free-form cinematic vocabulary into H3's natural-language shot-description grammar. Pair with the upstream H3 prompt-writing guide (`minimax-h3-skills:h3-prompt-writing`) which owns the field schema, label conventions (`<Subject N>` / `<Picture N>` / `<Video N>` / `<Audio N>`), and shot-timing format.

The skill includes:

- A **prompt formula** adapted for H3 (style descriptor + opening composition + camera setup + subject + lighting + camera-motion clause + color grading + technical closing clause).
- A **vocabulary mapping** for the five H3 modes (T2VA, I2VA, FL2VA, L2VA, Ref2VA).
- **Eleven recipe combos** — character study, cinematic landscape, action sequence, dialogue scene, montage, flashback, product showcase, animation style, period piece, dream sequence, POV shot.
- A **mood lookup** that cross-references palette + lighting + posture + sound for thirty moods.
- A **pre-flight checklist** covering schema, cut timing, audio routing, dialogue tags, and affirmative exclusion phrasing.
- **Twenty-one failure modes** documented from observed H3-class model behavior.
- **Ten reference files** with 700+ cinematography terms, organized so each opens with an "H3 mapping note (read first)" header.

### `character-sheet-lite-h3`

A character reference-sheet prompt that produces three full-body views + one close-up in a single image. The output feeds into H3 as `<Picture 1>` for I2VA mode or as the source defining `<Subject 1>` for Ref2VA mode, so the same character stays consistent across shots. Two paths:

- **Path A** — single-shot I2VA: 4-view sheet, then animate with H3 using the sheet as input.
- **Path B** — multi-shot Ref2VA: same sheet as the source for `<Subject 1>`, then produce a multi-shot sequence with `summary` + `subject_definitions` carrying the identity through.

### `oriental-scene-lite-h3`

A Wuxia / Chinese-fantasy / period-oriental / Eastern-aesthetic scene prompt that folds a six-layer scene formula (celestial background + atmospheric midground + character silhouette + sword / weapon detail + symbolic foreground + ambient particles) into H3's `[Shot 1] …` shot description. Includes the camera-motion clause conventions for H3 and a worked H3 prompt.

---

## How a client loads this plugin

Agent Plugins v1.0.0 clients follow this flow:

1. **Discover** the plugin at the path you install it under. Read the manifest at `plugin.json`.
2. **Validate** the manifest against `$schema` (`https://agent-plugins.org/schemas/1.0.0/plugin.schema.json`). Required fields: `$schema`, `name`. The plugin name (`cinematic-video-prompt-h3`) satisfies the naming constraints (lowercase alphanumeric + hyphens; no consecutive hyphens or periods; alphanumeric start and end).
3. **Discover skills** from the fixed location `skills/`. Each immediate child directory containing a `SKILL.md` is one skill. This plugin provides three: `cinematic-video-prompt-h3`, `character-sheet-lite-h3`, `oriental-scene-lite-h3`.
4. **Discover MCP servers** from `mcp.json`. Empty `mcpServers` is valid; no servers are registered.

Skills are not discovered from `mcp.json`, MCP servers are not discovered from `skills/`, and `plugin.json` cannot override these fixed locations.

See the [Agent Plugins Specification §6 Component discovery](https://agent-plugins.org/specification#6-component-discovery) for the normative flow.

---

## Why the same content lives in two repos

This package and [`ssm82/cinematic-video-prompt-skill-h3`](https://github.com/ssm82/cinematic-video-prompt-skill-h3) carry the same prompt content — the Agent Plugins-conformant layout here places the skills under `skills/<name>/` with YAML frontmatter and standard directory structure, while the older repo keeps the original (Claude-style) layout. A client that conforms to Agent Plugins v1.0.0 can load this package directly. A client that does not yet conform can load the older layout unchanged.

The vocabulary, the H3 prompt grammar, the worked examples, and the failure-mode list are byte-identical across the two repos. The only differences are structural: directory layout, file names, and the addition of the `plugin.json` manifest.

---

## Provenance and attribution

This skill is a derivative work of the upstream **`cinematic-video-prompt-skill`** ([Rylaispirit/cinematic-video-prompt-skill](https://github.com/Rylaispirit/cinematic-video-prompt-skill)), which provided the original 700+ term Vietnamese-language cinematography vocabulary. The upstream copyright notice and MIT license are preserved in [`LICENSE`](./LICENSE).

The H3 adaptation — structured-prompt grammar, mode templates, vocabulary mapping, recipes, mood lookup, pre-flight checklist, failure modes, references, and examples — is original work in this fork. The work is MIT-licensed under the same terms as the upstream.

| Repo | Purpose |
|---|---|
| `Rylaispirit/cinematic-video-prompt-skill` | Original Vietnamese-language cinematography vocabulary (MIT) |
| `ssm82/cinematic-video-prompt-skill-h3` | H3 adaptation, original (Claude-style) layout |
| `ssm82/cinematic-video-prompt-h3-plugin` | This package — H3 adaptation, Agent Plugins v1.0.0 conformant layout |

---

## Contributing

See [`CONTRIBUTING.md`](./CONTRIBUTING.md). PRs are welcome — please open an issue first for major vocabulary additions or template changes, and verify any new prompt vocabulary against an H3-class model before submitting.

## License

MIT. See [`LICENSE`](./LICENSE).

## Changelog

See [`CHANGELOG.md`](./CHANGELOG.md).