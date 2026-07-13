===============================================================================
Planner Architecture
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

The Planner is responsible for deciding how Hermes should solve a task.

It determines what information is required,
what capabilities should be used,
which providers should execute them,
and whether reasoning, tools, or autonomous execution are necessary.

The Planner never executes tasks.

It only creates execution plans.

===============================================================================
Core Philosophy
===============================================================================

The Planner exists to make good decisions before expensive decisions.

Thinking should always be cheaper than execution.

===============================================================================
Responsibilities
===============================================================================

The Planner is responsible for:

Understanding user intent

Estimating task complexity

Selecting required capabilities

Determining whether tools are necessary

Requesting context

Choosing execution strategy

Requesting human approval when required

Preparing execution plans

The Planner never performs execution itself.

===============================================================================
Planner Position
===============================================================================

User

↓

Runtime

↓

Planner

↓

Context Builder

↓

Router

↓

Execution

↓

Response

The Planner is the decision-making layer
between Runtime and Execution.

===============================================================================
Planning Process
===============================================================================

Receive Request

↓

Understand Intent

↓

Estimate Complexity

↓

Determine Required Context

↓

Select Required Capabilities

↓

Choose Execution Strategy

↓

Create Execution Plan

↓

Send Plan to Runtime

===============================================================================
Intent Understanding
===============================================================================

The Planner first determines what the user is asking.

Examples include:

Conversation

Question Answering

Research

Summarization

Coding

Vision

Automation

Reasoning

Agent Task

File Analysis

Planning

Future capabilities

Intent determines the overall execution strategy.

===============================================================================
Complexity Estimation
===============================================================================

Every task is assigned a complexity level.

Examples

Simple

Moderate

Complex

Autonomous

Complexity influences:

Model selection

Reasoning depth

Tool usage

Reflection level

Execution budget

===============================================================================
Capability Selection
===============================================================================

The Planner determines which capabilities are required.

Examples

Memory

Knowledge

Search

Calculator

Filesystem

Browser

Vision

Speech

Automation

MCP

Future capabilities

Capabilities are requested only when necessary.

===============================================================================
Execution Strategy
===============================================================================

The Planner selects an execution strategy.

Examples

Direct Response

Single Tool

Multiple Tools

Reasoning Model

Local Model

Cloud Model

Hybrid Execution

Agent Loop

Human Approval

The simplest valid strategy should always be preferred.

===============================================================================
Reasoning Policy
===============================================================================

Reasoning should only be used when it improves outcomes.

Simple requests should not invoke expensive reasoning.

Example

2 + 2

↓

Direct Answer

Complex software architecture

↓

Reasoning

The Planner optimizes for both quality and efficiency.

===============================================================================
Memory Requests
===============================================================================

The Planner determines whether memory is required.

Question

↓

Need Memory?

↓

No

↓

Continue

OR

↓

Request Relevant Memory

The Planner never retrieves memory directly.

===============================================================================
Knowledge Requests
===============================================================================

The Planner determines whether external knowledge is required.

Examples

Attached PDFs

Research papers

Documentation

Books

Knowledge retrieval is delegated
to the Context Builder.

===============================================================================
Tool Requests
===============================================================================

Tools should be requested only when necessary.

Examples

Calculator

Search

Filesystem

Browser

Automation

Image Generation

Speech

Future tools

Unnecessary tool usage should be avoided.

===============================================================================
Human Approval
===============================================================================

Certain plans require user confirmation.

Examples

Deleting files

Sending emails

Financial actions

Desktop automation

Robot movement

Security-sensitive operations

Approval requirements are delegated
to the Safety subsystem.

===============================================================================
Execution Plans
===============================================================================

The Planner produces structured execution plans.

Example

Need Search

Need Memory

Need Reflection

Use Local Model

Fallback to Cloud

Reflection Level 1

Return Response

Execution plans remain independent
from implementation details.

===============================================================================
Planner Constraints
===============================================================================

The Planner must never:

Execute tools

Call providers directly

Retrieve memory

Modify knowledge

Store memory

Perform reflection

Generate responses

Its responsibility is planning only.

===============================================================================
Future Planning
===============================================================================

Future versions may support:

Hierarchical Planning

Multi-Agent Planning

Recursive Planning

Task Decomposition

Dynamic Replanning

Collaborative Planning

Goal-Oriented Planning

Long-Horizon Planning

These extensions should preserve
the Planner's existing interface.

===============================================================================
Golden Rule
===============================================================================

The Planner decides how Hermes should solve a problem.

It never solves the problem itself.

===============================================================================
Architectural Invariants
===============================================================================

The following principles should remain true unless Hermes undergoes
a deliberate architectural redesign.

• The Planner never executes tasks.

• The Planner creates execution plans.

• Planning remains capability-driven.

• Tool usage is intentional.

• Memory requests remain intentional.

• Simpler execution strategies are preferred.

• Execution remains separate from planning.

• The Planner remains independent from providers.