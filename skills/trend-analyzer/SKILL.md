---
name: trend-analyzer
description: >
  Use this skill when the user asks for "post ideas", "what should I write about",
  "trending topics in frontend", "what's hot right now in tech", "content ideas based
  on trends", "what are companies hiring for", or when they want to align their content
  or positioning with current market demand. Also triggers for "market trends",
  "what should I focus on", or "what's relevant right now".
metadata:
  version: "0.1.0"
---

# Trend Analyzer

Identify high-signal content opportunities and market positioning angles for senior frontend engineers. Surface what's actually moving in the market — not what was trending 18 months ago.

## Core Objective

Match the user's real experience to topics with high current demand. Avoid overused angles that offer no differentiation.

## How to Generate Trend-Based Ideas

1. Start from the user's actual experience and tech stack
2. Cross-reference with current market signals (see `references/market-signals.md`)
3. Find the intersection: where does their specific experience meet a topic people are actively searching, debating, or hiring for?
4. Reject any idea that could be written by a generic "senior engineer" — it must require their specific experience to be credible

## Idea Evaluation Criteria

Score each content idea against these three axes before suggesting it:

| Axis | Question | Why it matters |
|------|----------|---------------|
| Technical credibility | Can this person write this from real experience? | Generic advice tanks credibility |
| Market timing | Is this topic live or trailing? | 6-month-old trends are noise |
| Differentiation | Is this angle crowded? | Avoid "my thoughts on AI" type posts |

Only suggest ideas that score well on all three.

## High-Signal Content Areas (2025–2026)

### Frontend + AI Integration
- Building streaming UIs for LLM outputs (SSE, chunked responses)
- Real-time state management for AI-generated content
- UX patterns for uncertain/probabilistic outputs (loading states, partial renders)
- RBAC and permissions in AI-powered multi-tenant apps
- Frontend architecture for AI products that aren't chatbots

### Frontend Architecture
- When to use a monorepo (and when not to)
- App Router adoption: what actually changed in production
- Design system scaling problems nobody talks about
- State management in 2025: Zustand vs. Jotai vs. Context — real trade-offs
- Module federation: when it solves problems and when it creates them

### Performance in Real Products
- Core Web Vitals: what actually moves the needle vs. what looks good in Lighthouse
- Hydration costs on complex Next.js apps
- Virtualization trade-offs in data-heavy dashboards
- Caching strategies for real-time data (not theoretical SWR explanations)

### Career / Senior Mindset (high engagement, lower competition)
- How code review quality reflects architectural thinking
- What makes a PR description useful
- When to push back on product decisions as an engineer
- The difference between writing code and designing systems
- Senior engineers who still write code vs. those who don't

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

See `references/market-signals.md` for current demand signals by category.