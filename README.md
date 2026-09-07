# Intuz — Your automation partner, one workflow at a time.

<p align="center">
  <picture>
    <img alt="Banner Image" src="https://github.com/user-attachments/assets/210f97fc-0fce-404a-b647-7dfe1302cd37" />
  </picture>
</p>

# Automate GitHub Pull Requests and JIRA Updates from Git Commits

Intuz helps organizations orchestrate AI, automation, and enterprise systems through scalable workflows. Our repository showcases proven implementations across healthcare, operations, customer support, document processing, sales, and back-office functions, enabling teams to accelerate automation initiatives without starting from scratch.

[N8N Creator](https://n8n.io/creators/intuz/) · [AI Automation Services](https://www.intuz.com/ai-automation-services/) · [Workflow Automation](https://www.intuz.com/workflow-automation-services/) · [For Custom Workflow Automation](https://www.intuz.com/get-started/)

---

This n8n template from [Intuz](https://www.intuz.com/) delivers a complete and automated solution to streamline your development workflow for a single repository.

By embedding specific keywords and a JIRA issue ID within your git commit commands, this workflow automatically creates a Pull Request in GitHub and simultaneously updates the corresponding JIRA ticket. This provides a complete, seamless integration that eliminates manual steps and keeps your project management perfectly in sync with your codebase.

## How it works

This workflow acts as a powerful bridge between your Git repository and your project management tools, driven entirely by the structure of your commit messages.

### 1. GitHub Webhook Trigger

The workflow starts when a developer pushes a new commit to a specified repository in GitHub.

### 2. Parse Commit Message

A Code node extracts key information from the commit message:

- The JIRA Issue Key (e.g., `FF-1196`).
- The base branch for the PR (e.g., `development`).
- Action commands like `[auto-pr]` and `[taskcompleted]`.

### 3. Conditional PR Creation

An IF node checks if the `[auto-pr]` command is present.

- **If yes:** It uses the GitHub node to automatically create a pull request from the developer’s branch to the specified base branch.
- **If no:** This step is skipped, allowing for multiple commits before a PR is made.

### 4. Conditional JIRA Update

Another IF node checks for the `[taskcompleted]` command.

- **If yes:** It uses the JIRA node to transition the corresponding issue to your **Done** status, such as **Task Completed** or **In Review**.
- **If no:** The JIRA issue remains in its current state, making it suitable for work-in-progress commits.

## How to Use: Quick Start Guide

### 1. Import the Workflow

Click the **"Use Template"** button to import this workflow into your n8n instance.

### 2. Configure the GitHub Trigger

- Open the **"GitHub Push Trigger"** node. It will display a unique Webhook URL. Copy this URL.
- In your GitHub repository, go to **Settings > Webhooks > Add webhook**.
- Paste the URL into the **Payload URL** field.
- Set the **Content type** to `application/json`.
- Under **"Which events would you like to trigger this webhook?"**, select **Just the push event**.
- Click **Add webhook**.

### 3. Connect Your Accounts

- **GitHub:** Select your GitHub API credential in the **"Create Pull Request"** node.
- **JIRA:** Select your JIRA API credential in the **"Update JIRA Issue Status"** node.

### 4. Customize the JIRA Transition

- Open the **"Update JIRA Issue Status"** node.
- In the **Transition** parameter, set the specific status you want to move the issue to, such as `Done`, `Completed`, or `In Review`.
- You can use the ID or the exact name of the transition from your JIRA project’s workflow.

### 5. Activate the Workflow

Save your changes and activate the workflow. You’re ready to automate!

## Example Commit Message

```bash
git commit -m "FF-1196 Implement OAuth login [auto-pr,development,taskcompleted]"
```
## Key Requirements to Use Template

- An active n8n instance.
- A GitHub account with repository admin permissions to create webhooks.
- A JIRA Cloud account with permissions to update issues.
- Developers who can follow the specified git commit message format.

## Connect with us

- **Website:** https://www.intuz.com/n8n-workflow-automation-templates/
- **Email:** [getstarted@intuz.com](mailto:getstarted@intuz.com)
- **LinkedIn:** https://www.linkedin.com/company/intuz/
- **Get Started:** https://n8n.partnerlinks.io/intuz
- **For Custom Workflow Automation:** https://www.intuz.com/get-started/
