# CV bullet rewrites — before / after

Extended examples by pattern. Workflow order: [cv-index.md](cv-index.md) → analysis → patterns → [bullet-rewrite.md](bullet-rewrite.md).

---

## Pattern: Vague Responsibility → Specific Impact

**Before:**
> Responsible for improving the performance of the frontend application

**After:**
> Reduced initial page load time by 38% through route-level code splitting, lazy loading, and caching layer redesign — improving Core Web Vitals scores across all key pages

---

## Pattern: "Helped with" → Owned It

**Before:**
> Helped the team migrate from JavaScript to TypeScript

**After:**
> Led end-to-end TypeScript migration across a 120k-line React codebase, establishing type conventions and eliminating ~60% of runtime errors flagged in production logs

---

## Pattern: Feature list → Outcome-driven

**Before:**
> Built dashboard interfaces for property management, reservations, and housekeeping

**After:**
> Designed and shipped data-heavy property management dashboards used daily by 200+ operators, consolidating 4 separate tools into a unified interface and reducing context-switching time by ~50%

---

## Pattern: Tool mention → Architectural decision

**Before:**
> Used Zustand and React Query for state management

**After:**
> Architected client-side state layer using Zustand + React Query, establishing clear boundaries between server state and UI state that reduced race conditions and simplified real-time synchronization across multi-user workflows

---

## Pattern: Real-time work → Scale + complexity

**Before:**
> Implemented real-time chat features

**After:**
> Built real-time multi-user chat and live event streaming with optimistic updates and conflict-free state synchronization, maintaining sub-100ms perceived response times under concurrent load

---

## Pattern: RBAC / security work → Specificity

**Before:**
> Built a permission system for the application

**After:**
> Designed and implemented a role-based access control (RBAC) system supporting multi-tenant access to YouTube data sources, with scoped permissions across account, channel, and content dimensions

---

## Metric Approximation Guide

When exact numbers aren't available, use these patterns:
- "reduced X by ~Y%" (approximate)
- "supporting N+ users/requests/items"
- "from Xs to Ys" (before/after measurements)
- "3x faster than the previous approach"
- "reduced [time/errors/overhead] significantly" — only as a last resort

Never invent metrics. If uncertain, use conservative approximations or qualitative framing.