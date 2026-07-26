# anyeler-skills

A collection of [GitHub Copilot Agent Skills](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills) that enhance Copilot's capabilities for specialized tasks.

## Skills

| Skill | Description |
|-------|-------------|
| [github-actions-debug](skills/github-actions-debug/SKILL.md) | Guide for debugging failing GitHub Actions workflows |

## Installing a skill

```sh
gh skill install Anyeler/anyeler-skills <skill-name>
```

For example:

```sh
gh skill install Anyeler/anyeler-skills github-actions-debug
```

## Specification compliance

All skills in this repository must pass the [Agent Skills specification](https://agentskills.io/specification). A GitHub Actions workflow validates every pull request automatically using `gh skill publish --dry-run`.

Each `SKILL.md` file must include:

- **`name`** — unique, lowercase, hyphen-separated identifier (matches the directory name).
- **`description`** — explains what the skill does and when Copilot should use it.
- **`license`** (recommended) — the license that applies to the skill.

## Security

- No secrets, credentials, or API tokens are embedded in any skill file or script.
- Scripts included in a skill directory are reviewed before being referenced in `SKILL.md`.
- The `allowed-tools` frontmatter field (an optional `SKILL.md` field that pre-approves tool use without confirmation) is omitted unless the tool list has been explicitly reviewed; the `shell`/`bash` tools are never pre-approved without explicit justification.
- Skills are scoped to their own directory and do not reference files outside their folder.
