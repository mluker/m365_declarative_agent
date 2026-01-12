# Contributing Guide

## Project Structure

### Configuration Files

- **`m365agents.yml`** - Main project configuration file. Defines provision, deployment, and publish workflows for the agent. Contains app creation, packaging, validation, and Teams Admin Center publishing steps.

- **`m365agents.local.yml`** - Local development environment configuration. Used for testing the agent locally before deploying.

### App Package Files (`appPackage/`)

- **`manifest.json`** - Teams app manifest. Defines app metadata (name, description, icons, permissions) and links to the declarative agent. Update version, name, or developer info here.

- **`declarativeAgent.json`** - Declarative agent configuration. Specifies agent name, description, instructions file, actions (plugins), and capabilities (OneDrive, SharePoint, Email, WebSearch, etc.).

- **`ai-plugin.json`** - API plugin definition. Defines functions available to the agent (e.g., Fabric Data Agent integration). Contains function schemas, parameters, and MCP runtime configurations.

- **`instruction.txt`** - Agent instructions/prompts. Contains the system prompt that defines agent behavior, tool usage rules, and response guidelines.

## Making Changes

### Update Agent Behavior
Edit `appPackage/instruction.txt` to modify how the agent responds and processes requests.

### Add/Remove Capabilities
Edit `appPackage/declarativeAgent.json` to add or remove capabilities like WebSearch, CodeInterpreter, or OneDrive access.

### Modify Functions/Plugins
Edit `appPackage/ai-plugin.json` to add new functions or update existing MCP integrations.

### Change App Details
Edit `appPackage/manifest.json` to update app name, description, icons, or permissions.

## Deployment

### Provision Only

Use the toolkit to `Provision` which will create the agent in your m365 tenant just for you.

1. Update the variable `TEAMS_APP_VERSION` in your .env with a higher version (add it if you don't have it, it looks like `TEAMS_APP_VERSION=1.0.5`)
2. Click `Provision`

![alt text](/images/toolkit.png)

## Workflow

1. **Edit** relevant files based on your changes
2. **Provision** to create/update cloud resources

## Environment Variables

Environment-specific values are stored in `env/` folder and referenced in config files using `${{VARIABLE_NAME}}` syntax.
