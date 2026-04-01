---
name: profile-optimizer
description: >
  Use this skill when the user asks to "improve my LinkedIn headline", "rewrite my
  LinkedIn summary", "optimize my LinkedIn profile", "fix my about section", "improve
  my LinkedIn positioning", or any request specifically about their LinkedIn profile
  fields (not posts). Also triggers for "LinkedIn SEO", "profile visibility", or
  "make my profile stand out". Works for any engineering track.
metadata:
  version: "0.3.0"
---

# LinkedIn Profile Optimizer

Optimize every section of a LinkedIn profile for senior tech professionals across all engineering tracks. The goal is discoverability by recruiters + credibility when someone lands on the profile. These two objectives sometimes conflict — resolve in favor of credibility.

## Writing Tone

Everything written for the user's profile should sound like they wrote it themselves on a good day — informed, direct, a bit of personality. Not templated, not corporate, not the LinkedIn default voice that everyone recognizes immediately. If it reads like it was AI-generated or written by a career coach, rewrite it.

No: "With over X years of experience, I have developed a deep expertise in..."
No: "I am passionate about building scalable solutions..."
No: "Results-driven senior engineer seeking..."

Yes: Write like a person who knows exactly what they do and why it matters.

## The Golden Rule

Your profile is not a resume. It's the answer to: **"Why should I talk to this person?"**

Every section should either build credibility, signal expertise, or create a reason to connect. Cut anything that does neither.

## Headline Optimization

The headline is the highest-leverage field on LinkedIn. It appears in search results, connection requests, and comment threads — not just the profile page.

### Formula Options

**Option A — Specialization + Stack:**
`Senior Backend Engineer | Go · Distributed Systems · Event-Driven Architecture | High-throughput APIs`
`Senior Frontend Engineer | React · Next.js · TypeScript | Real-time UIs & Frontend Architecture`

**Option B — Value-first:**
`Platform Engineer who builds developer infrastructure that scales | Kubernetes · Terraform · GitOps`
`Backend Engineer who designs APIs that handle millions of requests without drama | Go + PostgreSQL`

**Option C — Niche authority:**
`Senior ML Engineer specializing in LLM-powered products and RAG pipelines | Python · PyTorch`
`Senior Frontend Engineer specializing in AI-integrated UIs and frontend architecture | React · Next.js`

### Headline Rules
- "Engineer" > "Developer" for senior positioning in international markets
- Include 2–3 tech keywords for search visibility (adapt to track — what recruiters actually search)
- Avoid: "Open to work" in the headline (use the LinkedIn banner instead)
- Avoid: generic role + location only ("Senior Developer at Company X, São Paulo")
- Max 220 characters — LinkedIn truncates in search results at ~120, so front-load the signal

### Common Headline Problems

| Current pattern | Problem | Fix |
|----------------|---------|-----|
| Pipe-separated keyword dump | Reads like an SEO list, no human voice | Add one specific angle or specialization |
| Just the job title | Zero differentiation | Add tech stack + one specific strength |
| "Passionate about technology" | Meaningless | Replace with what you actually do |
| "Developer" not "Engineer" | Lower perceived seniority in US/EU | Use "Engineer" |

## About / Summary Section

The About section has ~2,600 characters. Use ~800–1,000 of them. Recruiters don't read walls of text.

### Structure
```
[Line 1–2: Who you are and what you do — the hook]

[Block 1: Core expertise — 3–4 lines on your technical depth]

[Block 2: What you've actually built — 2–3 concrete examples]

[Block 3: What you're looking for — optional, keep it tight]
```

### Writing Rules
- Write in first person but avoid "I am passionate about..." as an opener
- Start with a statement that establishes seniority immediately
- Reference real projects or outcomes, not just skills
- Do not copy-paste the CV summary — the About section should feel more human
- End with a clear signal about what you're looking for (type of role, not desperation)

### Banned About Section Patterns
- "I've always been passionate about..."
- "With X+ years of experience, I have developed..."
- "I am a results-driven professional who..."
- Bullet point lists (use LinkedIn's native formatting sparingly)

## Experience Section

Mirror the CV's impact-driven bullets, but:
- LinkedIn allows more white space — use it
- Add context for international readers who won't know local company names
- Include company one-liner for lesser-known companies: "Housi — Brazil's largest short-term rental management platform" or "Qonto — European SME banking API, 400k+ customers"

## Featured Section

If the user has nothing here, flag it. This is high-visibility real estate.

Recommend adding:
1. A strong post that performed well
2. A GitHub profile or portfolio link
3. A case study or article if they have one
4. A project demo or video (if available)

## Skills Section

LinkedIn's skill endorsements are weak signals, but the keywords matter for search.

Prioritize skills that appear in job descriptions for target roles. Adapt to the user's track:
- Frontend: React, TypeScript, Next.js, Frontend Architecture — always include
- Backend: the primary language (Go, Python, Java, Node.js), System Design, key databases and queues
- DevOps/Platform: Kubernetes, Terraform, CI/CD platform, cloud providers, Observability tooling
- AI/ML: Python, PyTorch or TensorFlow, MLOps tools, LLM frameworks if applicable
- All tracks: include System Design / Architecture for senior/staff roles

## Profile Photo and Banner

Not directly editable via text, but flag if the user mentions it:
- Photo: professional, good lighting, plain background — not a selfie
- Banner: blank banners miss an opportunity. Even a solid color with a tagline is better than the default gray.

See `references/headline-examples.md` for a swipe file of high-performing headlines by role type and engineering track.

## Saving to Notion + Local Backup

After generating a new headline or About section, offer to save it:

> "Want me to save this to your Notion profile version history?"

If yes:

**Notion — 🏆 Profile Versions database** (`96098fa1ce2f4b1797770a192575ac97`)

Create a new page in this database with the following properties:
- **Version** *(title)*: `v[N] — [angle]` e.g. `v2 — AI products focus` or `v3 — Staff positioning`
- **Date**: Today's date
- **Positioning** *(multi-select)*: Pick all that apply → `Senior`, `Staff`, `Principal`, `IC Lead`
- **Focus Keywords** *(multi-select)*: Pick all that apply → `AI products`, `Frontend Architecture`, `Performance`, `Design Systems`, `Remote-first`, `Real-time UIs`, `Creator Tools`, `Developer Tools`
- **Headline**: The exact new headline text
- **Summary Snippet**: First 2 sentences of the new About section
- **Notes**: What changed and why (e.g. "Shifted angle toward Staff IC positioning; added AI streaming work as lead proof point")
- **Local File**: path to the `.md` backup (see below)

Add the full headline + About section as the page body (child content of the entry).

Confirm: `"Saved to Notion → 🏆 Profile Versions."`

**Local `.md` backup:**
- File path: `linkedin/profile-v[N]-[slug].md` (e.g. `linkedin/profile-v2-ai-focus.md`)
- Content: version heading, headline, full About section, positioning tags, and change notes
- Use the Write tool to create this file immediately after the Notion save

If Notion MCP is not connected, prompt the user to configure it via `/mcp` (see `notion-setup`). If no workspace exists yet, run the Notion setup skill first.
