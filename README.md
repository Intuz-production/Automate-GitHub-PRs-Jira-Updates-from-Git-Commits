*Intuz — Your automation partner, one workflow at a time.*

<p align="center">
  <picture>
    <img alt="Banner Image" src="https://github.com/user-attachments/assets/210f97fc-0fce-404a-b647-7dfe1302cd37" />
  </picture>
</p>

[Intuz](https://www.intuz.com) helps organizations orchestrate AI, automation, and enterprise systems through scalable workflows. Our repository showcases proven implementations across healthcare, operations, customer support, document processing, sales, and back-office functions, enabling teams to accelerate automation initiatives without starting from scratch.

[N8N Creator](https://n8n.io/creators/intuz/) · [AI Automation Services](https://www.intuz.com/ai-automation-services/) · [Workflow Automation](https://www.intuz.com/workflow-automation-services/) · [For Custom Workflow Automation](https://www.intuz.com/get-started/)

# Automate GitHub Pull Requests and JIRA Updates from Git Commits

This n8n template from Intuz delivers a complete and automated solution to streamline your development workflow for a single repository.

By embedding specific keywords and a JIRA issue ID within your git commit commands, this workflow automatically creates a Pull Request in GitHub and simultaneously updates the corresponding JIRA ticket. This provides a complete, seamless integration that eliminates manual steps and keeps your project management perfectly in sync with your codebase.

## Why this version is different

This is the **single-repository** variant. One GitHub webhook, one repo, one JIRA project workflow.

Intuz also lists a **multi-repo** variant on the n8n template hub for teams that need several repositories to feed the same PR + JIRA automation from one workflow. Use this repo if you only need to cover one GitHub repository. Use the multi-repo listing if you need the same commit-message commands (`[auto-pr]`, `[taskcompleted]`, JIRA key, base branch) across more than one repo.

This workflow does **not** use an LLM. It is driven entirely by commit-message parsing, GitHub, and JIRA — so it is not an AI template.

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
## FAQ

**Is this template free to use?**
Yes. It's an open-source n8n workflow published by Intuz — copy the workflow JSON from this repo and import it into your own n8n instance at no cost.

**Do I need a paid n8n plan to run this?**
No. It runs on n8n's free self-hosted Community Edition or on n8n Cloud. You'll need your own credentials for the services this workflow connects to, not a specific n8n pricing tier.

**Does this work across multiple repositories?**
No. This version is built for a single GitHub repository. Intuz also lists a multi-repo variant on the n8n template hub if you need to cover several repos from one workflow.

**Does it use AI to write the PR or JIRA update?**
No. It parses the commit message for a JIRA key, `[auto-pr]`, `[taskcompleted]`, and the base branch, then calls GitHub and JIRA. There is no LLM step.

## Related n8n templates from Intuz

- [Automate GitHub, JIRA release notes with Google Gemini & notification over email](https://github.com/Intuz-production/Automate-GitHub-Jira-Release-Notes-with-AI)
- [Send pre-meeting Slack briefings using Google Calendar, Notion, GitHub, and Jira](https://github.com/Intuz-production/AI-meeting-assistant)
- [AI-Powered Support Ticket Triage and Routing](https://github.com/Intuz-production/AI-Support-Ticket-Triage-Routing-Automation)

See all of Intuz's free n8n templates: https://www.intuz.com/n8n-workflow-automation-templates/

## Connect with us

Intuz is a USA-based AI & workflow automation company with 16+ years of experience building custom AI-enabled workflow automations for SMBs and Enterprises, specializing in agentic AI, LLM integrations, and CRM/ERP sync across Healthcare, FinTech, eCommerce, Manufacturing, and Real Estate. Explore 30+ free templates at intuz.com/n8n-workflow-automation-templates or get a custom workflow built at intuz.com/get-started.

* **Website:** https://www.intuz.com/
* **Email:** [getstarted@intuz.com](mailto:getstarted@intuz.com)
* **LinkedIn:** https://www.linkedin.com/company/intuz/
* **Get Started:** https://n8n.partnerlinks.io/intuz

## For Custom Workflow Automation

[Click here - Get Started](https://www.intuz.com/get-started/)
