# RFC-0003 — Executive

**Status:** Accepted

**Version:** Runtime v1

---

# Summary

The Executive is the entry point of the Hermes Intelligence Runtime.

Its responsibility is to understand the user's intent and transform raw input into a structured execution request.

The Executive never executes work.

It never selects resources.

It never communicates with external systems.

It only understands *what the user wants*.

---

# Responsibilities

The Executive is responsible for:

- Receiving user requests.
- Normalizing input from different interfaces (UI, CLI, API, Voice, etc.).
- Understanding intent.
- Extracting objectives.
- Identifying constraints supplied by the user.
- Producing a structured request for the Reasoner.

The Executive must remain lightweight.

---

# The Executive Owns

The Executive owns only the understanding phase.

It may include:

- Intent analysis
- Goal extraction
- Constraint extraction
- Context collection
- Session references

Nothing more.

---

# The Executive Does NOT Own

The Executive must never own:

- execution
- scheduling
- resource selection
- adapters
- API calls
- memory retrieval
- browser automation
- filesystem operations
- planning
- graph generation

Those belong to other runtime subsystems.

---

# Inputs

Examples:

```
Write a Python script.
```

```
Summarize this PDF.
```

```
Book a flight tomorrow.
```

```
Research quantum computing.
```

---

# Outputs

The Executive produces a structured request.

Example:

```yaml
goal: Write a Python script

constraints:
  - Python

context:
  session: current
```

The exact schema may evolve, but the Executive always outputs structured understanding rather than executable work.

---

# Design Principles

## Stateless

The Executive should avoid long-term state.

Persistent knowledge belongs to Memory (future subsystem).

---

## Vendor Neutral

The Executive must not know:

- Gemini
- Claude
- GPT
- Ollama

It reasons only about intent.

---

## Side-Effect Free

The Executive should never produce side effects.

Running the Executive twice with the same input should produce equivalent understanding.

---

## Small Surface Area

The Executive should expose as few public methods as possible.

Its primary responsibility is transformation, not orchestration.

---

# Relationship to Other Subsystems

```
User

↓

Executive

↓

Reasoner
```

The Executive hands structured understanding to the Reasoner.

Its responsibility ends there.

---

# Future Extensions

The following may extend the Executive without changing its responsibility:

- multimodal input
- voice input
- OCR preprocessing
- gesture input
- biometric input
- BCI input

These are simply additional ways of understanding user intent.

---

# Acceptance

This RFC freezes the responsibility of the Executive for Runtime v1.

Future functionality should extend the Executive only if it contributes directly to understanding user intent.