Create a 14-slide conference talk presentation for a 25-minute tech meetup session.

TONE: Honest, funny, self-deprecating. This is a real story told by an Engineering Manager 
at a JavaScript library company. Think "post-mortem with laughs" not "corporate keynote". 
Use dark humor where appropriate. The speaker is Polish, presenting in English.

STYLE: Dark background, terminal/code aesthetic. Accent colors: electric blue and amber. 
Monospace font for code snippets and numbers. Keep slides minimal — big statements, 
not bullet walls. Each slide should have ONE strong visual hook or headline.

TITLE SLIDE
Title: "30,000 Lines Overnight"
Subtitle: "What Happens When You Let AI Rewrite Your Library in TypeScript"
Speaker note: The morning I came to work and found a TypeScript Handsontable

---

SLIDE 1 — "The Problem That Wouldn't Get Solved"
A JavaScript data grid library born in 2012 — the same year TypeScript was invented.
342,000 lines of JS. Over 1 million words.
The TypeScript migration task had been open for years. Multiple failed attempts.
Always the same verdict: too expensive, too risky, too disruptive.
An external contractor quoted $25,000 (success fee) to do it in 30 days.
The math never worked. Until it did.
Visual suggestion: a very old, dusty TODO ticket

---

SLIDE 2 — "Two Trains. One Year Apart."
2025: Traveling to a conference. Working on the TypeScript migration in Cursor 
with Claude Sonnet 3.7 on a train. Cursor crashed. Lost context constantly. 
Made the same silly mistakes on loop. Got nowhere.
Meanwhile: a colleague did a careful systematic POC. Got 900 TypeScript errors. 
Estimated 40+ man-days. Documented everything perfectly. Concluded: impossible in one go.
2026: Same train. Same conference. Same co-passenger. 
This time the job was already done.
Visual suggestion: a train window, two versions of the same journey

---

SLIDE 3 — "TypeScript: Before and After LLMs"
BEFORE: Better DX. Autocomplete. Refactoring safety. Self-documenting APIs.
Good reasons. Never enough to justify the cost for a stable library.
AFTER: LLMs work significantly better with strongly typed codebases.
Types are context. Types are constraints. Types are communication.
Dynamic JS gives an AI ambiguity at every function boundary. TypeScript gives it a map.
TypeScript went from a developer comfort feature to an AI collaboration requirement.
The migration that was "nice to have" quietly became necessary infrastructure.
Visual suggestion: a split before/after or a map metaphor

---

SLIDE 4 — "Why the Architecture Actually Helped"
Handsontable: microkernel + 40+ plugins. Each plugin is a bounded context.
The AI could reason about one plugin without holding 342k lines in mind.
But more importantly: years of custom ESLint rules acted as machine-readable 
architecture documentation. No raw window/document/console. No barrel imports. 
No cross-plugin direct calls. No native throw new Error(). Enforced automatically.
The linter didn't just catch bad code — it told the AI how to think about the codebase.
Good architecture helps humans and AIs for the same reasons.
Visual suggestion: a clean modular diagram, microkernel with plugins radiating outward

---

SLIDE 5 — "The YOLO Prompt" ← THIS IS THE KEY SLIDE
Nobody told me to do this. No ticket. No sprint item. No plan.
I'd been hearing about a new model. The kind of thing you read about at 11pm 
and think: "I wonder if this actually works."
So: one prompt. No strategy. No file-by-file discipline. Full YOLO mode.
Pointed it at the whole codebase. Left the machine on. Went home.
Came back in the morning expecting a mess.
Found something that compiled.
Then checked the Cursor billing. No spending limit was set. One night: ~$1,000.
Compare: contractor wanted $25,000. Colleague's careful POC: weeks of work.
Was it planned? No. Is it on the roadmap now? YES.
Visual suggestion: Erlich Bachman from Silicon Valley looking shocked/smug 
or the "not sure if genius or just lucky" meme format. Big "$1,000" number on screen.

---

