# Ticket Creation Guidelines

## Purpose

This document defines the workflow, guardrails, and quality standards for creating Jira tickets.

The goal is to ensure tickets are:

- Created only with explicit user approval.
- Placed in the correct project, board, epic, or parent item.
- Generated using project-specific requirements and conventions.
- Consistent, actionable, and easy to review.
- Sufficiently detailed for implementation, investigation, or planning.
- Focused on mandatory information first.

---

## Core Rule

The agent's role is to assist with ticket creation, not to make project decisions on behalf of the user.

The agent may:

- Recommend
- Explain
- Suggest
- Validate

The agent must not:

- Assume project structure
- Assume ticket placement
- Assume ticket type
- Generate tickets without approval
- Make project decisions on behalf of the user

Final decisions always remain with the user.

---

## Scope

These guidelines apply to all ticket types including:

- Story
- Task
- Bug
- Spike
- Epic
- Sub-task

Ticket-specific rules supplement the general workflow defined in this document.

---

## Documentation Priority

Before asking questions, review available project documentation.

Examples:

- SUMMARIZED.md
- README.md
- CONTRIBUTING.md
- TICKET_CREATION.md
- Project-specific documentation

The agent should gather available context before requesting clarification.

Do not ask the user for information that can be derived from documentation.

---

# Workflow

## 1. Creation Authorization

The agent must never create a ticket automatically.

Creating a ticket requires explicit user approval.

Valid authorization examples:

- Create the ticket
- Generate the story
- Proceed
- Go ahead

Not considered authorization:

- I think we need a ticket
- Should this be a story?
- Help me write a ticket
- Can you suggest a ticket?

Until explicit approval is received, remain in discovery mode.

---

## 2. Phase 1 - Ticket Placement Discovery

### Objective

Determine where the ticket belongs and what type of ticket should be created.

Before discussing ticket content determine:

### Destination

Examples:

- Jira Project
- Board
- Team
- Epic
- Parent Ticket

### Ticket Type

Examples:

- Story
- Task
- Bug
- Spike
- Epic
- Sub-task

The agent should:

1. Review available project documentation.
2. Identify valid destinations.
3. Identify valid ticket types.
4. Provide recommendations.
5. Ask the user to choose.

If multiple valid options exist provide:

- Recommendation
- Alternative options
- Reasoning

The final selection must always be made by the user.

Do not proceed until both destination and ticket type are confirmed.

---

## 3. Phase 2 - Mandatory Field Discovery

### Objective

Determine which fields are required for the selected ticket type and destination.

The agent should:

1. Review project documentation.
2. Review ticket requirements.
3. Identify mandatory fields.
4. Identify optional fields.

Examples:

Mandatory:

- Summary
- Description
- Acceptance Criteria

Optional:

- Story Points
- Labels
- Sprint
- Components

Do not assume required fields.

Discover them whenever possible.

---

## 4. Mandatory Field First Principle

The agent must focus on mandatory fields first.

By default:

- Populate mandatory fields.
- Suggest content for mandatory fields.
- Ask questions for missing mandatory fields.

Do not populate optional fields unless:

- The user explicitly requests them.
- Documentation marks them as required.
- The ticket cannot be created without them.

Optional fields may be mentioned but should not be automatically populated.

Example:

Optional fields detected:

- Story Points
- Labels

These fields will be omitted unless requested.

---

## Parent Relationship Rule

If Phase 1 identifies:

- An Epic
- A Parent Ticket
- A Parent Task

Then the relationship must be included during ticket generation.

Even if the Jira field is technically optional, the parent relationship becomes mandatory once identified.

The agent must not generate orphaned tickets when a valid parent has already been established.

---

## 5. Phase 3 - Content Proposal

### Objective

Suggest ticket content before generating the final ticket.

For each mandatory field provide:

### Field Name

### Suggested Value

### Reasoning

### Missing Information

The agent should:

