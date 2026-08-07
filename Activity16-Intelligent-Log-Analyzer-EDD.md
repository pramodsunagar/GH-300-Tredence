# Activity 16: Building an Intelligent Log Analyzer with GitHub Copilot

## Lab Title
**Evaluation-Driven Development (EDD) for Production Log Analysis using Python and GitHub Copilot**

## Difficulty Level
**Intermediate**

## Duration
**90-120 Minutes**

## Audience
- Software Developers
- DevOps Engineers
- SRE Engineers
- Python Developers
- AI-Assisted Development Professionals

---

# Learning Objectives

By the end of this lab, participants will be able to:

- Apply Evaluation-Driven Development (EDD) to a real-world scenario
- Use GitHub Copilot to generate production-quality Python code
- Design evaluation datasets before implementation
- Measure accuracy of an AI-assisted solution
- Improve business logic using evaluation results
- Generate reports and insights from application logs
- Understand how EDD applies to AI Agents and GitHub Copilot workflows

---

# Business Scenario

A company receives thousands of application log entries every day.

The Operations team wants an automated system that can:

- Read application logs
- Categorize incidents
- Identify severity levels
- Generate a summary report

Before deploying the solution, they want to ensure its accuracy using Evaluation-Driven Development.

---

# Architecture

```text
Application Logs
        |
        v
Log Analyzer
        |
        v
Predicted Severity
        |
        v
Evaluation Engine
        |
        v
Accuracy Report
```

---

# Expected Categories

```text
INFO
WARNING
ERROR
CRITICAL
```

---

# Step 1: Create Project Structure

Create a folder:

```text
edd-log-analyzer
```

Create:

```text
edd-log-analyzer/
│
├── logs.py
├── analyzer.py
├── evaluator.py
├── report.py
└── README.md
```

---

# Step 2: Generate Evaluation Dataset First

## Copilot Prompt 1

```text
Create a Python file named logs.py.

Generate 20 sample application log entries.

Each log should contain:
- timestamp
- message
- expected_severity

Use realistic scenarios including:
- Successful login
- Disk nearly full
- API timeout
- Database unavailable
- Service crash
- Configuration warning
- Cache failure
- Application startup
```

## Example Dataset

```python
logs = [
    {
        "timestamp": "2026-08-07T10:15:00Z",
        "message": "User login successful",
        "expected_severity": "INFO"
    },
    {
        "timestamp": "2026-08-07T10:20:00Z",
        "message": "Disk usage reached 85%",
        "expected_severity": "WARNING"
    },
    {
        "timestamp": "2026-08-07T10:25:00Z",
        "message": "Database connection failed",
        "expected_severity": "ERROR"
    },
    {
        "timestamp": "2026-08-07T10:30:00Z",
        "message": "Payment service crashed",
        "expected_severity": "CRITICAL"
    }
]
```

---

# Step 3: Build Initial Analyzer

Create:

```text
analyzer.py
```

## Copilot Prompt 2

```text
Create a Python function named classify_log_severity().

Accept a log message as input.

Return:
- INFO
- WARNING
- ERROR
- CRITICAL

Use keyword matching.

Keep the implementation simple.
```

## Example Generated Logic

```python
def classify_log_severity(message):

    text = message.lower()

    if "crash" in text:
        return "CRITICAL"

    if "failed" in text:
        return "ERROR"

    if "warning" in text:
        return "WARNING"

    return "INFO"
```

---

# Step 4: Build Evaluation Engine

Create:

```text
evaluator.py
```

## Copilot Prompt 3

```text
Create an evaluation framework.

Requirements:

- Import logs dataset
- Run analyzer against all logs
- Compare actual and expected values
- Show passed and failed cases
- Calculate:
  - Accuracy
  - Precision
  - Recall
- Print a summary report
```

## Example Formula

```python
accuracy = correct_predictions / total_records * 100
# For multi-class metrics, calculate precision and recall per severity label,
# then aggregate using macro-average or class-level summaries.
```

