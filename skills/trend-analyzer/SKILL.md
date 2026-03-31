---
name: trend-analyzer
description: >
  Use this skill when the user asks for "post ideas", "what should I write about",
  "trending topics in [any tech area]", "what's hot right now in tech", "content ideas based
  on trends", "what are companies hiring for", or when they want to align their content
  or positioning with current market demand. Also triggers for "market trends",
  "what should I focus on", or "what's relevant right now". Works for any engineering track.
metadata:
  version: "0.2.0"
---

# Trend Analyzer

Identify high-signal content opportunities and market positioning angles for senior software professionals across all engineering tracks. Surface what's actually moving in the market — not what was trending 18 months ago.

## Core Objective

Match the user's **real experience** to topics with high current demand. Avoid overused angles that offer no differentiation. This skill works for any track: frontend, backend, DevOps/platform, AI/ML, data engineering, mobile, full-stack.

## Writing Tone

When presenting ideas and analysis, keep it grounded and direct. Write like you're talking to an engineer who can tell the difference between a real insight and filler. Skip the hype. If a topic is genuinely hot, say why specifically — not just "this is trending."

## How to Generate Trend-Based Ideas

1. Start from the user's actual experience and tech stack (from `get-user-context` output or conversation)
2. Identify their primary track (or mix of tracks)
3. Cross-reference with current market signals (see `references/market-signals.md`)
4. Find the intersection: where does their specific experience meet a topic people are actively searching, debating, or hiring for?
5. Reject any idea that could be written by a generic "senior engineer" — it must require their specific experience to be credible

## Idea Evaluation Criteria

Score each content idea against these three axes before suggesting it:

| Axis | Question | Why it matters |
|------|----------|---------------|
| Technical credibility | Can this person write this from real experience? | Generic advice tanks credibility |
| Market timing | Is this topic live or trailing? | 6-month-old trends are noise |
| Differentiation | Is this angle crowded? | Avoid "my thoughts on AI" type posts |

Only suggest ideas that score well on all three.

## High-Signal Content Areas by Track (2025–2026)

### Frontend / Client
- Building streaming UIs for LLM outputs (SSE, chunked responses)
- Real-time state management for AI-generated content
- UX patterns for uncertain/probabilistic outputs (loading states, partial renders)
- App Router adoption: what actually changed in production
- Design system scaling problems nobody talks about
- State management in 2025: real trade-offs, not just comparisons

### Backend / APIs / Distributed Systems
- Designing for eventual consistency in high-throughput APIs
- When to use event-driven architecture — and when not to
- Database connection pooling and query optimization at scale
- gRPC vs REST vs GraphQL: real production trade-offs
- Background job reliability patterns (retry, idempotency, observability)
- API versioning strategies that don't create maintenance debt

### DevOps / Platform / SRE
- Platform engineering vs. DevOps: what the distinction actually means
- Building internal developer platforms that engineers actually use
- SLO-based incident response: what changed after we stopped using uptime as the metric
- Kubernetes cost optimization: where money actually goes
- GitOps in practice: what the docs don't tell you
- Observability beyond logging: traces, metrics, and the gaps in between

### AI / ML Engineering (Applied)
- Prompt engineering is not a job — but prompt reliability engineering is
- RAG architecture trade-offs in production (chunking, retrieval, reranking)
- Fine-tuning vs. few-shot prompting: when it's worth the overhead
- Evaluating LLM outputs at scale: what metrics actually predict quality
- ML platform design: what changes when you go from experiments to prod
- The hidden infra costs of running LLM-based features at scale

### Career / Senior Mindset (high engagement, broad appeal)
- How code review quality reflects architectural thinking
- What makes a PR description useful (and what makes it a waste of time)
- When to push back on product decisions as an engineer
- The difference between writing code and designing systems
- Senior engineers who still write code vs. those who don't
- What "ownership" actually means on a team of 15 engineers

## Saturated — Avoid Unless You Have a Genuinely Contrarian Angle

- "Why I love TypeScript / Rust / Go" (everyone has written this)
- Generic "AI will change everything" commentary
- "10 tips for X" listicles without production proof
- "Clean Code" takes without specifics
- Stack comparison posts without real production context

## Output Format

When the user asks for post ideas, deliver **3–5 strong, specific options** — not a menu of 20 weak ones.

For each idea, provide:
1. **Title / angle** — one sentence hook
2. **Why now** — why this has traction today
3. **Why you** — why this person specifically can write it credibly
4. **Suggested framework** — which post structure to use (from post-generator skill)

## Content Gap Analysis

When the user wants to build a content calendar:
1. Identify which content pillars are underrepresented in their recent posts
2. Suggest topics that balance: technical depth / opinion / career insight
3. Aim for a 60/30/10 split: 60% technical, 30% opinion/process, 10% career/personal

See `references/market-signals.md` for current demand signals by category and track.
