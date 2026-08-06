# Activity11 – Creating and Using a Testing & Debugging Skill for Python

## Objective

Create a reusable GitHub Copilot **Testing & Debugging Skill** that helps generate unit tests, debug Python applications, identify root causes, and recommend fixes using consistent engineering practices.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- pytest installed
- Sample Python or FastAPI project

---

## Lab Scenario

Your team spends significant time writing unit tests and debugging application issues. Instead of repeatedly describing testing standards and debugging expectations, you will create a reusable GitHub Copilot Skill that standardizes these activities.

---

## Task 1 – Create the Skills Folder

Verify the following folder exists in the repository:

```text
.github/skills/
```

If it does not exist, create it.

---

## Task 2 – Create a Testing & Debugging Skill

Create the following file:

```text
.github/skills/testing-debugging.md
```

Add the following content:

```text
# Testing & Debugging Skill

When reviewing or generating Python code:

Testing:
- Generate pytest unit tests.
- Use fixtures where appropriate.
- Include positive, negative and edge-case tests.
- Mock external services.
- Recommend code coverage improvements.

Debugging:
- Identify the root cause of errors.
- Explain the issue before fixing it.
- Recommend the safest solution.
- Preserve existing functionality.
- Suggest logging improvements.
- Recommend performance optimizations.
```

Save the file.

---

## Task 3 – Generate Unit Tests

Open GitHub Copilot Chat.

Prompt:

```text
Use the Testing & Debugging Skill to generate pytest unit tests for the EmployeeService class.

Include:
- CRUD operations
- Positive tests
- Negative tests
- Edge cases
```

Verify:

- Test functions
- Fixtures
- Assertions
- Mock objects where required

---

## Task 4 – Debug an Application Error

Introduce a simple bug into the project or use an existing one.

Prompt:

```text
Use the Testing & Debugging Skill to analyze this Python exception.

Identify:
- Root cause
- Possible fixes
- Recommended solution
```

Paste the stack trace and review the response.

---

## Task 5 – Improve Logging

Prompt:

```text
Use the Testing & Debugging Skill to replace print() statements with structured logging.

Configure reusable logging for the application.
```

Review the generated logging configuration.

---

## Task 6 – Detect Code Smells

Prompt:

```text
Use the Testing & Debugging Skill to review this project.

Identify:
- Duplicate code
- Long methods
- Poor naming
- Missing validation
- Exception handling issues
```

Review the recommendations.

---

## Task 7 – Improve Performance

Prompt:

```text
Use the Testing & Debugging Skill to identify performance bottlenecks.

Recommend improvements for:
- Memory usage
- Database access
- Loops
- API response time
```

---

## Task 8 – Test a FastAPI Application

Prompt:

```text
Use the Testing & Debugging Skill to generate pytest tests for the Product Management FastAPI application.

Include:
- API endpoint tests
- Validation tests
- Authentication tests
- Error response tests
```

Verify API test coverage.

---

## Task 9 – Compare Generic Prompt vs Skill

Run:

```text
Generate pytest unit tests for a FastAPI application.
```

Then run:

```text
Use the Testing & Debugging Skill to generate pytest tests for a FastAPI application.
```

Compare:

- Test coverage
- Fixtures
- Edge cases
- Mocking
- Code quality

---

## Challenge Exercise

Enhance the skill by adding:

```text
Always:
- Recommend Ruff linting.
- Suggest security improvements.
- Generate regression tests.
- Recommend performance profiling.
```

Use the updated skill to review the entire project.

---

## Key Takeaways

- Skills provide reusable testing and debugging guidance.
- Standardized prompts improve the consistency of generated tests.
- Skills help identify bugs, improve code quality, and reduce repetitive prompting.
