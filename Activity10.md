# Activity10 – Creating and Using GitHub Copilot Custom Skills for Python Development

## Objective

Learn how to create reusable GitHub Copilot **Custom Skills** that provide consistent, project-specific guidance for Python development. By the end of this lab, you will create multiple skills, invoke them from GitHub Copilot Chat, update them, and compare their output with generic prompts.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- Git
- A sample Python project opened in VS Code

---

## Lab Scenario

Your team frequently develops Python command-line utilities and FastAPI services. Developers repeatedly write similar prompts for project structure, coding standards, logging, testing, and documentation.

To improve consistency and reduce repetitive prompting, you will create reusable **Custom Skills** that can be shared across the repository.

---

## Task 1 – Create the Skills Folder

1. Open the project in Visual Studio Code.
2. Create the following folder if it does not already exist:

```text
.github/skills/
```

3. Verify the folder structure:

```text
.github/
└── skills/
```

---

## Task 2 – Create a Python Development Skill

Create a new Markdown file.

**File Name**

```text
.github/skills/python-development.md
```

Add the following content:

```text
# Python Development Skill

When generating Python code:

- Follow PEP 8 coding standards.
- Use meaningful variable and function names.
- Use type hints.
- Include docstrings.
- Prefer modular functions.
- Use logging instead of print().
- Handle exceptions gracefully.
- Suggest performance improvements.
- Generate production-ready code.
```

Save the file.

---

## Task 3 – Create a FastAPI Development Skill

Create another skill.

**File Name**

```text
.github/skills/fastapi-development.md
```

Add the following content:

```text
# FastAPI Development Skill

When generating FastAPI applications:

- Use modular project structure.
- Use Pydantic models.
- Use SQLAlchemy ORM.
- Generate RESTful APIs.
- Return proper HTTP status codes.
- Include dependency injection.
- Add Swagger documentation.
- Include centralized exception handling.
```

Save the file.

---

## Task 4 – Use the Python Skill

Open GitHub Copilot Chat.

Prompt:

```text
Use the Python Development Skill to create a command-line Employee Management application with SQLite, CRUD operations, logging and configuration support.
```

Verify the generated project contains:

- Modular structure
- Database layer
- CRUD implementation
- Logging
- Configuration module

---

## Task 5 – Use the FastAPI Skill

Prompt:

```text
Use the FastAPI Development Skill to generate a Product Management REST API using FastAPI, SQLAlchemy and SQLite.
```

Verify:

- Routers
- Models
- Schemas
- Services
- Database configuration
- Swagger support

---

## Task 6 – Extend a Skill

Update **python-development.md** by adding:

```text
- Generate pytest unit tests.
- Recommend Ruff for linting.
- Use environment variables for configuration.
```

Save the file.

Run the previous Employee Management prompt again and observe the improvements.

---

## Task 7 – Create a Documentation Skill

Create:

```text
.github/skills/documentation.md
```

Content:

```text
# Documentation Skill

Generate:

- README.md
- Installation guide
- Project structure
- Usage examples
- API documentation
```

Prompt:

```text
Use the Documentation Skill to generate a README for the Employee Management application.
```

---

## Task 8 – Compare Generic Prompt vs Skill

Run:

```text
Create a FastAPI CRUD application.
```

Then run:

```text
Use the FastAPI Development Skill to create a FastAPI CRUD application.
```

Compare:

- Project structure
- Code quality
- Validation
- Documentation
- Logging
- Maintainability

---

## Task 9 – Share Skills

Commit the skill files to the repository.

Verify they are stored under:

```text
.github/skills/
```

Discuss how team members can reuse the same skills.

---

## Challenge Exercise

Create a new skill named:

```text
.github/skills/testing.md
```

The skill should always instruct GitHub Copilot to:

- Generate pytest tests
- Use fixtures
- Include edge cases
- Measure code coverage
- Mock external services

Use the skill to generate tests for the FastAPI Product API.

---

## Key Takeaways

- Skills capture reusable development guidance in version-controlled Markdown files.
- Teams can standardize Python and FastAPI development practices.
- Updating a skill immediately improves future Copilot interactions.
- Skills reduce repetitive prompting and produce more consistent results across projects.
