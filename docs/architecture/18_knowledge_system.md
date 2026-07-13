===============================================================================
Knowledge System Architecture
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

The Knowledge System manages
persistent information
that Hermes can reference,
retrieve,
reason over,
and use during execution.

Knowledge is distinct
from conversational memory.

Knowledge represents
information resources,
not experiences.

===============================================================================
Core Philosophy
===============================================================================

Memory remembers.

Knowledge informs.

Hermes should distinguish
between what happened
and what is known.

===============================================================================
Responsibilities
===============================================================================

The Knowledge System is responsible for:

Managing user knowledge

Managing attached files

Managing documents

Managing images

Managing structured data

Providing retrieval

Supporting semantic search

Providing contextual references

Supporting long-term persistence

Knowledge never performs reasoning.

===============================================================================
Knowledge Sources
===============================================================================

Knowledge may originate from:

PDF documents

Word documents

Text files

Markdown

Images

Spreadsheets

Presentations

Source code

Databases

Web pages

APIs

Future data sources

New sources should integrate
without redesigning
the architecture.

===============================================================================
Knowledge Types
===============================================================================

Examples include:

Personal documents

Project documentation

Reference manuals

Research papers

Books

Lecture notes

Source repositories

Knowledge bases

Policies

User-provided datasets

Knowledge remains
source-independent.

===============================================================================
Knowledge Lifecycle
===============================================================================

Import

↓

Parse

↓

Extract

↓

Index

↓

Store

↓

Retrieve

↓

Update

↓

Archive

↓

Delete

Knowledge remains
traceable throughout
its lifecycle.

===============================================================================
Relationship With Memory
===============================================================================

Knowledge and Memory
are separate systems.

Memory stores:

Experiences

Preferences

Conversations

Reflections

Knowledge stores:

Documents

Facts

References

Resources

Structured information

Neither system
owns the other.

===============================================================================
Retrieval
===============================================================================

Knowledge retrieval
may include:

Semantic search

Keyword search

Metadata search

Hybrid retrieval

Graph traversal

Tag filtering

Source filtering

Time filtering

Retrieval strategy
remains configurable.

===============================================================================
Knowledge Context
===============================================================================

Retrieved knowledge
may become
temporary context
for reasoning.

Knowledge should not
automatically enter
working memory.

Only relevant information
should become context.

===============================================================================
Supported File Types
===============================================================================

Hermes should support
extensible parsing.

Examples

PDF

DOCX

TXT

MD

CSV

JSON

XML

YAML

HTML

Images

Audio

Video

Additional formats
may be added
through plugins
or capabilities.

===============================================================================
Knowledge Metadata
===============================================================================

Every knowledge item
should maintain metadata.

Examples

Identifier

Source

Owner

Creation date

Modified date

Tags

Permissions

Content type

Embedding status

Index version

Metadata improves
retrieval quality.

===============================================================================
Knowledge Permissions
===============================================================================

Knowledge access
must respect permissions.

Possible scopes

Current conversation

Current project

Specific agent

Specific Sentinel

Global knowledge

Temporary access

Permission enforcement
remains mandatory.

===============================================================================
Relationship With Planner
===============================================================================

The Planner may request
knowledge retrieval.

The Knowledge System
returns relevant resources.

Planning remains separate
from retrieval.

===============================================================================
Relationship With Reflection
===============================================================================

Reflection may recommend:

Updating knowledge

Removing outdated sources

Improving indexing

Refreshing metadata

Knowledge management
remains independent.

===============================================================================
Future Architecture
===============================================================================

Future versions may support:

Knowledge Graphs

Cross-document reasoning

Automatic document linking

Live knowledge synchronization

Version-aware retrieval

Collaborative knowledge

Distributed knowledge

Federated knowledge

Knowledge inheritance

The external interface
should remain stable.

===============================================================================
Golden Rule
===============================================================================

Knowledge exists
to provide reliable context,
not to replace reasoning.

===============================================================================
Architectural Invariants
===============================================================================

The following principles should remain true unless Hermes undergoes
a deliberate architectural redesign.

• Knowledge remains separate from Memory.

• Knowledge remains provider-independent.

• Retrieval remains configurable.

• Knowledge remains permission-aware.

• Knowledge may support multiple formats.

• Knowledge never performs reasoning.

• Knowledge may become temporary context.

• New knowledge sources should integrate without architectural changes.