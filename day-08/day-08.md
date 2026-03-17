# Day 08: The Sandbox Shift and the Morality of Models
*The Pareto Line --- a 30-day experiment in AI use*

## TL;DR

* Real-life caused delays with the series
* Implemented a "double-layered" sandbox using Docker inside a Vagrant VM to mitigate root access risks.
* Moving from OpenAI to Google Gemini Pro due to ethical concerns regarding military use and better
  convergence performance.
* Shifting to a repository-driven workflow where `prompt.md` files and commits serve as the primary interface.

---

## Recap & The Reality of the Pause
The experiment has been silent for a while. If there is one data point to be extracted from this hiatus, it is
this: AI assistants are not a stand-in for human agency. When the operator faces real-life hurdles, the
digital work stops. The tools may be ready to execute, but they lack the initiative to maintain the project’s
momentum independently. Now that the first sandbox is created and can be adapted, the system may finally be
allowed to assist in generating these very updates.

## Discoveries in the meantime

There was an interesting bit of news that came out between my publishing day-07 and this one, the one about
Meta's alignment director's e-mails being deleted by an AI assistant. This is not a random engineer, but the
person hired by one of the big tech companies as a prominent expert on AI. This is a vindication of what I and
other colleagues have been saying for a long time, that trusting an agent can be a really bad idea with
unwanted consequences. So let me repeat myself **AI is a multiplier** and **GIGO still applies**. If you're
not holding the wheel, you're simply speeding faster towards the rock you'll crash onto.

## The Architecture of Isolation
With the pause behind me, the focus has shifted to building a robust, reproducible environment for OpenCode.
I have successfully created a sandbox utilizing the OpenCode assistant within a Docker container. However, to
address the security concerns of Docker running as root, I have implemented a layer of double isolation: a
`Vagrant` configuration now deploys the environment in which the containers are deployed. This reduces the
probability some clever code is used to allow escaping the docker sandbox or otherwise overloading the system,
e.g. by filling the hard disks or hogging the CPU.

## The Pivot to Google Gemini
While the attempt to use Ollama models locally was a valuable exercise in sovereignty, it ultimately proved
unviable for the current workflow requirements, due to the resources required.
I am therefore shifting to paid Google Gemini (Google AI Pro) for three specific reasons:
1.  **Ethics:** A shift away from OpenAI following their change in stance regarding military applications.
2.  **Performance:** A general dissatisfaction with the effort required to reach convergence using OpenAI's
    current models.
3.  **Exploration:** The necessity of evaluating diverse models to find the right fit for this specific
    pipeline.
Although `Claude` is reportedly the best AI for coding, I'm looking for an all-around assistant, hence moving
to another model that I've seen being spoken highly-of

## Moving to the CLI
To eliminate the friction of browser-based "back-and-forth," the workflow is moving entirely to the CLI.
Communication will now occur via repository commits, and `prompt.md` files will be versioned to track the
evolution of our instructions. This "bootstrapping" method uses OpenCode to kickstart the transition into
other assistants, including Gemini. An additional benefit of this approach is that the repository also becomes
how history and interactions are tracked, simplifying the process and avoiding the need to refer to multiple
sources of truth.

## Next Steps
The infrastructure is expanding. A Gemini container is to be added, along with a PlantUML container to allow
creating diagrams when needed. The README for the pytest framework will also be refactored to serve
as a persistent prompt for the assistant as well as documentation. By having the PlantUML as part of the
toolbox, human beings are given more tools to help us visualize what's being done, thus more comfortably
shifting into an architectural and orchestration role.

This approach is how an actual project would have been implemented, meaning a "design, implement, identify,
iterate". Part of why "iterate" is necessary is that the project is meant to be good enough for production on
the conceptual level, while light enough to be run as a toybox on the implementation level. This means that,
eventually, each component will be a black box with a well-defined perimeter, but that can have anything
inside and be of any size. It's absolutely a very ambitious goal, however the challenge is part of what makes
the effort meaningful.

---

## Links

### Project & Articles
- **Experiment repository on [github](https://github.com/constantinos-solomonides/pytest-framework-example)**
- **Articles & prompts repository on
  [github](https://github.com/constantinos-solomonides/30-days-ai-articles)**
- [Business insider - Meta AI alignment director shares her OpenClaw email-deletion nightmare](https://www.businessinsider.com/meta-ai-alignment-director-openclaw-email-deletion-2026-2?op=1)

---

## Disclosure
*This article is part of **The Pareto Line** series — a 30-day experiment in AI use, focused on producing
Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses AI systems to draft articles and generate derivative content. A Pareto approach
is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected
manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, not as an authority. It is
approached like an enthusiastic junior: helpful when guided and reviewed, capable of creating serious problems
when allowed to operate without supervision.*
