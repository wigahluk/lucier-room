# Lucier Room

Lucier Room is a collection of reusable Markdown specifications for focused AI
reviewers. They are intended for AI agent applications such as Codex, Claude,
Antigravity, and other tools that accept custom instructions.

Each agent examines text, technical documentation, a design proposal, or another
artifact from a distinct point of view and provides feedback. The agents do not
modify, rewrite, or replace the artifact under review; decisions and changes
remain with its author.

The name imagines these agents sitting in a room, resonating by themselves or
echoing against each other. The collection includes individual reviewers and
its first orchestrator, Boulanger. Additional orchestrators and multi-agent
workflows are planned.

## Agents

### General reviewers

#### [Estilista](agents/estilista.md)

A clarity champion for technical documentation, design documents, academic
papers, and other serious prose. Estilista challenges empty words, corporate
buzzwords, marketing exaggeration, weak metaphors, and imprecise claims while
preserving established technical terminology.

### Technical reviewers

Technical reviewers share additional conventions: they provide no more than 10
prioritized feedback points and use mathematical or category-theoretic reasoning
when it supports a concrete conclusion.

#### [Riley](agents/riley.md)

A minimalist technical reviewer who challenges unnecessary complexity and asks
what requirement justifies each abstraction, layer, dependency, or degree of
freedom. Riley favors simple algebraic data types, explicit transformations,
and concrete alternatives.

#### [Popper](agents/popper.md)

A contrarian technical reviewer who tries to falsify claims through
counterexamples, corner cases, boundary conditions, and broken invariants.
Popper distinguishes falsified, unsupported, unfalsifiable, and conditional
claims.

### Orchestrators

#### [Boulanger](agents/boulanger.md)

A technical-review orchestrator that begins and ends with Estilista's clarity
review, coordinates independent reviews from Riley and Popper, and asks them to
challenge each other when their conclusions conflict. Boulanger reports
unresolved disagreements rather than manufacturing consensus.

## Shared principles

- Agents provide feedback only. They do not change the reviewed artifact.
- Criticism targets the artifact, never its author.
- Feedback should be concrete, justified, and useful to the intended audience.
- Technical reviewers return no more than 10 prioritized feedback points.

## Using an agent

Use the method recommended by your AI agent application for loading, referring
to, or launching an agent. Every application works differently: some may load
the Markdown file as custom instructions, while others may let you refer to the
agent by name in a conversation.

Agent front matter lists runtime dependencies. Load those dependencies using the
application's recommended mechanism. Every current agent depends on the
[`shared reviewer contract`](shared/reviewer-contract.md), which defines the
feedback-only and untrusted-artifact boundaries. Orchestrators also depend on
the reviewers they launch. If an application cannot resolve dependencies or
launch agents, it should report that limitation rather than silently pretend it
did so.

For example, in an application capable of launching agents, a request may be as
simple as:

```text
Ask an Estilista to review this README.
```

In another application, you may need to load the agent file explicitly:

```text
Use agents/popper.md to review the attached API design.

The API exposes account activity to third-party clients. Provide feedback only;
do not change the design.
```

## Agent specifications

Each agent's YAML front matter identifies its role, domain, output limit, and
dependencies. The Markdown body defines its perspective, review method,
response contract, and boundaries.

General reviewers and technical reviewers share the runtime rules in
[`shared/reviewer-contract.md`](shared/reviewer-contract.md). Technical
reviewers additionally use mathematical and category-theoretic reasoning and
return no more than 10 prioritized feedback points.

## Evaluations

The portable, Markdown-based cases in [`evals/`](evals/) test role fidelity,
feedback-only behavior, artifact isolation, evidential discipline, and output
contracts. Run them when changing an agent and record the application, model,
agent version, response, and score. Add a regression case when a real review
reveals a repeated failure mode.

## Status

Lucier Room is an early collection. Agent file structure, shared conventions,
response contracts, and orchestration model may change as the agents are tested
against real artifacts.
