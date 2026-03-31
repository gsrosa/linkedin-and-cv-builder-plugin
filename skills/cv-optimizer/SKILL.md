---
name: cv-optimizer
description: >
  Use this skill when the user asks to "optimize my CV", "rewrite my resume", "improve
  my bullet points", "update my CV for a senior role", "tailor my resume for this job",
  "review my experience section", or any request involving a resume or CV file. Also
  triggers for "ATS optimization", "resume feedback", or "CV for remote roles".
  Works for any engineering track: frontend, backend, DevOps, AI/ML, full-stack, etc.
metadata:
  version: "0.3.0"
---

# CV / Resume Optimizer

Optimize CVs for senior tech professionals targeting remote-first, international, or high-growth companies. Focus exclusively on impact, specificity, and positioning — not responsibilities. Works for any software engineering track.

## Writing Tone

Everything written on behalf of the user must read like it came from them, not from a CV template or an AI. Write the way an experienced engineer actually describes their work — specific, grounded, confident without being loud. Avoid anything that sounds polished for the sake of it.

Banned phrases: "passionate about", "results-driven", "team player", "fast learner", "love to code", "responsible for", "helped with", "contributed to", "leveraged", "utilized".

The goal is a CV that sounds like a real person wrote it, not a document that was optimized.

## Core Principles

- Every bullet point must answer: "So what?" If it doesn't show impact, rewrite it.
- Metrics beat descriptions. If the user doesn't have exact numbers, use approximations or relative terms ("reduced by ~40%", "3x faster", "supporting 50k+ users").
- Responsibilities are table stakes. Results are differentiators.
- Avoid passive voice. "Led", "Built", "Reduced", "Designed" — not "Responsible for" or "Helped with".

## 2-Page Hard Limit

The final CV must fit in **2 pages maximum**. This is not a suggestion — it is a requirement.

Enforcement rules:
- Roles older than 8–10 years: max 2 bullets each, or list company/title/dates only
- Current and most recent roles: max 4–5 bullets each
- Professional Summary: 3–4 lines, not a paragraph
- Skills section: grouped categories, no descriptions per skill, no proficiency bars
- Education: one line per degree unless it was a differentiator
- If content still doesn't fit: ask the user which older roles or projects matter most for the target role, then trim accordingly

When generating the `.docx`, enforce formatting constraints (font size, margins) that keep content within 2 pages — see "Generating the .docx" section below.

## ATS Optimization Rules

ATS (Applicant Tracking Systems) scan the `.docx` before a human reads it. Format and content both matter:

### Content — make keywords land
- Use the **exact job title** from the JD in the headline/summary at least once
- Mirror keywords from the JD in bullets and skills: if they say "distributed systems", use that phrase, not "scalable infrastructure"
- Spell out acronyms at least once: "Kubernetes (K8s)", "CI/CD (GitHub Actions, ArgoCD)"
- Include the main technologies from the JD in the Skills section — if you've used them, list them
- Avoid keyword stuffing — place keywords where they fit naturally in context

### Format — make the file readable by machines
- Use standard section headings: **Work Experience**, **Skills**, **Education** — not custom names
- No text in headers or footers (ATS parsers often miss them)
- No tables for core content — ATS parsers skip table cells
- No columns — single-column layout only
- No graphics, icons, or progress bars in skills
- Standard date format: `Jan 2022 – Present` or `2022 – Present`
- Avoid text boxes — content inside text boxes is invisible to most ATS

## CV Structure (Optimal Order)

```
1. Name + Title + Contact + Location
2. Professional Summary (3–4 lines max)
3. Work Experience (reverse chronological)
4. Skills (categorized, not just listed)
5. Education
6. Languages (if relevant for international roles)
```

## Section-by-Section Rules

### Headline / Title
- Use "Senior [Specific Area] Engineer" not just "Software Engineer"
- Add "— Remote" or location context if targeting remote roles
- Avoid stacking adjectives: "Passionate, driven, results-oriented" → cut all of it

### Professional Summary
- Open with what you are, not what you want
- Include: years of experience + core specialization + 1–2 standout technical areas
- Close with: what kind of role/problem you solve (not "seeking opportunities")
- Banned phrases: "passionate about", "love to code", "team player", "fast learner"

### Experience Bullets

Use this formula: **[Action verb] + [What you built/did] + [Result/Impact]**

```
Good: "Reduced API p99 latency by 60% by replacing synchronous calls with an event-driven pipeline, cutting timeout errors from 2% to 0.1%"
Bad:  "Responsible for performance improvements to the backend services"

Good: "Led migration from a monolith to microservices, enabling 4 independent teams to deploy without coordination for the first time"
Bad:  "Helped with the microservices migration"
```

**High-impact action verbs for senior engineers:**
Architected, Designed, Built, Led, Reduced, Increased, Migrated, Unified, Eliminated, Shipped, Scaled, Owned, Automated, Established

### Skills Section

Organize by category — not a flat list. Categories vary by track; adapt to the user's actual stack.

**Frontend example:**
- Languages / Frameworks: React, Next.js (App Router), TypeScript
- Architecture: Component systems, design systems, monorepos
- Performance: SSR/SSG, bundle optimization, Core Web Vitals
- Testing: Jest, Playwright, React Testing Library

