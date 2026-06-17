# Git Commit Guidelines

## 1. Core Principles

* **Human Approval Required:** Never create commits without explicit user approval.

* **Review Before Action:** Always present pending changes before staging or committing.

* **Transparency First:** Clearly explain what will be staged and committed.

* **No Silent Git Operations:** Never perform git actions without communicating intent and expected outcome.

* **Verify Repository State First:** Before presenting modified files, staging changes, or proposing a commit, run:

  - `git status`
  - `git diff`
  - `git diff --staged` (if staged changes exist)

  Base all commit recommendations on actual repository state.

* **No-Change Guardrail:** If `git status` shows no modified, staged, untracked, or deleted files, report that the working tree is clean and stop. Do not propose commits.

---

## 2. Commit Workflow

Follow this workflow:

1. Run repository status checks.
2. Review modified files.
3. Present proposed staged files.
4. Present commit summary.
5. Request approval.
6. Stage approved files.
7. Create commit.
8. Confirm commit result.

Do not skip approval steps.

---

## 3. Before Staging

Before staging files:

Present:

- modified files
- newly created files
- deleted files

Identify:

- unrelated changes
- generated files
- temporary files
- accidental modifications

If both staged and unstaged changes exist:

- clearly identify staged files
- clearly identify unstaged files
- explain what will be included in the commit

Ask for confirmation before staging.

---

## 4. Before Commit

Before creating a commit:

Show:

### Files Included

List all staged files.

### Change Summary

Provide a concise summary of:

- features added
- bugs fixed
- refactors performed
- documentation updates

### Proposed Commit Message

Present the exact commit message.

Example:

```text
feat(job-extractor): add Workday pagination support
```

Wait for explicit approval before committing.

---

## 5. Commit Message Standards

Prefer:

```text
type(scope): summary
```

Examples:

```text
feat(search): add location filtering

fix(parser): handle malformed salary ranges

refactor(api): simplify retry handling

docs(commenting): update comment guidelines

test(scraper): add pagination coverage
```

### Commit Types

| Type | When to Use |
|--------|--------|
| feat | A new feature |
| fix | A bug fix |
| refactor | Code change that neither fixes a bug nor adds a feature |
| docs | Documentation-only changes |
| test | Adding missing tests or correcting existing tests |
| perf | Performance improvements |
| build | Build system or dependency changes |
| ci | CI/CD changes |
| chore | Repository maintenance tasks |

Keep summaries concise and descriptive.

---

## 6. After Commit

After committing:

Show:

- commit hash
- commit message
- files included

Confirm commit creation.

---

## 7. Protected Operations

Never perform the following without explicit confirmation:

- git reset --hard
- git rebase
- git clean
- git checkout with destructive effects
- branch deletion
- tag deletion

### Branch Safety

Never:

- create a branch without approval
- switch branches without approval
- assume the target branch name

Always confirm the target branch name before:

- creating a branch
- switching branches

---

## 8. Remote Repository Safety

Agents may assist with:

- reviewing changes
- staging files
- creating commits

Agents must never:

- `git push`
- `git push --force`
- `git push --tags`
- delete remote branches
- delete remote tags

Remote repository operations are user-owned actions.

Pushing changes is a manual user responsibility.

---

## 9. Multi-Commit Changes

If changes logically belong to multiple commits:

Recommend commit separation.

Example:

```text
Commit 1:
feat(parser): add salary extraction

Commit 2:
test(parser): add salary extraction tests
```

Do not automatically split commits without approval.

---

## 10. AI Agent Rules

* Never auto-stage.
* Never auto-commit.
* Never assume approval.

* Always verify repository state before proposing actions.

* Always show:
  - modified files
  - staged files
  - commit message

* Prefer smaller, reviewable commits.

* Avoid mixing unrelated changes into a single commit.

* If repository state is unclear, stop and ask for clarification.

---

## 11. Final Validation

### Before Commit

* Was `git status` reviewed?
* Was `git diff` reviewed?
* Are the correct files staged?
* Are staged and unstaged changes clearly separated?
* Does the commit message accurately describe the changes?
* Are unrelated changes excluded?
* Has approval been received?

If any answer is unclear, stop and request clarification.
````
