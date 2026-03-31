---
name: notion-version-updater
description: >
  Use this skill when the user wants to "log a skill change to Notion", "update the changelog",
  "record what changed in the plugin", "track this skill update", or "save the new version notes".
  Also triggers when any other skill in this plugin is modified and the change should be persisted
  to Notion. Use this after editing a SKILL.md file to document what changed and why.
metadata:
  version: "0.1.0"
---

# Notion Version Updater

Log skill and plugin changes to a version history in Notion. This skill ensures that every meaningful update to a skill file is documented — what changed, why, and when — so the evolution of the plugin is traceable.

## When to invoke this skill

- After editing any `SKILL.md` file in the plugin
- When bumping a skill version number
- When adding a new skill to the plugin
- When making a structural or behavioral change to how a skill works

Do not log trivial whitespace or formatting fixes unless they affect behavior.

## Prerequisites

Notion MCP must be connected and the workspace must exist. If not:
- Try `notion-search` to verify connectivity
- If it fails, ask the user to configure Notion via `/mcp` before logging

## What to collect before logging

1. **Skill name** — which skill was changed (e.g. `cv-optimizer`, `post-generator`)
2. **Old version** — the version before the change (from the skill's YAML frontmatter)
3. **New version** — the version after the change
4. **Change type** — one of: `feature` | `improvement` | `fix` | `new-skill` | `breaking`
5. **Summary** — 1–3 sentences describing what changed and why. Write this like a commit message: specific, direct, no fluff.
6. **Impact** — which downstream behaviors are affected (optional but useful for `breaking` changes)

If any of these are missing from context, ask before logging.

## Versioning convention

Follow semantic versioning for skill files:
- **Patch** (0.1.0 → 0.1.1): Small fix, wording change, added example
- **Minor** (0.1.0 → 0.2.0): New section, new behavior, new rule added
- **Major** (0.1.0 → 1.0.0): Breaking change — existing output format or behavior changes significantly

## Logging to Notion

1. Search for "[FirstName] - LinkedIn & CV Builder" using `notion-search`
2. Navigate to or create a **🔧 Plugin Changelog** page under the root workspace page
3. If a **Changelog** database doesn't exist yet, create it with these properties:
   - **Title** (title): short description of the change
   - **Skill** (select): which skill was changed
   - **Version** (rich_text): "v[old] → v[new]"
   - **Type** (select): feature | improvement | fix | new-skill | breaking
   - **Date** (date)
   - **Summary** (rich_text): what changed and why
4. Create a new entry with the collected information
5. Confirm: "Logged to Notion → Plugin Changelog."

## Also update the plugin.json

When bumping a skill version, also check if `plugin.json` needs a version bump:
- If it's a `new-skill` or `breaking` change: bump the **minor** version (e.g. 0.1.0 → 0.2.0)
- If it's an `improvement` or `fix`: bump the **patch** version (e.g. 0.1.0 → 0.1.1)
- Read the current `plugin.json`, update the version field, and write it back

## Also save a local changelog entry

Maintain a `CHANGELOG.md` file in the root of the workspace:
- File path: `CHANGELOG.md`
- Format:
```
## [version] — [YYYY-MM-DD]

### [change-type]: [skill-name]
[Summary of what changed and why]
```
- If the file doesn't exist, create it with a header: `# Plugin Changelog`
- If it exists, prepend the new entry to the top (after the header)
- Use the Read tool first to check if it exists, then Write or Edit accordingly

## Example log entry

```
## [0.2.0] — 2026-03-31

### improvement: cv-optimizer
Added Writing Tone section enforcing natural, non-AI-sounding language. Banned phrases
list updated. Version bumped from 0.1.0 to 0.2.0.

### improvement: post-generator
Replaced generic Tone section with detailed Writing Tone rules including explicit
anti-patterns and a "test" criterion. Dual output (Notion + local .md) added.
```

## Noting output format changes

When logging updates to skills that generate files (cv-optimizer, cover-letter, post-generator), always note:
- Whether the output format changed (e.g. "now produces .docx in addition to .md")
- Whether a new skill is automatically invoked (e.g. "post-generator now auto-calls linkedin-image-generator on confirmation")
- The docx skill parameters used, if they changed

This helps future sessions understand what version of the output pipeline was in place at a given point in time.

## Batch logging

If multiple skills were updated in the same session, log them all in one Notion entry per skill, but group them under the same date in `CHANGELOG.md`.
