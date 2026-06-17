# Documentation Guidelines

## 1. Purpose

Documentation should help engineers understand, use, operate, maintain,
and extend the system.

Documentation explains:

- what the system does
- why decisions were made
- how components interact
- how data flows through the system
- how to use and operate the system

Documentation should complement source code, not duplicate it.

---

## 2. Documentation Discovery

Before creating or updating documentation:

1. Review the relevant code and implementation.
2. Review existing documentation.
3. Identify discrepancies between code and documentation.
4. Treat the implementation as the primary source of truth unless explicitly instructed otherwise.
5. Update documentation to reflect actual system behavior.

Do not generate documentation solely from:

- existing documentation
- outdated architecture diagrams
- previous summaries
- assumptions

Documentation should be derived from the current implementation.

---

## 3. System Understanding First

Before documenting a feature or system:

- understand the purpose
- identify major components
- understand data flow
- identify external dependencies
- identify important constraints

Documentation should explain the system and its behavior,
not merely describe source files, classes, or functions.

Prefer explaining:

- architecture
- workflows
- responsibilities
- design decisions
- tradeoffs
- constraints

over implementation details already visible in code.

---

## 4. Core Principles

* **Documentation Is Part of the Implementation:** When behavior changes, documentation must be reviewed and updated.

* **Explain Why, Not Just What:** Focus on decisions, constraints, tradeoffs, assumptions, and rationale.

* **Prefer a Single Source of Truth:** Avoid duplicating the same information across multiple documents.

* **Keep Documentation Close to Ownership:** Store documentation near the code, service, or feature it describes when practical.

* **Prioritize Clarity Over Completeness:** Concise, accurate documentation is preferred over exhaustive but stale documentation.

---

## 5. When Documentation Must Be Updated

Review documentation when changing:

- user-facing behavior
- APIs
- configuration
- architecture
- workflows
- deployment processes
- operational procedures
- setup instructions
- business rules

If documentation is affected, update it as part of the same change.

---

## 6. Documentation Hierarchy

Prefer documenting information in the most appropriate location.

### README

Use for:

- project overview
- setup instructions
- local development
- common workflows

Do not place detailed architecture or feature specifications in the README.

---

### Architecture Documentation

Use for:

- system design
- component relationships
- data flow
- service boundaries
- architectural decisions

---

### Feature Documentation

Use for:

- feature behavior
- business rules
- usage examples
- configuration

---

### Runbooks

Use for:

- operations
- troubleshooting
- deployment
- incident response

---

### Migration Documentation

Use for:

- breaking changes
- upgrade paths
- schema migrations
- compatibility notes

---

## 7. Avoid Code Duplication

Documentation should complement source code, not mirror it.

Do not document:

- function names
- class names
- method lists
- parameter lists
- implementation steps already obvious from code

Instead document:

- behavior
- intent
- responsibilities
- constraints
- assumptions
- tradeoffs
- architectural decisions

❌ BAD

```text
UserService contains:
- createUser()
- updateUser()
- deleteUser()
```

✅ GOOD

```text
UserService manages the user lifecycle and enforces
account validation rules before persistence.
```

---

## 8. Writing Guidelines

Documentation should be:

- accurate
- concise
- actionable
- searchable

Prefer:

- short sections
- descriptive headings
- examples where useful
- diagrams when helpful
- bullet points for procedures

Avoid:

- repeating source code
- excessive prose
- unnecessary implementation details

### Documentation Style

* Maintain a clean and professional Markdown style.
* Prefer simple headings, lists, tables, and examples.
* Avoid excessive formatting and visual decoration.

---

## 9. Examples and Commands

Commands and examples should be:

- tested when possible
- copy-paste friendly
- realistic
- up to date

Avoid placeholder examples unless clearly marked.

### Example Values

Use generic example values in commands, configurations, and code samples.

Examples:

- `your-api-key-here`
- `example-user`
- `example-project`
- `example-database`

Avoid repository-specific, environment-specific, or workspace-specific values.

---

## 10. Architecture and Decision Documentation

Document:

- major decisions
- constraints
- tradeoffs
- assumptions
- rejected alternatives when relevant

Focus on why a decision exists rather than restating implementation details.

---

## 11. Documentation Maintenance

Remove or update:

- stale documentation
- obsolete workflows
- outdated examples
- deprecated behavior

Do not leave documentation in a partially updated state.

Documentation should remain synchronized with implementation.

### Documentation References

* Verify documentation links before creating references.
* Do not create placeholder links to documentation that does not exist.

### Documentation Discoverability

* When creating new documentation, update the appropriate index, navigation, sidebar, table of contents, or discovery mechanism when applicable.

---

## 12. AI Agent Rules

* Read and understand the implementation before writing documentation.

* Treat code as the primary source of truth.

* Prefer explaining systems over describing code.

* Avoid creating duplicate documentation.

* Prefer existing documentation locations.

* Keep documentation synchronized with implementation.

* Do not invent undocumented behavior.

* Clearly identify assumptions when information is missing.

* Follow `COMMENTING.md` for code comments and docstrings.

---

## 13. Final Review Questions

Before finalizing documentation:

* Does the documentation reflect the current implementation?
* Does it explain the system rather than the code?
* Does it explain why decisions were made?
* Is the information stored in the correct location?
* Are examples and commands still valid?
* Does it avoid duplicating information already visible in code?
* Have all documentation references been verified?
* Is new documentation discoverable from existing documentation?
* Would a new engineer understand how the system works after reading it?

If not, revise before publishing.
````
