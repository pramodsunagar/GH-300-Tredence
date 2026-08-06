# Activity12 – Creating and Using Security Hooks for Python Applications

## Objective

Create GitHub Copilot Security Hooks that automatically encourage secure coding practices whenever Python or FastAPI code is generated or modified.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Python 3.11+
- Sample FastAPI project

---

## Lab Scenario

Your organization requires every Python application to follow secure coding practices. Instead of manually reminding developers, you will create repository-based security hooks that guide GitHub Copilot during code generation.

---

## Task 1 – Create the Hooks Folder

Create the following folder if it does not exist:

```text
.github/hooks/
```

Verify:

```text
.github/
└── hooks/
```

---

## Task 2 – Create a Security Hook

Create:

```text
.github/hooks/security.md
```

Add the following instructions:

```text
# Python Security Hook

Whenever Python or FastAPI code is generated:

- Never hardcode passwords, API keys or secrets.
- Recommend environment variables or Azure Key Vault.
- Validate all user input.
- Use parameterized database queries.
- Follow OWASP secure coding practices.
- Recommend secure password hashing.
- Validate JWT tokens.
- Sanitize file uploads.
- Use least-privilege permissions.
- Explain security recommendations before generating code.
```

Save the file.

---

## Task 3 – Generate a Secure Login API

Prompt:

```text
Create a FastAPI login API using JWT authentication.

Apply the Security Hook.
```

Verify:

- Password hashing
- JWT authentication
- Input validation
- Proper HTTP status codes
- No hard-coded secrets

---

## Task 4 – Secure Database Access

Prompt:

```text
Generate a Product repository using SQLAlchemy.

Apply the Security Hook.
```

Verify:

- ORM usage
- No SQL injection risks
- Safe query patterns

---

## Task 5 – Secure File Upload

Prompt:

```text
Generate a FastAPI endpoint for uploading product images.

Apply the Security Hook.
```

Verify:

- File type validation
- File size validation
- Safe storage recommendations

---

## Task 6 – Secret Management

Prompt:

```text
Review this project and identify secrets that should be moved to environment variables.

Recommend improvements.
```

Verify recommendations for:

- .env
- Azure Key Vault
- Secure configuration

---

## Task 7 – Review for Security Issues

Prompt:

```text
Review the entire project.

Identify:

- Hardcoded credentials
- Injection risks
- Authentication weaknesses
- Missing authorization
- Sensitive data exposure
```

Review the findings.

---

## Task 8 – Compare Without and With the Hook

Run:

```text
Generate a FastAPI authentication API.
```

Then run:

```text
Generate a FastAPI authentication API and apply the Security Hook.
```

Compare:

- Secret handling
- Validation
- Authentication
- Error handling
- Security recommendations

---

## Task 9 – Enhance the Hook

Update the hook with:

```text
Always:

- Recommend HTTPS.
- Suggest rate limiting.
- Recommend security headers.
- Recommend dependency vulnerability scanning.
- Recommend audit logging.
```

Run the authentication prompt again and observe the changes.

---

## Challenge Exercise

Create another hook:

```text
.github/hooks/api-security.md
```

Configure it to enforce:

- OAuth2 support
- Role-based authorization
- Secure cookies
- CSRF guidance
- API versioning
- Request throttling

Use the hook to generate a secure Order Management API.

---

## Key Takeaways

- Hooks provide automatic, repository-wide security guidance.
- Security practices become consistent across Python and FastAPI projects.
- Hooks help developers reduce common security mistakes without repetitive prompting.
