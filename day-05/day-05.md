# AI Day 05 & 05.5 — A Pause and a Step Back
## The Pareto Line series: a 30-day experiment in AI use

> **Reminder**
> Articles in this series are intentionally written mostly by AI, with human guidance, constraints, and corrections applied explicitly. Any remaining roughness is deliberate.

---

### TL;DR

The sandbox worked.
Local models worked.
The agent framework mostly worked.

**The workflow did not.**

Not because the tools were broken, but because **coordination cost, hidden defaults, and operational drag outweighed the gains** once agentic development was attempted seriously.

This was not a failure of engineering.
It was a failure of expectations.

---

## What I set out to do

The goal for Day 05 was explicit:

Use a **model that runs locally**, deploy an **agent on top of it**, and let that agent **iterate over programmatic tasks** with minimal human intervention.

The objective was not to demo autonomy, but to test whether an agentic loop could meaningfully replace or accelerate parts of real development work under constraints: isolation, reproducibility, and bounded scope.

If agent-based workflows were going to be viable locally, this was the point where that should become visible.

---

## What actually happened

Progress happened, but not cleanly.

I ended up working far more **offline** than planned. Not because the AI was unavailable, but because many of the issues were not visible at the prompt level. They lived one layer below: in defaults, naming conventions, implicit behavior, and undocumented expectations.

I repeatedly had to correct commands produced by the AI, even when constraints were explicit. Things like using `docker` instead of `docker compose`, or ignoring boundaries around persistence and scope, kept reappearing. Each instance was minor. Together, they consumed attention.

I also had to investigate **model sizing and performance limits** after the fact. There was no early warning that some “supported” local configurations would be slow enough to distort the experiment itself. The limitation was discoverable, but not surfaced.

Finally, I had to read the OpenHands and LiteLLM documentation directly to understand how they actually interact, rather than how examples imply they do.

None of this moved the experiment forward. It was corrective work.

---

## The hidden cost of “helpfulness”

Even with an explicit RIS and repeated corrections, the system defaulted to being *too helpful*.

Helpfulness showed up as:
- completion prioritized over compliance
- filling gaps instead of respecting boundaries
- confidently proposing solutions that violated project rules
- hallucinations introduced to “move things along”

Each violation was small. The accumulation was not.

This is not about model capability. It is about **mismatch**: between how assistance is shaped and how constrained engineering work actually progresses.

---

## Where things broke

The failure mode here was not catastrophic. Nothing exploded. The agent did not go rogue.

Instead, it failed by **consuming attention**.

Every correction required inspection, context rebuilding, validation, and often rollback. At that point, the question stopped being “can this work?” and became “is this the right trade-off?”

---

## Rebalancing effort

Continuing with the same effort distribution would have been irrational.

For week 2, **I will change my approach**.

Instead of expecting AI to carry the workflow end-to-end, I will shift to a **60/40 split**:
- 60% AI contribution is success
- 40% remains manual, deliberate, and owned

AI moves from *agent* to **tooling**: scaffolding, boilerplate, exploration, review.

Whether this improves throughput is an empirical question. That is the experiment.

---

## Cost estimates — assumptions and calculations

This pause also forced a more explicit cost evaluation.

### Online agents

Assumptions:
- ~8 hours/day
- ~30 days/month
- ~1–2M tokens/day once retries, replanning, and context growth are included

Estimated monthly costs:
- OpenAI-class models: **€450–€900**
- Anthropic-class models: **€400–€800**
- Google-class models: **€300–€600**

**Caveats:**
- These estimates were produced with the help of ChatGPT.
- I could not independently verify them in a rigorous way, as **no authoritative public sources publish concrete token counts for real agentic development tasks**.
- I explicitly tasked ChatGPT to produce a cost estimate based on observed behavior and reasonable assumptions.
  **Link to prompt / method:** _TO BE INSERTED_
- I plan to eventually integrate a **paid, online agent**, purchase tokens, let it run until convergence, and publish the **actual usage data** once available.

### Local agents

A realistic local setup capable of running non-trivial agents:

- high-core-count CPU
- **64–96 GB RAM**
- GPU in the **24 GB VRAM class**
- storage, cooling, and power margin

Indicative cost: **€2,500–€4,000 upfront**

Obsolescence horizon:
- ~2–3 years of practical relevance
- likely <18 months before parity with hosted models is lost again

Additional considerations:
- Hardware prices rise with demand.
- Providers are still in discovery mode.
- Once ROI pressure increases and competitors drop out, pricing dynamics change.
- Concrete examples of agentic development costs (in tokens or money) are still rare.

---

## Evaluation

Nothing failed technically.

The sandbox held.
Local models responded.
The agent framework behaved as designed.

And yet the workflow did not feel lighter.

What failed was **operational efficiency under real constraints**. The overhead required to make the agent comply offset the gains it was supposed to deliver.

This is not a rejection of agentic approaches. It is a narrowing of where they currently make sense.

---

## Results summary

Day 05 did not produce a clean win.

An agent exists.
A hybrid stack exists.
The system is closer to usable.

But the costs — cognitive, temporal, and financial — are now visible.

Day 05.5 exists because ignoring that would have been dishonest.

---

## Links

### Project & Articles
- **The Pareto Line — 30-day AI experiment (project repository)**
  https://github.com/constantinos-solomonides/30-days-ai-articles

- **Articles archive (prompts, drafts, and published versions)**
  https://github.com/constantinos-solomonides/30-days-ai-articles/tree/main/articles

### Pricing
- **OpenAI API Pricing (official)**
  https://openai.com/api/pricing/

- **Anthropic Claude API Pricing — plans and per-token costs**
  https://intuitionlabs.ai/articles/claude-pricing-plans-api-costs

- **LLM API Pricing Comparison (OpenAI, Anthropic, Google)**
  https://www.cloudidr.com/llm-pricing

### Local inference & discussion
- **llama.cpp — Local LLM inference on consumer hardware**
  https://github.com/ggml-org/llama.cpp

- **Ollama FAQ — memory usage and system requirements**
  https://docs.ollama.com/faq

- **VRAM requirements for running local LLMs with Ollama**
  https://localllm.in/blog/ollama-vram-requirements-for-local-llms

---

## Next

Day 06 will take the current approach to completion, even if imperfect.
Day 07 will be a retrospective, separating time lost *because of AI* from time saved *because of AI*.
