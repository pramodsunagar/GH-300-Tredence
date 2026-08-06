# Activity14 – Enterprise Python Development using GitHub Copilot Custom Agents, Skills, Hooks, and Repository Instructions

## Objective

Build an enterprise-ready Python backend by combining GitHub Copilot **Custom Agents**, **Skills**, **Hooks**, and repository-level instructions. You will create reusable guidance, generate an Inventory Management application, and observe how these components improve consistency, quality, and collaboration.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- Git
- Empty Python workspace

---

## Lab Scenario

Your team is developing an **Inventory Management System**. The organization requires consistent coding standards, documentation, testing, security, and API design across all repositories.

Instead of repeating these requirements in every prompt, you will configure reusable guidance in a structured order:

1. Create and use **Custom Agents**
2. Add **Skills**
3. Add **Hooks**
4. Add repository-wide instructions using **copilot-instructions.md**

---

## Recommended Order of Setup

Use the following order when setting up GitHub Copilot guidance:

1. **Custom Agents** – define specialized assistants for specific tasks such as backend development, code review, testing, or security review.
2. **Skills** – add reusable domain knowledge for Python, FastAPI, testing, architecture, or deployment.
3. **Hooks** – enforce repository standards and guidance automatically during development.
4. **copilot-instructions.md** – provide repository-wide instructions that apply to all interactions.

---

## Task 1 – Create Repository Structure

Create the following folders and files:

```text
.github/
├── agents/              # Custom agents
├── skills/              # Reusable skills
├── hooks/               # Repository hooks
└── copilot-instructions.md
```

If your environment uses chat modes or prompt files instead of a dedicated agents folder, adapt the location accordingly, but keep the same purpose and order.

---

## Task 2 – Create and Use a Custom Agent

Create a Custom Agent file such as:

```text
.github/agents/python-backend-agent.md
```

Include instructions that define:

- The agent’s role and purpose
- When the agent should be used
- The expected output style
- Coding and architecture preferences
- Security and testing expectations

Example guidance to include:

- Act as an enterprise Python backend architect
- Prefer FastAPI, SQLAlchemy, Pydantic, and pytest
- Focus on modular design, clean APIs, and secure defaults
- Explain trade-offs and assumptions
- Produce production-ready code with tests and documentation

Save the file.

Then open GitHub Copilot Chat and use the agent in a prompt such as:

```text
Use the Python Backend Agent to generate an Inventory Management REST API.
```

Verify that the agent’s instructions influence the generated design and output.

---

## Task 3 – Create a Python Development Skill

Create:

```text
.github/skills/python-development.md
```

Add guidance to always:

- Follow PEP 8
- Use type hints
- Add docstrings
- Create modular code
- Use logging
- Generate pytest tests
- Explain assumptions

Save the file.

---

## Task 4 – Create a FastAPI Skill

Create:

```text
.github/skills/fastapi-development.md
```

Include guidance to:

- Generate modular FastAPI projects
- Use SQLAlchemy
- Use Pydantic
- Follow REST conventions
- Generate OpenAPI documentation
- Use dependency injection

Save the file.

---

## Task 5 – Create Hooks

Create a Python standards hook:

```text
.github/hooks/python-standards.md
```

Configure the hook to automatically recommend:

- PEP 8 compliance
- Type hints
- Logging
- Exception handling
- Reusable functions
- Environment variables for configuration

Create a security hook:

```text
.github/hooks/security.md
```

Configure the hook to:

- Prevent hard-coded secrets
- Recommend environment variables
- Validate inputs
- Recommend secure password hashing
- Use parameterized database queries
- Recommend HTTPS and audit logging

Save the hooks.

---

## Task 6 – Add Repository-Wide Instructions

Create:

```text
.github/copilot-instructions.md
```

Add repository-wide guidance such as:

- Preferred architecture and folder structure
- Coding standards for Python and FastAPI
- Testing expectations with pytest
- Security expectations
- Documentation standards
- Logging and configuration conventions

This file should be used as the final layer of default guidance for the repository.

---

## Task 7 – Generate the Application

Open GitHub Copilot Chat.

Prompt:

```text
Use the Python Backend Agent, apply the Python Development Skill, FastAPI Development Skill, Python Standards Hook, Security Hook, and the repository instructions to generate an Inventory Management REST API.

Requirements:
- FastAPI
- SQLite
- SQLAlchemy
- CRUD operations
- Product search
- Stock management
- Logging
- Configuration using environment variables
```

Verify the generated project contains:

- app/
- routers/
- models/
- schemas/
- services/
- database.py
- main.py

---

## Task 8 – Add Authentication

Prompt:

```text
Extend the application with JWT authentication.

Apply the Custom Agent, Skills, Hooks, and repository instructions.
```

Verify:

- Login endpoint
- Password hashing
- Protected APIs
- No hard-coded secrets

---

## Task 9 – Generate Tests and Documentation

Prompt:

```text
Generate pytest unit tests and README documentation for the Inventory Management application.
```

Verify:

- pytest tests
- README.md
- Installation steps
- API usage examples

---

## Task 10 – Review the Application

Prompt:

```text
Review the complete project.

Recommend improvements for:

- Security
- Performance
- Maintainability
- Scalability
- Documentation
```

Review all recommendations.

---

## Task 11 – Compare Results

Generate the Inventory Management application:

1. Using Generic Copilot.
2. Using the configured Custom Agent, Skills, Hooks, and repository instructions.

Compare:

- Folder structure
- Code quality
- Documentation
- Logging
- Security
- Testing
- Maintainability

---

## Challenge Exercise

Enhance the application by generating:

- Dockerfile
- docker-compose.yml
- GitHub Actions workflow
- Azure DevOps pipeline
- OpenAPI documentation
- Health check endpoint
- Application configuration using .env

Ensure the Custom Agent, Skills, Hooks, and repository instructions are all applied.

---

## Key Takeaways

- Custom Agents provide specialized behavior for specific tasks.
- Skills provide reusable domain knowledge for development work.
- Hooks enforce repository standards automatically.
- copilot-instructions.md provides repository-wide defaults for all Copilot interactions.
- Using these components in the correct order creates more consistent and enterprise-ready code.
