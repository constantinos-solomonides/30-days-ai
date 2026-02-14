# AI Day 07 -- First Week Retrospective

## TL;DR

- Writing speed increased, but convergence and tone quality are lacking
- Coding with AI starts fast but converges slowly, and is needlessly complicated
- I had to throw most of the code I got out.
- Bootstrapping a sandbox environment proved far more difficult than hyped
- No "low code" or "no code" for me. I had to manually intervene

After one week, the results are mixed. AI helps generate output quickly
but struggles with quality, stability and integration. The 20/80 expectation
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
effort in prompt-writing yields 80% of the finished product, I would call it
success. This applies to both coding and writing.

After one week, I had to revise that expectation. 20/80 proved
unrealistic. 40/60 is closer to observed reality.

I remain skeptical of the hype. I also avoid dismissing the tool entirely. As per Amara's Law:

> We tend to overestimate the effect of a technology in the short run
> and underestimate the effect in the long run.

However, as part of this retrospective, I also include my concerns from a more abstract, ideological perspective. This is a one-off for this series, but I feel it must be said at least once. These are not criticisms about the tool itself, but concerns about the dangers of giving more dangerous tools to humanity.

------------------------------------------------------------------------

## Writing Experience

Writing output was generated quickly. Drafts become articles faster. Structure
appears early. Expanding bullet points into full sections is easier.

However, iteration cost is higher than expected. Articles require
repeated refinement. The language is often "fluffy" and pompous, even with RIS rules and
repeated prompts to simplify it.

For example:

> Iterations increase API usage. Costs accumulate mainly during
> debugging loops. Output gains in drafting do not remove engineering
> convergence overhead.

So the end result is ready faster, but has no identity, contains hallucinated references (for example, even with explicitly given links to two repositories on day 05, it added a random one for the second one) and is many small and not-so-small ways sub-par. The conversations in the project repository chronicle my frustration with the outputs. Additionally, I am still undecided on how much my manual writing speed would increase if I wrote myself a prompt and built the article around that. It's a data point I plan to add one of the coming days.

Not to say there's nothing good. LinkedIn posts writing performs better because the task is constrained: "shorten this." That is easier than "write this from scratch." Then again, the claim and goal isn't to easily do what's easy. Still, that's what my experience has been so far.

------------------------------------------------------------------------

## Coding Experience

Coding suffers more than article writing. The first draft of code usually appears quickly. It looks plausible.
It compiles. It even runs -usually-. Then edge cases appear or things don't work as expected. Assumptions
fail. For example, in the first iteration for the sandbox, it set and used two environment variables, `UID`, and `GID` in a `bash` script. The problem is that `UID` is read-only, and `GID` isn't set by `bash`. So the script failed out-of-the-box and had to be modified to bypass this. More importantly, when asked to persist data, it structured the series of mounts in such a way that the mounted volume would mask the contents, causing failures, and would be inconsistent with locations being mounted. This was way more blocking than renaming a variable in a couple of points

Debugging becomes an iterative process without an agent. I act as a mediator between model output
and runtime behavior. Some suggestions improve the situation. Others
create new problems.

The model performs well enough with tightly scoped, simple tasks. When the solution would need someone
who thinks critically, and real solutions often do, it fails. A rubber duck should be silent or critical. AI
is anything but. There's a reason git imperative exists and it's not because tone is a priority.

The issues exist despite the bias built-in to the experiment because of who runs it. I am a software engineer;
writing instructions for machines is nothing new to me; solving problems using code is what I do, both by
vocation and profession. And yet. This tool constrains me as much as it helps. Maybe more.

As a result, despite all my efforts, the sandbox remains unrealized. Without it, I will not
allow an agent access to my machine. The choices shouldn't be "risk becoming a cautionary tale or don't use
it"

