===============================================================================
Project Structure
===============================================================================

Version:
    1.0

Status:
    Stable

-------------------------------------------------------------------------------
Purpose
-------------------------------------------------------------------------------

The Hermes project is organized around responsibilities rather than features.

Each directory has a single primary purpose.

As Hermes grows, new capabilities should integrate into the existing structure
instead of creating parallel architectures.

A folder should exist because it represents a long-term architectural concept,
not because a feature temporarily needs a place to live.

-------------------------------------------------------------------------------
Design Goals
-------------------------------------------------------------------------------

The project structure should provide:

• Clear ownership

• Low coupling

• High cohesion

• Replaceable implementations

• Easy discoverability

• Long-term scalability

-------------------------------------------------------------------------------
Top-Level Layout
-------------------------------------------------------------------------------

The repository is divided into several major areas.

Source Code

    hermes/

Contains the runtime implementation.

This directory represents the intelligence runtime itself.

-------------------------------------------------------------------------------

Documentation

    docs/

Contains architectural specifications.

Documentation describes how Hermes should behave.

The implementation should follow the documentation.

-------------------------------------------------------------------------------

Tests

    tests/

Contains automated validation.

Every major subsystem should have corresponding tests.

-------------------------------------------------------------------------------

Configuration

    configs/

Contains user-editable configuration files.

Configuration belongs here instead of source code whenever practical.

-------------------------------------------------------------------------------

Data

    data/

Persistent runtime data.

Examples include:

• embeddings

• indexes

• cached files

• downloaded assets

-------------------------------------------------------------------------------

Logs

    logs/

Runtime logs.

No subsystem should write logs outside this directory.

-------------------------------------------------------------------------------

Resources

    resources/

Static assets required by Hermes.

These may include:

• prompts

• templates

• personalities

• icons

• localization

-------------------------------------------------------------------------------
Source Structure
-------------------------------------------------------------------------------

The hermes package is divided by responsibility.

Example:

hermes/

    ai/
        Intelligence providers.

    capabilities/
        Search
        Vision
        Browser
        Memory
        Calculator
        ...

    config/
        Runtime configuration.

    conversation/
        Conversation state.

    core/
        Shared abstractions.

    kernel/
        Runtime pipeline.

    llm/
        Model adapters.

    memory/
        Memory subsystem.

    network/
        HTTP clients.

    plugins/
        Extension system.

    providers/
        External integrations.

    runtime/
        Application lifecycle.

    services/
        Shared services.

    ui/
        User interfaces.

    utils/
        Helper utilities.

-------------------------------------------------------------------------------
Folder Rules
-------------------------------------------------------------------------------

Every folder should answer one question.

Examples

memory/

    Stores and retrieves information.

network/

    Handles network communication.

providers/

    Connects external services.

ui/

    Displays information.

If a folder cannot be described in one sentence,
its responsibility is probably too broad.

-------------------------------------------------------------------------------
Dependency Direction
-------------------------------------------------------------------------------

Dependencies should generally flow downward.

UI

↓

Kernel

↓

Capabilities

↓

Providers

↓

Infrastructure

Never the opposite.

Lower layers must not depend on higher layers.

-------------------------------------------------------------------------------
Future Growth
-------------------------------------------------------------------------------

New features should be added by extending existing responsibilities.

Avoid creating folders for individual features when an existing subsystem
already owns that responsibility.

Hermes should grow horizontally through capabilities rather than vertically
through duplicated architecture.

-------------------------------------------------------------------------------
Summary
-------------------------------------------------------------------------------

The directory structure is part of the architecture.

It should remain understandable years into the project's evolution.

Folders should represent stable concepts rather than temporary implementation
details.

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