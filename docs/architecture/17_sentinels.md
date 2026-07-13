===============================================================================
Sentinel Architecture
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

Sentinels are persistent background agents
that monitor conditions,
observe events,
and initiate execution
when predefined criteria are satisfied.

Unlike normal agents,
Sentinels do not wait
for direct user requests.

They work continuously
on behalf of the user.

===============================================================================
Core Philosophy
===============================================================================

An assistant responds.

A Sentinel watches.

Hermes should assist
even when the user
is not actively chatting.

===============================================================================
Responsibilities
===============================================================================

Sentinels are responsible for:

Monitoring events

Checking scheduled conditions

Watching resources

Observing external changes

Triggering workflows

Starting loops

Sending notifications

Requesting user approval

Sentinels never bypass Safety.

===============================================================================
Position In Runtime
===============================================================================

External Event

OR

Scheduled Check

↓

Sentinel

↓

Planner

↓

Safety

↓

Execution

↓

Observation

↓

Reflection

↓

Sleep

===============================================================================
Sentinel Lifecycle
===============================================================================

Every Sentinel follows
a predictable lifecycle.

Created

↓

Registered

↓

Sleeping

↓

Wake

↓

Evaluate Condition

↓

Condition Met?

↓

Yes

↓

Trigger Workflow

↓

Observe

↓

Sleep

OR

No

↓

Sleep

===============================================================================
Trigger Types
===============================================================================

A Sentinel may wake because of:

Scheduled time

System event

Memory condition

External webhook

File change

API event

User location

Battery level

Calendar event

Network availability

Custom triggers

New trigger types
may be added
without changing
the Sentinel architecture.

===============================================================================
Supported Examples
===============================================================================

Monitor stock prices

Watch package delivery

Check examination dates

Observe weather alerts

Track project deadlines

Monitor API health

Watch websites

Check email

Observe file changes

Follow news topics

Monitor server uptime

Observe IoT devices

These are examples only.

===============================================================================
Relationship With Loops
===============================================================================

Sentinels do not perform
long-running execution.

Instead,
they trigger Loops.

Sentinel

↓

Loop

↓

Execution

↓

Completion

The responsibilities
remain separated.

===============================================================================
Relationship With Planner
===============================================================================

A Sentinel
does not create plans.

It provides context.

The Planner decides
how the task
should be executed.

===============================================================================
Relationship With Memory
===============================================================================

Sentinels may use:

Working Memory

Long-Term Memory

Knowledge Memory

Reflection Memory

Preference Memory

Sentinels may update memory
only after successful execution.

===============================================================================
Relationship With Safety
===============================================================================

Every Sentinel action
passes through Safety.

Safety remains mandatory.

Background execution
never bypasses authorization.

===============================================================================
Notifications
===============================================================================

A Sentinel may notify
the user.

Examples

Reminder

Progress update

Price alert

Deadline warning

Health notification

System status

Notifications should remain
useful rather than intrusive.

===============================================================================
Execution Frequency
===============================================================================

Sentinels should support
flexible schedules.

Examples

Every minute

Every hour

Daily

Weekly

Monthly

Cron schedules

Event-driven

Adaptive schedules

The scheduling mechanism
remains implementation-independent.

===============================================================================
Resource Management
===============================================================================

Sentinels should minimize
resource usage.

Examples

Sleep when idle

Wake only when necessary

Avoid duplicate work

Cache previous results

Respect rate limits

Use lightweight providers
whenever practical.

===============================================================================
Failure Handling
===============================================================================

Sentinel failures
should remain isolated.

Possible actions

Retry

Delay

Fallback provider

Notify user

Pause Sentinel

Disable Sentinel

Failure should not affect
other Sentinels.

===============================================================================
Future Architecture
===============================================================================

Future versions may support:

Collaborative Sentinels

Distributed Sentinels

Multi-device Sentinels

Predictive Sentinels

Learning Sentinels

Autonomous Sentinels

Physical-device Sentinels

Multi-agent Sentinels

The Sentinel interface
should remain stable.

===============================================================================
Golden Rule
===============================================================================

Sentinels observe.

They do not control.

Execution belongs
to the Runtime.

===============================================================================
Architectural Invariants
===============================================================================

The following principles should remain true unless Hermes undergoes
a deliberate architectural redesign.

• Sentinels monitor conditions.

• Sentinels trigger workflows.

• Sentinels never bypass Safety.

• Sentinels remain lightweight.

• Sentinels remain interruptible.

• Sentinels respect user permissions.

• Sentinels may remain persistent.

• Sentinels remain provider-independent.