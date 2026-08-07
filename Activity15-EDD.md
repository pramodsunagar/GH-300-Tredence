# Activity 15: Evaluation-Driven Development (EDD) with GitHub Copilot and Python

## Lab Overview

### Objective
By the end of this lab, learners will be able to:

- Understand the concept of Evaluation-Driven Development (EDD).
- Use GitHub Copilot Chat to generate Python code.
- Create an evaluation dataset before improving an application.
- Run automated evaluations against expected results.
- Use Copilot to improve implementation based on failed test cases.
- Compare evaluation scores before and after improvements.

---

# Scenario

You are building a small Python function that checks password strength.

The function should classify a password as:

- Weak
- Medium
- Strong

Instead of manually checking a few examples, you will follow EDD:

1. Define expected behavior.
2. Create evaluation test cases.
3. Generate initial code using GitHub Copilot.
4. Run evaluations.
5. Identify failures.
6. Improve the code with Copilot.
7. Re-run evaluation and compare results.

---

# Prerequisites

## Software Required

- Visual Studio Code
- Python 3.10 or later
- GitHub Copilot Extension
- GitHub Copilot Chat Extension
- Active GitHub Copilot subscription/access

---

# Project Structure

Create a folder:

```text
edd-password-lab
```

Create the following files:

```text
edd-password-lab/
│
├── password_checker.py
├── evaluation_data.py
├── evaluator.py
└── README.md
```

---

# Step 1: Create and Open Project

1. Open Visual Studio Code.
2. Create a new folder named:

```text
edd-password-lab
```

3. Open the folder in VS Code.
4. Open GitHub Copilot Chat.

---

# Step 2: Create README.md

Create a file named:

```text
README.md
```

Add:

```markdown
# EDD Password Strength Lab

This project demonstrates Evaluation-Driven Development using Python and GitHub Copilot.
```

---

# Step 3: Create Evaluation Dataset First

## Copilot Prompt 1

```text
Create a Python file named evaluation_data.py that contains a list of password evaluation test cases.

Each test case should include:
- password
- expected: Weak, Medium, or Strong
- reason

Use around 12 test cases covering short passwords, missing uppercase letters, missing digits, missing special characters, and strong passwords.
Keep the code simple for beginners.
```

## evaluation_data.py

```python
evaluation_cases = [
    {
        "password": "abc",
        "expected": "Weak",
        "reason": "Too short and lacks complexity"
    },
    {
        "password": "password",
        "expected": "Weak",
        "reason": "Common lowercase word without digits or special characters"
    },
    {
        "password": "PASSWORD",
        "expected": "Weak",
        "reason": "Only uppercase letters without digits or special characters"
    },
    {
        "password": "pass1234",
        "expected": "Medium",
        "reason": "Has lowercase and digits but no uppercase or special characters"
    },
    {
        "password": "Password",
        "expected": "Medium",
        "reason": "Has uppercase and lowercase but no digit or special character"
    },
    {
        "password": "Password1",
        "expected": "Medium",
        "reason": "Has uppercase, lowercase, and digit but no special character"
    },
    {
        "password": "Pass@1",
        "expected": "Medium",
        "reason": "Has mixed character types but is shorter than 8 characters"
    },
    {
        "password": "Password@1",
        "expected": "Strong",
        "reason": "Has uppercase, lowercase, digit, special character, and sufficient length"
    },
    {
        "password": "Admin@123",
        "expected": "Strong",
        "reason": "Meets all complexity requirements"
    },
    {
        "password": "12345678",
        "expected": "Weak",
        "reason": "Only digits, no letters or symbols"
    },
    {
        "password": "P@ssw0rd",
        "expected": "Strong",
        "reason": "Strong pattern with all required character types"
    },
    {
        "password": "pass@123",
        "expected": "Medium",
        "reason": "Has lowercase, digits, and special character but no uppercase"
    }
]
```

---

# Step 4: Generate Initial Password Checker

Create:

```text
password_checker.py
```

## Copilot Prompt 2

```text
Create a Python function named check_password_strength(password).

The function should return:
- Weak
- Medium
- Strong

Rules:
- Weak if password is shorter than 6 characters
- Strong if password is at least 8 characters and contains uppercase, lowercase, digit, and special character
- Otherwise return Medium
```

## Sample Code

