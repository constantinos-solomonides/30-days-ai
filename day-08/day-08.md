### Day 08: The Sandbox Shift and the Morality of Models

**TL;DR**
* **The Pause:** Project momentum remains tied to human agency; AI cannot yet bridge the gap during real-life interruptions.
* **Isolation Architecture:** Implemented a "double-layered" sandbox using Docker inside a Vagrant VM to mitigate root access risks.
* **The Pivot:** Moving from OpenAI to Google Gemini Pro due to ethical concerns regarding military use and better convergence performance.
* **CLI First:** Shifting to a repository-driven workflow where `prompt.md` files and commits serve as the primary interface.

---

**Recap & The Reality of the Pause**
The experiment has been silent for a while. If there is one data point to be extracted from this hiatus, it is this: AI assistants are not a stand-in for human agency. When the operator faces real-life hurdles, the digital work stops. The tools may be ready to execute, but they lack the initiative to maintain the project’s momentum independently. Now that the first sandbox is created and can be adapted, the system may finally be allowed to assist in generating these very updates.

**The Architecture of Isolation**
With the pause behind me, the focus has shifted to building a robust, reproducible environment for OpenCode. I have successfully established a sandbox utilizing the OpenCode assistant within a Docker container. However, to address the security concerns of Docker running as root, I have implemented a layer of double isolation: a `Vagrant` configuration now manages the containers. This ensures that the experimentation remains contained and the host system remains protected.

**The Pivot to Google Gemini**
While the attempt to use Ollama models locally was a valuable exercise in sovereignty, it ultimately proved unviable for the current workflow requirements. I am making a deliberate shift to Google Gemini (Google AI Pro) for three specific reasons:
1.  **Ethics:** A shift away from OpenAI following their change in stance regarding military applications.
2.  **Performance:** A general dissatisfaction with the effort required to reach convergence using OpenAI's current models.
3.  **Exploration:** The necessity of evaluating diverse models to find the right fit for this specific pipeline.

**Moving to the CLI**
To eliminate the friction of browser-based "back-and-forth," the workflow is moving entirely to the CLI. Communication will now occur via repository commits, and `prompt.md` files will be versioned to track the evolution of our instructions. This "bootstrapping" method uses OpenCode to kickstart the transition into other assistants, including Gemini.

**Next Steps**
The infrastructure is expanding. Next, the sandbox will incorporate a PlantUML container to facilitate document editing and diagram generation. The README for the pytest framework will also be refactored to serve as a persistent prompt for the assistant.

---

## Links

### Project & Articles
- **Experiment repository on [github](https://github.com/constantinos-solomonides/pytest-framework-example)**
- **Articles & prompts repository on [github](https://github.com/constantinos-solomonides/30-days-ai-articles)**

---

## Disclosure
*This article is part of **The Pareto Line** series — a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses AI systems to draft articles and generate derivative content. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, capable of creating serious problems when allowed to operate without supervision.*