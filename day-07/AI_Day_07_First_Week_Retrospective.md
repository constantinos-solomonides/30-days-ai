# AI Day 07 -- First Week Retrospective

## TL;DR

-   Writing speed increased, but convergence and tone quality required
    heavy iteration.
-   Coding with AI starts fast but converges slowly, often exposing
    hidden logical gaps.
-   Bootstrapping a sandbox environment proved far more difficult than
    expected.

After one week, the results are mixed. AI helps generate output quickly
but struggles with stability and integration. The 20/80 expectation
proved too optimistic, and I had to downgrade it to 40/60.

------------------------------------------------------------------------

## Introduction

For thirty days, I am running an experiment: use AI as much as possible
and document what actually happens. The goal is not to defend or attack
AI. The goal is to measure effort, output, friction, and stability.

To reduce noise from mid-session model degradation, I am using the Plus
tier of ChatGPT. The plan is to bootstrap a sandbox environment through
interactive prompting. Inside that sandbox, I intend to run a local
agent and re-develop a tool I previously built during earlier
employment. This allows comparison. I know roughly how much manual
effort that tool required. If AI meaningfully reduces that effort, it
will be visible.

I deliberately avoided using a ready-made sandbox. If I used a pre-built
one, I would not know how much of the result belongs to me and how much
belongs to someone else's preparation. Building it myself gives me a
clearer baseline.

To evaluate success, I used the Pareto principle. If 20% of the manual
effort in prompt-writing yields 80% of the finished product, I call it
success. This applies to both coding and writing.

After one week, I had to revise that expectation. 20/80 proved
unrealistic. 40/60 is closer to observed reality.

As per Amara's Law:

> We tend to overestimate the effect of a technology in the short run
> and underestimate the effect in the long run.

I remain skeptical of hype. I also avoid dismissing the tool entirely.
Transformation may come. It is not visible yet in daily engineering
work.

------------------------------------------------------------------------

## Writing Experience

Writing output increased quickly. Drafts assemble faster. Structure
appears early. Expanding bullet points into full sections is easier.

However, iteration cost is higher than expected. Articles require
repeated refinement. The language often drifts into inflated phrasing.
It develops a polished but generic tone.

For example:

> Iterations increase API usage. Costs accumulate mainly during
> debugging loops. Output gains in drafting do not remove engineering
> convergence overhead.

This reads cleanly. It also reads interchangeable.

Over time, tone compression becomes obvious. Sentence rhythm
standardizes. Word choice narrows. When I push back against certain
phrasing, similar bias reappears in different form.

LinkedIn posts perform better because the task is constrained: "shorten
this." That is easier than "write this from scratch."

Output increased. Ownership decreased.

------------------------------------------------------------------------

## Coding Experience

Coding is more difficult.

The first draft of code usually appears quickly. It looks plausible. It
compiles. It even runs. Then edge cases appear. Small logical gaps
emerge. Fixing one issue reveals another.

Debugging becomes iterative. I act as a mediator between model output
and runtime behavior. Some suggestions improve the situation. Others
create new problems.

The model performs well with tightly scoped tasks. Reliability drops
when integration or broader system reasoning is required. Context
weakens across multiple iterations. Multi-step debugging remains
unstable.

There is also bias in the experiment itself. I am a software engineer.
Writing instructions for machines is not new to me. That background
likely improves results. It does not eliminate instability.

Despite effort, the sandbox remains unrealized. Without it, I will not
allow an agent access to my machine. Risk containment matters.

The downgrade from 20/80 to 40/60 reflects this reality. That is not a
failure. It is a measured outcome.

------------------------------------------------------------------------

## Pay-to-Win

AI is a product. Better models cost money. Running agents locally
requires hardware. Iterative convergence increases API usage.

The larger the project, the higher the accumulated cost. Debugging loops
multiply usage. Writing may feel cheap. Engineering convergence is not.

Cost-to-convergence becomes visible at scale.

------------------------------------------------------------------------

## Broader Concerns

### Environmental Impact

Large-scale AI systems require significant compute resources. Training
models consumes substantial energy. Inference at scale also accumulates
cost. Individual use may feel small, but the aggregate footprint is
large.

The environmental tradeoff is rarely visible at the prompt level. It
remains part of the system-level equation.

### Knowledge Work Displacement

AI tools can replicate structured text production and pattern-based
reasoning. Roles built around repeatable synthesis may face earlier
disruption than high-context engineering work.

The effect is uneven. Some professionals gain leverage. Others face
compression of demand. The distribution of impact matters.

### Concentration of Power

Model training, infrastructure, and large-scale compute are concentrated
in a small number of organizations. This creates dependency risk. Access
to advanced capability depends on pricing, policy, and platform
stability.

Centralization changes who controls the tools of knowledge production.

### Acceleration vs Exploitation

Acceleration increases output for those who can constrain and validate
results. It may also increase pressure on roles that depend on
standardized production.

The same mechanism that expands leverage can intensify competition.
Whether this becomes empowerment or exploitation depends on structure
and incentives.

------------------------------------------------------------------------

## Conclusion

After one week, AI increases writing output but reduces stylistic
ownership. It accelerates initial coding drafts but struggles with
stable convergence.

The sandbox barrier limits autonomy. The 20/80 expectation proved
unrealistic and was adjusted to 40/60.

AI does not replace engineering judgment. It behaves more like an eager
junior engineer: fast, confident, and in need of supervision.

The experiment continues.
