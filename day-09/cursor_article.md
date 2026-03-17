# Day 09: Convergence Through Iteration
*The Pareto Line --- a 30-day experiment in AI use*

## TL;DR

- Used two AI models (Gemini and Cursor) on the same design document and merged their outputs
- The merge was low-conflict but not zero-effort; neither model was strictly better
- Iterative propose-review-approve loops caught formatting bugs AI missed
- 17 technology decisions made in a single session by applying simple selection criteria
- Documentation was the primary deliverable; no code was written

------------------------------------------------------------------------

## Introduction

For thirty days, I am running an experiment: use AI as much as possible
and document what actually happens. This is day nine. The sandbox is
finally functional, multiple agents are accessible from a single terminal
via `screen`, and files can be created and edited directly. The
infrastructure friction that dominated earlier days is largely gone.

Today's session introduced a new tool: Cursor, backed by Claude. Prior
days used ChatGPT (days 1-7) and Google Gemini (days 8-9). The task was
not to write code but to finalize a design document that already
contained raw outputs from both Gemini and a previous Cursor session. The
question: can two different AI models contribute to the same artifact, and
can a human steer the merge into something better than either produced
alone?

------------------------------------------------------------------------

## The Setup: Two Models, One Document

The README for the pytest-framework project had three sections marked
`TODO AI`. Each section contained two blocks of raw AI output: one from
Gemini, one from Cursor (generated in separate prior sessions). Both
models had been given the same context and the same task. The outputs
overlapped significantly but diverged in structure and granularity.

Gemini produced fewer items per section but formatted them with explicit
Pros/Cons for each option. Cursor produced more items -- sometimes three
to four times as many -- but used flat bullet lists without weighing
trade-offs. Neither approach was wrong. Gemini was more structured; Cursor
was more thorough. The useful output was the union, not either one alone.

------------------------------------------------------------------------

## The Process: Propose, Review, Approve

The merge followed a strict loop: the AI proposed a concatenated section,
I reviewed it, and only after explicit approval was it written to the
file. No content was committed without a green light. This sounds obvious,
but it matters. AI assistants default to "generate and move on." Forcing
a gate between proposal and commit is what keeps the human in the loop
rather than merely in the room.

The loop caught a real issue on the first section. I noticed that a
markdown blockquote placed immediately after a bullet list -- without a
blank line -- would be absorbed into the last bullet item by most
parsers. The AI had not flagged this. It is exactly the kind of
formatting-level detail that AI consistently misses because it operates
on semantic intent, not on rendering behavior. The fix was trivial (add
a blank line), but the bug would have been invisible until someone
rendered the document and wondered why the notes looked wrong.

This is not a criticism of the tool. It is a data point about where human
review adds value. Semantic correctness is necessary but not sufficient;
presentation correctness requires a different kind of attention.

------------------------------------------------------------------------

## The Merge: Low-Conflict, Not Zero-Effort

After the first pass produced concatenated sections, a second pass
compared the Cursor and Gemini concatenations side by side, summarized
differences, and produced a final merged version. The result:

- The Cursor concatenation was strictly more complete in all three
  sections. Every component and test case in the Gemini version was
  present in the Cursor version, but not the other way around.
- Gemini added a small number of items Cursor missed: an explicit con for
  ruff (newer than established alternatives), PostgreSQL and session-based
  auth as alternatives, a database persistence integration test, a
  whitespace sanitization unit test, and a timestamp comparator unit test.
- The merge amounted to roughly five one-liner insertions into an
  already comprehensive list. Low-conflict, but not something you could
  skip.

The takeaway: running two models on the same task and merging their
outputs is a viable workflow. The effort is modest -- comparable to a
code review -- and the result is more complete than either model alone.
Whether the marginal completeness justifies the cost depends on how much
you trust a single model's coverage. For a design document that will
drive implementation, I would rather spend the extra twenty minutes.

------------------------------------------------------------------------

## Decision Mode: Lightweight Selection Criteria

With the design sections finalized, the document had summary tables with
"TBD" in every cell. Filling them required technology decisions. Rather
than debating each one exhaustively, I applied two simple criteria: pick
the most lightweight option, and favor those with an official Docker
image. This resolved most decisions instantly.

Two items needed discussion: the Artifact Tracker and the Log Tracker.
The Artifact Tracker had a tension between "lightest" (GitHub Packages,
zero infrastructure) and "has a Docker image" (Local Docker Registry).
I chose the registry -- self-contained, fits the single-host constraint,
does not depend on internet or storage quotas.

The Log Tracker became the most interesting design discussion of the
session. Instead of picking an off-the-shelf tool, I proposed a custom
REST API with a specific contract: accepts JSON logs, retrieves by time
range, exposes `/info` and `/version` endpoints, stores data in a
dedicated SQLite file. The AI surfaced six specification gaps I had not
considered: retrieval key strategy, internal storage format, metadata
normalization, endpoint semantics, concurrency implications, and
retention policy. Three rounds of Q&A later, the spec was tight enough
to implement without ambiguity.

This was specification through discussion, not specification through
prompting. The AI asked questions; I made decisions. The result is
something neither of us would have produced alone in the same amount of
time.

------------------------------------------------------------------------

## The System on Paper

