# AI Day 03 — Agentic Freedom vs Operational Safety

Most AI demos assume you're fine giving an agent broad access and letting it "figure things out".

I'm not.

On Day 03 of "The Pareto Line series", I built an **AI-assisted Vim sandbox** with the opposite bias:
tight isolation, explicit constraints, and no unsupervised execution.

Between
**Agentic freedom**  → speed through unrestricted iteration
and
**Operational safety**  → friction through boundaries, mounts, and human approval

I chose safety.

The AI produced usable scaffolding, but also:
- installed tools in non-existent paths
- misunderstood Vim autoload semantics
- masked its own work via bind mounts

The result?
- My effort vs results roughly matched the 20/80 rule
- No clear win over using existing boilerplate
- I got to see new-ish approaches to a problem I knew how to solve

The real change wasn't AI vs no AI.
It was **reading and validating generated code instead of writing it**. And that may be where AI use causes the big issues.

📄 Full article:
- Substack 👉 https://open.substack.com/pub/csolomonides/p/day-03-building-an-ai-assisted-vim?r=1g7elm&utm_campaign=post&utm_medium=web&showWelcomeOnShare=true
- WordPress 👉 https://anthropocentricsoftware.wordpress.com/2026/02/02/day-03-building-an-ai-assisted-vim-sandbox/

📁 Repo 👉 https://github.com/constantinos-solomonides/30-days-ai

Next: **Day 04 — Putting the environment to the test**
