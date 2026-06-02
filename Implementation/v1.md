# Implementation Rules and Execution Guidelines

## 1. Core Philosophy

* **Implement, Do Not Re-Architect:** Follow the approved implementation plan and existing architecture unless explicitly instructed otherwise.

* **Implement the Plan:** Your primary responsibility is to implement the approved plan. Do not redesign, reinterpret, optimize, or expand the plan unless explicitly instructed. Surface ambiguities and conflicts instead of inventing solutions.

* **Prefer Minimal Changes:** Modify only the code necessary to complete the task.

* **Consistency Over Creativity:** Reuse existing patterns, abstractions, naming conventions, and architectural approaches before introducing new ones.

* **Do Not Invent Requirements:** Never add speculative features, abstractions, validations, optimizations, or edge-case handling that were not requested or implied by existing project patterns.

* **Preserve Existing Behavior:** Avoid changing stable behavior outside the scope of the requested implementation.

* **Avoid Broad Refactors:** Do not refactor unrelated modules or restructure systems unless explicitly requested.

* **Localize Changes:** Keep implementation scope tightly bounded to affected areas.

---

## 2. Priority Hierarchy

When conflicts occur, follow this priority order:

1. Explicit user instructions
2. Approved implementation plans/specifications
3. Existing architecture and repository patterns
4. Repository documentation and guidelines
5. Agent optimization preferences

Never override explicit plans with inferred "better" solutions.

---

## 3. Implementation Workflow

Follow this execution process:

1. Read and understand the implementation plan.
2. Identify impacted modules and dependencies.
3. Review existing patterns before coding.
4. Implement incrementally in small logical changes.
5. Validate functionality after major changes.
6. Run relevant tests and checks.
7. Update comments/documentation if required.
8. Verify implementation matches the requested scope.

Avoid implementing multiple unrelated concerns simultaneously.

---

## 4. Pattern Reuse

Before creating new:

- abstractions
- utilities
- helpers
- services
- hooks
- middleware
- interfaces
- base classes

first check whether equivalent patterns already exist.

Prefer extending or reusing existing systems over introducing parallel implementations.

❌ BAD

- Create a new retry utility when an equivalent helper already exists.

✅ GOOD

- Extend the existing retry helper to support additional retry conditions.

---

## 5. Refactoring Rules

* Refactor only when necessary for the requested implementation.
* Keep refactors scoped and incremental.
* Preserve public interfaces unless explicitly approved.
* Avoid mixing implementation work with stylistic rewrites.
* Avoid renaming stable entities without clear necessity.

❌ BAD

- Refactor unrelated modules while implementing a pagination fix.

✅ GOOD

- Limit refactoring to pagination-related logic required by the fix.

---

## 6. Dependency Rules

* Do not introduce new dependencies unless necessary.
* Prefer existing project libraries and utilities.
* Avoid dependency duplication.
* Justify large or impactful dependency additions.
* Prefer lightweight solutions over large frameworks when possible.

Before adding a dependency:

1. Check if equivalent functionality already exists internally.
2. Check if an existing dependency already provides the feature.
3. Evaluate maintenance and operational impact.

---

## 7. Validation and Testing

* Validate implementations against the original specification.
* Run relevant tests after major modifications.
* Do not ignore failing tests without explicit approval.
* Add tests only where appropriate and aligned with repository patterns.
* Avoid rewriting unrelated tests.

When fixing bugs:

- verify reproduction conditions
- confirm root cause
- validate the fix directly addresses the issue

---

## 8. Scope Control

* Stay within the requested implementation scope.
* Avoid speculative future-proofing.
* Avoid solving hypothetical future problems.
* Avoid introducing abstractions for unconfirmed future needs.

❌ BAD

- Introduce plugin architecture for a feature with only one implementation.

✅ GOOD

- Implement the required behavior using existing extension patterns.

---

## 9. Documentation and Comments

* Follow `COMMENTING.md` for all generated comments and documentation.
* Update documentation only for affected behavior.
* Avoid generating excessive documentation for trivial changes.
* Keep implementation notes concise and accurate.

---

## 10. File and Module Safety

* Avoid modifying sensitive configuration files unless required.
* Avoid unnecessary edits to:
  - lockfiles
  - build configurations
  - CI/CD pipelines
  - deployment scripts
  - database migrations

* Never remove operational directives such as:
  - lint suppressions
  - compiler directives
  - type-check overrides
  - test annotations

unless explicitly instructed.

---

## 11. Error Handling

* Follow existing repository error-handling patterns.
* Prefer explicit failures over ambiguous silent failures.
* Avoid swallowing exceptions silently.
* Preserve useful debugging information.
* Avoid excessive defensive programming unless required.
* Do not introduce new error-handling paradigms without justification.

❌ BAD

- Catch all exceptions and ignore failures silently.

✅ GOOD

- Log contextual failure details and return structured errors.

---

## 12. AI Agent Behavior Rules

* Do not expose chain-of-thought or internal reasoning.
* Avoid speculative architectural redesigns.
* Avoid introducing unnecessary abstractions.
* Avoid excessive file modifications.
* Preserve repository consistency.
* Prefer deterministic and maintainable implementations.
* Keep diffs readable and review-friendly.
* Prefer incremental implementation over large rewrites.

* **Minimize Diff Noise:** Do not reformat untouched code, reorder imports, modify whitespace, change naming styles, or apply stylistic rewrites outside the implementation scope unless explicitly requested or required by repository tooling.

* **No Code Truncation:** When generating code, provide complete implementations or precise modifications. Do not omit logic using placeholders, ellipses, pseudocode, or comments such as:
  - `// existing logic here`
  - `// implementation omitted`
  - `repeat for remaining cases`

* **No Partial Implementations:** Do not leave stub methods, placeholder returns, mock implementations, TODO-driven logic, or intentionally incomplete code unless explicitly requested.

❌ BAD

```ts
throw new Error("TODO");
```

❌ BAD

```python
return None  # implement later
```

❌ BAD

```go
panic("not implemented")
```

---

## 13. Final Review Questions

Before finalizing implementation:

* Does the implementation strictly follow the approved plan?
* Were unrelated systems left untouched?
* Were existing repository patterns reused where possible?
* Was unnecessary abstraction avoided?
* Were tests or validations performed?
* Does the implementation preserve existing stable behavior?
* Are comments and documentation aligned with `COMMENTING.md`?
* Is the implementation minimal, maintainable, and reviewable?