With all decisions made, the session's final act was producing an
IMPLEMENTATION.md -- a versioned operational guide that turns the
README's architecture into something a developer can actually follow.
The design, taken together, looks like this:

Five containers orchestrated by Docker Compose on a single host. A
React/TypeScript frontend served on port 3000. A FastAPI/Python backend
on port 8000 handling authentication via JWT, post validation, and the
10-second duplicate rejection rule. A custom log tracker API on port 8001
with its own SQLite database file, deliberately separated from the
application database so a runaway log table cannot take down the app. A
notification service stub on port 8002, placeholder for future Slack and
email integrations. And a local Docker Registry (`registry:2`) on port
5000 for storing built images.

The CI/CD pipeline is two GitHub Actions workflows. The first runs ruff
on every push -- fast, single-binary linting that catches issues before
anything else happens. The second triggers on non-draft pull requests and
runs the full sequence: build all images, push to the local registry,
deploy via `docker compose up`, wait for health checks on every service,
run unit tests, then integration tests (pytest + HTTPX hitting the API
directly), then E2E tests (Playwright in a Docker container driving the
frontend), upload results to the log tracker, and tear down.

Configuration is managed through a `.env` file with seven variables:
database paths for both SQLite files, JWT secret and expiry, log line
size cap (16KB), total log storage cap (256MB with FIFO eviction), and
the registry port.

The known limitations are documented upfront rather than discovered
later. SQLite serializes writes on both databases -- acceptable for a toy
setup, but the implementation guide notes where PostgreSQL and a message
queue would replace it. The log tracker has no search capability in v1 --
time-range retrieval only -- with a note that reverse indexing or an
Elasticsearch backend would handle it in production. Internal services
have no authentication; the guide names mutual TLS and API keys as the
production path. None of these are surprises. They are deliberate
trade-offs, written down before anyone hits them during implementation.

The test plan spans three levels: 18 end-to-end tests covering the full
user workflow (timeline viewing, posting, authentication, character
limits, duplicate detection), 16 integration tests validating API
contracts and boundary conditions (including precise 10-second/11-second
duplicate timing and malformed token rejection), and 14 unit tests
isolating validators, duplicate detection logic, and credential handling.

Nothing here is built yet. But it is specified tightly enough that the
implementation phase can focus on writing code rather than making
decisions.

------------------------------------------------------------------------

## The Junior Colleague Metaphor Holds

One pattern that has solidified over the past few days: handling the AI
agent is akin to guiding a junior colleague. It accepts direct feedback,
adjusts without ego, and improves its output when corrected. My
relatively extensive experience with teaching and mentoring turns out to
be directly useful when guiding these agents. The skills transfer.

But the metaphor has limits. A junior colleague builds context over days
and weeks. The agent's context resets between sessions; continuance is
more complicated than it should be. And unlike a junior colleague, the
agent does not push back unless instructed to. The structured rules file
(RIS) I use with Cursor helps -- it tells the agent to be skeptical, to
question claims, to flag conflicts -- but this is artificial scaffolding
for behavior that a good human collaborator would exhibit naturally.

Token expenditure is another concern. When context runs away -- large
files, long sessions, repeated reads -- costs accelerate. The shifting
between two agents for the README plan was done sub-optimally this time;
I need to find ways to improve speed and reduce redundant context
loading.

------------------------------------------------------------------------

## Documentation as the Deliverable

No code was written today. The outputs were:

- A finalized README with clean architecture sections, 17 technology
  decisions pinned in summary tables, and a detailed Log Tracker API spec
- A versioned IMPLEMENTATION.md covering prerequisites, project
  structure, container inventory, configuration, build/deploy commands,
  test execution, and known limitations
- A structured YAML summary of the full session, intended to be parsed
  for article generation (which is what produced this draft)

This is deliberate. The design exists before the code. The test plan
exists before the tests. The implementation guide exists before the
implementation. Whether this survives contact with reality is the
experiment's next question.

------------------------------------------------------------------------

## What Changed

- The sandbox works. Multiple agents from a single terminal. Files
  edited directly. The infrastructure friction of earlier days is gone.
- Multi-model workflows are viable. Running Gemini and Cursor on the
  same task, then merging, produced a more complete result than either
  model alone.
- Iterative approval loops are essential, not optional. The formatting
  bug caught during review would have been invisible to the AI.
- Scope discipline matters. The Log Tracker could have expanded into a
  full service design. Holding the line on v1 scope -- deferring features
  as documented future capabilities -- kept the session productive.

------------------------------------------------------------------------

## Next Steps

- Start actual implementation of the project using agents
- Expand the RIS (rules/instructions) to make tests a first-class
  citizen and ensure high quality
- Find ways to reduce context-switching overhead between agents
- Agents remain manually steered; autonomous operation is not yet
  preferred

------------------------------------------------------------------------

## Links

### Project & Articles
- **Experiment repository on [GitHub](https://github.com/constantinos-solomonides/pytest-framework-example)**
- **Articles & prompts repository on
  [GitHub](https://github.com/constantinos-solomonides/30-days-ai-articles)**

------------------------------------------------------------------------

## Disclosure
*This article is part of **The Pareto Line** series -- a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses AI systems to draft articles and generate derivative content. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, capable of creating serious problems when allowed to operate without supervision.*
