# Notion Data Map

Full reference of what each skill saves to Notion, and where.

## Workspace Structure

```
[FirstName] - LinkedIn & CV Builder        ← ROOT PAGE
├── 👤 Profile                             ← PROFILE PAGE
├── 💼 LinkedIn                            ← LINKEDIN SECTION
│   ├── Posts (database)                   ← POSTS DB
│   └── Profile Versions (database)        ← PROFILE VERSIONS DB
└── 📄 CV                                  ← CV SECTION
    ├── 📌 Current CV (page)               ← CURRENT CV PAGE
    └── CV Versions (database)             ← CV VERSIONS DB
```

---

## Per-Skill Save Map

### branding-strategy → Profile Page

When the branding strategy skill runs and produces output, save to the **Profile page**:

| Data | Notion block |
|------|-------------|
| Positioning statement | Callout block (⚡) |
| Content pillars (3–4) | Bulleted list under a heading |
| LinkedIn headline options | Numbered list |
| Target roles / market | Short paragraph |
| Tech stack summary | Inline text or toggle |
| Notes / session date | Footer paragraph |

Update the page on each run (replace, don't append). Use `notion-update-page`.

---

### post-generator → Posts Database

When a post is generated or approved by the user, create a new entry in the **Posts** database:

| Field | Value |
|-------|-------|
| Title | First 6–8 words of the post |
| Status | `Draft` (default) |
| Type | Detected from content: Technical / Opinion / Lesson Learned / Architecture / Career |
| Hook | First line of the post |
| Notes | Optional context from the conversation |
| Date | Today's date |

Full post content: create the database entry, then add the full post text as a child page of that entry.

Ask before saving: "Want me to save this draft to Notion?" — don't auto-save unless the user confirmed setup.

---

### cv-optimizer → CV Versions Database + Current CV Page

When a CV section is rewritten or a full CV pass is done:

1. Create a new entry in the **CV Versions** database:

| Field | Value |
|-------|-------|
| Title | "v[N] — [target role or date]" |
| Target Role | From conversation context |
| Key Changes | Summary of what was rewritten |
| Date | Today |

2. Update the **Current CV** page with the latest full version if a full rewrite was done.

---

### profile-optimizer → Profile Versions Database

When a new headline or About section is generated:

| Field | Value |
|-------|-------|
| Title | "v[N] — [angle, e.g. 'AI focus']" |
| Headline | The new headline generated |
| Summary Snippet | First 2 lines of the new About section |
| Target Role | From context |
| Date | Today |
| Notes | What changed and why |

---

### trend-analyzer → Profile Page (Content Pillars section)

If new content pillars or post ideas are generated, append them to the **Profile page** under a `Content Ideas` section. Don't replace the existing pillars — add a dated block with the new suggestions.

---

## Lookup Pattern (All Skills)

Before saving, always resolve page/database IDs dynamically:

```
1. notion-search("[FirstName] - LinkedIn & CV Builder")
2. Traverse to the relevant child page or database
3. notion-create-pages or notion-update-page as needed
```

Never store or assume hardcoded IDs. The workspace name is the stable identifier.