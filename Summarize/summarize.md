# Project Summarization Guidelines

## 1. Purpose

The purpose of a summary is to help engineers understand a system,
repository, service, feature, or architecture without reading the
entire codebase.

A summary should explain:

- what the system does
- why it exists
- how it works
- how major components interact
- how data flows through the system
- important architectural decisions
- key dependencies and integrations
- operational constraints
- known risks and assumptions

The goal is understanding, not documentation generation.

---

## 2. Discovery Process

Before generating a summary:

1. Review implementation.
2. Review project structure.
3. Review configuration files.
4. Review dependency definitions.
5. Review entry points.
6. Review architecture documentation.
7. Review deployment configuration.
8. Review external integrations.
9. Review major workflows.

Implementation should be treated as the primary source of truth.

Do not generate summaries from:

- filenames alone
- folder names alone
- README files alone
- architecture diagrams alone
- previous summaries alone

---

## 3. Repository Discovery Order

When analyzing a repository, prefer the following order:

1. Entry points
2. Configuration files
3. Dependency definitions
4. Architecture documentation
5. Core business workflows
6. External integrations
7. Supporting modules and utilities

Prioritize understanding system behavior and architecture before
reviewing implementation details.

Avoid spending disproportionate effort on utility code before
understanding the primary system responsibilities.

---

## 4. Core Principles

* **Code First:** Derive understanding primarily from implementation.

* **Evidence Over Assumptions:** Base conclusions on observable code, configuration, architecture, or documented behavior.

* **Architecture Over File Listings:** Explain systems through responsibilities and interactions rather than file inventories.

* **Unknown Over Hallucinated:** Unknown information is preferred over unsupported assumptions.

* **Single Source of Truth:** Maintain one authoritative summary whenever practical.

* **System Understanding Over Syntax:** Explain how the system works, not how individual statements are written.

---

## 5. System Understanding

Before summarizing, identify:

- system purpose
- primary users
- business objectives
- major workflows
- external dependencies
- operational boundaries

Answer:

- What problem does the system solve?
- What are its primary responsibilities?
- Who uses it?
- What are the critical workflows?
- What systems does it interact with?

---

## 6. Architecture Analysis

Identify:

- services
- modules
- components
- layers
- integration points
- ownership boundaries

Describe:

- responsibilities
- interactions
- architectural patterns
- dependency relationships

### Prohibit Raw File Trees

Do not output raw directory listings, complete repository trees,
or large file inventories unless explicitly requested.

Describe systems through:

- components
- responsibilities
- workflows
- boundaries
- interactions

rather than folder hierarchies.

Prefer:

"Job ingestion service collects and normalizes jobs before persistence."

Over:

"The repository contains ingestion.py and normalization.py."

---

## 7. Data Flow Analysis

Identify how information moves through the system.

Describe:

- inputs
- processing stages
- storage
- outputs
- external integrations

Prefer workflow-oriented descriptions.

Example:

Portal → Extraction → Normalization → Storage → Search API

rather than isolated implementation details.

---

## 8. Component Analysis

For major components identify:

- purpose
- responsibilities
- dependencies
- interactions
- constraints

Focus on what a component contributes to the system.

Avoid listing every:

- file
- function
- class
- interface

unless explicitly requested.

---

## 9. External Integrations

Identify:

- databases
- queues
- APIs
- cloud services
- authentication providers
- third-party systems

Describe:

- why they exist
- how they interact with the system
- operational dependencies

Do not assume integrations exist without evidence.

---

## 10. Risks, Constraints, and Assumptions

Identify:

- technical constraints
- operational constraints
- scaling assumptions
- architectural tradeoffs
- known limitations

Classify information as:

### Verified

Supported by implementation or documentation.

### Inferred

Reasonable conclusion supported by evidence.

### Unknown

Cannot be verified from available information.

Unknown is preferred over unsupported assumptions.

---

## 11. Summary Output Format

Use the following structure when possible.

### Executive Summary

High-level description of the system.

### Purpose

Problem solved by the system.