**Backend example:**
- Languages / Frameworks: Go, Node.js (Fastify/Express), Python
- Data: PostgreSQL, Redis, Kafka, Elasticsearch
- Infrastructure: AWS (ECS, Lambda, RDS), Docker, Terraform
- Observability: OpenTelemetry, Datadog, structured logging

**DevOps / Platform example:**
- Cloud & Infra: AWS, GCP, Kubernetes, Terraform, Helm
- CI/CD: GitHub Actions, ArgoCD, Flux, GitOps workflows
- Observability: Prometheus, Grafana, Datadog, PagerDuty
- Developer Experience: Backstage, internal platforms, self-service tooling

**AI/ML example:**
- ML Frameworks: PyTorch, Scikit-learn, Hugging Face Transformers
- LLM / AI: OpenAI API, RAG pipelines, LangChain, prompt engineering
- MLOps: MLflow, Weights & Biases, SageMaker, feature stores
- Data: Spark, dbt, Airflow, BigQuery

Adapt categories to the user's actual work. Do not list tools they have only used once or superficially.

## Adapting for Target Roles

### Senior / Staff Engineer (any track)
- Lead with architecture and system design decisions
- Show ownership: "I designed X, not just implemented it"
- Highlight scale: user counts, team size, request volume, data size

### Remote-First Companies (US/EU)
- Add GitHub profile link if present
- Mention async communication patterns if applicable
- English fluency should be evident from CV quality itself

### AI-Product Companies (high demand in 2025–2026)
- Emphasize real-time, streaming, or event-driven experience
- Show any AI tool integration work, even as supporting infrastructure
- Highlight reliability and observability ownership

## Common CV Problems to Fix

| Problem | Fix |
|---------|-----|
| Overlapping employment dates | Clarify if concurrent (consulting, contract) in job title |
| No metrics anywhere | Add at least 1 metric per role, even relative ones |
| Missing links (GitHub, portfolio) | Flag it — senior engineers should have at least one |
| "Seeking opportunities" in summary | Replace with what value you bring |
| Old or irrelevant early roles taking up space | Compress to 1–2 bullets max after 8+ years |
| Vague impact statements | Rewrite with the formula: Action + What + Result |
| Skills listed as a flat dump | Group into categories by area |
| Generic title ("Software Engineer") | Specialize: "Senior Backend Engineer", "Staff Platform Engineer" |
| Exceeds 2 pages | Trim older roles, cut Summary to 3 lines, compress Skills |

## Output Format

When rewriting CV content, always output:
1. The rewritten section
2. A brief note on what changed and why

When giving feedback only, use:
- **Strong** → keep as-is
- **Rewrite** → suggested improved version
- **Add** → something missing that should be there
- **Remove** → unnecessary content

Reference workflow: `references/cv-index.md` (hub). Holistic pass: `cv-analyze.md` → `cv-review-strengths-weaknesses.md` → `cv-rewrite.md`. Single bullets: `bullet-analyze.md` → `bullet-patterns.md` → `bullet-rewrite.md`. Examples: `bullet-rewrites.md`.

## Generating the .docx

After the user confirms the rewritten content, generate a formatted `.docx` file using the **docx** skill. This is always the final output — not optional.

### Formatting parameters for the docx skill:
- **Margins**: 1.8cm top/bottom, 2cm left/right — tight but readable
- **Font**: Calibri 10pt for body, 11pt for company names and section headers, 14pt for the name
- **Section headers**: Bold, 11pt, 1.5pt bottom border line, 4pt spacing before
- **Bullet points**: Standard list bullets, 10pt, 2pt spacing between bullets
- **Spacing**: 0pt between bullets within a role, 6pt between roles, 10pt between sections
- **Name**: 14pt bold, left-aligned
- **Contact line**: 9pt, one line, separated by · dots
- **Single column layout only** (ATS requirement — no columns, no tables)
- **Page size**: A4 or Letter depending on user's target market (ask if unknown)
- **Page limit**: Target 2 pages. If content runs long, reduce body font to 9.5pt and margins to 1.5cm

### File naming:
- `cv/cv-v[N]-[slug].docx` (e.g. `cv/cv-v3-senior-backend-remote.docx`)

After generating, show the user a preview of the formatting and ask:
> "Here's the .docx — 2-page, ATS-ready. Do you want any formatting changes before I save the final version?"

## Saving to Notion + Local Backup

After the `.docx` is confirmed:

1. Search for "[FirstName] - LinkedIn & CV Builder" using `notion-search`
2. Navigate to the **CV Versions** database under the CV section
3. Create a new entry:
   - **Title**: "v[N] — [target role or context, e.g. 'Senior remote, US-focused']"
   - **Target Role**: from conversation context
   - **Key Changes**: bullet summary of what was rewritten
   - **Date**: Today
   - **Format**: DOCX + MD
4. If this was a full CV rewrite, also update the **📌 Current CV** page with the new content
5. Add the full CV content as a child page of the version entry
6. Confirm: "Saved to Notion → CV / CV Versions."

Save locally — both formats:
- Markdown: `cv/cv-v[N]-[slug].md` — full CV content in plain markdown
- Word doc: `cv/cv-v[N]-[slug].docx` — the formatted file from the docx skill

Confirm:
> "Saved: `cv/cv-v[N]-[slug].docx` (formatted, 2-page) + `cv/cv-v[N]-[slug].md` (plain text backup)."

If Notion MCP is not connected, prompt the user to configure it via `/mcp` (see `notion-setup`). If no workspace exists yet, run the Notion setup skill first.
