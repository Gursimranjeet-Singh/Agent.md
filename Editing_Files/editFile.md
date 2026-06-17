# File Editing and Modification Guidelines

## 1. Core Principles

* **Minimize Diffs:** Prefer the smallest reasonable change that solves the problem while maintaining readability, maintainability, correctness, and existing architectural principles.

* **Stay In Scope:** Modify only files directly related to the task.

* **Preserve Existing Behavior:** Do not change unrelated functionality.

* **Respect Existing Style:** Follow existing project conventions before introducing new patterns.

* **Prefer Extension Over Rewrite:** Extend existing implementations before replacing them.

* **Escalate Before Expanding Scope:** If implementation reveals a substantially larger change than originally expected, stop and discuss the new scope before proceeding.

---

## 2. Scope Control

Only modify files that are:

- required for the task
- directly impacted by the change
- necessary for validation or testing

Avoid editing:

- unrelated modules
- unrelated tests
- unrelated documentation
- generated files

If additional files appear necessary, explain why before modifying them.

---

## 3. Minimal Change Rule

Prefer:

- targeted edits
- localized fixes
- incremental changes

Avoid:

- large rewrites
- broad refactors
- stylistic rewrites
- unnecessary file moves

* **Preserve Existing Contracts:** Avoid changing public interfaces,
  function signatures, control flow structure, or module contracts
  unless required by the task or necessary to correct a design limitation.

❌ BAD

- Rewrite an entire module to fix a small bug.

✅ GOOD

- Modify only the affected logic.

---

## 4. Formatting and Style

Follow existing repository conventions.

Do not:

- reformat untouched code
- change quote styles
- reorder imports
- rename symbols
- change file structure

unless:

- required by tooling
- required by the task
- explicitly requested

* Follow `COMMENTING.md` for all generated comments and documentation.

* **No Code Truncation:** Never replace existing code with placeholders,
  ellipses, summaries, or comments such as:

  - `// existing logic`
  - `// rest of implementation`
  - `...`

  Always provide complete modifications for the code being changed.

---

## 5. Refactoring Rules

Refactor only when:

- required to implement the change
- necessary to remove blocking complexity
- explicitly requested

Keep refactors:

- small
- isolated
- reviewable

Do not combine unrelated refactors with feature work.

---

## 6. Architectural and Large-Scale Changes

Before performing changes that significantly affect:

- architecture
- module boundaries
- public APIs
- database schemas
- repository structure
- deployment behavior

the agent must:

1. Explain the required change.
2. Explain why smaller changes are insufficient.
3. Describe impacted areas.
4. Present the proposed approach.
5. Obtain approval before proceeding.

Do not perform major architectural modifications implicitly.

---

## 7. Existing Code Preservation

Before replacing existing code:

- understand its purpose
- verify it is no longer needed
- confirm behavior remains correct

Do not remove code solely because it appears unused.

Consider:

- configuration usage
- reflection
- dynamic imports
- framework conventions

---

## 8. File Creation Rules

Create new files only when:

- existing files cannot reasonably contain the change
- architectural patterns require separation
- explicitly requested

Avoid unnecessary file proliferation.

Prefer existing locations and structures.

---

## 9. Renaming Rules

Avoid renaming:

- files
- classes
- functions
- interfaces
- modules

unless:

- required by the task
- fixing incorrect naming
- explicitly requested

Explain significant renames before making them.

---

## 10. Dependency Awareness

Before modifying a file:

- identify consumers
- identify dependencies
- identify public interfaces

Avoid breaking:

- imports
- APIs
- contracts
- integrations

without explicit approval.

---

## 11. Generated and Managed Files

Do not manually edit:

- generated code
- lockfiles
- build artifacts
- vendor files

unless explicitly required.

Never modify generated artifacts directly using file-writing tools.

Examples:

- `package-lock.json`
- `yarn.lock`
- `pnpm-lock.yaml`
- `Cargo.lock`
- generated SDKs
- build outputs

Use the appropriate tooling or package manager and allow the system
to regenerate these files automatically.

Prefer updating the source that generates them.

---

## 12. Multi-File Changes

When multiple files must change:

- explain why each file is affected
- keep changes logically grouped
- avoid opportunistic cleanup

Do not use a task as justification for unrelated improvements.

---

## 13. AI Agent Rules

* Prefer review-friendly diffs.

* Avoid touching unrelated lines.

* Preserve repository consistency.

* Avoid speculative improvements.

* Avoid mass formatting changes.

* Avoid large-scale rewrites.

* Prefer incremental modifications.

* Escalate architectural changes before implementation.

* Escalate significant scope increases before implementation.

When uncertain:

- stop
- explain the concern
- request clarification

---

## 14. Final Review Questions

Before finalizing edits:

* Were only necessary files modified?
* Is the diff as small as reasonably possible?
* Were unrelated changes avoided?
* Does the change preserve existing behavior?
* Were existing patterns reused?
* Is the change easy to review?
* Would another engineer immediately understand why each file changed?
* Did the implementation stay within the approved scope?
* Were architectural changes approved before implementation?

If not, simplify the modification.
```
