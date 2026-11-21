---
name: platon-cloud
description: Use the Platon Cloud MCP connector to inventory Platon projects, VPSs, VPCs, DNS, domains, storage, inference, email, billing, and support, or to plan and carry out requested changes in Platon Cloud.
---

# Platon Cloud

Use the connected Platon Cloud MCP tools. When the connector is unavailable, use the host's remote MCP setup with `https://api.platoncloud.com/functions/v1/mcp` and sign in through the Platon OAuth consent page. The host handles OAuth credentials.

For a new or ambiguous workspace, call `core_whoami` to identify the authorization scope. Use `project_list` when the request depends on a project that the user did not identify. Check the available tools and their input schemas. Platon filters tool discovery by organization or project scope, permissions, and enabled modules. Explain a missing permission in terms of the requested operation.

- **Inventory and troubleshooting.** Use the relevant list or detail tools and identify the project and resource by name or ID. Follow pagination when the user asks for a complete inventory. Distinguish the provider's current state from a queued change.
- **Provisioning and billing.** For a requested configuration change on existing resources, use the tool's documented `dry_run` when available and report the planned changes. Direct purchases, upgrades, and balance top-ups to the Platon Console. Use billing tools for authorized queries about existing resources and charges.
- **Destructive changes.** Obtain explicit confirmation for the specific action and resource before calling a destructive tool. Supply only the confirmation fields its schema requires, such as the resource name, slug, or `confirm`. Report queued operations as pending until the status tool confirms the outcome.
- **Credentials.** Direct the user to the Platon Console when they need passwords, API keys, or other secrets. Keep credential values out of chat and generated artifacts.

[Platon MCP tool catalog and OAuth details](https://api.platoncloud.com/functions/v1/mcp/llms.txt)