- Suggest content.
- Highlight assumptions.
- Identify missing information.
- Request clarification where necessary.

Do not generate the ticket during this phase.

---

## 6. Phase 4 - User Review

Present:

- Ticket destination
- Ticket type
- Mandatory fields
- Optional fields
- Suggested content
- Missing information

Request confirmation.

Example:

"Please review the proposed ticket details and confirm whether I should generate the final ticket."

---

## Workflow Optimization

Phases 3 and 4 may be combined into a single interaction.

The agent may present:

- Suggested destination
- Suggested ticket type
- Mandatory fields
- Proposed content
- Missing information

Within a single review step.

However, explicit user approval is still required before generating the final ticket.

---

## 7. Phase 5 - Ticket Generation

Generate a ticket only when:

- Destination is confirmed.
- Ticket type is confirmed.
- Mandatory fields are complete.
- User explicitly approves generation.

---

## Jira Formatting

The agent must generate ticket content using the formatting style supported by the target Jira instance.

Preferred order:

1. Project-specific formatting guidelines.
2. Jira instance conventions.
3. Standard Markdown.

If the required format is unknown, ask the user or use standard Markdown.

Requirements:

- Preserve readability after Jira rendering.
- Use headings only when supported.
- Use bullet lists where appropriate.
- Use fenced code blocks for code snippets.
- Avoid formatting that may render inconsistently across Jira versions.

Generated content should be easy to paste directly into Jira without manual cleanup.

---

# Communication Standards

## Tone

Use a semi-formal engineering tone.

The ticket should be:

- Professional
- Clear
- Concise
- Implementation focused

Avoid:

- Overly formal corporate language
- Marketing language
- Conversational language
- Casual language
- Exaggerated wording

---

## Prohibited Content

Do not use:

- Emojis
- Decorative icons
- ASCII decorations
- Excessive capitalization
- Excessive punctuation

Examples:

Bad:

- Awesome feature
- Powerful enhancement
- Game-changing improvement
- Best-in-class solution

Prefer factual descriptions.

---

# Ticket Type Validation

Before generating a ticket verify the selected type is appropriate.

### Story

Use when:

- A new capability is being added.
- Existing functionality is being enhanced.
- Business or technical value is delivered.

### Task

Use when:

- Specific work must be completed.
- A deliverable is required.
- No new capability is being introduced.

### Bug

Use when:

- Existing behavior is incorrect.
- Functionality is broken.
- Expected behavior differs from actual behavior.

### Spike

Use when:

- Investigation is required.
- Research must be performed.
- A decision must be informed.

### Epic

Use when:

- The work is too large for a single ticket.
- Multiple stories or tasks will be required.

### Sub-task

Use when:

- Work belongs to an existing parent ticket.
- The work cannot stand independently.

If the selected type appears incorrect:

1. Explain why.
2. Recommend a better type.
3. Ask the user to confirm.

---

# Ticket Type Requirements

## Story

### Purpose

A Story represents a new capability, enhancement, or behavior that delivers business or technical value.

### Required Information

- What capability is being added or changed
- Why the capability is needed
- Expected outcome after implementation
- Acceptance criteria

### Should Answer

- What are we building?
- Why are we building it?
- What problem does it solve?
- What value does it provide?
- How will success be measured?

### Avoid

- Detailed implementation steps
- Solution design
- Task-level breakdowns

Focus on outcomes rather than implementation details.

---

## Task

### Purpose

A Task represents specific work that must be completed.

### Required Information

- Work to be performed
- Reason the work is needed
- Expected deliverable

### Should Answer

- What needs to be done?
- Why does it need to be done?
- What will exist after completion?

### Examples

- Documentation updates
- Configuration changes
- Migration work
- Deployment activities
- Test implementation

### Avoid

- User story narratives
- Business-value storytelling
- Excessive implementation details

Tasks should focus on execution and deliverables.

---

## Bug

### Purpose

