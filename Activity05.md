# GitHub Copilot MCP with GitHub -- Hands-on Lab

## Lab Title

**Using GitHub Copilot MCP to Work with GitHub Repositories**

## Target Audience

-   Intermediate Python Developers
-   Backend Developers
-   Full Stack Developers
-   DevOps Engineers

------------------------------------------------------------------------

## Learning Objectives

By the end of this lab, you will be able to:

-   Understand how GitHub MCP extends GitHub Copilot
-   Connect GitHub Copilot to your GitHub account
-   Search repositories using natural language
-   Create and manage GitHub Issues
-   Review Pull Requests
-   Search code across repositories
-   Analyze GitHub Actions workflow runs
-   Generate release notes
-   Improve developer productivity using MCP

------------------------------------------------------------------------

## Estimated Duration

**60 Minutes**

------------------------------------------------------------------------

## Prerequisites

-   Visual Studio Code
-   GitHub Copilot Business or Enterprise
-   GitHub Copilot Chat Extension
-   Agent Mode enabled
-   GitHub account
-   GitHub Personal Access Token (PAT)
-   GitHub MCP Server installed
-   Python 3.11 or later

------------------------------------------------------------------------

# Scenario

Your organization hosts all source code in GitHub. Instead of manually
browsing GitHub, you will use GitHub Copilot with the GitHub MCP Server
to interact with repositories, issues, pull requests, releases,
workflows, and code using natural language.

------------------------------------------------------------------------

# Task 1 -- Configure the GitHub MCP Server

Configure the following environment variables:

``` text
GITHUB_TOKEN=<Personal Access Token>
GITHUB_OWNER=<GitHub Username>
GITHUB_DEFAULT_REPOSITORY=<Repository Name>
```

Start the GitHub MCP Server and verify it starts successfully.

------------------------------------------------------------------------

# Task 2 -- Configure VS Code

Open the `settings.json` file and register the GitHub MCP server.

Example:

``` json
{
  "mcp": {
    "servers": {
      "github": {
        "command": "node",
        "args": ["server.js"]
      }
    }
  }
}
```

Restart Visual Studio Code.

Open GitHub Copilot Chat and verify that the GitHub MCP server is
connected.

------------------------------------------------------------------------

# Task 3 -- Discover Available MCP Tools

Open GitHub Copilot Chat and switch to **Agent Mode**.

Prompt:

``` text
List all tools exposed by the GitHub MCP server.
```

Observe capabilities such as:

-   Repository Search
-   Code Search
-   Issues
-   Pull Requests
-   Workflow Runs
-   Releases
-   Branches
-   Commits
-   Discussions

------------------------------------------------------------------------

# Task 4 -- Explore a Repository

Prompt:

``` text
Summarize the repository architecture.
```

Next:

``` text
Explain how authentication is implemented.
```

Finally:

``` text
Identify the entry point of this application.
```

------------------------------------------------------------------------

# Task 5 -- Search Code

Prompt:

``` text
Search for all implementations of JWT authentication.
```

Next:

``` text
Find every REST API endpoint related to Orders.
```

Next:

``` text
Where is the database connection configured?
```

Finally:

``` text
Which files reference environment variables?
```

------------------------------------------------------------------------

# Task 6 -- Create a GitHub Issue

Prompt:

``` text
Create a GitHub Issue.

Title:
Improve Login Performance

Body:
Investigate slow login response during peak traffic.

Labels:
enhancement
backend

Assign it to me.
```

Review the generated issue and approve the action.

Verify that the issue appears in GitHub.

------------------------------------------------------------------------

# Task 7 -- Analyze Pull Requests

Prompt:

``` text
List all open Pull Requests.
```

Next:

``` text
Summarize Pull Request #15.
```

Next:

``` text
What files were modified?
```

Next:

``` text
Identify potential merge conflicts.
```

Finally:

``` text
Review the code and suggest improvements following Python best practices.
```

------------------------------------------------------------------------

# Task 8 -- Analyze GitHub Actions

Prompt:

``` text
Show the latest failed GitHub Actions workflow.
```

Next:

``` text
Explain why the workflow failed.
```

Next:

``` text
Summarize the workflow logs.
```

Finally:

``` text
Suggest possible fixes and recommend improvements to reduce workflow execution time.
```

------------------------------------------------------------------------

# Task 9 -- Repository Insights

Prompt:

``` text
Summarize repository activity during the last seven days.

Include:
- New Pull Requests
- Closed Pull Requests
- New Issues
- Closed Issues
- Workflow Status
- Recent Releases
```

------------------------------------------------------------------------

# Task 10 -- Generate Release Notes

Prompt:

``` text
Generate release notes for Version 2.4.

Include:
- New Features
- Bug Fixes
- Performance Improvements
- Breaking Changes
- Contributors
- Deployment Notes
```

Review the generated release notes.

------------------------------------------------------------------------

# Challenge Exercise

Generate a sprint health report that includes:

-   Repository Summary
-   Open Issues
-   Critical Bugs
-   Pending Pull Requests
-   Failed Workflows
-   Latest Release
-   Active Contributors
-   Deployment Readiness
-   Recommended Next Actions

Present the report in an executive-friendly format.

------------------------------------------------------------------------

# Discussion Questions

1.  How does GitHub MCP differ from Azure DevOps MCP?
2.  Which GitHub resources can GitHub Copilot access through MCP?
3.  Which actions require user approval?
4.  How does MCP reduce context switching?
5.  What security best practices should be followed when using GitHub
    MCP?

------------------------------------------------------------------------

# Key Takeaways

-   GitHub MCP securely connects GitHub Copilot to GitHub repositories.
-   Natural language can be used to search repositories, manage issues,
    review pull requests, and analyze workflows.
-   MCP transforms GitHub Copilot into a repository-aware AI engineering
    assistant.
-   Human approval is recommended for write operations.
-   MCP improves productivity by reducing context switching.
