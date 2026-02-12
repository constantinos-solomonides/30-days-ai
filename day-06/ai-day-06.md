# AI Day 06 -- A day of manual work

*The Pareto Line --- a 30-day experiment in AI use*

------------------------------------------------------------------------

**Disclaimer**\
Each "day" in this series represents a work-day of effort. The posting
delay reflects real-world obligations, not retroactive rewriting or
assisted optimization. Day 06 was intentionally conducted without AI
assistance.

------------------------------------------------------------------------

## TL;DR

Day 06 was a deliberate no-AI day in the middle of a high-AI-usage
experiment.\
The goal was comparison, not regression.

Manual work felt slower but more linear.\
AI-assisted workflows feel faster but noisier.

The verdict: removing AI mid-stream exposes both the genuine leverage it
provides and the structural inefficiencies it introduces. The comparison
only makes sense when done inside active usage---not after the fact.

------------------------------------------------------------------------

## What I Set Out to Do

The primary objective was straightforward: continue building the sandbox
manually.

Secondary objectives were more important:

-   Compare manual work against AI-assisted work while still immersed in
    heavy AI usage.
-   Observe whether AI usage had already become habitual.
-   Prevent masking the ratio of human vs AI effort by reverting
    entirely to automation.

The build-from-scratch constraint was intentional. If I allowed AI to
"help" in small invisible ways, the experiment would blur. Day 06 had to
be clean.

------------------------------------------------------------------------

## What Actually Happened

The work became more linear.

Without AI suggesting branching paths, I approached debugging through
experience:

Start at the end.\
Verify connectivity.\
Measure response time.\
Increase verbosity.\
Reduce the request to something trivial --- "say hi to me."

Connectivity worked.\
cURL returned fast, predictable responses.

The slowdown was not in raw communication.

The friction appeared earlier in the stack: OpenHands introduced
excessive context into requests --- including large instruction payloads
that were not relevant to the immediate task. The latency was not
computational; it was structural. This was not an intelligence problem.
It was request bloat.

The paradox remains: building a sandbox so AI can be safely used, using
AI, is unnecessarily painful. The abstraction layers accumulate faster
than they are justified.

------------------------------------------------------------------------

## The Hidden Cost of Helpfulness

AI tools increasingly generate their own documentation using AI. The
tone is confident. The structure is impressive. The human optimization
is weak.

Automatically generated scaffolding looks complete, but it is often not
optimized for how engineers reason under time pressure. It assumes
patience and unlimited cognitive bandwidth.

Chatbot helpers are useful.\
Their generated structures are frequently sub-par.

This becomes visible only when you remove them and compare.

Manual work exposes friction that AI hides by absorbing it through
verbosity.

------------------------------------------------------------------------

## Where Things Broke

The most significant issue was unsolicited context.

OpenHands injected material into requests that expanded payload size
without adding task relevance. That is a textbook example of AI bloat:
assistance that increases cost without increasing precision.

The first search for a lightweight alternative led to OpenClaw. It was
not the right fit --- more oriented toward chat interactions than
focused sandbox execution.

Its documentation suffered from the same issue identified earlier:
optimized for completeness, not for constrained human cognition.

Work then began toward integrating OpenCode instead.

By the end of the day:

-   A simple Ubuntu container was introduced.
-   The container can be rebuilt deterministically.
-   No local AI agent is fully integrated yet.

This is not accidental. It is transitional.

------------------------------------------------------------------------

## Rebalancing Effort

Manual debugging was slower in wall-clock time but more predictable.

AI-assisted debugging feels faster but involves lateral exploration. It
suggests options. It expands context. It consumes tokens. It generates
scaffolding that may not be structurally optimal.

The key difference:

Human work is linear.\
AI-assisted work is branching.

Experience enables targeted interventions without random exploration. AI
sometimes simulates exploration until something works.

Neither approach is inherently superior. The cost model differs.

------------------------------------------------------------------------

## Evaluation

**Structural clarity:** Higher without AI.\
**Iteration speed:** Higher with AI.\
**Noise ratio:** Lower without AI.\
**Cognitive overhead:** Mixed --- AI reduces typing but increases
validation burden.

The most relevant insight:

Blind trust in tools remains a mistake.

AI agents, especially paid ones, would have multiplied costs here.
Without visibility into request composition, unnecessary payload
inflation would have directly translated to expense.

Day 06 exposed that risk before scaling it.

------------------------------------------------------------------------

## Results Summary

-   No local AI agent created yet.
-   Communication pipeline validated.
-   Excessive context injection identified as performance bottleneck.
-   Cleaner container baseline established.
-   Alternative tooling exploration initiated.

This is not failure. It is calibration.

The experience resembles earlier professional situations where friction
analysis produced durable knowledge later applied under pressure.

The process is still enjoyable. The learning curve is real. The absence
of immediate success does not invalidate the trajectory.

------------------------------------------------------------------------

## Cost Estimates (Illustrative)

Assume:

-   5 exploratory AI iterations per debugging cycle.
-   15k tokens per expanded request (including unsolicited context).
-   \$10 per 1M tokens (representative paid model rate).

Cost per cycle: 15,000 × 5 = 75,000 tokens\
75,000 / 1,000,000 × \$10 = \$0.75 per debugging cycle

If 40 such cycles occur: \$0.75 × 40 = \$30

This excludes: - Retry amplification - Context growth over time - Agent
orchestration overhead

The cost is not catastrophic.\
But inefficiency compounds.

Visibility matters before scale.

------------------------------------------------------------------------

## Continuity Hook

Tomorrow (Day 07), I will write a retrospective separating:

-   Time genuinely saved because of AI\
-   Time lost because of AI

Not impressions.\
Measured differences.

------------------------------------------------------------------------

## Disclosure

This experiment tracks real working days.\
Day 06 was intentionally AI-free.\
The goal was comparison under live conditions --- not nostalgia for
manual workflows.
