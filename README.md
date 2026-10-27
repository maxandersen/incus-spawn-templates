# incus-spawn-templates

Personal template images and tool definitions for [incus-spawn](https://github.com/Sanne/incus-spawn).

These extend isx's built-in `tpl-minimal` with environments that include a coding agent (Pi), pre-cloned repositories, and primed dependency caches.

## Setup

Add this directory as a search path in `~/.config/incus-spawn/config.yaml`:

```yaml
searchPaths:
  - /path/to/incus-spawn-templates
```

Then build and branch:

```shell
isx build isx-jbang
isx branch my-feature --from isx-jbang
```

## Templates

| Template | Parent | Description |
|----------|--------|-------------|
| `isx-base-agent` | `tpl-minimal` | Base agent layer: mise, Pi (OpenAI provider), selected skills |
| `isx-jbang` | `isx-base-agent` | jbangdev/jbang source, dependencies primed |
| `isx-tamboui` | `isx-base-agent` | tamboui/tamboui source, dependencies primed |

`isx-base-agent` sets `default-action: pi`, so branching one of these opens straight into the Pi coding agent. Pi uses the `openai` provider; configure it with `isx account add openai` (or override the `provider` param in `images/base-agent.yaml`).

## Tools

| Tool | Description |
|------|-------------|
| `mise` | [mise](https://mise.jdx.dev/) runtime/version manager |

## Contributing

To add a new template, create a YAML file in `images/` — see the [incus-spawn documentation](https://github.com/Sanne/incus-spawn) for the image definition format. Custom tools go in `tools/`.
