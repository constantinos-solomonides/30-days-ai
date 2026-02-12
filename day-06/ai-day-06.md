# AI Day 06 -- A day of manual work

*The Pareto Line --- a 30-day experiment in AI use*

------------------------------------------------------------------------

**Disclaimer**: \
Each "day" in this series represents a work-day of effort. The posting
delay reflects real-world obligations, not retroactive rewriting or
assisted optimization. Day 06 was intentionally conducted without AI
assistance.

------------------------------------------------------------------------

## TL;DR

* Day 06 was a deliberate no-AI day in the middle of a high-AI-usage experiment
* Manual work was more linear
* AI-assisted workflows feel faster but noisier
* AI tools can increase costs tremenduously by introducing unwanted and unneeded context

------------------------------------------------------------------------

## What I Set Out to Do

The primary objective was straightforward: continue building the sandbox manually.

Secondary objectives were more important:

-   Compare manual work against AI-assisted work while still immersed in heavy AI usage.
-   Observe whether AI usage had already become habitual or not
-   Prevent masking the ratio of human vs AI effort by using sandboxes by others

The build-from-scratch constraint was intentional. There are many sandboxes already available, but I wanted
something I built from scratch, as a bootstrapping test.

------------------------------------------------------------------------

## What Actually Happened

The work became more linear.

Without AI suggesting branching paths, I approached debugging through
experience:

* Reduce the request to something trivial --- "say hi to me."
* Add a container running a vanilla `ubuntu:latest` image, to use as a testing jumpbox
* Start at from the last node of the call chain (`ollama` in this case)
* Increase verbosity
* Verify functionality and measure response time

From doing so I discovered the following:

Using cURL returned fast, predictable responses from both Ollama and litellm

The slowdown was caused by OpenHands. It introduced excessive context into requests, large instruction
payloads that were not relevant to the immediate task. Essentially, there were no delays. The local model was
working hard to reply to a request that started simple from the user ("say hi to me") that ended up having
tons of needless comment from the tool

The problem remains: Building a sandbox so AI can be safely used, using AI, is unnecessarily painful. The
options shouldn't be "trust everyting or suffer"

------------------------------------------------------------------------

## Documentation bloat due to AI. A vicous circle.

AI tools naturally generate their own documentation using AI. The tone is confident. The structure is
impressive. The human-consumption optimizations are weak to say the least.

With tradional "from human for human" documentation, there were some "rubber-duck" benefits. The person trying
to explain would find their lack of understanding and clarify for the readers too. AI lacks that filter.

The end-result is documentation that can be parsed by machines, but is not always fit and clear for human
perusal. The sites offer chatbots to help of course, but that assumes that the blindspots have been at some
point identified.

------------------------------------------------------------------------

## Direction after openhands

Openhands may have been sufficient with a much higher-end machine. One I do not think will be accessible to
the majority of people. As it is, the injected payload, in the form of constraints, added into the requests
forced its removal.

That is a textbook example of AI bloat:
assistance that increases cost without increasing precision.

The first search for a lightweight alternative led to OpenClaw. It was
not the right fit --- more oriented toward chat interactions than
focused sandbox execution.

Its documentation suffered from the same issue identified earlier:
optimized for completeness, not for constrained human cognition.

Work then began toward integrating OpenCode instead.

At the end of the day, there is still no working model. But there are also no longer endless cycles of small
corrections, but instead leaps of trial-failure and deterministic next steps.

The next steps will see continued use of the `ubuntu:latest` container. Do the installs, verify and upon
success automate

------------------------------------------------------------------------

## Rebalancing Effort

Manual debugging was slower in wall-clock time but more predictable.

AI-assisted debugging feels faster but involves lateral exploration. It
suggests options. It expands context. It consumes tokens. It generates
scaffolding that may not be structurally optimal.

The key difference:

Human work is linear.\
AI-assisted work is iterative.

Experience enables targeted interventions without random exploration. AI
sometimes simulates exploration until something works.

Neither approach is inherently superior. The cost model differs.

Manual work requires that a human is working on the issue.\
Physical-world delays block outcomes.\
The human being becomes the bottleneck.

AI can be set to run until success.\
For local models, the cost is simply that of electricity. For remote, the cost is tokens. Machines don't need
rest, but the termination rules and the parameters must be set right.

An added risk is that what will converge will not necessarily be maintainable. Code is rarely an one-off
thing and it's already hard to read. This is something to experiment on once the sandbox is up and running

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

- No local AI agent created yet.
- Communication pipeline validated
- Excessive context injection identified as performance bottleneck.
- Openhands and litellm approach rejected. A simpler restart has taken place
- Cleaner container baseline established.
- Alternative tooling exploration initiated.

I may not have succeeded in getting the sandbox but this is still a success, albeit so far mostly for the manual approach.
The process is still enjoyable. The learning curve is real.

This is something I fear use of AI takes away. Many of the things we learnt and applied to our work came from mucking around for fun. As always, there's an XKCD comic for that

[!Usefulness in my career](!https://imgs.xkcd.com/comics/11th_grade.png)

------------------------------------------------------------------------

## Coming up

Day 07 will be a retrospective of the outcomes so far. An evaluation between the ease -or not- of using AI vs doing the work manually, using libraries and boilerplate.

------------------------------------------------------------------------

## Disclosure
*This article is part of **The Pareto Line** series — a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses AI systems to draft articles and generate derivative content. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, capable of creating serious problems when allowed to operate without supervision.*
