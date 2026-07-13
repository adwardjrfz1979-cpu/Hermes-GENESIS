===============================================================================
Router Architecture
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

The Router is responsible for selecting the best execution path for every
request.

It does not answer questions.

It does not perform reasoning.

It decides where work should happen.

===============================================================================
Core Philosophy
===============================================================================

Routing is a resource allocation problem.

Not an intelligence problem.

The Router should make decisions using measurable system information,
never subjective reasoning.

===============================================================================
Responsibilities
===============================================================================

The Router decides:

• which execution mode

• which capability

• which provider

• which model

• local vs cloud

• fallback order

• retry policy

• execution priority

The Router never changes the user's request.

===============================================================================
Routing Inputs
===============================================================================

The Router receives:

Intent

Execution Plan

Context Size

Privacy Level

Capabilities Required

Available Providers

Available Local Models

Rate Limit Status

Quota Status

Latency Statistics

Health Statistics

User Preferences

===============================================================================
Routing Outputs
===============================================================================

The Router produces an Execution Plan.

Example

Execution Mode

↓

Capability

↓

Provider

↓

Model

↓

Fallback Chain

↓

Execution Constraints

===============================================================================
Routing Decision Factors
===============================================================================

The Router evaluates:

Provider availability

Model availability

Current latency

Failure history

API quota

Rate limits

Estimated cost

Expected response quality

Privacy requirements

Required modalities

GPU availability

CPU availability

Memory pressure

===============================================================================
Execution Modes
===============================================================================

Examples

Conversation

Reasoning

Vision

Search

Automation

Agent

Loop

MCP

A2A

Background Task

Computer Control

Future execution modes should integrate without modifying the Router.

===============================================================================
Provider Selection
===============================================================================

Providers compete on objective metrics.

The Router may prefer:

Lower latency

Higher reliability

Lower cost

Local execution

Higher capability

User preference

Provider priority

No provider is permanently preferred.

===============================================================================
Model Selection
===============================================================================

Model selection is independent of provider.

Examples

Tiny Local

↓

Qwen 1.5B

Reasoning

↓

Qwen 7B

Cloud

↓

GLM 4.7 Flash

Vision

↓

GLM Vision

Future models register themselves.

===============================================================================
Fallback Strategy
===============================================================================

Failure should not terminate execution immediately.

Possible fallback chain

Local

↓

Secondary Local

↓

Cloud

↓

Secondary Cloud

↓

Final Emergency Model

Fallback decisions are automatic.

===============================================================================
Health Monitoring
===============================================================================

Every provider has a health score.

Metrics include:

Recent failures

Average latency

Timeout rate

429 responses

Availability

Health scores continuously update.

===============================================================================
Adaptive Routing
===============================================================================

Routing should improve over time.

Examples

Repeated provider failures

↓

Temporary deprioritization

Fast provider

↓

Higher priority

High error rate

↓

Cooldown period

The Router adapts without changing architecture.

===============================================================================
Privacy Routing
===============================================================================

Sensitive requests should prefer:

Local models

Offline capabilities

Encrypted storage

Cloud routing should occur only when necessary.

===============================================================================
Quota Awareness
===============================================================================

The Router tracks:

Daily quotas

Minute quotas

Concurrent requests

Budget limits

Provider-specific restrictions

Quota exhaustion triggers fallback.

===============================================================================
Capability Awareness
===============================================================================

Some capabilities require specific providers.

Examples

Vision

Speech

Browser

Embeddings

The Router understands these constraints.

===============================================================================
Future Routing
===============================================================================

The Router must support:

World Models

Agent Swarms

MCP Servers

A2A Networks

Distributed Inference

Edge Devices

Robots

BCI

without architectural redesign.

===============================================================================
Golden Rule
===============================================================================

The Router should always select
the simplest,
fastest,
most reliable,
and least expensive path
that still satisfies the user's request.

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