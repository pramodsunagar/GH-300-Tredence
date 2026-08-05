# GitHub Copilot Lab — Prompt Engineering for Code Generation

## Lab Title

**Writing Effective, Scope-Bounded Prompts**


## Prerequisites

* VS Code with GitHub Copilot and GitHub Copilot Chat installed and signed in
* Python 3.10+ available in your terminal
* A Git repository (to check diffs with `git diff --stat`)

## Learning Objectives

By the end of this lab you will be able to:

1. Write prompts using four principles — **Single, Specific, Short, Surround** — that produce predictable, reviewable code
2. Structure any prompt touching existing code as **Task + Scope + Constraint + Format**
3. Generate functions, API endpoints, and data-processing logic using scope-bounded prompts
4. Compare weak vs. strong prompts and identify which invite unintended refactoring
5. Recognize the 5 most common prompt anti-patterns that cause UAT regressions, and rewrite them safely
6. Write reproducible prompts and verify that with a repeatable test

---

# Setup: One File, Built Incrementally

Every exercise in this lab builds the same file — `user_api.py` — one step at a time. This mirrors how you'll actually use Copilot: prompting against real, growing context rather than isolated snippets.

Create `user_api.py`:

```python
from fastapi import FastAPI

app = FastAPI()

# Lab Exercise — add endpoints below this line
```

Prompts in this lab are typed **as comments directly in the file**, immediately above where the new code should go — the same way Copilot is used day to day. This also means you can trigger, review, and undo (`Ctrl+Z`) each one quickly.

---

# Step 1: SINGLE — One Task Per Prompt

Combining multiple tasks in one prompt forces Copilot to guess priority and scope — every guess is a regression risk.

