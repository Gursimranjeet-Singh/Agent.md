# Commenting Standards

## 1. Core Principles

* **Prefer Self-Documenting Code:** Use clear naming, small focused entities, and strong abstractions before adding comments.

* **Prefer Refactoring First:** Before adding comments, improve naming, structure, or decomposition if the code itself can be made clearer.

* **Explain Reasoning, Not Syntax:** Comments should explain intent, constraints, tradeoffs, or non-obvious behavior — not restate syntax already visible in code.

* **Keep Comments Minimal:** Prefer fewer high-value comments over excessive inline narration.

* **Comment Density:** Only add comments where understanding materially improves.

* **Avoid Redundancy:** Do not write comments that merely describe obvious operations.

* **Avoid Decorative Comments:** Do not use banner or separator comments.

BAD:
```text
// ******** MAIN LOOP ********
```

* **Remove Generation Artifacts:** Never leave temporary planning comments, AI narration, scaffolding text, step-by-step descriptions, or placeholder comments in final code.

BAD:
```python
# Step 1: Fetch users
# Step 2: Validate users
```

BAD:
```python
# TODO: Improve later
```

GOOD:
```python
# TODO: Replace polling with websocket updates once backend support exists
```

* **Preserve Tool & Compiler Directives:** Never remove, rewrite, or relocate operational comments required by the compiler, bundler, formatter, linter, type-checker, test runner, or build system unless explicitly instructed.

Examples:
- `// eslint-disable-next-line`
- `# type: ignore`
- `// @ts-expect-error`
- `/* webpackChunkName: "..." */`
- `# pragma: no cover`

* **Keep Comments Updated:** Remove or update comments whenever related logic changes.

* **No Stale Comments:** Comments that no longer reflect implementation behavior must be updated or removed immediately.

* **Keep Comments Concise:** Prefer short precise explanations over long descriptive paragraphs.

---

## 2. Documentation Hierarchy

Use comments in the following order:

1. File/module-level documentation
2. Entity-level documentation
3. Inline reasoning comments only where necessary

Avoid excessive inline commenting when higher-level documentation is sufficient.

---

## 3. File-Level Documentation

Major files or modules should include a top-level documentation block describing:

* Purpose of the file
* Primary responsibility
* Important constraints
* External integrations if relevant
* Important architectural decisions when necessary

GOOD:
```python
"""
Handles extraction and normalization of external job listings.

Responsibilities:
- Fetch raw listings
- Normalize engineering role titles
- Deduplicate results
- Standardize metadata for downstream ranking
"""
```

---

## 4. Entity-Level Documentation

* **Use Native Documentation Formats:** Always use the documentation syntax standard to the target language.

Examples:
- TypeScript/JavaScript:
  Use JSDoc (`/** ... */`) for documentation comments.
  Do not use regular block comments (`/* ... */`) for entity documentation.

- Python:
  Use standard PEP 257 docstrings (`""" ... """`).

- Rust:
  Use line documentation comments (`///`).

- Go:
  Use standard line comments (`//`) directly above entities.

- Java/C#:
  Use language-native documentation comment formats.

Public or reusable entities should include structured documentation comments.

Entities may include:
- functions
- classes
- interfaces
- modules
- components
- services
- hooks
- middleware
- routes
- utilities
- schemas
- jobs
- handlers
- pipelines
- reusable scripts

Documentation should describe:

* Purpose and responsibility
* Inputs and outputs
* Side effects
* Assumptions and preconditions
* Exceptions or failure behavior if relevant
* Important implementation decisions when non-obvious

Prefer structured tags such as:
- `@param`
- `@returns`
- `@throws`

over dense prose.

GOOD:
```python
def normalize_job_title(title: str) -> str:
    """Convert company-specific job titles into normalized engineering role categories.

    Args:
        title: Raw title extracted from a careers portal.

    Returns:
        Standardized engineering role name.
    """
```

BAD:
```python
def normalize_job_title(title):
    """Normalize title."""
```

---

## 5. Inline Comments

### Rule

Inline comments must explain:
- reasoning
- constraints
- business rules
- non-obvious behavior
- external system quirks

Inline comments must never narrate syntax or describe obvious operations.

* **Enforce Comment Width Limits:** Wrap comment text to a maximum width of 100 characters unless project-specific formatting rules require otherwise.

Prefer multiple short comment lines over long horizontal lines.

---

### Appropriate Uses

Use inline comments only for:

* Complex or non-obvious logic
* Business rules
* API inconsistencies
* Performance optimizations
* Concurrency or synchronization behavior
* Parsing edge cases
* Workarounds and temporary fixes
* Important architectural constraints

GOOD:
```python
# Retry because the upstream API occasionally returns
# stale pagination tokens after filtering
retry_request()
```

GOOD:
```python
# Deduplicate because some jobs appear across multiple regions
jobs = deduplicate_jobs(results)
```

GOOD:
```python
# Temporary workaround for inconsistent location metadata
# returned by the Workday API during pagination
```

---

### Avoid Inline Narration

BAD:
```python
# Increment counter
counter += 1
```

BAD:
```python
# Loop through jobs
for job in jobs:
```

BAD:
```python
# Return results
return results
```

---

## 6. Temporary Workarounds

Temporary fixes must explain:

* Why the workaround exists
* What limitation it addresses
* Removal conditions if known

GOOD:
```python
# Temporary workaround for duplicate job IDs returned
# by concurrent pagination requests.
# TODO(platform-team): Remove once upstream engineering
# fixes the cursor idempotency bug.
```

---

## 7. AI Agent Commenting Rules

When generating or modifying comments:

* Avoid narrating implementation steps
* Avoid placeholder comments
* Avoid decorative comments
* Avoid excessive comment generation
* Preserve existing project comment style
* Prefer concise high-signal comments
* Remove stale comments during refactors
* Do not expose internal reasoning or chain-of-thought

---

## 8. Comment Review Checklist

Before finalizing comments:

* Would a competent engineer understand the code without this comment?
  - If yes, remove the comment.

* Does the comment explain reasoning or intent?
  - If no, rewrite or remove it.

* Does the comment still accurately reflect implementation behavior?
  - If no, update or remove it.

* Would improving naming or structure remove the need for this comment?
  - If yes, refactor first.

* Does the comment materially improve maintainability or readability?
  - If no, remove it.