---

# Step 5: Execute Baseline Evaluation

Run:

```bash
python evaluator.py
```

Expected result:

```text
Total Logs: 20

Passed: 14

Failed: 6

Accuracy: 70%
```

---

# Discussion

Ask participants:

Why did failures occur?

Possible reasons:

```text
"timeout" not detected

"service unavailable" not detected

"database offline" not detected
```

The analyzer logic is too simplistic.

---

# Step 6: Improve with GitHub Copilot

## Copilot Prompt 4

```text
Review these failed classifications.

Enhance classify_log_severity().

Requirements:

Critical:
- crash
- fatal
- shutdown
- service unavailable

Error:
- exception
- failed
- timeout
- connection error

Warning:
- warning
- high memory
- disk usage

Info:
- startup
- successful
- connected

Refactor the code using dictionaries or rule mappings.
```

## Expected Improved Logic

```python
CRITICAL_KEYWORDS = [
    "crash",
    "fatal",
    "shutdown",
    "service unavailable"
]

ERROR_KEYWORDS = [
    "failed",
    "exception",
    "timeout",
    "connection error"
]

WARNING_KEYWORDS = [
    "disk",
    "high memory",
    "warning"
]
```

---

# Step 7: Re-run Evaluation

```bash
python evaluator.py
```

Expected:

```text
Total Logs: 20

Passed: 19

Failed: 1

Accuracy: 95%
```

---

# Step 8: Generate Operational Summary

Create:

```text
report.py
```

## Copilot Prompt 5

```text
Create a reporting module.

Requirements:

Calculate:

- Total INFO logs
- Total WARNING logs
- Total ERROR logs
- Total CRITICAL logs

Display results as a formatted report.

Include percentages.
```

## Example Output

```text
Operational Summary

INFO      : 35%
WARNING   : 20%
ERROR     : 30%
CRITICAL  : 15%
```

---

# Step 9: Add Trend Analysis

## Copilot Prompt 6

```text
Enhance report.py.

Create functions to:

- Find top recurring issues
- Count failure patterns
- Rank most common incidents

Return top 5 incidents.
```

## Example Output

```text
Top Incidents

1. API Timeout             12
2. Database Failure        10
3. Disk Usage Warning       8
4. Service Crash            4
5. Cache Failure            3
```

---

# Step 10: Add Evaluation Dataset Expansion

## Copilot Prompt 7

```text
Generate 30 additional log records designed to break the current analyzer.

Include:
- ambiguous messages
- unusual wording
- multiple issues in the same message
- typo variations

Label expected severity.
```

---

# Step 11: EDD Improvement Cycle

```text
Generate Logs
     ↓
Evaluate
     ↓
Identify Failures
     ↓
Improve Logic
     ↓
Re-Evaluate
     ↓
Compare Metrics
```

---

# Bonus Challenge (Advanced)

Convert keyword matching into a scoring engine.

Example:

```python
CRASH = 100
FATAL = 100
FAILED = 50
TIMEOUT = 50
DISK_WARNING = 20
```

Classification:

```text
0-20     INFO
21-50    WARNING
51-80    ERROR
81-100   CRITICAL
```

---

# Copilot Agent Mode Challenge

```text
Analyze this entire project.

Review:
- analyzer.py
- evaluator.py
- report.py

Improve:
- code quality
- modularity
- performance
- testing

Generate updated files and explain the changes.
```

---

# Real-World Mapping

- Log Records → Azure Monitor Logs
- Analyzer → Monitoring Service
- Evaluation Dataset → Benchmark Dataset
- Evaluator → AI Evaluation Framework
- Report Generator → Operations Dashboard
- Improvement Cycle → EDD Process

---

# Key Takeaway

**EDD is not about generating code faster.**

**EDD is about generating code, measuring outcomes, learning from failures, and improving systematically.**

This log analyzer scenario closely mirrors real-world enterprise AI projects and is an excellent intermediate-level GitHub Copilot and Python lab.