**Try this first (don't keep it):**
```python
# Create an API, add authentication, connect to a database, and write tests
```
Notice how much this decides on your behalf — framework choice, auth placement, DB config, test structure — from one line. Undo it.

**Now try the scope-bounded version — keep this one:**
```python
# Create a POST endpoint /users that accepts name and email and returns HTTP 201 Created
```

### Expected Outcome

Run `git diff --stat HEAD` — only `user_api.py` should appear, and the change should be limited to one endpoint.

> **Rule:** One task per prompt. If your prompt has "and" joining unrelated actions, split it into separate prompts.

---

# Step 2: SPECIFIC — Name Every Requirement

A vague prompt produces plausible-looking code that fails in UAT, not in review.

Add a shared data store beneath your Step 1 code — you'll use this for the rest of the lab:

```python
USER_STORE = {
    1: {"id": 1, "name": "Alice", "email": "alice@example.com"},
    2: {"id": 2, "name": "Bob",   "email": "bob@example.com"},
}
```

**Weak prompt (don't use):** `# Create a user API` — no framework, no fields, no error handling, no scope boundary specified.

**Specific, scope-bounded prompt — keep this one:**
```python
# Task: Create a PUT endpoint /users/{user_id} to update name and email
# Scope: This function only — do not modify USER_STORE or any endpoint above
# Constraint: Use a Pydantic BaseModel; return 404 with detail="User not found" if missing;
#             return the updated user with 200; no new imports
```

### Expected Outcome

Check: Pydantic model used? `USER_STORE` referenced, not replaced? 404/200 handled as specified? No other endpoint touched?

> **Rule:** Name the framework, fields, and error behavior explicitly — don't leave decisions for Copilot to make.

---

# Step 3: SHORT — Cut the Filler

Length isn't the problem — hidden requirements are. Phrases like "best practices," "enterprise-grade," and "if possible" give Copilot room to add scope you never asked for (extra logging libraries, middleware, dependencies you don't have installed).

**Verbose prompt (don't use):**
```
# I am building a very large enterprise-grade scalable service and I need you to help me
# generate a simple endpoint, ideally using best practices and maybe some logging if possible
```

**Short, precise prompt — keep this one:**
```python
# Create a DELETE /users/{user_id} endpoint — return 204 on success, 404 if not found
```

### Expected Outcome

Check: is the function under 15 lines? Any unexpected imports, logging, or decorators Copilot added on its own? Does it reference `USER_STORE`?

> **Rule:** Say only what's needed. Filler words are where scope creep sneaks in.

---

# Step 4: SURROUND — Give Copilot Real Context

Copilot fills gaps it can't see with invented imports, variable names, and error formats.

**Context-starved prompt:** in a separate, blank file `scratch.py`, type only:
```python
# Add validation and return 400 if invalid
```
Accept it and note what Copilot invented — a framework? variable names? its own idea of "invalid"? This is **context starvation**.

**Context-rich prompt:** back in `user_api.py`, below your existing endpoints, add:
```python
from pydantic import BaseModel
from fastapi import HTTPException

class UserCreate(BaseModel):
    name: str
    email: str

@app.post("/users", status_code=201)
def create_user(user: UserCreate):
    # Validate: name non-empty, email contains '@'; return 400 with detail per violation
    # If valid, add to USER_STORE with an auto-incremented id and return the new user
```

### Expected Outcome

Compare the two: the second version should use `HTTPException` (visible above), reference `USER_STORE`, and match your existing style — because it can see all three.

> **Rule:** Place prompts next to the real code, types, and imports they should use. An empty file forces Copilot to guess.

---

# Step 5: The Prompt Anatomy (Underlying All Four Rules)

Every "Specific" prompt in this lab already followed this structure — here it is made explicit:

```python
# Task:       [verb] + [what to build] + [expected behaviour]
# Scope:      [exact file / function / line range — nothing else]
# Constraint: [what NOT to import, touch, or change]
# Format:     [return type, error style, naming convention]
```

`Task` and `Scope` are required on every prompt that touches existing code. `Constraint` and `Format` matter most once other people's code — or a live API contract — depends on the result.

---

# Step 6: Spot and Rewrite 5 Dangerous Prompts

These prompts are short but give Copilot no real boundary. Each has caused real regressions.

| # | Dangerous Prompt | What Goes Wrong | Regression Signal |
|---|---|---|---|
| 1 | `Refactor this entire file` | Renames functions/variables, adds imports, restructures logic | Tests fail with `TypeError: takes 2 args but 3 given`, or import errors |
| 2 | `Fix the bug` | No bug named — Copilot guesses and may "fix" the wrong thing | A different test suite starts failing after the "fix" |
| 3 | `Make the tests pass` | May delete or weaken tests instead of fixing logic | CI is green but production returns wrong values |
| 4 | `Add validation` | Applied everywhere, may add an uninstalled library | `ModuleNotFoundError` in production |
| 5 | `Update the database schema` | May drop or rename existing columns | `OperationalError: no such column` after deploy |

**Worked example — rewriting #2:**
```python
# Task: Fix the KeyError in get_user_by_email() when email is not in USER_STORE
# Scope: get_user_by_email() function only
# Constraint: Use .get() with a None default — do not restructure the function
#             Do not change how the caller handles the return value
```

**Now rewrite #1, #3, #4, and #5 yourself**, using the same Task/Scope/Constraint/Format structure, before checking with your facilitator.

---

# Step 7: Reproducibility Test

A prompt is **reproducible** if 3 runs produce structurally equivalent results — same function, same scope respected, no stray imports (not necessarily identical code, since some variation is normal).

Write a scope-safe prompt for:

> Add `get_user_by_email(email: str)` to `user_api.py`. Look up by email in `USER_STORE`, return the user dict, or raise `HTTPException(404)` if not found. Don't modify any existing function.

Trigger it 3 times (accept → undo → repeat) and score each run:

| Criterion | Run 1 | Run 2 | Run 3 |
|---|---|---|---|
| Correct function name/signature | | | |
| Iterates `USER_STORE.values()` | | | |
| Raises `HTTPException(404)` | | | |
| No new imports | | | |
| No other function touched | | | |

**Target:** 5/5 on every run. Scoring below 4/5 on any run means your `Constraint` field is too loose — tighten it and retry.

---

# Discussion Questions

1. Which of the four rules (Single, Specific, Short, Surround) caught the most problems in your own testing?
2. In Step 6, which of the 5 dangerous prompts have you seen used for real?
3. Did your reproducibility test in Step 7 score 5/5 on the first try — if not, what did you tighten?

---

# Key Takeaways

* **Single, Specific, Short, Surround** — the four habits that keep Copilot's output predictable
* **Task + Scope + Constraint + Format** is the underlying structure behind every "Specific" prompt
* Vague verbs — *fix, refactor, validate, update the schema* — are the clearest red flags for regressions
* A reproducible prompt isn't about identical code every run — it's about staying inside the scope and constraints you named, every time

---

## Quick Reference

| Rule | Do | Avoid |
|---|---|---|
| **Single** | One task per prompt | Task bundling ("and also...") |
| **Specific** | Name framework, fields, error codes | "Create a user API" |
| **Short** | Say only what's needed | "best practices," "if possible" |
| **Surround** | Prompt next to real code/types | Prompting on a blank file |

**Template:**
```python
# Task:       what to build
# Scope:      exactly which file/function — nothing else
# Constraint: what NOT to change or import
# Format:     return type, error style, naming convention
```

**Red flags — rewrite on sight:** `refactor this entire file` · `fix the bug` · `make the tests pass` · `add validation` · `update the schema` · `best practices` · `and also` · `if possible`

---

**End of Lab**
