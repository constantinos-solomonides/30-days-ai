
# AI Day 02 — On Writing Good Documentation
## The Pareto Line series: a 30-day experiment in AI use

## TL;DR

- Documentation is often avoided, not because it’s difficult, but because it’s treated as optional
- Writing it later usually means writing fiction
- Consistency matters more than polish
- AI helps with cleanup and structure, not understanding

---

## Why Documentation Goes Wrong

Most developers will say documentation matters.

Then it doesn’t get written.

Or it gets written at the end, from memory, under time pressure, when attention has already shifted elsewhere.

That’s when documentation becomes unreliable. Not because people are careless, but because context is already gone.

The effects tend to show up later:
- Testing takes longer than expected
- Releases depend on tribal knowledge
- A small number of people become bottlenecks

Some of this is systemic. Agile and SCRUM are often misinterpreted as processes that make documentation unnecessary. Documentation is also rarely treated as a first-class deliverable, which makes it easy to deprioritize indefinitely.

Other issues are not systemic. Treating documentation as boring is a choice. Treating it as someone else’s responsibility is a choice. Waiting for the “right time” is also a choice. Those are areas where individual action still matters, even in imperfect environments.

---

## Documentation Isn’t for Now

Think of it like this. Most of us are familiar with two ways of handling laundry.

One is to throw everything into a growing pile. It’s fast and cheap in the moment. The cost appears later, when something specific is needed and finding it turns into work.

The other is to carefully fold and put everything away immediately. That keeps things easy to find, but it costs time and effort every single day. Maintaining it requires discipline, and when things get busy, it tends to collapse.

Documentation has the same tension. Optimizing only for speed creates a mess. Optimizing only for order becomes expensive.

---

## What Documentation Is Actually Doing

### What Kind of Documentation Exists

Documentation isn’t one thing. Developer notes, testing instructions, user guides, and design rationale all serve different purposes. Problems arise when only one of these is considered worth writing, or when everything exists only as spoken explanation.

### Who It’s Actually For

Documentation is often framed as something written for others. In practice, one of its most important audiences is a future version of the person writing it. Writing things down while they’re still obvious saves time later. Waiting assumes memory will cooperate. It usually doesn’t.

### How to Do It Without Burning Time

This is where the laundry metaphor matters.

What tends to work is not choosing one extreme, but mixing the two.

Keep a small pile of what you’re actively wearing. Let immediate work live in a rough, messy place. At the same time, keep most things in their proper place so they don’t get lost. Then, every chance you get, sort the pile.

Applied to documentation, that means:
- Keep rough notes while working
- Don’t block progress on perfect structure
- Periodically rewrite from a clean state
- Explicitly record assumptions while they’re still visible

Documentation doesn’t need to be clean all the time. It needs to be sorted often enough.

---

## A Concrete Example

At one point, testing work had to be done for a team that provided no written documentation.

Their process was “we’ll show you how it works.” There were no step-by-step setup instructions and no generic documentation, only demos.

That hid problems. Important limitations went unmentioned. Assumptions only surfaced once things started breaking.

Progress only happened once everything was written down. First in a personal file. Then in a shared document. Then rewritten again from a clean state, with assumptions made explicit instead of implied.

Months later, when the same work had to be picked up again, almost nothing was remembered. It didn’t matter. Most of the work could be resumed without questions or walkthroughs. Other people could also take over without being guided step by step.

---

## A Shift That Stuck

This approach didn’t come from theory. It came from a layoff.

Work was left behind as a mess. Later, that layoff was converted into an internal move. The same people were still around, and it became clear that the work wasn’t something to take pride in, because it couldn’t be handed over cleanly.

Since then, documentation has been approached differently. Daily work goes into a rough file. From time to time, it gets rewritten from scratch. Steps are recorded. Assumptions are written down.

It isn’t elegant. It is reliable.

With repetition, it also becomes easier. Handover stops being a major event and becomes routine.

---

## Where AI Helps (and Where It Doesn’t)

AI lowers the cost of cleanup. It helps reorganize notes, reduce repetition, and turn rough material into something readable.

It doesn’t help with understanding. It doesn’t know which assumptions are wrong or which details matter.

The same rule applies here as elsewhere: AI is useful, but it requires supervision.

One new category is emerging, though: documentation written specifically so AI tools can work without guessing. That doesn’t replace human documentation; it adds another audience that also needs clarity.

---

## Closing

Documentation is often framed as wasted time. In practice, it’s thinking time.

Trying to explain how something works forces gaps, contradictions, and fragile assumptions to surface. Those problems exist whether or not they’re written down. Documentation simply removes the ability to ignore them.

If AI doesn’t make consistency easier, that will still be a meaningful result.

---

*This article is part of **The Pareto Line** series — a 30-day experiment in AI use, focused on producing pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses the paid version of OpenAI to draft articles and generate shortened LinkedIn posts. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, but not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, and capable of creating serious problems when allowed to operate without supervision.*

*Alongside writing, a mix of local and online AI models is also being used to rebuild scaled-down versions of older projects previously developed under enterprise constraints. Older projects are chosen on purpose to provide a known baseline, making it easier to assess what AI actually changes in both workflow and outcome.*