SLIDE 6 — "What 'It Compiled' Actually Meant"
Zero @ts-ignore comments. tsc --noEmit passes with 0 errors. ✅
Also: ~138 any usages. ~79 object types. ~194 as unknown as casts. ~2,088 unknown usages.
AI solved the activation energy problem. Not the whole problem.
Visual suggestion: iceberg — clean surface, chaos below

---

SLIDE 7 — "The Dirty Truth About `any`"
The AI defaults to escape hatches under ambiguity.
Walkontable sub-module alone: 87 `any` occurrences.
Manual cleanup required understanding actual types, not just annotating them.
strict: true is still off. Enabling it is a 5-phase plan.
AI gives you 80% fast. The last 20% is still yours.
Visual suggestion: a code snippet showing `any` everywhere, highlighted in red

---

SLIDE 8 — "When Your .d.ts Files Are Lying"
235 hand-authored .d.ts files. Types retrofitted over years.
Some didn't match the real implementation.
The TypeScript compiler became an API audit nobody asked for.
And it found real problems.
A TypeScript migration is also a reckoning with your own past promises.
Visual suggestion: a broken contract or a "THIS IS FINE" dog in a fire

---

SLIDE 9 — "The PR That Reveals the Scale of Done"
PR #12011. Branch: feature/typescript-2026. 23 commits. Opened February 2026.
All 6 framework wrappers affected: React, Angular, Vue (and their wrappers).
~970 test files still in JavaScript.
34 spec files differ from develop.
The PR is open. Cannot be merged. It's a breaking change.
The scope of "done" expands once you start looking.
Visual suggestion: a large iceberg or a very long checklist

---

SLIDE 10 — "E2E Tests as the Only Source of Truth"
Rule: all e2e tests must pass. Zero changes to test code allowed.
This constraint was the most important decision of the whole migration.
Without a strong test suite you cannot trust an AI-generated migration.
The tests are the contract.
Visual suggestion: a safety net or a referee card

---

SLIDE 11 — "The Hidden Cost: Framework Wrappers"
React. Angular. Vue. Vue3. React-wrapper. Angular-wrapper.
TypeScript strictness exposed interface mismatches in all of them.
Not automated. Each needed human review.
The library is not the whole system. Plan for the ecosystem.
Visual suggestion: 6 wrapper logos with a wrench icon

---

SLIDE 12 — "The Merge Problem Nobody Warned You About"
Development continued on `develop` during the entire migration.
Every commit to develop is a potential conflict with the TS branch.
The branch still cannot be merged. It's a breaking change.
Timing and branching strategy matter as much as the migration itself.
Visual suggestion: a git graph with two diverging branches growing further apart

---

SLIDE 13 — "Lessons Learned"
Present as a clean, punchy list — one lesson per line, short and sharp:
- AI removes activation energy, not effort
- Set a spending limit before you go to bed
- TypeScript is no longer just about DX — it's about AI readability
- Microkernel + plugins: good for humans, great for AI agents
- Custom linter rules are architecture docs — write them for the AI too
- Let your e2e suite be the contract
- `any` is technical debt with a friendly face
- .d.ts files are promises you may have quietly broken
- A migration branch vs an active codebase is a ticking clock
- Sometimes the most important bets are the ones you almost didn't make
Visual suggestion: minimal list, each item appearing with weight

---

SLIDE 14 — "What's Next + Q&A"
Branch exists. Compiles clean. Waiting for the right release window.
A library born before TypeScript is about to ship it natively. Full circle.
Same train. Same conference. One year apart. Different world.
Question for the room: how do you ship a breaking change responsibly?
Visual suggestion: a railway track disappearing into the horizon or a full circle motif

---

DESIGN NOTES FOR GAMMA:
- Dark theme throughout, terminal/code aesthetic
- Slide 5 (YOLO prompt) should be the most visually dramatic — big numbers, high contrast
- Slide 13 (lessons) should feel like a closing monologue — spacious, confident
- Use monospace font (like JetBrains Mono or similar) for all code, numbers, and 
  technical terms like `any`, `unknown`, `tsc`
- Where Gamma suggests stock photos, prefer: code screenshots, terminal windows, 
  abstract geometric patterns, or leave space for custom images the speaker will add