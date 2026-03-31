# LinkedIn & CV Builder

A Claude Code plugin for software professionals who want a sharp, credible presence on LinkedIn and on paper — across frontend, backend, platform, AI/ML, and other tracks.

## What It Does

Six skills under the namespace `linkedin-and-cv-builder` (invoke with `/linkedin-and-cv-builder:<skill-folder>` after loading the plugin). Skills are discovered from `skills/*/SKILL.md`.

| Skill | What it does | Trigger phrase |
|-------|-------------|----------------|
| **Get User Context** | Collects CV, LinkedIn URL, and profession-aware Q&A so other skills can personalize output | "onboarding", "my background", "what do you need", before CV/LinkedIn/post work |
| **Notion Setup** | Creates your Notion workspace and seeds it with CV/profile data | "set up Notion", "create my workspace", runs when persistence is needed |
| **CV Optimizer** | Rewrites CV bullets for impact, metrics, and senior positioning | "optimize my CV", "rewrite this bullet", "tailor for remote" |
| **Profile Optimizer** | Rewrites your headline, About section, and experience for LinkedIn | "improve my headline", "rewrite my summary" |
| **Post Generator** | Writes high-quality LinkedIn posts with scroll-stopping hooks | "create a post about X", "post ideas" |
| **Trend Analyzer** | Identifies high-signal content and market opportunities | "what should I write about", "trending topics", "post ideas" |

## Usage

Start with **Get User Context** if you're setting up from scratch (CV + LinkedIn + profile questions). It feeds everything else.

For ongoing use, the most common flows are:
- **Content creation**: Trend Analyzer → Post Generator
- **Job search**: CV Optimizer → Profile Optimizer
- **Full setup**: Get User Context → Profile Optimizer → CV Optimizer → Post Generator

## Install & test (Claude Code)

From the repository root:

```bash
claude --plugin-dir .
```

Reload after changes: `/reload-plugins`. Invoke a skill by name, for example: `/linkedin-and-cv-builder:get-user-context`.

## Setup

**Notion (required):** This plugin is built around a **Notion workspace** for CV versions, profile drafts, and posts. The chat will guide you to **configure the Notion MCP during the chat** if it is not connected yet:

1. Open **`/mcp`** in Claude Code (or run `claude mcp add --transport http notion https://mcp.notion.com/mcp`).
2. Add the **Notion** server and complete **OAuth** when prompted.
3. After connection, say **"set up my Notion workspace"** so the plugin can create the structure below.

The repo includes `.mcp.json` with Notion’s hosted MCP URL (`https://mcp.notion.com/mcp`). See [CONNECTORS.md](CONNECTORS.md) for details.

Once Notion is connected, the plugin can create a dedicated structure such as:

```
[YourName] - LinkedIn & CV Builder
├── 👤 Profile         — positioning, content pillars, career goals
├── 💼 LinkedIn
│   ├── Posts          — draft and published posts with metadata
│   └── Profile Versions — headline and About section history
└── 📄 CV
    ├── 📌 Current CV  — latest version
    └── CV Versions    — full version history by target role
```

If you upload a CV at the start of a session, that data will be automatically seeded into the workspace.

## Output Standards

Every output from this plugin is evaluated against three criteria before delivery:
1. Could this have been written by anyone? → If yes, it gets rewritten
2. Does it reflect senior-level thinking? → Generic = rejected
3. Is there any filler? → Removed
The goal is not more content. It's sharper, more credible content.
