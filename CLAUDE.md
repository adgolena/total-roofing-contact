# n8n Workflow Builder

## Project Purpose

This project uses Claude to design and build automation workflows inside a live n8n instance. The goal is to produce high-quality, production-ready workflows by combining Claude's reasoning with direct n8n tooling.

## Available Tools

### 1. n8n MCP Server
Direct API access to the user's n8n instance. Use it to:
- Create, update, activate, and delete workflows
- List existing workflows and inspect their nodes
- Execute workflows and check run results
- Manage credentials and connections

### 2. n8n Skills
Purpose-built skills for workflow construction. Use them to:
- Scaffold common workflow patterns (webhooks, scheduled jobs, data pipelines)
- Generate well-structured node configurations
- Validate workflow logic before deploying

## How to Work in This Project

When the user asks to build or modify a workflow:
1. Clarify the trigger (webhook, schedule, manual, event) and the desired outcome
2. Identify which n8n nodes are needed and in what order
3. Use the n8n MCP server to create or update the workflow directly in the instance
4. Verify the workflow runs correctly by checking execution results
5. Return the workflow name/ID and a brief summary of what it does

## Quality Standards

- Every workflow should have a descriptive name and, where n8n supports it, node notes explaining non-obvious logic
- Prefer native n8n nodes over HTTP Request nodes when an integration exists
- Use expressions (`{{ }}`) over hardcoded values for anything that may vary
- Error handling: add an Error Trigger or On Error path for workflows that affect external systems
- Credentials must be referenced by name — never embed secrets in node parameters