At the end of the day, I had to do manual work and downgrade my 20/80 expectation to 40/60. The day-06 article (available on [wordpress](
https://anthropocentricsoftware.wordpress.com/2026/02/12/ai-day-06-a-day-of-manual-work/
)
and [substack](https://open.substack.com/pub/csolomonides/p/ai-day-06-a-day-of-manual-work?r=1g7elm&utm_campaign=post&utm_medium=web&showWelcomeOnShare=true))
contains more details on why I did it and how. It's not a failure of the experiment, it's an outcome.

------------------------------------------------------------------------

## Pay-to-Win

AI is a product. Better models cost money. Running agents locally
requires hardware. Iterative convergence increases API usage, and that costs time and money.

The larger the project, the higher the accumulated cost. Debugging loops
multiply usage of tokens, input and output. Writing may feel cheap but the bill at the end may prove it's
anything but.

Cost-to-convergence becomes visible at scale, and even then, it doesn't get you everything. For example, [this experiment by anthropic](https://www.anthropic.com/engineering/building-c-compiler) was conducted by someone who's not just a software engineer, but by someone working for Anthropic. According to them, it took two weeks, 2,000 Claude code sessions and 20,000 USD to get something that doesn't work fully, as cleanly stated in the article. The [issues section of the repository](https://github.com/anthropics/claudes-c-compiler/issues) is an interesting read. And that's for a problem that's very well defined, and whose solution was most likely used to train the agents. As I said: I am *very* skeptical of the hype.

------------------------------------------------------------------------

## Broader Concerns

As AI is still an emerging technology, albeit rapidly expanding, research for socio-economic impact has yet to catch-up. This section contains anecdotes and conjecture and should be read with this in mind.

The direct technical issues aren't the only ones that exist and need to be considered. There are environmental, moral, and other angles to consider, with short, mid and long-term impacts for our lives. These are all things that I can't measure as part of this experiment but that I **must** take into consideration while using the tool. This section departs from a technical PoV, but that is also within the scope of Engineering. We are after all problem solvers, and a solution causing bigger problems is no solution at all.


### Knowledge (White collar) Work Displacement
AI is touted at least in part as a drop-in replacement for coding and other knowledge-related skills. As such, it's been used as an excuse by companies to do massive layoffs, flooding the job market and causing issues on multiple fronts. What's worse, is that the tool doesn't really deliver what everyone is claiming it does in term of profit boost, to the point where discussions of an "AI bubble" are becoming more common. AI adoption is criticized as premature overcommit, or in many cases a smoke-screen to allow the layoffs without stock impacts.

Additionally, training AI seems to have been made possible thanks to a huge copyright infringement. In other words, AI harmed intellectual workers before it even took off.

### Concentration of Power

Model training, infrastructure, and large-scale compute are concentrated
in a small number of organizations. This creates dependency risk. Access
to advanced capability depends on pricing, policy, and platform
stability. Centralization changes who controls the tools of knowledge production.

On top of that, paying for something means supporting all the causes the owning company supports. Lately, the ideological gap between the average person and CEOs and owners of the companies profiting from AI seems to be growing at an accelerated pace.

### Environmental Impact

Large-scale AI systems require significant resources. Training
models consumes substantial energy. Data centers need to be built, equipped and powered.
Individual use may feel small, but the aggregate footprint is large.

The environmental cost is rarely -if ever- visible at the prompt level. It
remains part of the system-level equation, and that's the bill we'll be called to pay in the end.

### Other problems with AI uses

Growth and innovation to a tool don't happen selectively. Once the tool becomes better, it's better when used for good and more efficient when used for evil. This is true for everything, from transportation to power tools. AI is not special in that sense. What sets it aside, is that it expands the scope for doing good and evil way beyond what was feasible until now. Smart weapons, mass surveillance, facial recognition, there are multiple ways to abuse it, even as it is used to accelerate research in service of health and progress.

Even when not intentionally used for evil, it can harm. It's the ideal yes-man, the quintessential enabler. Making it more convincing may lead to more unfortunate incidents, like the one where [a son killed his mother and himself due to AI fueling his paranoia](https://nypost.com/2025/08/29/business/ex-yahoo-exec-killed-his-mom-after-chatgpt-fed-his-paranoia-report/). I fear for the generation that is exposed to it during their formative years, as well as those that follow. Experts already speak of [AI psychosis in teens](https://www.cbsnews.com/chicago/news/ai-chatbot-girlfriend-boyfriend-teens-psychosis/). All branches of engineering have some horror stories of catastrophic failure that led to stricter regulations. AI may be it for Software Engineering.

------------------------------------------------------------------------

## Conclusion

The impression from the first week is that AI increases writing output but disproportionately reduces quality. It accelerates creating initial coding drafts but struggles with stable convergence and understanding the specs.

AI does not replace engineering judgment. It does seem to behave more like an eager junior engineer: fast, confident, and in need of supervision.

The experiment continues, with hopes of better outcomes by the end of it.

---

## Links

### Project & Articles
- **Experiment repository on** [**github**](
    https://github.com/constantinos-solomonides/pytest-framework-example)
- **Articles & prompts repository on** [**github**](
    https://github.com/constantinos-solomonides/30-days-ai-articles)
- [Bootstrapping_\(
    compilers\) at Wikipedia](https://en.wikipedia.org/wiki/Bootstrapping_\(compilers\))
- [Amara's law](
    https://www.computer.org/publications/tech-news/trends/amaras-law-and-tech-future)
- [Git Commit Styleguide](
    https://github.com/goodbyekansas/git-commit-styleguide)
- [Companies Are Laying Off Workers Because of AI’s Potential—Not Its Performance](
    https://hbr.org/2026/01/companies-are-laying-off-workers-because-of-ais-potential-not-its-performance)
- [‘AI-washing’ and ‘forever layoffs’: Why companies keep cutting jobs, even amid rising profits](
    https://fortune.com/2026/02/10/ai-washing-and-forever-layoffs-why-companies-keep-cutting-jobs-even-amid-rising-profits/)
- [Companies are blaming AI for job cuts. Critics say it’s a 'good excuse'](
    https://www.cnbc.com/2025/10/19/firms-are-blaming-ai-for-job-cuts-critics-say-its-a-good-excuse.html)
- [OpenAI’s President Gave Millions to Trump. He Says It’s for Humanity](
    https://www.wired.com/story/openai-president-greg-brockman-political-donations-trump-humanity/)
- [Artificial Intelligence: The New Eyes Of Surveillance](
    https://www.forbes.com/councils/forbestechcouncil/2024/02/02/artificial-intelligence-the-new-eyes-of-surveillance/)
- [How AI Is Used In War Today](
    https://www.forbes.com/sites/bernardmarr/2024/09/17/how-ai-is-used-in-war-today/)
- [AI Copyright Lawsuit Developments in 2025: A Year in Review](
    https://copyrightalliance.org/ai-copyright-lawsuit-developments-2025/)
- [How ChatGPT fueled delusional man who killed mom, himself in posh Conn. town](
    https://nypost.com/2025/08/29/business/ex-yahoo-exec-killed-his-mom-after-chatgpt-fed-his-paranoia-report/)
- [issues section of antrhopic's experiment repository](https://github.com/anthropics/claudes-c-compiler/issues)
- [AI psychosis in teens](https://www.cbsnews.com/chicago/news/ai-chatbot-girlfriend-boyfriend-teens-psychosis/)

------------------------------------------------------------------------

## Coming up

A two-day pause to take-care of physical-world tasks and then

Day 08 - Back to building the sandbox, using "opencode"

------------------------------------------------------------------------

## Disclosure
*This article is part of **The Pareto Line** series — a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses AI systems to draft articles and generate derivative content. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, capable of creating serious problems when allowed to operate without supervision.*
