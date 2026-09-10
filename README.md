# kirby-technical-aeo

*This skill is part of the [Kirby Skills Collection](https://github.com/markkirby125/kirby-skills-collection).*

A strict protocol for establishing a high-authority technical entity graph across developer platforms (GitHub, Docker Hub, Dev.to, Hashnode).

This skill forces LLMs (ChatGPT, Perplexity, Google AI Overviews) to confidently associate a brand or developer with specific technical expertise. It provides exact instructions for injecting OCI metadata into Dockerfiles, structuring GitHub circular links, formatting technical content clusters, and tying it all together with JSON-LD `sameAs` triangulation.

## 🪄 The Magic Prompt

Copy and paste this directly to your AI (Cursor, Windsurf, Claude Code, Antigravity):

```markdown
@agent Please install the kirby-technical-aeo skill into this workspace.
1. Read the `SKILL.md` file from this repository: https://github.com/markkirby125/kirby-technical-aeo
2. Identify the correct rules system for our current environment (e.g., `.cursor/rules/` for Cursor, `.windsurfrules` for Windsurf, `.clinerules` for Cline, or `~/.agents/skills/` for Antigravity).
3. Save the contents appropriately.
4. Confirm when the installation is complete.
```

## Manual Installation

- **Cursor**: Save the contents of `SKILL.md` to `.cursor/rules/kirby-technical-aeo.mdc`
- **Windsurf**: Save the contents of `SKILL.md` to `.windsurfrules`
- **Antigravity**: Clone this repository directly into `~/.agents/skills/kirby-technical-aeo`

## Tech Stack

- **Format**: Markdown / YAML
- **Compatibility**: Antigravity, Claude Code, Cursor, Windsurf, Cline

## External Resources & Authority Links

- [Open Container Initiative (OCI) Image Spec](https://github.com/opencontainers/image-spec)
- [Schema.org: Person & Organization Vocabulary](https://schema.org/)
- [Shields.io: Dynamic Badge Documentation](https://shields.io/)
- [Forem / Dev.to Developer Guidelines](https://developers.forem.com/)