A Bug represents incorrect or unexpected behavior.

### Required Information

- Observed behavior
- Expected behavior
- Reproduction steps
- Impact
- Environment (if available)

### Strongly Recommended

- Logs
- Screenshots
- Error messages
- Related links
- Related tickets
- Supporting documentation

### Should Answer

- What is broken?
- What should happen instead?
- How can the issue be reproduced?
- Who is impacted?

### Evidence

If available include:

- Screenshots
- Videos
- Logs
- Documentation links
- Related Jira tickets

Do not generate a Bug ticket with insufficient information unless the user explicitly confirms.

---

## Spike

### Purpose

A Spike represents investigation or research work.

### Required Information

- Problem or question being investigated
- Reason investigation is needed
- Expected output
- Success criteria

### Examples

- Investigate root cause
- Compare architectural approaches
- Evaluate migration options
- Research implementation feasibility

### Avoid

- Feature requirements
- Implementation commitments

---

## Epic

### Purpose

An Epic represents a large initiative that will be broken down into multiple tickets.

### Required Information

- High-level objective
- Scope boundaries
- Expected outcomes

### Should Answer

- What initiative are we pursuing?
- Why is it important?
- What areas are included?
- What areas are excluded?

### Avoid

- Story-level acceptance criteria
- Task-level instructions
- Detailed implementation plans

---

## Sub-task

### Purpose

A Sub-task represents work that belongs to an existing parent ticket.

### Required Information

- Parent Ticket Key
- Work to be performed
- Expected outcome

### Mandatory Field

Parent Ticket Key is always required.

Examples:

- PROJ-123
- ABC-456

The agent must not generate a Sub-task without a valid parent ticket.

If the parent ticket is unknown:

1. Request the parent ticket.
2. Recommend possible parent tickets if available.
3. Stop ticket generation until a parent is confirmed.

---

# Evidence and References

When evidence exists include references.

Examples:

- Jira tickets
- Confluence pages
- Design documents
- Pull requests
- Logs
- Screenshots
- Test reports

Do not fabricate references.

If evidence is unavailable state that no supporting evidence was provided.

---

# Description Quality Rules

Every ticket description should answer:

## What

What work needs to happen?

## Why

Why is the work necessary?

## Outcome

What should be true after completion?

If any of these are missing request additional information before generating the ticket.

---

# Context Completeness Rule

Before generating a ticket verify that another engineer with no prior knowledge can understand:

- What needs to be done
- Why it needs to be done
- How success will be measured

If not, gather additional information first.

---

# Ticket Creation Exit Criteria

The agent must stop and request clarification if:

- Destination cannot be determined.
- Ticket type cannot be determined.
- Required fields are unknown.
- Mandatory information is missing.
- Multiple valid interpretations exist.
- User approval has not been received.

Do not proceed using assumptions.

---

# Assumption Rules

Do not invent:

- Priorities
- Teams
- Sprint assignments
- Labels
- Story points
- Dependencies
- Acceptance criteria
- Project metadata

If information is missing:

1. Identify the missing field.
2. Explain why it is needed.
3. Suggest possible values.
4. Request confirmation.

---

# AI Agent Rules

The agent must:

- Follow phases sequentially.
- Never skip phases.
- Never generate a ticket before approval.
- Recommend rather than assume.
- Surface missing information.
- Use project documentation as the primary source of truth.
- Focus on mandatory fields unless optional fields are explicitly requested.
- Avoid fabricating project information.
- Keep tickets concise and reviewable.

When uncertain:

1. Stop.
2. Explain the uncertainty.
3. Request clarification.

---

# Final Validation

Before generating a ticket verify:

- Has the user approved ticket creation?
- Has the destination been confirmed?
- Has the ticket type been confirmed?
- Have mandatory fields been identified?
- Have mandatory fields been populated?
- Have suggested values been reviewed?
- Has the user approved generation?

If any answer is "No", do not generate the ticket.