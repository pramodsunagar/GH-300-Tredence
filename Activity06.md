# Activity06 – GitHub Copilot Custom Chat Mode for Python Code Generation

## Objective

Create a GitHub Copilot custom chat mode that behaves like a Senior Python
Developer and use it to generate, refactor, document, and test a Python
application.

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- Git

## Task 1 – Create a Custom Chat Mode

1. Open your project in Visual Studio Code.
2. Open GitHub Copilot Chat.
3. Create a custom chat mode or equivalent custom agent instruction file.

**Mode Name**

```text
Python Development Expert
```

Create a file in the repository with a clear, file-system-friendly name:

```text
.github/agents/python-development-expert.agent.md
```

> If your Copilot experience uses the newer agent workflow, create the agent in the UI and keep the same instructions. The file-based example above is the repository-based approach used in many labs.

## Task 2 – Configure the Chat Mode

```text
You are a Senior Python Software Engineer.

Generate production-ready Python applications.

Always:
- Follow PEP 8.
- Use type hints and docstrings.
- Use logging instead of print().
- Handle exceptions.
- Write modular code.
- Generate pytest tests when requested.
- Explain assumptions.
- Ask clarifying questions if requirements are incomplete.
```

## Task 3 – Generate an Employee Management Application

Prompt:

```text
Create a command-line Employee Management application using SQLite, CRUD operations, object-oriented design, logging, and a menu-driven interface.
```

Verify the project structure, modules, and CRUD implementation.

## Task 4 – Enhance the Application

Prompt:

```text
Add input validation, employee search, salary update, delete confirmation, and custom exception handling.
```

## Task 5 – Refactor

Prompt:

```text
Refactor the application to improve readability, modularity, and maintainability.
```

## Task 6 – Documentation

Prompt:

```text
Generate README.md with installation steps, project structure, and usage examples.
```

## Task 7 – Unit Tests

Prompt:

```text
Generate pytest unit tests for all CRUD operations.
```

## Task 8 – Code Review

Prompt:

```text
Review the application and recommend improvements for performance, security, error handling, and maintainability.
```

## Task 9 – Compare

Run the same prompt using Generic Copilot and the custom chat mode. Compare
code quality, structure, and documentation.

## Challenge

```text
Build an Inventory Management application using SQLite, CRUD operations, logging, pytest, and README documentation.
```

## Key Takeaways

- Custom chat modes provide consistent development guidance.
- Specialized instructions improve code quality.
- Custom instructions reduce repetitive prompting.
