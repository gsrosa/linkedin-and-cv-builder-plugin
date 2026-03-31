---
name: cv-optimizer
description: >
  Use this skill when the user asks to "optimize my CV", "rewrite my resume", "improve
  my bullet points", "update my CV for a senior role", "tailor my resume for this job",
  "review my experience section", or any request involving a resume or CV file. Also
  triggers for "ATS optimization", "resume feedback", or "CV for remote roles".
  Works for any engineering track: frontend, backend, DevOps, AI/ML, full-stack, etc.
metadata:
  version: "0.1.0"
---

# CV / Resume Optimizer

Optimize CVs for senior tech professionals targeting remote-first, international, or high-growth companies. Focus exclusively on impact, specificity, and positioning — not responsibilities. Works for any software engineering track.

## Core Principles

- Every bullet point must answer: "So what?" If it doesn't show impact, rewrite it.
- Metrics beat descriptions. Always. If the user doesn't have exact numbers, use approximations or relative terms ("reduced by ~40%", "3x faster", "supporting 50k+ users").
- Responsibilities are table stakes. Results are differentiators.
- Avoid passive voice. "Led", "Built", "Reduced", "Designed" — not "Responsible for" or "Helped with".

## CV Structure (Optimal Order)

```
1. Name + Title + Contact + Location
2. Professional Summary (4–6 lines max)
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

## Saving to Notion

After a rewrite pass, offer to save the new version:

> "Want me to save this version to your Notion CV history?"

If yes:
1. Search for "[FirstName] - LinkedIn & CV Builder" using `notion-search`
2. Navigate to the **CV Versions** database under the CV section
3. Create a new entry:
   - **Title**: "v[N] — [target role or context, e.g. 'Senior remote, US-focused']"
   - **Target Role**: from conversation context
   - **Key Changes**: bullet summary of what was rewritten
   - **Date**: Today
4. If this was a full CV rewrite, also update the **📌 Current CV** page with the new content
5. Confirm: "Saved to Notion → CV / CV Versions."

If Notion MCP is not connected, prompt the user to configure it via `/mcp` (see `notion-setup`). If no workspace exists yet, run the Notion setup skill first.
