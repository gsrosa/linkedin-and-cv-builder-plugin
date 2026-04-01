# Plugin Changelog

## [0.4.0] — 2026-03-31

### infrastructure: Notion databases created
Three structured databases are now live in the "Guilherme - LinkedIn & CV Builder" Notion workspace:
- **🏆 Profile Versions** (`96098fa1ce2f4b1797770a192575ac97`) — tracks every profile optimizer run with Positioning tags (Senior, Staff, Principal, IC Lead) and Focus Keywords (AI products, Frontend Architecture, Performance, Design Systems, etc.)
- **📄 CV Versions** (`0b54fd1c27884ca5aa8c729fccf61e58`) — tracks every CV version with Status (Active/Draft/Archived), Level tags, Tech Focus tags (React, Vue, Angular, etc.), and Market tags (Remote, US, EU, LATAM, Canada)
- **✉️ Cover Letters** (`598395c2778c4b5dae18bcdd59fb7e67`) — tracks every cover letter with Company, Role, Status (Draft/Sent/In Review/Archived), Company Type tags, and Level tags

### improvement: profile-optimizer (0.2.0 → 0.3.0)
Updated Notion save instructions to point directly to the 🏆 Profile Versions database with exact property names and tag options. Skills now know the database ID — no searching required. Positioning and Focus Keywords multi-selects documented inline.

### improvement: cv-optimizer (0.3.0 → 0.4.0)
Updated Notion save instructions to point directly to the 📄 CV Versions database. Status lifecycle documented (Draft → Active; previous Active becomes Archived). Level, Tech Focus, and Market multi-selects documented inline with all options.

### improvement: cover-letter (0.2.0 → 0.3.0)
Updated Notion save instructions to point directly to the ✉️ Cover Letters database. Company Type and Level multi-selects documented inline. Notes field now explicitly records what was left as a placeholder.

---

## [0.3.0] — 2026-03-31

### feature: post-generator (0.2.0 → 0.3.0)
Post confirmation now automatically triggers image generation (no separate request needed). Post type determines image format automatically: opinions/lessons → bold text card, architecture/breakdowns → concept diagram or numbered list, 4+ point posts → carousel. Both the `.md` post file and the `.png` image (or carousel slides) are saved locally after approval. Notion post entry now includes image file path reference.

### feature: cv-optimizer (0.2.0 → 0.3.0)
Added 2-page hard limit with explicit enforcement rules (trimming old roles, summary length, font/margin fallbacks). Added full ATS optimization section: keyword mirroring, standard section headings, single-column requirement, no tables/columns/graphics. Added "Generating the .docx" section: invokes the docx skill with specific formatting parameters (Calibri 10pt, 1.8cm margins, no columns). Output is now always both `.docx` + `.md` saved locally.

### feature: cover-letter (0.1.0 → 0.2.0)
Added ATS optimization rules section (mirrors CV: single column, no tables, keyword use). Added "Generating the .docx" section: invokes docx skill with cover-letter-specific formatting (Calibri 11pt, 2.5cm margins, 1-page hard limit). Output is now always both `.docx` + `.md` saved locally. Hard 1-page constraint added with trim priority order.

### improvement: notion-version-updater
Updated to reflect that skill changes now produce docx files and that post-generator auto-triggers image generation — both are changes that should be noted when logging updates.

---

## [0.2.0] — 2026-03-31

### improvement: get-user-context
Added Step 0 — a mandatory Notion MCP gate that runs before any profile questions. The skill now attempts a `notion-search` call first: if it succeeds, the connector is marked active in context; if it fails, the skill stops and enforces Notion setup before proceeding. Added Writing Tone section. Added local `.md` backup on save. Downstream use updated to include cover-letter generator.

### improvement: cv-optimizer
Added Writing Tone section with explicit banned phrases and the principle that the CV must sound like the person wrote it, not like a template. "Saving to Notion" section renamed to "Saving to Notion + Local Backup" with instructions to also write a local `.md` file to `cv/cv-v[N]-[slug].md`.

### improvement: profile-optimizer
Added Writing Tone section with explicit anti-patterns for AI-sounding language. Updated save instructions to also write a local `.md` backup to `linkedin/profile-v[N]-[slug].md`.

### improvement: post-generator
Replaced generic Tone section with detailed Writing Tone section including explicit anti-patterns, a "test" criterion (could a non-expert write this?), and guidance on starting mid-thought. Updated save instructions to also write a local `.md` backup to `linkedin/posts/[date]-[slug].md`.

### improvement: trend-analyzer
Added Writing Tone section emphasizing direct, hype-free delivery.

### new-skill: cover-letter
New skill for writing cover letters for senior tech professionals. Covers tone rules (no AI-sounding openers), structure (4-paragraph format), company-type adaptations (startup vs. large tech vs. remote-first), and dual Notion + local `.md` output.

### new-skill: linkedin-image-generator
New skill for generating visual assets to accompany LinkedIn posts. Covers image types (text card, concept diagram, quote card, before/after, numbered list), LinkedIn specs, carousel post structure, and a generation process using the canvas-design skill.

### new-skill: notion-version-updater
New skill for logging skill and plugin changes to a Notion changelog database. Covers versioning conventions (semver), what to collect before logging, Notion database structure, plugin.json bumping, and local CHANGELOG.md maintenance.

---

## [0.1.0] — Initial release

Skills included: get-user-context, cv-optimizer, profile-optimizer, post-generator, trend-analyzer, notion-setup.
