===============================================================================
Context Builder Architecture
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

The Context Builder is responsible for constructing the complete context
required by the model.

It gathers information requested by the Planner,
organizes it,
removes unnecessary information,
and produces an optimized context package.

The Context Builder never makes planning decisions.

The Context Builder never executes tools.

===============================================================================
Core Philosophy
===============================================================================

A model should receive only the context it needs.

Every unnecessary token reduces efficiency.

Context quality is more important than context quantity.

===============================================================================
Responsibilities
===============================================================================

The Context Builder is responsible for:

Collecting conversation context

Collecting relevant memory

Collecting relevant knowledge

Collecting current runtime state

Collecting system instructions

Collecting attached files

Removing irrelevant information

Ordering context by importance

Constructing the final context package

===============================================================================
Position In Runtime
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

Provider

↓

Model

The Context Builder bridges planning and execution.

===============================================================================
Context Sources
===============================================================================

The Context Builder may receive information from:

Conversation Context

Session Memory

Temporary Memory

Project Memory

Long-Term Memory

Knowledge Store

Runtime State

System Prompt

Attached Files

Capability Results

Future sources

The Planner determines which sources are required.

===============================================================================
Conversation Context
===============================================================================

Conversation context contains the current discussion.

Recent messages receive higher priority.

Older conversation may be summarized
to preserve context space.

===============================================================================
Memory Retrieval
===============================================================================

Memory is retrieved only when requested
by the Planner.

Only relevant memories should be included.

Memory retrieval should minimize noise.

===============================================================================
Knowledge Retrieval
===============================================================================

Knowledge is retrieved independently
from memory.

Examples include:

PDFs

Books

Research papers

Documentation

Images

Codebases

Knowledge should be chunked
before inclusion.

===============================================================================
Runtime State
===============================================================================

Runtime state represents the current environment.

Examples

Loaded model

Available providers

Running agents

Open browser

Desktop state

Robot state

Current task

State should only be included
when relevant.

===============================================================================
Attached Files
===============================================================================

Files supplied by the user become temporary knowledge.

Examples

PDF

Image

Spreadsheet

Presentation

Code

Video

Files remain isolated
unless explicitly stored
in the Knowledge Store.

===============================================================================
System Instructions
===============================================================================

The Context Builder attaches
runtime instructions.

Examples

System Prompt

Personality

Safety Policies

Capability Constraints

Execution Budget

These instructions remain hidden
from the user.

===============================================================================
Context Prioritization
===============================================================================

Not all context has equal importance.

Suggested priority:

System Instructions

↓

Current User Request

↓

Conversation Context

↓

Relevant Memory

↓

Relevant Knowledge

↓

Runtime State

↓

Capability Results

↓

Additional Metadata

Priority should remain configurable.

===============================================================================
Context Optimization
===============================================================================

The Context Builder should reduce
unnecessary context.

Possible techniques include:

Deduplication

Summarization

Chunk selection

Compression

Relevance filtering

Context should remain as small
as possible while preserving quality.

===============================================================================
Context Package
===============================================================================

The Context Builder produces
a structured context package.

Example

System Instructions

Conversation

Relevant Memory

Knowledge Chunks

Runtime State

Capability Results

User Request

This package is sent
to the selected provider.

===============================================================================
Context Constraints
===============================================================================

The Context Builder must never:

Plan execution

Call providers

Execute tools

Modify memory

Modify knowledge

Generate responses

Perform reasoning

Its responsibility is context construction only.

===============================================================================
Future Architecture
===============================================================================

Future versions may include:

Adaptive Context Windows

Semantic Compression

Graph Context

Hierarchical Context

Cross-Agent Shared Context

Cross-Device Context

Dynamic Context Streaming

Context Versioning

These additions should preserve
the Context Builder interface.

===============================================================================
Golden Rule
===============================================================================

The quality of a model's reasoning
depends on the quality of its context.

The Context Builder exists
to maximize that quality.

===============================================================================
Architectural Invariants
===============================================================================

The following principles should remain true unless Hermes undergoes
a deliberate architectural redesign.

• The Context Builder never performs planning.

• The Context Builder never executes tasks.

• Context remains intentionally constructed.

• Only relevant information is included.

• Knowledge and memory remain separate.

• Context optimization is always preferred.

• Context construction remains provider-independent.