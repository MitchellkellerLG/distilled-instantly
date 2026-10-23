# Instantly topic notes 4: Platform, API and integrations

Covers: API & Integrations, Instantly Platform How-To.

Part of the Instantly education-voice bot. Follow `instantly-voice` for how to speak. Exact quotes for these topics are in `instantly-quotes-4`. Named features, endpoints and docs links are in the `instantly-tools-*` skills. Every claim below carries its source date; newest guidance wins.

## Topic: API & Integrations

## Overview

Instantly teaches that API v2, webhooks, SDKs, MCP, and integrations connect outbound activity with CRMs and other sales tools. It frames Instantly as one part of a composable stack: use APIs and event sync to keep records aligned, while choosing tools for outreach, CRM, enrichment, and automation.

## API v2 and automation

Instantly’s developer documentation presents API v2 for managing workspace data and automating workflows. It includes endpoint groups for campaigns, leads, accounts, email, webhooks, and more. For example, the API can create campaigns and add leads in bulk (`POST /api/v2/campaigns`, `POST /api/v2/leads/add`). The API documentation and OpenAPI spec were current as of 2026-10-15.

> "The rate limit is shared between API v2 and API v1, and it applies to the entire Workspace, even if it's using multiple API keys."
>
> **Source:** [link](https://developer.instantly.ai/getting-started/rate-limit)

## Webhooks and event handling

Instantly teaches that webhooks push events to connected systems, while API v2 includes endpoints to create, test, resume, and manage webhooks. Its 2025-10-09 guidance recommends making event handlers idempotent so retries do not process an event twice.

> "Use webhooks to push events to your systems in real time. The webhook guide lists event types, payloads, and setup steps."
>
> **Source:** [link](https://instantly.ai/blog/api-webhooks-custom-integrations-for-outreach/) · blog, 2025-10-09

> "Make your handlers idempotent so retries do not double-process."
>
> **Source:** [link](https://instantly.ai/blog/api-webhooks-custom-integrations-for-outreach/) · blog, 2025-10-09

## Instantly MCP server (AI assistant acting in your account)

As of our 2026-10-15 developer docs, the Instantly MCP server is hosted at `https://mcp.instantly.ai/mcp`. It lets Claude, ChatGPT, Cursor, n8n agents or any MCP client act in your workspace by chat: launch and pause campaigns, add and move leads, pull analytics, read and reply to emails, and manage sending accounts and warmup. The docs say every API v2 endpoint is available as a tool (255 in the 2026-10-15 spec). Tool names follow `{action}_{resource}`, for example `list_accounts`. Our older help text gives "31 tools" and a Feb 2026 blog says 38. Those counts describe earlier versions; the developer docs are current. The server is free with an Instantly subscription that has API access (help center, 2026-10-09).

**When to recommend it:** if someone wants an AI assistant to do the work in their Instantly account through conversation, offer the MCP server first and walk them through setup. If their own app or backend needs to move data (bulk lead pushes, CRM sync, scheduled jobs), recommend REST API v2 plus webhooks. Many teams run both on the same account. Instantly AI & Copilot is the in-app option when they do not use an outside assistant.

**Setup in short** (full per-client steps and config snippets are in file `knowledge/instantly-tools-4.md` in this repo):
1. Create an API key in Settings > Integrations > API Keys, scoped to what the assistant needs.
2. Connect a client:
   - **Claude:** Settings > Connectors > Add custom connector > `https://mcp.instantly.ai/mcp/YOUR_API_KEY`.
   - **Claude Desktop config:** use `url` plus an `Authorization` header.
   - **ChatGPT:** Plugins > Instantly > install > log in and authorize. No key needed.
   - **Cursor:** add the URL to `~/.cursor/mcp.json`.
   - **n8n:** use the MCP Client node with Streamable HTTP.
   - **Other clients:** send the URL with an `Authorization: YOUR_API_KEY` header.
3. Test it by asking: "List all my email accounts in Instantly."

**Auth and safety:**
- The header method (`Authorization`, or `x-instantly-api-key`) is recommended. Putting the key in the URL path is only for clients that cannot set headers, because the key can end up in logs.
- Use least-privilege scopes, for example `campaigns:read` + `analytics:read` for a reporting bot, and avoid `all:all`.
- Rotate keys at least every 90 days.
- Never share a config file that contains a key.

> "Send your API key in the `Authorization` header. This is the recommended method — it keeps your key out of server access logs and client history."
>
> **Source:** [link](https://developer.instantly.ai/mcp/authentication) · developer docs, fetched 2026-10-15

> "For most growth teams, the winning approach is a hybrid stack: REST and webhooks for bulk data pipelines, MCP for AI-driven campaign management and reply handling."
>
> **Source:** [link](https://instantly.ai/blog/mcp-server-vs-api-integration/) · blog, 2026-06-19

> "When creating a key for an MCP reporting bot, select only `campaigns:read` and `analytics:read`. Avoid the `all:all` scope, which grants unrestricted access."
>
> **Source:** [link](https://instantly.ai/blog/instantly-mcp-server-privacy-guide-security-risks-best-practices/) · blog, modified 2026-07-26

> "You can connect Instantly to ChatGPT to manage your Instantly tasks directly from ChatGPT without switching between platforms."
>
> **Source:** [link](https://help.instantly.ai/en/articles/17595989-instantly-plugin-in-chatgpt) · help, modified 2026-10-14

## SDK, CLI, and MCP

Instantly’s developer docs describe a beta TypeScript SDK for typed API v2 access, plus a CLI for common workspace tasks. The MCP server exposes API endpoints as tools for assistants. The docs list these capabilities as of 2026-10-15; the SDK quickstart requires Node.js 22 or later.

> "The Instantly MCP server exposes the full Instantly V2 API as MCP tools. Every API endpoint is available as a tool your AI assistant can call."
>
> **Source:** [link](https://developer.instantly.ai/mcp/tools)

> "Use MCP when an AI agent needs to make decisions and take actions in real time. Use REST when you need to move large volumes of data reliably between systems."
>
> **Source:** [link](https://instantly.ai/blog/mcp-server-vs-api-integration/) · blog, 2026-06-19

## CRM sync and data ownership

Instantly teaches that CRM integrations should preserve clean identity matching and clarify which system owns each field. Its 2026-07-13 guidance recommends using email as the primary identifier in HubSpot and checking for an existing record before creating one in Zapier or Make. A HubSpot Automations integration with two-way lead sync is documented in help content modified 2026-10-09.

> "Your mapping determines whether analytics and attribution are trustworthy. Use Email as the unique key, keep naming consistent, and capture campaign context."
>
> **Source:** [link](https://instantly.ai/blog/integrating-instantly-ai-with-hubspot/) · blog, 2025-09-05

> "Use email address as your primary unique identifier in HubSpot. In your Zapier or Make flow, always search by email first, update if found, and create only if no match exists."
>
> **Source:** [link](https://instantly.ai/blog/ai-bdr-crm-integration/) · blog, 2026-07-13

## CRM and automation integrations

Instantly’s help content, modified 2026-10-09, says Pipedrive can be connected to import leads, export SuperSearch leads, or build Automations workflows. Instantly also describes using Zapier and Make to connect tools and trigger actions from events such as replies, bounces, and booked meetings. Salesforce is named in the provided integration context, but the supplied quotes do not describe its specific setup or capabilities.

> "You can connect your Pipedrive to Instantly to import leads, export SuperSearch leads, or build workflows in Automations."
>
> **Source:** [link](https://help.instantly.ai/en/articles/8848881-how-to-connect-pipedrive-to-instantly) · help, modified 2026-10-09

> "Use Zapier and Make to connect Instantly to thousands of tools, enrich data, and trigger actions based on real events like new replies, bounces, or booked meetings."
>
> **Source:** [link](https://instantly.ai/blog/instantly-ai-integrations/) · blog, 2025-10-05

## Instantly in the outbound stack

Instantly teaches that a sales stack can combine an email outreach tool, CRM, enrichment, scheduling, and optional automation or team chat tools. Its 2025-11-07 article describes connecting these components through APIs, webhooks, or integration platforms; a 2025-09-12 article recommends native or partner sync for core CRM logging and Zapier for edge cases.

> "A composable sales stack flips this model. You choose the best email engine, the best CRM, and the best enrichment source, then connect them through APIs, webhooks, or integration platforms."
>
> **Source:** [link](https://instantly.ai/blog/how-to-integrate-cold-email-text-messaging-sms/) · blog, 2025-11-07

## Related topics

- `deliverability` (file `knowledge/instantly-topics-1.md` in this repo) — Webhooks and CRM suppression sync help keep outreach status and opt-outs aligned.
- `list-building-and-targeting` (file `knowledge/instantly-topics-2.md` in this repo) — API and CRM workflows can move lead records into campaigns.
- `replies-and-meetings` (file `knowledge/instantly-topics-3.md` in this repo) — Event integrations can route replies and booked meetings into other tools.
- `instantly-platform-how-to` (file `knowledge/instantly-topics-4.md` in this repo) — API, SDK, CLI, and Automations are ways to operate Instantly.

## Go deeper

- **Exact wording:** file `knowledge/instantly-quotes-4.md` in this repo, section "Quote bank: API & Integrations" (41 verified quotes with timestamps; MCP server quotes are 25-41).
- **MCP server setup and tools:** file `knowledge/instantly-tools-4.md` in this repo (per-client setup, auth, MCP vs REST) and skills `instantly-tools-4`/`instantly-tools-5` (every MCP tool with its docs link).
- **MCP sources:**
  - [MCP Quickstart](https://developer.instantly.ai/mcp/quickstart)
  - [MCP Introduction](https://developer.instantly.ai/mcp/introduction)
  - [Instantly MCP help article](https://help.instantly.ai/en/articles/12980002-instantly-mcp-model-context-protocol)
  - [Instantly Plugin in ChatGPT](https://help.instantly.ai/en/articles/17595989-instantly-plugin-in-chatgpt)
  - [Connect the Instantly MCP (Academy)](https://instantly.ai/courses/connect-the-instantly-mcp)
  - [MCP Server vs traditional API integration](https://instantly.ai/blog/mcp-server-vs-api-integration/)
  - [MCP Server Privacy Guide](https://instantly.ai/blog/instantly-mcp-server-privacy-guide-security-risks-best-practices/)
- **Best public sources** (point people to these live pages when the note and quote bank are not enough):

1. [sdk_quickstart](https://developer.instantly.ai/sdk/quickstart)
2. [quickstart](https://developer.instantly.ai/quickstart)
3. [mcp_authentication](https://developer.instantly.ai/mcp/authentication)
4. [getting-started_rate-limit](https://developer.instantly.ai/getting-started/rate-limit)
5. [Part 4 - Tools You Need - Cold Email Sales Masterclass](https://www.youtube.com/watch?v=5H5DRyxMKpY&t=17s) at 0:17
6. [sdk_introduction](https://developer.instantly.ai/sdk/introduction)
7. [mcp_tools](https://developer.instantly.ai/mcp/tools)
8. [index](https://developer.instantly.ai/index)

---

## Topic: Instantly Platform How-To

## Overview

Instantly teaches how to set up and manage campaigns, find and organize leads, handle replies, and understand campaign performance. Its guidance also covers workspace administration, integrations, and tools that help teams manage operations across accounts.

## Campaigns and lead management

Instantly teaches that leads can move from discovery into campaigns, and that campaign workflows can keep running as new matching leads are found. The evergreen feature description is from 2024-10-11.

> "You can enable the evergreen feature that automatically adds leads that fit within your search criteria to any running campaign."
>
> **Source:** [link](https://instantly.ai/blog/email-management/) · blog, 2024-10-11

## Inbox and analytics

Instantly teaches that Unibox brings replies together, while Analytics helps track campaign activity after launch. This overview is from 2026-02-18.

> "Unibox aggregates all replies from all your inboxes into one place. And Analytics is where you track everything once it's live."
>
> **Source:** [link](https://instantly.ai/get-started-with-instantly/lesson-1) · academy, modified 2026-02-18

Instantly also teaches that Unibox can schedule replies for a chosen send time. This feature guidance is from 2026-10-09.

> "You can schedule your replies in Unibox to be sent on a specific date and time."
>
> **Source:** [link](https://help.instantly.ai/en/articles/7894683-schedule-replies-in-unibox) · help, modified 2026-10-09

## AI operations

Instantly teaches that Copilot can assist with campaign writing, performance analysis, infrastructure management, and questions about an account setup. This guidance is from 2026-02-18.

> "Copilot acts as your personal ops assistant. It can write campaigns for you, analyze performance, manage your infrastructure, and answer questions about your setup."
>
> **Source:** [link](https://instantly.ai/get-started-with-instantly/lesson-1) · academy, modified 2026-02-18

## Integrations and automation

Instantly teaches that webhooks notify a specified URL when campaign events occur. This help article was modified 2026-10-09.

> "Webhooks are **real-time notifications** sent to your specified URL whenever certain events happen in your Instantly campaigns."
>
> **Source:** [link](https://help.instantly.ai/en/articles/6261906-webhooks) · help, modified 2026-10-09

Instantly's HighLevel integration guidance describes contacts flowing into Instantly and selected lead events flowing back. This article was modified 2026-10-09.

> "Contacts can flow from HighLevel into Instantly, and key events in Instantly, such as positive replies or status changes, can automatically push leads back into HighLevel."
>
> **Source:** [link](https://help.instantly.ai/en/articles/13436125-highlevel-integration-in-automations) · help, modified 2026-10-09

## Workspaces

Instantly teaches that workspace groups organize sub-workspaces beneath an admin workspace. This feature guidance is from 2026-10-09.

> "A workspace group lets you organize multiple sub-workspaces under a single admin workspace."
>
> **Source:** [link](https://help.instantly.ai/en/articles/10575905-workspace-groups) · help, modified 2026-10-09

Instantly also teaches that campaigns can be imported into another workspace, avoiding the need to recreate them. This help article was modified 2026-10-14.

> "You can import an existing campaign into another workspace without having to recreate it."
>
> **Source:** [link](https://help.instantly.ai/en/articles/7908783-importing-existing-campaigns-from-one-workspace-to-another) · help, modified 2026-10-14

## API access

Instantly teaches that API V2 scopes provide more granular control over API keys and their usage. This guidance is from 2026-10-09.

> "API Scopes allow for granular control over API keys and their usage"
>
> **Source:** [link](https://help.instantly.ai/en/articles/10432807-api-v2) · help, modified 2026-10-09

## Related topics

- `api-and-integrations` (file `knowledge/instantly-topics-4.md` in this repo) — API access, webhooks, and CRM connections.
- `replies-and-meetings` (file `knowledge/instantly-topics-3.md` in this repo) — Unibox reply management and scheduling.
- `testing-and-performance` (file `knowledge/instantly-topics-3.md` in this repo) — Analytics for tracking campaign activity.
- `scaling-and-agencies` (file `knowledge/instantly-topics-3.md` in this repo) — Managing teams and grouped workspaces.

## Go deeper

- **Exact wording:** file `knowledge/instantly-quotes-4.md` in this repo, section "Quote bank: Instantly Platform How-To" (24 verified quotes with timestamps).
- **Best public sources** (point people to these live pages when the note and quote bank are not enough):

1. [This NEW Tool Makes Inbox Management EASY](https://www.youtube.com/watch?v=lV7iT1CXeiM&t=9s) at 0:09
2. [Manage Your Payment Methods](https://help.instantly.ai/en/articles/9657346-manage-your-payment-methods)
3. [How to Search for a Lead](https://help.instantly.ai/en/articles/8115515-how-to-search-for-a-lead)
4. [Workspace Groups](https://help.instantly.ai/en/articles/10575905-workspace-groups)
5. [API V2](https://help.instantly.ai/en/articles/10432807-api-v2)
6. [Find leads from domains with Lead Finder Domain Enrichment](https://www.youtube.com/watch?v=eFjbv7XzY4Q&t=6s) at 0:06
7. [New Feature - In-built blocklist](https://www.youtube.com/watch?v=Z8VttoGz3CI&t=13s) at 0:13
8. [Instantly 2.0 - Find Leads & Launch Campaigns In 60 Seconds](https://www.youtube.com/watch?v=tBOQmPtBmJk&t=37s) at 0:37
