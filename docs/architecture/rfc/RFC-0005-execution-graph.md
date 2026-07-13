# RFC-0005 — Execution Graph

**Status:** Accepted

**Version:** Runtime v1

---

# Summary

The Execution Graph is the executable representation of intelligence inside the Hermes Runtime.

It is produced by the Reasoner.

It is consumed by the Scheduler.

The graph represents work as connected nodes with explicit dependencies.

The Execution Graph is the central data structure of the runtime.

---

# Purpose

The graph answers one question:

> **"What work must happen, and in what order?"**

The graph contains no knowledge of:

- vendors
- APIs
- resources
- adapters
- operating systems

It only represents work.

---

# Graph Properties

The Execution Graph is a Directed Acyclic Graph (DAG).

Properties:

- deterministic
- inspectable
- serializable
- restartable
- parallelizable
- observable

---

# Node

A node represents one unit of reasoning or execution.

Examples:

- Chat
- Search
- Browser
- Read File
- Generate Image
- Python
- Calendar
- Decision
- Merge
- Reflection

Future runtime versions may introduce additional node types without changing graph semantics.

---

# Edges

Edges represent dependencies.

Example:

Research

↓

Summarize

↓

Presentation

Summarize cannot begin until Research completes.

---

# Parallel Execution

Independent branches may execute simultaneously.

Example:

          Research

        /          \

 Finance          Marketing

        \          /

      Presentation

The Scheduler determines actual execution order.

The graph only expresses dependencies.

---

# Graph Ownership

The Execution Graph owns:

- nodes
- edges
- dependency relationships
- execution state

The graph does not own:

- scheduling
- resource selection
- adapters
- external communication

---

# Immutability

Once accepted by the Scheduler, the graph should remain stable.

Future runtime versions may support controlled graph expansion through specialized graph transformations.

---

# Observability

Every node transition should emit runtime events.

Typical transitions include:

- Pending
- Ready
- Running
- Completed
- Failed

Future node states may be added without changing graph semantics.

---

# Design Principles

## Minimal

The graph should remain structurally simple.

Complex reasoning belongs in the Reasoner.

---

## Vendor Neutral

Nodes express capabilities.

Never providers.

---

## Restartable

Execution should resume from completed nodes whenever possible.

---

## Inspectable

Users and developers should be able to visualize the graph.

The graph should become a first-class debugging tool.

---

# Relationship to Other Subsystems

Executive

↓

Reasoner

↓

Execution Graph

↓

Scheduler

The graph is the contract between reasoning and execution.

---

# Long-Term Vision

Future versions of Hermes may support:

- distributed execution
- live graph editing
- graph optimization
- graph caching
- reflection nodes
- memory nodes
- trust nodes
- robotic control graphs

These extensions should preserve the graph abstraction.

---

# Acceptance

This RFC freezes the Execution Graph as the central execution model of Hermes Runtime v1.

Every executable workflow inside Hermes should ultimately become an Execution Graph.