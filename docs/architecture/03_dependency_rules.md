===============================================================================
Dependency Rules
===============================================================================

Version:
    1.0

Status:
    Stable

Author:
    Aryan + ChatGPT

Last Updated:
    July 2026

===============================================================================
Purpose
===============================================================================

Hermes is designed as a layered architecture.

Every layer has a clearly defined responsibility.

Dependencies must always flow in one direction.

Violating these rules increases coupling, introduces circular imports,
reduces maintainability, and makes future replacement of components
significantly harder.

These rules are mandatory for every subsystem.

===============================================================================
Design Goals
===============================================================================

The dependency architecture exists to provide:

• Replaceable components

• Stable interfaces

• Low coupling

• High cohesion

• Predictable data flow

• Easy testing

• Independent evolution

===============================================================================
Dependency Principle
===============================================================================

Dependencies always point downward.

Higher layers may depend on lower layers.

Lower layers must never depend on higher layers.

Correct:

UI
↓

Kernel
↓

Capabilities
↓

Providers
↓

Infrastructure

Incorrect:

Provider
↓

Capability

or

Memory
↓

UI

===============================================================================
Layer Definitions
===============================================================================

Layer 1

User Interfaces

Examples

• Desktop UI

• Telegram

• Discord

• CLI

• REST API

Responsibilities

Receive user requests.

Display responses.

Collect user interaction.

Never perform reasoning.

-------------------------------------------------------------------------------

Layer 2

Kernel

Responsibilities

Coordinate the complete request lifecycle.

Select workflows.

Manage execution.

Handle orchestration.

The kernel is the conductor of Hermes.

-------------------------------------------------------------------------------

Layer 3

Intelligence

Examples

Planner

Router

Reasoner

Reflection

Observation

Memory Decision

Responsibilities

Decide how Hermes should solve a task.

No external APIs belong here.

-------------------------------------------------------------------------------

Layer 4

Capabilities

Examples

Search

Vision

Browser

Calculator

Memory

Filesystem

Weather

GitHub

Responsibilities

Perform a single capability.

Capabilities should remain independent.

Capabilities should not know about each other.

-------------------------------------------------------------------------------

Layer 5

Providers

Examples

OpenAI

Anthropic

Gemini

Groq

GLM

Ollama

Tavily

NewsAPI

Weather API

Responsibilities

Translate Hermes requests into provider-specific requests.

Providers contain implementation details.

-------------------------------------------------------------------------------

Layer 6

Infrastructure

Examples

HTTP Client

Logger

Configuration

Cache

Utilities

Database

Responsibilities

Provide reusable building blocks.

Contain no business logic.

===============================================================================
Allowed Dependencies
===============================================================================

User Interface

↓

Kernel

↓

Planning

↓

Capabilities

↓

Providers

↓

Infrastructure

Every dependency should follow this direction.

===============================================================================
Forbidden Dependencies
===============================================================================

Providers importing UI.

Capabilities importing Telegram.

Memory importing Desktop UI.

Router importing OpenAI directly.

Planner importing HTTP libraries.

Reflection importing Discord.

Infrastructure importing Providers.

Anything that violates the layer order.

===============================================================================
Interface Rule
===============================================================================

Every subsystem should expose an interface.

The implementation behind that interface should remain replaceable.

Example

Search Capability

↓

Search Interface

↓

Tavily Provider

↓

Future Provider

The capability should never care which provider is active.

===============================================================================
Capability Independence
===============================================================================

Capabilities should not communicate directly.

Incorrect

Vision

↓

Search

Correct

Vision

↓

Kernel

↓

Search

The Kernel coordinates capabilities.

Capabilities execute work.

===============================================================================
Provider Independence
===============================================================================

Providers should never know each other.

Incorrect

OpenAI

↓

Groq

Correct

Router

↓

OpenAI

or

↓

Groq

The Router selects providers.

Providers never select themselves.

===============================================================================
Configuration Rule
===============================================================================

Configuration belongs outside business logic.

Changing:

API Keys

Priorities

Timeouts

Rate Limits

Fallback Order

Preferred Models

should never require modifying implementation code.

===============================================================================
Model Independence
===============================================================================

Hermes must never depend on a particular model.

Examples

GLM

Gemini

OpenAI

Claude

Qwen

Phi

Llama

Ollama

must all be replaceable.

Models are plugins.

Architecture is permanent.

===============================================================================
Protocol Independence
===============================================================================

Protocols evolve.

Hermes should support protocols through adapters.

Examples

MCP

A2A

Future Standards

These should integrate without changing core architecture.

===============================================================================
Testing Rule
===============================================================================

Every subsystem should be testable independently.

Providers should be mockable.

Capabilities should be isolated.

Kernel workflows should be reproducible.

Business logic should not require internet access.

===============================================================================
Future Growth
===============================================================================

As Hermes grows, new features should integrate into existing layers.

Do not introduce new architectural layers unless they represent a genuinely
new responsibility.

Growth should happen through extension, not duplication.

===============================================================================
Golden Rule
===============================================================================

Architecture is more important than implementation.

Implementation changes frequently.

Architecture should survive years of technological change.

When in doubt:

Protect the architecture.

===============================================================================
Architectural Invariants
===============================================================================

The following must remain true unless Hermes undergoes a major architectural
revision.

• Capabilities remain independent.

• Capabilities never import each other directly.

• The Runtime coordinates execution.

• Capabilities expose stable interfaces.

• Adding a capability must not require Runtime modification.

• Configuration should remain external.

• Capabilities should remain individually testable.