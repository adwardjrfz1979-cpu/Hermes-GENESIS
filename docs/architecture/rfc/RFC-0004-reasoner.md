# RFC-0004 — Reasoner

**Status:** Accepted

**Version:** Runtime v1

---

# Summary

The Reasoner is the cognitive engine of the Hermes Intelligence Runtime.

It transforms structured intent into an executable Execution Graph.

The Reasoner answers one question:

> **"What work must be performed to satisfy the user's intent?"**

The Reasoner never executes work.

The Reasoner never selects resources.

The Reasoner never communicates with external systems.

It only reasons.

---

# Responsibilities

The Reasoner is responsible for:

- Transforming intent into executable work.
- Decomposing complex goals.
- Identifying required capabilities.
- Building the Execution Graph.
- Defining dependencies between nodes.
- Creating reasoning strategies.

---

# The Reasoner Owns

The Reasoner owns:

- execution graph construction
- task decomposition
- dependency analysis
- reasoning strategies
- graph optimization
- capability requirements

Nothing else.

---

# The Reasoner Does NOT Own

The Reasoner must never own:

- scheduling
- resource selection
- adapters
- API calls
- browser automation
- filesystem execution
- network communication
- vendor selection

Those responsibilities belong to later runtime stages.

---

# Inputs

The Reasoner receives structured understanding from the Executive.

Example:

```yaml
goal:
  Create a business presentation.

constraints:
  deadline: tomorrow
```

---

# Outputs

The Reasoner produces an Execution Graph.

Example:

```text
Research
    │
    ▼
Summarize
    │
    ▼
Create Slides
    │
    ▼
Review
```

The graph is executable.

It contains nodes, dependencies, and required capabilities.

---

# Execution Graph

The graph is a Directed Acyclic Graph (DAG).

Each node represents one unit of work.

Nodes may execute:

- sequentially
- independently
- in parallel

Future runtime versions may support dynamic graph expansion while preserving DAG guarantees.

---

# Design Principles

## Capability Driven

The Reasoner reasons about capabilities.

Example:

```
Need:

Search
```

Not:

```
Need:

Gemini
```

---

## Vendor Neutral

The Reasoner never knows:

- model names
- providers
- API endpoints
- credentials

These are implementation details handled later.

---

## Pure Reasoning

Running the Reasoner twice with the same input should produce equivalent execution graphs.

The Reasoner should avoid side effects.

---

## Explainability

Every node should exist for a reason.

Future runtime versions should allow inspection of why nodes were generated.

Reasoning should be transparent rather than opaque.

---

## Extensibility

Future reasoning modules may include:

- Reflection
- Memory Retrieval
- Trust Evaluation
- Self-Correction
- Multi-Agent Planning
- Scientific Reasoning
- Mathematical Proof Systems

These modules extend the Reasoner rather than replacing it.

---

# Relationship to Other Subsystems

```
Executive

↓

Reasoner

↓

Execution Graph

↓

Scheduler
```

The Reasoner hands a completed Execution Graph to the Scheduler.

Its responsibility ends there.

---

# Long-Term Vision

The Reasoner is expected to become the primary location for intelligence evolution inside Hermes.

Future advances in reasoning should strengthen this subsystem while preserving the same interface to the rest of the runtime.

The Scheduler should never need to know how the graph was produced.

---

# Acceptance

This RFC freezes the Reasoner's responsibility for Runtime v1.

The Reasoner owns intelligence.

Execution belongs elsewhere.