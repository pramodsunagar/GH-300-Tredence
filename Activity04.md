# GitHub Copilot MCP with Azure DevOps -- Hands-on Lab

## Lab Title

**Using GitHub Copilot MCP to Work with Azure DevOps**

## Target Audience

-   Intermediate Python Developers
-   Backend Developers
-   DevOps Engineers

------------------------------------------------------------------------

## Learning Objectives

By the end of this lab, you will be able to:

-   Understand the purpose of Model Context Protocol (MCP)
-   Configure an Azure DevOps MCP Server
-   Connect GitHub Copilot to Azure DevOps
-   Query Azure Boards, Repositories, Pull Requests, and Pipelines using
    natural language
-   Create Azure DevOps work items from GitHub Copilot
-   Generate sprint and executive summaries using MCP

------------------------------------------------------------------------

## Prerequisites

-   Visual Studio Code (latest)
-   GitHub Copilot Business or Enterprise
-   GitHub Copilot Chat extension
-   Agent Mode enabled
-   Azure DevOps organization and project
-   Azure DevOps Personal Access Token (PAT)
-   Azure DevOps MCP Server
-   Python 3.11 or later

------------------------------------------------------------------------

# Scenario

Your development team uses Azure DevOps for planning, source control,
pull requests, and CI/CD. Instead of switching between Visual Studio
Code and the Azure DevOps portal, you will use GitHub Copilot with an
Azure DevOps MCP server to perform common development tasks using
natural language.

------------------------------------------------------------------------

# Task 1 -- Configure the Azure DevOps MCP Server

Configure the following environment variables:

``` text
AZURE_DEVOPS_ORG=https://dev.azure.com/<organization>
AZURE_DEVOPS_PROJECT=<project-name>
AZURE_DEVOPS_PAT=<personal-access-token>
```

Start the MCP server according to your installation instructions.

Verify that the server starts successfully without errors.

------------------------------------------------------------------------

# Task 2 -- Configure VS Code

Open the VS Code `settings.json` file and register the MCP server.

Example:

``` json
{
  "mcp": {
    "servers": {
      "azure-devops": {
        "command": "node",
        "args": ["server.js"]
      }
    }
  }
}
```

Restart Visual Studio Code.

Open GitHub Copilot Chat and verify that the Azure DevOps MCP server is
available.

------------------------------------------------------------------------

# Task 3 -- Discover Available MCP Tools

Open GitHub Copilot Chat and switch to **Agent Mode**.

Prompt:

``` text
List all tools exposed by the Azure DevOps MCP server.
```

Observe the available capabilities such as:

-   Azure Boards
-   Work Items
-   Repositories
-   Pull Requests
-   Pipelines
-   Wiki
-   Test Plans

------------------------------------------------------------------------

# Task 4 -- Query Azure Boards

Prompt:

``` text
Show all active User Stories assigned to me.
```

Next, execute:

``` text
Which work item has the highest priority?
```

Finally:

``` text
Summarize all active bugs in the current sprint.
```

------------------------------------------------------------------------

# Task 5 -- Search the Repository

Prompt:

``` text
Search the Backend repository for authentication middleware.
```

Next:

``` text
Which file contains JWT validation?
```

Finally:

``` text
Explain how authentication is implemented in this repository.
```

------------------------------------------------------------------------

# Task 6 -- Create a Work Item

Prompt:

``` text
Create a Product Backlog Item.

Title:
Improve Login Performance

Description:
Investigate slow authentication response when more than 500 concurrent users access the API.

Priority:
1
```

Review the generated work item and approve the action.

Verify that the work item appears in Azure Boards.

------------------------------------------------------------------------

# Task 7 -- Review Pull Requests

Prompt:

``` text
List all active pull requests.
```

Next:

``` text
Summarize Pull Request #42.
```

Then:

``` text
What files were modified in Pull Request #42?
```

Finally:

``` text
Highlight potential risks before approving this pull request.
```

------------------------------------------------------------------------

# Task 8 -- Investigate Pipelines

Prompt:

``` text
Show the latest failed pipeline.
```

Next:

``` text
Why did this pipeline fail?
```

Then:

``` text
Summarize the build logs.
```

Finally:

``` text
Suggest possible fixes.
```

------------------------------------------------------------------------

# Task 9 -- Generate a Sprint Summary

Prompt:

``` text
Generate a sprint summary including:

- Completed User Stories
- Open Bugs
- Pending Pull Requests
- Failed Pipelines
- Deployment Status
```

------------------------------------------------------------------------

# Task 10 -- Generate an Executive Report

Prompt:

``` text
Create an executive summary for today's development activities.

Include:
- Repository activity
- Completed work
- Open issues
- Deployment health
- Code review status

Keep the report concise.
```

------------------------------------------------------------------------

# Challenge Exercise

Generate a release readiness report that includes:

-   Sprint Progress
-   Critical Bugs
-   Pending Pull Requests
-   Latest Build Status
-   Deployment Readiness
-   Top Risks
-   Recommended Next Actions

Present the report in a format suitable for a release review meeting.

------------------------------------------------------------------------

# Discussion Questions

1.  How does MCP differ from standard GitHub Copilot Chat?
2.  What Azure DevOps services can be accessed through MCP?
3.  Why is user approval important for write operations?
4.  How does MCP reduce developer context switching?
5.  What security considerations should be followed when using MCP?

------------------------------------------------------------------------

# Key Takeaways

-   MCP allows GitHub Copilot to securely interact with Azure DevOps.
-   Natural language can be used to query and update Azure DevOps
    resources.
-   Developers can reduce context switching and improve productivity.
-   Human review and approval remain essential before executing write
    operations.
