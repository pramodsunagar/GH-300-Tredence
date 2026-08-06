# Activity07 – GitHub Copilot Custom Agent for FastAPI Backend Development

## Objective

Create a GitHub Copilot Custom Agent that acts as a Senior Python Backend Engineer. Use the agent to build a production-ready FastAPI REST API following modern backend development practices.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- FastAPI installed
- Git

---

## Task 1 – Create a Custom Agent

1. Open your FastAPI project in Visual Studio Code.
2. Open **GitHub Copilot Chat**.
3. Select **Agents → Create New Agent**.

**Agent Name**

```text
Backend API Development Expert
```

Save the agent as:

```text
.github/chatmodes/Backend API Development Expert.chatmode.md
```

---

## Task 2 – Configure the Agent

Replace the default instructions with:

```text
You are a Senior Python Backend Engineer.

Generate production-ready FastAPI applications.

Always:
- Follow REST API best practices.
- Use FastAPI, SQLAlchemy and Pydantic.
- Create modular project structures.
- Validate requests using Pydantic.
- Return proper HTTP status codes.
- Implement centralized exception handling.
- Use logging instead of print().
- Use environment variables for configuration.
- Generate secure JWT authentication when requested.
- Generate pytest tests when requested.
- Explain assumptions before generating code.
- Ask clarifying questions when requirements are incomplete.
```

Save the agent.

---

## Task 3 – Generate a FastAPI Project

Prompt:

```text
Create a FastAPI application for Product Management.

Requirements:
- Modular folder structure
- CRUD APIs
- SQLite database
- SQLAlchemy ORM
- Pydantic models
- Dependency Injection
- Swagger documentation
```

Verify:
- app folder
- models
- schemas
- routers
- services
- database configuration
- main.py

---

## Task 4 – Add Authentication

Prompt:

```text
Implement JWT authentication.

Include:
- Login endpoint
- Password hashing
- Token generation
- Protected APIs
```

Verify authentication flow.

---

## Task 5 – Add Business Features

Prompt:

```text
Enhance the Product API.

Add:
- Pagination
- Search by product name
- Category filtering
- Sorting by price
- Stock validation
```

---

## Task 6 – Improve Error Handling

Prompt:

```text
Implement centralized exception handling and standardized API responses.

Include validation errors and custom exceptions.
```

---

## Task 7 – Generate Unit Tests

Prompt:

```text
Generate pytest unit tests for all Product APIs.

Include:
- Positive tests
- Negative tests
- Edge cases
```

---

## Task 8 – Generate CI Pipeline

Prompt:

```text
Create a GitHub Actions workflow to:

- Install dependencies
- Run Ruff linting
- Execute pytest
- Build the application
```

Verify the workflow file is created under:

```text
.github/workflows/
```

---

## Task 9 – Review the Project

Prompt:

```text
Review the entire FastAPI project and recommend improvements for:

- Security
- Performance
- Scalability
- Maintainability
```

---

## Task 10 – Compare Generic Copilot vs Custom Agent

Run this prompt using Generic Copilot:

```text
Create a FastAPI CRUD application.
```

Run the same prompt using the **Backend API Development Expert** agent.

Compare:
- Folder structure
- API design
- Validation
- Security
- Logging
- Documentation
- Code quality

---

## Challenge Exercise

Prompt:

```text
Build an Order Management REST API.

Requirements:
- FastAPI
- SQLite
- SQLAlchemy
- JWT Authentication
- CRUD operations
- Pagination
- Search APIs
- pytest tests
- GitHub Actions workflow
- README documentation
```

---

## Key Takeaways

- Custom Agents provide reusable backend development expertise.
- Project-specific instructions improve consistency and code quality.
- FastAPI projects can be generated faster with less repetitive prompting.
- Custom Agents help enforce architecture and engineering standards across teams.
