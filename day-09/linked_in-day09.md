I gave two AI models the same design document and merged their outputs by hand. The results were more interesting than I expected.

This is part of a 30-day experiment where I use AI tools daily and document what actually happens. Day 09 used both Google GEMINI and CURSOR (Claude) on the same README, filling in three architecture sections that had been left as placeholders.

The outputs overlapped significantly but diverged in style. GEMINI produced fewer items with explicit trade-offs for each option. CURSOR produced three to four times as many items but as flat lists without weighing alternatives. Neither was wrong. The useful result was the union -- about five one-liner additions from one model into the other. Low-conflict, comparable to a code review.

The more interesting part was what came after. I proposed a custom Log Tracker API and the AI, instructed to be skeptical, surfaced six specification gaps I had not addressed: retrieval strategy, storage format, metadata normalization, endpoint semantics, concurrency, and retention. Three rounds of discussion later, the spec was tight enough to implement without ambiguity. It turns out that years of mentoring junior engineers transfers directly to guiding AI agents -- the same patience, the same iterative correction, the same insistence on specificity.

No code was written. The deliverables were a finalized architecture with 17 pinned technology decisions, a versioned implementation guide, and 48 test cases across three levels. Documentation before code. Whether it survives implementation is the next question.


Substack: https://open.substack.com/pub/csolomonides/p/day-09-convergence-through-iteration?r=1g7elm&utm_campaign=post&utm_medium=web&showWelcomeOnShare=true

WordPress: https://anthropocentricsoftware.wordpress.com/2026/03/18/day-09-convergence-through-iteration/

Repo: https://github.com/constantinos-solomonides/pytest-framework

#AIAssistedDevelopment #SoftwareEngineering #TestAutomation #Cursor #Gemini #SystemDesign #DevOps #DocumentationFirst #ParetoLine
