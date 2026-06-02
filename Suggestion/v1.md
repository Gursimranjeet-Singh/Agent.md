# Software Review and Improvement Guidelines

## 1. Purpose

The purpose of this review is to identify meaningful improvements to code, architecture,
documentation, maintainability, reliability, security, and developer experience.

Suggestions are advisory only.

Do not automatically implement recommendations unless explicitly requested.

---

## 2. Core Principles

* **Suggest, Don't Implement:** Present recommendations separately from implementation work.

* **Evidence Over Opinion:** Every suggestion must be supported by observable code patterns, risks, or maintenance concerns.

* **Prioritize Impact:** Focus on improvements that provide meaningful value.

* **Respect Existing Constraints:** Consider repository conventions, architecture, team standards, and business requirements.

* **Avoid Preference-Based Feedback:** Do not suggest changes based solely on personal style preferences.

* **Minimize Noise:** Prefer a few high-value recommendations over many low-impact observations.

---

## 3. Engineering Principles

Use these as review lenses, not strict rules.

### KISS (Keep It Simple)

Prefer simpler solutions when they provide equivalent functionality.

Review for:
- unnecessary complexity
- excessive indirection
- overengineering

---

### YAGNI (You Aren't Gonna Need It)

Avoid building for hypothetical future requirements.

Review for:
- speculative abstractions
- unused extension points
- premature generalization

---

### DRY (Don't Repeat Yourself)

Reduce duplication when it creates maintenance cost.

Review for:
- duplicated business logic
- repeated validation
- repeated transformations

Do not recommend abstractions for minor duplication.

---

### SOLID

Use SOLID as a diagnostic tool, not a checklist.

Review for:
- multiple unrelated responsibilities
- tightly coupled implementations
- oversized interfaces
- brittle inheritance hierarchies

Do not recommend SOLID-driven abstractions without clear benefit.

---

### Make It Work, Make It Right, Make It Fast

Prioritize improvements in this order:

1. Correctness
2. Maintainability
3. Performance

Avoid premature optimization.

---

### Self-Documenting Code

Prefer improving:
- naming
- structure
- decomposition

before recommending additional comments.

Follow COMMENTING.md for documentation guidance.

---

### Principle of Least Surprise

Prefer predictable and consistent behavior.

Review for:
- unexpected side effects
- inconsistent naming
- inconsistent APIs
- surprising behavior

---

## 4. Review Areas

Evaluate the codebase for:

### Readability

- unclear naming
- overly complex functions
- deep nesting
- difficult control flow
- excessive cognitive load

### Maintainability

- duplicated logic
- excessive coupling
- poor separation of concerns
- hidden dependencies
- difficult-to-test designs

### Error Handling

- silent failures
- swallowed exceptions
- inconsistent error handling
- poor observability
- missing contextual information

### Performance

- unnecessary database calls
- repeated expensive operations
- excessive allocations
- inefficient algorithms
- avoidable network requests

Only suggest optimization when measurable benefit is likely.

### Security

- input validation
- authentication boundaries
- authorization concerns
- secrets handling
- injection risks
- insecure defaults

### Testing

- missing test coverage
- brittle tests
- duplicated tests
- untestable designs
- insufficient edge case coverage

### Documentation

- missing documentation
- misleading documentation
- stale comments
- undocumented assumptions

Follow COMMENTING.md standards.

---

## 5. Suggestion Format

Each recommendation should contain:

### Observation

What was observed.

### Impact

Why it matters.

### Recommendation

Suggested improvement.

### Priority

One of:

- Critical
- High
- Medium
- Low

Example:

Observation:
Pagination retry logic is duplicated across three modules.

Impact:
Future bug fixes must be applied in multiple locations.

Recommendation:
Extract retry behavior into the existing retry utility.

Priority:
Medium

---

## 6. When NOT to Suggest Changes

Do not suggest changes solely because:

- a different style is preferred
- another framework exists
- a newer language feature exists
- a different architecture could be used

Avoid suggestions that:

- increase complexity without clear benefit
- create speculative abstractions
- optimize hypothetical future requirements
- conflict with approved architecture

---

## 7. Architecture Awareness

Respect existing architectural decisions.

Before suggesting architectural changes:

- identify the actual problem
- explain the limitation
- estimate impact
- justify the proposed change

Avoid recommending rewrites without strong evidence.

---

## 8. Refactoring Recommendations

Recommend refactoring only when it improves:

- readability
- maintainability
- testability
- reliability

Do not recommend refactoring solely for stylistic reasons.

BAD:
- Convert all classes to functional style.

GOOD:
- Reduce duplication by extracting shared validation logic.

---

## 9. Review Severity Guidelines

### Critical

May cause:
- security vulnerabilities
- data corruption
- production outages

### High

May cause:
- significant maintenance burden
- major reliability concerns
- severe performance issues

### Medium

Would improve:
- readability
- maintainability
- consistency

### Low

Nice-to-have improvements.

---

## 10. Final Review Questions

Before presenting suggestions:

* Is the recommendation evidence-based?
* Does it provide measurable value?
* Does it respect existing architecture?
* Is the recommendation actionable?
* Is the priority level justified?
* Would the codebase be objectively better after applying it?

If not, do not suggest it.
```
