---
name: cover-letter
description: >
  Use this skill when the user asks to "write a cover letter", "create a cover letter for this job",
  "draft an application letter", "tailor my cover letter", or any request to write a letter
  accompanying a job application. Also triggers for "motivation letter", "application email",
  or "why I want to work at X". Works for any engineering track and any target company type.
metadata:
  version: "0.3.0"
---

# Cover Letter Generator

Write cover letters for senior tech professionals that actually get read — not the standard three-paragraph format everyone skips. The goal is a letter that sounds specific, credible, and genuinely interested — not desperate or generic.

## Writing Tone

Cover letters are one of the easiest places to fall into AI-sounding language. Don't. Every sentence must feel like it was written by the person applying — specific to this company, this role, their actual experience.

No: "I am excited to apply for the position of..."
No: "I am a passionate and dedicated software engineer with a proven track record..."
No: "I believe my skills and experience make me an excellent candidate..."
No: "I would love the opportunity to contribute to your team..."

Yes: Open with something specific about the company or role that shows they actually know what they're talking about. Write like someone who already understands the job and wants to discuss it.

The test: could this letter have been sent to five other companies with minor edits? If yes, it needs to be more specific.

## Prerequisites

Before writing, you need:
1. **User context** — from `get-user-context` output or the current conversation: years of experience, track, key projects, tech stack, strengths.
2. **Job description** — ask the user to paste the full JD or share the key details: company, role title, main responsibilities, tech stack mentioned.
3. **Target company** — what do they know about the company? Any specific products, engineering blog posts, or public work they can reference?

If the user doesn't have context loaded, ask for the three things above before drafting anything.

## ATS Optimization Rules

Cover letters also pass through ATS before a human reads them. Apply the same rules as the CV:

- Use the **exact job title** from the JD at least once in the letter
- Mirror key terms from the JD naturally in the body (don't keyword-stuff — weave them in)
- Keep formatting clean and machine-readable: no fancy formatting, no text boxes, single column
- Standard date format in the header: `March 31, 2026`
- No tables, no columns, no text inside shapes

## Structure

A cover letter for a senior tech role should be:
- **3–4 short paragraphs**, not 5+ dense blocks
- **Under 400 words** — hiring managers read these in 30 seconds
- **Fits one page** — hard limit, just like a 2-page CV for a cover letter means 1 page
- **No generic opener** — start with something that signals you've done the work

### Paragraph 1: Hook + Specific interest
Open with what specifically drew them to this company or role. Not "I saw your job posting on LinkedIn." Reference something real: their engineering blog, a product decision, the team's known tech approach, their scale or domain. One sentence on why them, not just any company.

### Paragraph 2: Why they're a fit — one strong story
Pick **one specific project or achievement** from their background that maps directly to what the role requires. Not a laundry list of skills — one thing, told concisely with context and outcome. This is the most important paragraph.

### Paragraph 3: What they bring at this level
One paragraph on how they work at a senior level: the kind of problems they own, how they collaborate, what they bring beyond technical execution. Keep this grounded and specific — not just "I'm a great team player."

### Paragraph 4 (optional): Close
Short. Direct. Express genuine interest and availability. No "I would be thrilled beyond words to join your incredible team."

## Common Cover Letter Problems to Fix

| Problem | Fix |
|---------|-----|
| Generic opener | Reference something specific to the company |
| Skills list in paragraph form | Replace with one concrete story |
| "I'm passionate about X" | Replace with a specific thing they've actually done |
| More than one page | Cut to under 400 words — if it's long, it won't be read |
| Restating the CV | The letter should add context the CV doesn't have |
| Ends with "I look forward to hearing from you" | Fine to keep but cut everything else after the close |

## Adapting by Company Type

### High-growth startup / Series B–D
- Emphasize ownership, breadth, shipping in ambiguous environments
- Show you've worked without perfect processes and still delivered
- Reference their product specifically — show you actually use it or understand it

### Large tech company (FAANG-tier or equivalent)
- Emphasize scale, cross-team impact, system design
- Show you've worked with distributed teams across time zones
- Reference their engineering principles if publicly available

### Remote-first international company
- Mention async communication skills if relevant
- Show you've shipped independently without hand-holding
- English quality in the letter itself is a signal — it needs to be clean

## Output Format

1. The full draft cover letter (plain text in the chat first for review)
2. A short note: what angle was chosen and why, and where the user might want to personalize further (e.g. if a specific company detail was left as a placeholder)

If the job description is missing key details, note what's assumed and what to verify.

## Generating the .docx

After the user confirms the letter is final, generate a formatted `.docx` using the **docx** skill. This is always the final output — not optional.

### Formatting parameters for the docx skill:
- **Page**: A4 or Letter (match what was used for the CV if available)
- **Margins**: 2.5cm on all sides — cover letters breathe more than CVs
- **Font**: Calibri 11pt for body
- **Header**: Name (12pt bold), contact line below (9pt) — same style as CV for consistency
- **Date and recipient**: 11pt, separated by a blank line from the salutation
- **Body paragraphs**: 11pt, 6pt spacing between paragraphs, no extra indent
- **Salutation**: "Dear [Hiring Manager / specific name if known]," — not "To Whom It May Concern"
- **Sign-off**: "Best regards," followed by name — nothing more formal
- **Single column, no tables, no text boxes** (ATS requirement)
- **Page limit**: 1 page strictly — if it runs over, shorten Paragraph 3 first, then Paragraph 1

### File naming:
- `cv/cover-letters/[YYYY-MM-DD]-[company-slug]-[role-slug].docx`
  (e.g. `cv/cover-letters/2026-03-31-stripe-senior-backend.docx`)

After generating, show the user:
> "Here's the cover letter as a .docx — 1 page, ATS-ready. Anything you'd like to adjust?"

## Saving to Notion + Local Backup

After the `.docx` is confirmed:

Use the **✉️ Cover Letters database** (`598395c2778c4b5dae18bcdd59fb7e67`) — see full schema below.

Save locally — both formats:
- Markdown: `cv/cover-letters/[YYYY-MM-DD]-[company-slug]-[role-slug].md` — plain text version
- Word doc: `cv/cover-letters/[YYYY-MM-DD]-[company-slug]-[role-slug].docx` — formatted file

Confirm:
> "Saved: `cv/cover-letters/[date]-[company]-[role].docx` (formatted) + `.md` (plain text backup)."

---

**Notion — ✉️ Cover Letters database** (`598395c2778c4b5dae18bcdd59fb7e67`)

Create a new page in this database with the following properties:
- **Title** *(title)*: `[Company] — [Role]` e.g. `Stripe — Senior Backend Engineer` or `Generic — Senior Frontend (no JD)`
- **Company**: Company name (or "Generic" if no specific company)
- **Role**: Role title from the JD (or target role if generic)
- **Date**: Today's date
- **Status** *(select)*: `Draft` on creation; user can update to `Sent`, `In Review`, or `Archived` later
- **Company Type** *(multi-select)*: Pick all that apply → `Startup`, `Scale-up`, `Enterprise`, `Remote-first`, `FAANG`, `AI product`, `Developer Tools`, `Creator Tools`, `SaaS`
- **Level** *(multi-select)*: Pick all that apply → `Senior`, `Staff`, `Principal`
- **Notes**: What angle was used, what was left as a placeholder (e.g. "Para 1 is a placeholder — user needs to add company-specific hook before sending")
- **Local File**: path to the `.docx` file

Add the full cover letter text as the page body (child content of the entry).

Confirm: `"Saved to Notion → ✉️ Cover Letters."`