### Architecture Overview

Major components and responsibilities.

### Data Flow

How information moves through the system.

### External Integrations

Databases, APIs, services, and dependencies.

### Key Workflows

Most important operational flows.

### Risks and Constraints

Important limitations and assumptions.

### Unknowns

Areas that could not be verified.

---

## 12. Summary Persistence

When explicitly requested to summarize a repository,
service, feature, or architecture, save the generated
summary to a dedicated summary document when appropriate.

Preferred locations:

- SUMMARIZED.md
- docs/SUMMARIZED.md

Prefer updating existing summaries over creating duplicates.

Do not create multiple competing summary documents
describing the same system.

### Summary Maintenance

When updating an existing summary:

- preserve accurate information
- remove outdated information
- update architecture changes
- update workflows
- update integrations
- update assumptions and constraints

Treat implementation as authoritative when documentation
conflicts with code.

### Last Reviewed

Include:

- Date
- Scope
- Commit/State Reference
- Summary Depth

Example:

- Date: 2026-06-02
- Scope: Full repository analysis
- Commit/State Reference: feature/job-ingestion
- Summary Depth: Level 2

---

## 13. Summary Depth Levels

### Level 1 — Executive Summary

Provide:

- purpose
- major responsibilities
- high-level architecture

Audience:

- stakeholders
- managers
- new team members

---

### Level 2 — Engineering Summary

Provide:

- architecture overview
- component responsibilities
- data flow
- integrations
- major workflows

Audience:

- engineers
- maintainers
- reviewers

---

### Level 3 — Architecture Deep Dive

Provide:

- detailed architecture
- component interactions
- dependency analysis
- workflow analysis
- operational constraints
- architectural tradeoffs

Audience:

- architects
- senior engineers
- system owners

---

## 14. Review Limitations

Clearly document:

- reviewed sources
- excluded sources
- assumptions
- unknown areas
- verification limitations

Do not claim complete understanding if portions of
the system were not reviewed.

Do not present assumptions as facts.

### Unknown Infrastructure

Do not assume:

- deployment topology
- production scale
- cloud architecture
- disaster recovery mechanisms
- high availability architecture
- performance characteristics

unless supported by implementation,
infrastructure definitions,
deployment configuration,
or architecture documentation.

If such information cannot be verified,
document it as Unknown.

---

## 15. AI Agent Rules

* Read implementation before generating summaries.

* Treat code as the primary source of truth.

* Do not infer architecture solely from filenames.

* Do not invent workflows, integrations, or behaviors.

* Avoid copying documentation verbatim.

* Reconcile existing summaries with current implementation.

* Do not overwrite existing summaries without reviewing them.

* Distinguish clearly between:
  - Verified
  - Inferred
  - Unknown

* Unknown is preferred over unsupported assumptions.

### Prohibit Raw File Trees

Do not generate large directory trees,
file inventories,
or folder hierarchies unless explicitly requested.

Prefer explaining:

- architecture
- workflows
- responsibilities
- boundaries
- interactions

over file organization.

### No Scalability Speculation

Do not assume:

- Kubernetes
- auto-scaling
- high availability
- fault tolerance
- production scale
- cloud architecture

unless supported by implementation,
infrastructure code,
deployment configuration,
or architecture documentation.

If evidence is unavailable,
classify the information as Unknown.

### No Tech-Stack Speculation

Do not infer:

- databases
- queues
- messaging systems
- caches
- cloud providers
- observability platforms
- deployment targets

solely from:

- filenames
- imports
- dependencies
- partial references

Report technologies only when supported by evidence.

---

## 16. Final Review Questions

* Does the summary explain what the system does?
* Does it explain how major components interact?
* Does it explain data flow?
* Are conclusions supported by evidence?
* Are assumptions clearly identified?
* Are unknowns explicitly documented?
* Does the summary focus on architecture rather than file listings?
* Is the summary stored or updated in the appropriate summary document?
* Would a new engineer gain a useful understanding of the system?

If not, continue analysis before finalizing the summary.
```
