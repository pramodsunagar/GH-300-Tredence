# Activity08 – GitHub Copilot Custom Agent for Code Review & Refactoring

## Objective

Create a GitHub Copilot Custom Agent that performs code reviews, identifies code smells, and refactors Python applications using clean coding principles.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- Sample Python/FastAPI project

---

## Task 1 – Create a Custom Agent

Open GitHub Copilot Chat and create a new Custom Agent.

**Agent Name**

```text
Python Code Review Expert
```

Save the agent as:

```text
.github/chatmodes/Python Code Review Expert.chatmode.md
```

---

## Task 2 – Configure the Agent

Use the following instructions:

```text
You are a Senior Python Software Architect and Code Reviewer.

Always:
- Review code for readability, maintainability and security.
- Detect code smells and anti-patterns.
- Follow PEP 8 and SOLID principles.
- Recommend meaningful names.
- Add type hints and docstrings.
- Replace duplicated code with reusable functions.
- Suggest logging instead of print().
- Improve exception handling.
- Explain every recommendation before refactoring.
```

Save the agent.

---

## Task 3 – Review Existing Code

Prompt:

```text
Review the currently opened Python project.

Identify:
- Code smells
- Duplicate code
- Poor naming
- Missing validation
- Security issues
- Performance issues
```

Record the findings.

---

## Task 4 – Refactor the Project

Prompt:

```text
Refactor the application while preserving functionality.

Apply:
- SOLID principles
- Modular design
- Type hints
- Docstrings
- Better exception handling
```

Review the generated changes before accepting.

---

## Task 5 – Improve Logging

Prompt:

```text
Replace all print() statements with structured logging and configure a reusable logger.
```

---

## Task 6 – Improve Error Handling

Prompt:

```text
Implement centralized exception handling and create meaningful custom exceptions.
```

---

## Task 7 – Improve Performance

Prompt:

```text
Review the application and recommend optimizations for performance and memory usage.
```

---

## Task 8 – Generate Unit Tests

Prompt:

```text
Generate pytest unit tests for the refactored code.

Include positive, negative and edge-case tests.
```

---

## Task 9 – Generate a Pull Request Review

Prompt:

```text
Create a pull request review summary including:

- Major improvements
- Remaining issues
- Security observations
- Overall recommendation
```

---

## Challenge Exercise

Prompt:

```text
Review and refactor a FastAPI Order Management application.

Improve architecture, security, logging, validation, documentation and testability without changing functionality.
```

---

## Key Takeaways

- Custom review agents improve code consistency.
- Refactoring with GitHub Copilot helps reduce technical debt.
- Specialized agents produce more actionable reviews than generic prompts.
