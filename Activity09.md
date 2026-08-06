# Activity09 – GitHub Copilot Custom DevOps Agent for Azure DevOps

## Objective

Create a GitHub Copilot Custom Agent that acts as a Senior Azure DevOps Engineer. Use the agent to automate CI/CD, generate Azure Pipelines, review pipeline failures, and improve deployment for an ASP.NET Core application such as **eShopOnWeb**.

---

## Prerequisites

- Visual Studio Code
- GitHub Copilot Business or Enterprise
- GitHub Copilot Chat
- Azure DevOps Organization
- Azure DevOps Project
- eShopOnWeb application cloned locally
- Azure Subscription
- Azure App Service (optional)
- Git

---

## Task 1 – Create a Custom Agent

1. Open the **eShopOnWeb** solution in Visual Studio Code.
2. Open **GitHub Copilot Chat**.
3. Select **Agents → Create New Agent**.

**Agent Name**

```text
Azure DevOps DevOps Expert
```

Save the agent as:

```text
.github/chatmodes/Azure DevOps DevOps Expert.chatmode.md
```

---

## Task 2 – Configure the Agent

Use the following instructions.

```text
You are a Senior Azure DevOps Engineer.

Your expertise includes:

- Azure Pipelines
- YAML Pipelines
- Azure App Service
- Azure Container Apps
- Azure Kubernetes Service
- Azure Repos
- Azure Artifacts
- Azure Test Plans
- Azure Boards
- GitHub Copilot
- CI/CD Best Practices

Always:

- Generate production-ready Azure Pipelines.
- Follow Azure DevOps best practices.
- Generate reusable YAML templates.
- Use variables and variable groups.
- Use pipeline caching where appropriate.
- Recommend secure service connections.
- Use deployment stages.
- Include build, test and publish tasks.
- Explain assumptions before generating code.
- Ask clarifying questions if information is missing.
```

Save the agent.

---

## Task 3 – Generate a CI Pipeline

Prompt:

```text
Generate an Azure DevOps YAML pipeline for the eShopOnWeb ASP.NET Core application.

Include:
- Restore NuGet packages
- Build solution
- Execute unit tests
- Publish test results
- Publish build artifacts
- Pipeline caching
```

Verify the generated file:

```text
azure-pipelines.yml
```

---

## Task 4 – Generate a Multi-Stage Pipeline

Prompt:

```text
Convert the CI pipeline into a multi-stage Azure Pipeline.

Stages:
- Build
- Test
- Staging Deployment
- Production Deployment

Use deployment approvals before Production.
```

Review the generated YAML.

---

## Task 5 – Configure Azure App Service Deployment

Prompt:

```text
Extend the pipeline to deploy the published artifacts to Azure App Service.

Use:
- Azure Resource Manager service connection
- Deployment slots
- Production slot swap
```

Verify deployment tasks are generated.

---

## Task 6 – Improve Pipeline Performance

Prompt:

```text
Review the Azure Pipeline and recommend improvements.

Include:
- Caching
- Parallel jobs
- Artifact optimization
- Secure variables
```

Review the recommendations.

---

## Task 7 – Analyze Pipeline Failures

Prompt:

```text
Review the following Azure Pipeline failure and identify:

- Root cause
- Possible fixes
- Recommended best practices
```

Paste any failed pipeline log from Azure DevOps.

Review the generated analysis.

---

## Task 8 – Generate Release Pipeline Documentation

Prompt:

```text
Generate deployment documentation for the Azure DevOps pipeline.

Include:
- Pipeline overview
- Build process
- Deployment stages
- Required service connections
- Environment variables
```

Review the generated documentation.

---

## Task 9 – Review the DevOps Configuration

Prompt:

```text
Review the eShopOnWeb DevOps implementation.

Recommend improvements for:

- Security
- Deployment strategy
- Reliability
- Monitoring
- Maintainability
```

---

## Task 10 – Compare Generic Copilot vs Custom Agent

Run using Generic Copilot:

```text
Generate an Azure DevOps YAML pipeline for eShopOnWeb.
```

Run the same prompt using the **Azure DevOps DevOps Expert** agent.

Compare:

- YAML quality
- Reusability
- Security
- Deployment strategy
- Variable management
- Azure DevOps best practices

---

## Challenge Exercise

Prompt:

```text
Create a complete Azure DevOps CI/CD solution for the eShopOnWeb application.

Requirements:

- Multi-stage YAML pipeline
- Build
- Unit testing
- Code coverage
- Artifact publishing
- Azure App Service deployment
- Staging and Production slots
- Deployment approvals
- Variable groups
- Key Vault integration
- Pipeline caching
- Rollback strategy
- Release documentation
```

---

## Key Takeaways

- Custom DevOps Agents generate consistent Azure DevOps pipelines.
- Project-specific instructions improve CI/CD quality.
- GitHub Copilot can accelerate Azure DevOps implementation for enterprise applications such as eShopOnWeb.
- Custom Agents help standardize DevOps practices across development teams.
