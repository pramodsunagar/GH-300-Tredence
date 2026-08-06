
# Activity13 – Introduction to GitHub Copilot Hooks

## Objective

In this lab, you will learn how to create and use GitHub Copilot Hooks to automatically apply coding standards and development guidance whenever GitHub Copilot generates Python or FastAPI code.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- Sample Python or FastAPI project

---

## Lab Scenario

Your development team follows common coding standards for Python projects. Instead of repeating these requirements in every prompt, you will configure repository-based Copilot Hooks so that GitHub Copilot consistently follows your development guidelines.

---

## Task 1 – Create the Hooks Folder

1. Open your project in Visual Studio Code.
2. Create the following folder if it does not already exist:

```text
.github/hooks/
```

Verify the structure:

```text
.github/
└── hooks/
```

---

## Task 2 – Create a Python Coding Standards Hook

Create the following file:

```text
.github/hooks/python-standards.md
```

Add the following instructions:

```text
# Python Coding Standards Hook

Whenever generating Python code:

- Follow PEP 8.
- Use meaningful names.
- Use type hints.
- Include docstrings.
- Use logging instead of print().
- Handle exceptions gracefully.
- Generate modular and reusable code.
- Recommend pytest tests where appropriate.
```

Save the file.

---

## Task 3 – Generate a Python Application

Open GitHub Copilot Chat.

Prompt:

```text
Create a command-line Student Management application using SQLite and object-oriented programming.

Apply the Python Coding Standards Hook.
```

Verify the generated code includes:

- PEP 8 formatting
- Type hints
- Logging
- Modular classes
- Exception handling

---

## Task 4 – Create a FastAPI Hook

Create:

```text
.github/hooks/fastapi-standards.md
```

Add:

```text
# FastAPI Standards Hook

Whenever generating FastAPI applications:

- Use a modular folder structure.
- Use Pydantic models.
- Use SQLAlchemy ORM.
- Return proper HTTP status codes.
- Use dependency injection.
- Generate OpenAPI documentation.
- Include centralized exception handling.
```

Save the file.

---

## Task 5 – Generate a FastAPI Application

Prompt:

```text
Generate a Product Management REST API using FastAPI.

Apply the FastAPI Standards Hook.
```

Verify:

- Routers
- Models
- Schemas
- Services
- Dependency injection
- Swagger documentation

---

## Task 6 – Update an Existing Hook

Update the Python Coding Standards Hook by adding:

```text
- Recommend Ruff linting.
- Use environment variables for configuration.
- Recommend configuration using python-dotenv.
```

Save the file.

Run the Student Management prompt again and compare the generated output.

---

## Task 7 – Compare Without and With Hooks

Run:

```text
Generate a FastAPI CRUD application.
```

Then run:

```text
Generate a FastAPI CRUD application and apply the FastAPI Standards Hook.
```

Compare:

- Folder structure
- Validation
- Logging
- Error handling
- Documentation
- Code quality

---

## Task 8 – Share Hooks

Commit the hook files to the repository.

Verify they are stored under:

```text
.github/hooks/
```

Discuss how other developers automatically benefit from the same coding standards.

---

## Challenge Exercise

Create another hook:

```text
.github/hooks/documentation.md
```

Configure it to automatically:

- Generate docstrings
- Create README.md
- Document project structure
- Add API usage examples

Use the hook while generating a FastAPI Order Management application.

---

## Key Takeaways

- Hooks provide repository-wide development guidance.
- Coding standards are applied consistently without repetitive prompts.
- Hooks improve code quality, maintainability, and team collaboration.
