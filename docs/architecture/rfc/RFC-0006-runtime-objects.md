# RFC-0006 — Runtime Objects

**Status:** Accepted

**Version:** Runtime v1

---

# Summary

Hermes is a **data-driven Intelligence Runtime**.

Everything that users, administrators, or future automation should configure must exist as a **Runtime Object**, not as hardcoded program logic.

The Runtime executes objects.

The UI edits objects.

The code defines behavior.

---

# Motivation

Traditional software often requires code changes to add new integrations or modify behavior.

Hermes aims to eliminate unnecessary code changes by representing configurable concepts as structured runtime objects.

Examples include:

- Resources
- Models
- Pipelines
- Policies
- Themes
- Trust Profiles
- Memory Stores
- User Profiles

The runtime loads these objects and executes them without requiring source code modifications.

---

# Core Principle

Behavior belongs in code.

Configuration belongs in Runtime Objects.

Never confuse the two.

---

# Runtime Object Definition

A Runtime Object is a structured configuration entity loaded by the runtime.

Every Runtime Object must:

- possess a unique identity
- be serializable
- be editable
- be validated
- be observable
- support future versioning

---

# Examples

## Resource

```yaml
id: resource-gemini-personal

name: Gemini Personal

adapter: openai-compatible

capabilities:
  - chat

priority: 1

enabled: true
```

---

## Trust Policy

```yaml
id: trust-default

max_risk: medium

allow_external_execution: false
```

---

## Theme

```yaml
id: midnight

accent: purple

mode: dark
```

---

# Runtime Responsibilities

The Runtime is responsible for:

- loading Runtime Objects
- validating Runtime Objects
- indexing Runtime Objects
- exposing Runtime Objects to runtime subsystems
- saving Runtime Object changes

---

# UI Responsibilities

The UI never edits source code.

The UI edits Runtime Objects.

Example:

```
Add Resource

↓

Fill Form

↓

Save

↓

Runtime Reloads Object
```

The Runtime immediately recognizes the new object.

---

# Code Responsibilities

Code defines:

- algorithms
- execution behavior
- lifecycle
- validation rules

Code should not contain user-specific configuration.

---

# Runtime Object Lifecycle

```
Create

↓

Validate

↓

Store

↓

Load

↓

Execute

↓

Observe

↓

Modify

↓

Persist
```

---

# Design Principles

## Data Driven

Configuration should exist as data rather than source code whenever practical.

---

## Human Editable

Objects should remain understandable to both users and developers.

---

## Machine Editable

Future versions of Hermes may create or modify Runtime Objects automatically.

---

## Versionable

Runtime Objects should support schema evolution over time.

---

## Portable

Users should be able to export and import Runtime Objects between Hermes installations.

---

# Future Runtime Objects

Examples include:

- Resources
- Models
- Capabilities
- Memory Providers
- Trust Policies
- Pipelines
- Agent Profiles
- Automation Rules
- User Preferences
- UI Layouts
- Keyboard Shortcuts
- Voice Profiles
- Security Policies

Additional Runtime Objects may be introduced without changing runtime architecture.

---

# Relationship to the Runtime

```
Hermes UI

↓

Runtime Objects

↓

Hermes Runtime

↓

Execution
```

The Runtime executes object behavior.

The UI manages object configuration.

---

# Acceptance

This RFC establishes Runtime Objects as the primary mechanism for configurable behavior within Hermes Runtime v1.

Future features that users should configure through the UI should, whenever practical, be represented as Runtime Objects rather than hardcoded source code.