```python
import string


def check_password_strength(password):
    has_uppercase = any(char.isupper() for char in password)
    has_lowercase = any(char.islower() for char in password)
    has_digit = any(char.isdigit() for char in password)
    has_special = any(char in string.punctuation for char in password)

    if len(password) < 6:
        return "Weak"

    if (
        len(password) >= 8
        and has_uppercase
        and has_lowercase
        and has_digit
        and has_special
    ):
        return "Strong"

    return "Medium"
```

---

# Step 5: Build Evaluation Runner

Create:

```text
evaluator.py
```

## Copilot Prompt 3

```text
Create a Python evaluation script named evaluator.py.

It should:
- import evaluation_cases
- import check_password_strength
- run each test case
- compare actual result against expected result
- print pass/fail lines and a summary
- calculate overall accuracy
```

## Sample Code

```python
from evaluation_data import evaluation_cases
from password_checker import check_password_strength


def run_evaluation():
    total_cases = len(evaluation_cases)
    passed = 0
    failed_cases = []

    for case in evaluation_cases:
        actual = check_password_strength(case["password"])
        expected = case["expected"]
        status = "PASS" if actual == expected else "FAIL"

        print(f"{status}: {case['password']} -> expected={expected}, actual={actual}")

        if status == "PASS":
            passed += 1
        else:
            failed_cases.append(case)

    accuracy = (passed / total_cases) * 100

    print("\nEvaluation Summary")
    print(f"Total cases: {total_cases}")
    print(f"Passed: {passed}")
    print(f"Failed: {len(failed_cases)}")
    print(f"Accuracy: {accuracy:.2f}%")


if __name__ == "__main__":
    run_evaluation()
```

---

# Step 6: Run Evaluation

Open Terminal:

```bash
python evaluator.py
```

Expected result:

```text
Accuracy: 75%
```

(Note: Actual results may vary.)

---

# Step 7: Analyze Failures

Review failed password classifications.

Ask:

- Why did the evaluation fail?
- Which passwords were misclassified?
- What rules are missing?

This is a key EDD stage.

---

# Step 8: Improve Using GitHub Copilot

## Copilot Prompt 4

```text
Improve this password strength function based on evaluation failures.

Rules:
- Weak if password length is less than 6
- Weak if password contains only one character type
- Strong if it contains uppercase, lowercase, digit and special character and is at least 8 characters long
- Otherwise Medium

Keep the code beginner friendly.
```

## Improved Version

```python
import string


def check_password_strength(password):
    has_uppercase = any(char.isupper() for char in password)
    has_lowercase = any(char.islower() for char in password)
    has_digit = any(char.isdigit() for char in password)
    has_special = any(char in string.punctuation for char in password)

    character_type_count = sum([
        has_uppercase,
        has_lowercase,
        has_digit,
        has_special
    ])

    if len(password) < 6:
        return "Weak"

    if character_type_count == 1:
        return "Weak"

    if (
        len(password) >= 8
        and has_uppercase
        and has_lowercase
        and has_digit
        and has_special
    ):
        return "Strong"

    return "Medium"
```

---

# Step 9: Re-run Evaluation

```bash
python evaluator.py
```

Expected:

```text
Accuracy: 100%
```

---

# Step 10: Generate EDD Report

## Copilot Prompt 5

```text
Create a Markdown section for README.md explaining:

- What was evaluated
- Evaluation dataset
- Initial result
- Improvement made
- Final result
- Key learning
```

---

# Optional Challenge

## Copilot Prompt 6

```text
Enhance the password checker to return:

- Classification
- Numeric score (0-100)

Add points based on:
- Length
- Uppercase
- Lowercase
- Digits
- Special characters

Update evaluator.py accordingly.
```

---

# Trainer Discussion Points

Discuss:

1. Why evaluation datasets should be created before optimization.
2. Differences between EDD and TDD.
3. Why AI-generated code should be evaluated.
4. How GitHub Copilot accelerates the EDD workflow.
5. How EDD can be applied to:
   - AI Agents
   - RAG Applications
   - MCP Solutions
   - Custom GitHub Copilot Agents

---

# Key Takeaway

Evaluation-Driven Development (EDD) ensures that changes are measured against predefined evaluation criteria rather than relying on assumptions.

Instead of saying:

```text
The code looks correct.
```

Say:

```text
The code was evaluated and validated against measurable test cases.
```

That is the core principle of Evaluation-Driven Development.
