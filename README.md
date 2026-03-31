# LinkedIn & CV Builder

A Cowork plugin for senior tech professionals who want to build a sharp, credible, and differentiated presence — on LinkedIn, on paper, and in how they think about their career.

Built for frontend engineers. Works for any senior IC or tech lead.

## What It Does

Six skills covering the full lifecycle of personal branding, backed by a persistent Notion workspace:

| Skill | What it does | Trigger phrase |
|-------|-------------|----------------|
| **Notion Setup** | Creates your Notion workspace and seeds it with CV/profile data | "set up Notion", "create my workspace", runs automatically on first use |
| **Get User Context** | Collects CV, LinkedIn URL, and profession-aware Q&A so other skills can personalize output | "onboarding", "my background", "what do you need", before CV/LinkedIn/post work |
| **Post Generator** | Writes high-quality LinkedIn posts with scroll-stopping hooks | "create a post about X", "make this viral", "post ideas" |
| **Profile Optimizer** | Rewrites your headline, About section, and experience for LinkedIn | "improve my headline", "rewrite my summary" |
| **CV Optimizer** | Rewrites CV bullets for impact, metrics, and senior positioning | "optimize my CV", "rewrite this bullet", "tailor for remote" |
| **Trend Analyzer** | Identifies high-signal content and market opportunities | "what should I write about", "trending topics", "post ideas" |

## Usage

Start with **Get User Context** if you're setting up from scratch (CV + LinkedIn + profile questions). It feeds everything else.

For ongoing use, the most common flows are:
- **Content creation**: Trend Analyzer → Post Generator
- **Job search**: CV Optimizer → Profile Optimizer
- **Full setup**: Get User Context → Profile Optimizer → CV Optimizer → Post Generator

## Setup

**Required**: The **Notion** plugin must be installed and connected in Cowork for persistence features to work.

Once Notion is connected, say "set up my Notion workspace" — the plugin will create a dedicated workspace with the following structure:

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
