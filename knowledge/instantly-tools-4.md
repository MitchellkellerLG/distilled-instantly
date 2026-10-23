# Instantly tools catalog 4 of 5

This skill holds: Part 4, Instantly MCP server (what it is, MCP vs REST, setup by client, auth and scopes, tool count) plus MCP tools for: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists, CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification.

Rules: name the feature or endpoint, give its exact docs link and say "as of <date>"; suggest checking the live docs. Recommend only items listed in the `instantly-tools-*` skills; never invent a feature, endpoint, parameter, limit or plan. Always write API keys as `YOUR_API_KEY`; never ask for or repeat a real key.

Where the rest of the catalog lives:
- `instantly-tools-1`: Part 1 (product features and tools) and Part 2 (developer guides)
- `instantly-tools-2`: Part 3, API v2 endpoint groups: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists
- `instantly-tools-3`: Part 3, API v2 endpoint groups: CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification, AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members
- `instantly-tools-4`: Part 4, Instantly MCP server (what it is, MCP vs REST, setup by client, auth and scopes, tool count) plus MCP tools for: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists, CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification
- `instantly-tools-5`: Part 4 continued, MCP tools for: AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members

---

## Part 4: Instantly MCP server (as of 2026-10-15)

Sources: developer.instantly.ai MCP pages ([Introduction](https://developer.instantly.ai/mcp/introduction), [Quickstart](https://developer.instantly.ai/mcp/quickstart), [Authentication](https://developer.instantly.ai/mcp/authentication), [Available tools](https://developer.instantly.ai/mcp/tools)), re-fetched live 2026-10-15 and unchanged; help article [Instantly MCP (Model Context Protocol)](https://help.instantly.ai/en/articles/12980002-instantly-mcp-model-context-protocol) (modified 2026-10-09); [Instantly Plugin in ChatGPT](https://help.instantly.ai/en/articles/17595989-instantly-plugin-in-chatgpt) (modified 2026-10-14); Academy lesson [Connect the Instantly MCP](https://instantly.ai/courses/connect-the-instantly-mcp) (2026-03-19); blog [MCP Server vs traditional API integration](https://instantly.ai/blog/mcp-server-vs-api-integration/) (2026-06-19) and [MCP server privacy guide](https://instantly.ai/blog/instantly-mcp-server-privacy-guide-security-risks-best-practices/) (modified 2026-07-26). Shipped per @InstantlyAI on X, 2025-12-02 (announced "coming soon" 2025-09).

### What it is

The Instantly MCP server is our hosted [Model Context Protocol](https://modelcontextprotocol.io) server. It lets an AI assistant (Claude, ChatGPT, Cursor, n8n agents, any MCP client) act directly in your Instantly workspace by chat: create and launch campaigns, add and move leads, pull analytics, read and reply to emails, manage sending accounts and warmup. It is free with your Instantly subscription; you just need an account with API access (help center, 2026-10-09).

| Item | Value (as of 2026-10-15) |
|---|---|
| Server URL | `https://mcp.instantly.ai/mcp` (hosted, nothing to install) |
| Transport | Streamable HTTP (remote server) |
| Auth, recommended | API v2 key in the `Authorization` header (`Authorization: YOUR_API_KEY`; `Bearer YOUR_API_KEY` also accepted) |
| Auth, alt header | `x-instantly-api-key: YOUR_API_KEY` for clients that cannot set `Authorization` |
| Auth, URL path | `https://mcp.instantly.ai/mcp/YOUR_API_KEY`, only for clients that cannot set headers (the key can end up in logs) |
| Auth, OAuth | The ChatGPT plugin connects by logging in to Instantly and authorizing (no key to paste). The live server also advertises OAuth discovery (authorization server `https://api.instantly.ai`, authorization-code flow with PKCE), observed 2026-10-15. |
| Tools | Every API v2 endpoint as one tool (255 endpoints in the 2026-10-15 spec, listed below). Names follow `{action}_{resource}`. |
| Cost | Free with your Instantly subscription; AI agent actions it triggers still use Instantly Credits |
| Docs | [Introduction](https://developer.instantly.ai/mcp/introduction) · [Quickstart](https://developer.instantly.ai/mcp/quickstart) · [Authentication](https://developer.instantly.ai/mcp/authentication) · [Available tools](https://developer.instantly.ai/mcp/tools) · [Help article](https://help.instantly.ai/en/articles/12980002-instantly-mcp-model-context-protocol) |

Placeholders only: always write `YOUR_API_KEY`. Never ask for, repeat or store a real key. Tell people to keep their key private, never share an MCP config file that contains it, and never commit it to source control.

### MCP server or REST API: which do we recommend?

From our blog (2026-06-19): "Use MCP when an AI agent needs to make decisions and take actions in real time. Use REST when you need to move large volumes of data reliably between systems."

| Situation | Recommend |
|---|---|
| "I want Claude / ChatGPT / Cursor to launch campaigns, add leads, pull stats, pause losers, reply to emails for me" | **MCP server first** (setup below) |
| Weekly performance reviews, reply triage, campaign changes driven by an AI agent in conversation | **MCP server** |
| My app or backend pushes leads into Instantly, syncs CRM data, runs on a schedule, needs high volume | **REST API v2** (Part 3, skills `instantly-tools-2`/`instantly-tools-3`, e.g. `POST /api/v2/leads/add`) |
| My system must react the moment something happens (reply, bounce, interested) | **Webhooks** (Hyper Growth or above), plus REST |
| Both | Run both on the same account: REST and webhooks for data pipelines, MCP for AI-driven campaign management and reply handling. The MCP server wraps API v2, so the same API keys work. |
| Fast campaign generation inside the Instantly app, no outside AI | **Instantly AI & Copilot** (Part 1, file `knowledge/instantly-tools-1.md` in this repo) |

### Setup by client (as of 2026-10-15)

**Step 1, every client except ChatGPT: create an API key.** In Instantly go to **Settings > Integrations > API Keys** ([link](https://app.instantly.ai/app/settings/integrations)), click **Create API Key**, choose scopes (see Auth below), copy the key and store it safely.

**Claude Desktop / Claude.ai (custom connector, easiest).** Settings > Connectors > **Add custom connector**. Name it (for example "Instantly MCP"), enter `https://mcp.instantly.ai/mcp/YOUR_API_KEY` with your key in place of the placeholder, click **Add**. No restart needed. Under **Configure** you can set read, write and delete tools to "always allow" or keep per-action approval. Our blog notes the full connector settings need a paid Claude plan (Pro, Max, Team or Enterprise).

**Claude Desktop (config file).** Settings > Developer > **Edit Config**, add:

```json
{
  "mcpServers": {
    "instantly": {
      "url": "https://mcp.instantly.ai/mcp",
      "headers": { "Authorization": "YOUR_API_KEY" }
    }
  }
}
```
Save, then fully quit and restart Claude Desktop.

**ChatGPT (Instantly plugin).** ChatGPT > **Plugins** > search **Instantly** > click **+** to install > log in to Instantly if asked > **Authorize** the connection. Then ask ChatGPT to create or manage campaigns, check replies or pull performance data. No API key to paste ([help](https://help.instantly.ai/en/articles/17595989-instantly-plugin-in-chatgpt), 2026-10-14).

**Cursor.** Cursor > Settings > search **MCP** > edit, or add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "instantly": { "url": "https://mcp.instantly.ai/mcp/YOUR_API_KEY" }
  }
}
```
Save and restart Cursor.

**n8n (AI agent workflows).** Add the **MCP Client** node, choose **Streamable HTTP** transport, URL `https://mcp.instantly.ai/mcp/YOUR_API_KEY`, connect it to your AI Agent node. Give each agent only the tools it needs.

**Windsurf and any other MCP client.** URL `https://mcp.instantly.ai/mcp` with header `Authorization: YOUR_API_KEY`. If the client cannot set headers, use `https://mcp.instantly.ai/mcp/YOUR_API_KEY`.

**Test it.** Ask: "List all my email accounts in Instantly." The assistant should call `list_accounts`. Or "What campaigns do I have in Instantly?"

**Troubleshooting (help center, 2026-10-09).** Connection failed: check the key. Unauthorized: regenerate the key. No response: restart the client. Server unavailable: check your connection and retry.

**Hosted vs local.** Some of our older posts (Feb 2026) describe a community-maintained local Python package (Python 3.10+, `claude_desktop_config.json`). Newer docs use the hosted server at `mcp.instantly.ai`, which needs no install. Recommend the hosted server.

### Auth and API key scopes

- The MCP server uses the same API v2 keys and scopes as REST ([Authorization guide](https://developer.instantly.ai/getting-started/authorization)). The assistant can only do what the key allows.
- **Least privilege** (security guide, modified 2026-07-26): a reporting bot gets `campaigns:read` + `analytics:read`; a campaign-building assistant gets `campaigns:create` + `leads:create` but not `api_keys:delete` or billing. Avoid `all:all` unless you really need full access. (The March 2026 Academy lesson selects "All" scopes for simplicity; the newer security guidance wins.)
- Use separate keys per assistant or per client, rotate keys at least every 90 days, and delete any leaked key right away.
- Destructive tools (delete) are clearly marked. In Claude you can require approval per action.
- Scopes per tool are the ones listed for its endpoint in Part 3 (files `knowledge/instantly-tools-2.md` and `knowledge/instantly-tools-3.md` in this repo). Scope format: `<resource>:<create|read|update|delete|all>` or `all:<action>`.

### Tool count note

The developer docs (live 2026-10-15) say the server "exposes the full Instantly V2 API as MCP tools" and tools are auto-generated from the API spec, so the 255 endpoints below are the tool set as of 2026-10-15. Older material gives smaller counts: the help center's n8n tip says "31 tools across 5 categories" and a Feb 2026 blog says 38 tools across 6. Those describe the earlier tool set; the developer docs are the current source. The connected client always shows the live list, so if someone needs exact tool names, tell them to ask their assistant to list the Instantly tools.

### Every MCP tool (one per API v2 endpoint, as of 2026-10-15)

Tool names follow `{action}_{resource}`. Names confirmed in our docs: `list_accounts`, `list_campaigns`, `create_lead`, `get_campaign_analytics`. For the rest, refer to the tool by what it does (the "Tool" column is the endpoint's docs title) and let the client show its exact name. Parameters and responses are on each docs page.

#### Email Accounts (16 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create account** | Create account. | `POST /api/v2/accounts` | [docs](https://developer.instantly.ai/api-reference/account/create-account) | 2026-10-15 |
| **Delete account** | Delete account. | `DELETE /api/v2/accounts/{email}` | [docs](https://developer.instantly.ai/api-reference/account/delete-account) | 2026-10-15 |
| **Disable warmup for accounts** | Initiates a background job to disable warmup for the specified accounts. The response will contain the initial background job object. You can… | `POST /api/v2/accounts/warmup/disable` | [docs](https://developer.instantly.ai/api-reference/account/disable-warmup-for-accounts) | 2026-10-15 |
| **Enable warmup for accounts** | Initiates a background job to enable warmup for the specified accounts. The response will contain the initial background job object. You can… | `POST /api/v2/accounts/warmup/enable` | [docs](https://developer.instantly.ai/api-reference/account/enable-warmup-for-accounts) | 2026-10-15 |
| **Get account** | Get account. | `GET /api/v2/accounts/{email}` | [docs](https://developer.instantly.ai/api-reference/account/get-account) | 2026-10-15 |
| **Get custom tracking domain status** | Get custom tracking domain status. | `GET /api/v2/accounts/ctd/status` | [docs](https://developer.instantly.ai/api-reference/account/get-custom-tracking-domain-status) | 2026-10-15 |
| **Get daily account analytics** | Get daily account analytics showing the number of emails sent per day for each email account. Useful for tracking daily sending activity across… | `GET /api/v2/accounts/analytics/daily` | [docs](https://developer.instantly.ai/api-reference/account/get-daily-account-analytics) | 2026-10-15 |
| **Get warmup analytics** | Get warmup analytics. | `POST /api/v2/accounts/warmup-analytics` | [docs](https://developer.instantly.ai/api-reference/account/get-warmup-analytics) | 2026-10-15 |
| **List account** (`list_accounts`) | List account. | `GET /api/v2/accounts` | [docs](https://developer.instantly.ai/api-reference/account/list-account) | 2026-10-15 |
| **Mark an account as fixed** | Sets the account to active and clears leftover error metadata such as status_message. Idempotent when the account is already active. | `POST /api/v2/accounts/{email}/mark-fixed` | [docs](https://developer.instantly.ai/api-reference/account/mark-an-account-as-fixed) | 2026-10-15 |
| **Move accounts between workspaces** | Move accounts between workspaces. IMPORTANT: this endpoint should be called ONLY with an ADMIN workspace API key (check the workspace group docs:… | `POST /api/v2/accounts/move` | [docs](https://developer.instantly.ai/api-reference/account/move-accounts-between-workspaces) | 2026-10-15 |
| **Patch account** | Patch account. | `PATCH /api/v2/accounts/{email}` | [docs](https://developer.instantly.ai/api-reference/account/patch-account) | 2026-10-15 |
| **Pause an account** | Pause an account. | `POST /api/v2/accounts/{email}/pause` | [docs](https://developer.instantly.ai/api-reference/account/pause-an-account) | 2026-10-15 |
| **Pause multiple accounts** | Pauses up to 100 email accounts in the authenticated workspace. Each unique email is returned in either `paused_emails` or `failed_emails`. | `POST /api/v2/accounts/pause` | [docs](https://developer.instantly.ai/api-reference/account/pause-multiple-accounts) | 2026-10-15 |
| **Resume a paused account** | Resume a paused account. | `POST /api/v2/accounts/{email}/resume` | [docs](https://developer.instantly.ai/api-reference/account/resume-a-paused-account) | 2026-10-15 |
| **Test account vitals** | Test account vitals. | `POST /api/v2/accounts/test/vitals` | [docs](https://developer.instantly.ai/api-reference/account/test-account-vitals) | 2026-10-15 |

#### Account Campaign Mapping (1 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get campaigns associated with an email** | Get campaigns associated with an email. | `GET /api/v2/account-campaign-mappings/{email}` | [docs](https://developer.instantly.ai/api-reference/accountcampaignmapping/get-campaigns-associated-with-an-email) | 2026-10-15 |

#### AI Deliverability Agent (13 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Complete a Deliverability Agent feed item** | Mark a supported pending recommendation complete after the default agent verifies that its underlying issue has been resolved. Currently,… | `POST /api/v2/ai-agents/deliverability/feed-items/{id}/complete` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/complete-a-deliverability-agent-feed-item) | 2026-10-15 |
| **Delete an AI Deliverability Agent** | Delete an AI Deliverability Agent, removing its activity history and any queued runs. Returns the core fields of the deleted agent. Deploying… | `DELETE /api/v2/ai-agents/deliverability/{id}` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/delete-an-ai-deliverability-agent) | 2026-10-15 |
| **Deploy the default AI Deliverability Agent** | Create or reactivate the workspace default AI Deliverability Agent. This operation is idempotent when the agent is already active and schedules an… | `POST /api/v2/ai-agents/deliverability/deploy` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/deploy-the-default-ai-deliverability-agent) | 2026-10-15 |
| **Get AI Deliverability Agent state** | Get the live state of an AI Deliverability Agent: current activity, schedule, latest run summary, and the activity feed. | `GET /api/v2/ai-agents/deliverability/{id}/state` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/get-ai-deliverability-agent-state) | 2026-10-15 |
| **Get an AI Deliverability Agent** | Retrieve a single AI Deliverability Agent. | `GET /api/v2/ai-agents/deliverability/{id}` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/get-an-ai-deliverability-agent) | 2026-10-15 |
| **Get the default AI Deliverability Agent state** | Get the live state of the workspace default AI Deliverability Agent, including current activity, schedule, latest run summary, and activity feed.… | `GET /api/v2/ai-agents/deliverability/state` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/get-the-default-ai-deliverability-agent-state) | 2026-10-15 |
| **Get the default AI Deliverability Agent** | Retrieve the workspace default AI Deliverability Agent. The `agent` field is `null` if one has not been deployed. Use the returned `agent.id` with… | `GET /api/v2/ai-agents/deliverability` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/get-the-default-ai-deliverability-agent) | 2026-10-15 |
| **List AI Deliverability Agent feed items** | List the activity-feed items of an AI Deliverability Agent, newest first. | `GET /api/v2/ai-agents/deliverability/{id}/feed-items` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/list-ai-deliverability-agent-feed-items) | 2026-10-15 |
| **Pause accounts affected by a deliverability recommendation** | Pause active email accounts currently affected by the default agent's DNS-health or blocklist recommendation. The recommendation is revalidated… | `POST /api/v2/ai-agents/deliverability/feed-items/{id}/pause-affected-accounts` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/pause-accounts-affected-by-a-deliverability-recommendation) | 2026-10-15 |
| **Pause campaign sending for affected accounts** | Pause campaign sending for 14 days on self-managed accounts affected by the default agent's bounce-health or warmup-score recommendation. Calling… | `POST /api/v2/ai-agents/deliverability/feed-items/{id}/pause-campaign-sending` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/pause-campaign-sending-for-affected-accounts) | 2026-10-15 |
| **Run Deliverability Agent now** | Run Deliverability Agent now. | `POST /api/v2/ai-agents/deliverability/run-now` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/run-deliverability-agent-now) | 2026-10-15 |
| **Update an AI Deliverability Agent** | Update an AI Deliverability Agent. Set `slack` to connect Slack notifications, or to null to disconnect them. | `PATCH /api/v2/ai-agents/deliverability/{id}` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/update-an-ai-deliverability-agent) | 2026-10-15 |
| **Update the default AI Deliverability Agent settings** | Update Slack notification settings for the workspace default AI Deliverability Agent. Set `slack` to `null` to disconnect Slack notifications. | `PATCH /api/v2/ai-agents/deliverability/settings` | [docs](https://developer.instantly.ai/api-reference/aideliverabilityagent/update-the-default-ai-deliverability-agent-settings) | 2026-10-15 |

#### AI Inbox Manager (16 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create an AI Inbox Manager guidance** | Create a guidance for an AI Inbox Manager. The BASICS category is an upsert: it carries tone/length options instead of an instruction, is always… | `POST /api/v2/ai-agents/inbox-manager/{id}/guidances` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/create-an-ai-inbox-manager-guidance) | 2026-10-15 |
| **Create an AI Inbox Manager** | Create a new AI Inbox Manager with its configuration and optional initial guidance, saved together. The agent is created active. Including… | `POST /api/v2/ai-agents/inbox-manager` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/create-an-ai-inbox-manager) | 2026-10-15 |
| **Delete an AI Inbox Manager guidance** | Delete a guidance of an AI Inbox Manager. | `DELETE /api/v2/ai-agents/inbox-manager/{id}/guidances/{guidance_id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/delete-an-ai-inbox-manager-guidance) | 2026-10-15 |
| **Delete an AI Inbox Manager** | Delete an AI Inbox Manager. Returns the core fields of the deleted agent. | `DELETE /api/v2/ai-agents/inbox-manager/{id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/delete-an-ai-inbox-manager) | 2026-10-15 |
| **Get AI Inbox Manager analytics by date** | Get daily analytics aggregates for an AI Inbox Manager over an optional date window. | `GET /api/v2/ai-agents/inbox-manager/{id}/analytics/summary-by-date` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/get-ai-inbox-manager-analytics-by-date) | 2026-10-15 |
| **Get AI Inbox Manager analytics summary** | Get aggregated analytics for an AI Inbox Manager over an optional date window. | `GET /api/v2/ai-agents/inbox-manager/{id}/analytics/summary` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/get-ai-inbox-manager-analytics-summary) | 2026-10-15 |
| **Get an AI Inbox Manager guidance** | Retrieve a single guidance of an AI Inbox Manager. | `GET /api/v2/ai-agents/inbox-manager/{id}/guidances/{guidance_id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/get-an-ai-inbox-manager-guidance) | 2026-10-15 |
| **Get an AI Inbox Manager reply** | Retrieve a single reply generated by an AI Inbox Manager, including its HTML body. | `GET /api/v2/ai-agents/inbox-manager/{id}/replies/{reply_id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/get-an-ai-inbox-manager-reply) | 2026-10-15 |
| **Get an AI Inbox Manager** | Retrieve a single AI Inbox Manager with its full configuration. | `GET /api/v2/ai-agents/inbox-manager/{id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/get-an-ai-inbox-manager) | 2026-10-15 |
| **List AI Inbox Manager activity** | Get the paginated unified activity feed (replies, follow-ups and no-show recoveries) for an AI Inbox Manager, newest first. | `GET /api/v2/ai-agents/inbox-manager/{id}/analytics/activity` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/list-ai-inbox-manager-activity) | 2026-10-15 |
| **List AI Inbox Manager guidances** | List the guidances configured for an AI Inbox Manager. | `GET /api/v2/ai-agents/inbox-manager/{id}/guidances` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/list-ai-inbox-manager-guidances) | 2026-10-15 |
| **List AI Inbox Manager replies** | List the replies and follow-ups generated by an AI Inbox Manager, newest first. | `GET /api/v2/ai-agents/inbox-manager/{id}/replies` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/list-ai-inbox-manager-replies) | 2026-10-15 |
| **List AI Inbox Managers** | List the AI Inbox Managers of the workspace, newest first. | `GET /api/v2/ai-agents/inbox-manager` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/list-ai-inbox-managers) | 2026-10-15 |
| **Update an AI Inbox Manager guidance** | Update a guidance of an AI Inbox Manager. BASICS guidances keep an empty instruction and stay active; a guidance cannot be changed to or from the… | `PATCH /api/v2/ai-agents/inbox-manager/{id}/guidances/{guidance_id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/update-an-ai-inbox-manager-guidance) | 2026-10-15 |
| **Update an AI Inbox Manager reply** | Update a reply generated by an AI Inbox Manager: leave feedback on the reply or mark its pending action as handled. | `PATCH /api/v2/ai-agents/inbox-manager/{id}/replies/{reply_id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/update-an-ai-inbox-manager-reply) | 2026-10-15 |
| **Update an AI Inbox Manager** | Update an AI Inbox Manager, including its configuration. | `PATCH /api/v2/ai-agents/inbox-manager/{id}` | [docs](https://developer.instantly.ai/api-reference/aiinboxmanager/update-an-ai-inbox-manager) | 2026-10-15 |

#### AI Lead Finder Agent (13 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create an AI Lead Finder Agent** | Create an AI Lead Finder Agent that keeps a campaign topped up with fresh leads. The agent immediately runs its first check after creation. | `POST /api/v2/ai-agents/lead-finder` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/create-an-ai-lead-finder-agent) | 2026-10-15 |
| **Delete a saved enrichment workflow** | Delete a saved workflow. Agents that already loaded it keep their copied chain. | `DELETE /api/v2/ai-agents/lead-finder/enrichment-workflows/{id}` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/delete-a-saved-enrichment-workflow) | 2026-10-15 |
| **Delete an AI Lead Finder Agent** | Delete an AI Lead Finder Agent. Leads it already added to the campaign stay in the campaign. | `DELETE /api/v2/ai-agents/lead-finder/{id}` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/delete-an-ai-lead-finder-agent) | 2026-10-15 |
| **Get AI Lead Finder Agent lifetime stats** | Lifetime activity totals of an AI Lead Finder Agent. | `GET /api/v2/ai-agents/lead-finder/{id}/stats` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/get-ai-lead-finder-agent-lifetime-stats) | 2026-10-15 |
| **Get an AI Lead Finder Agent** | Retrieve a single AI Lead Finder Agent with its full configuration. | `GET /api/v2/ai-agents/lead-finder/{id}` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/get-an-ai-lead-finder-agent) | 2026-10-15 |
| **List AI Lead Finder Agent activities** | List the activity events of an AI Lead Finder Agent, newest first. | `GET /api/v2/ai-agents/lead-finder/{id}/activities` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/list-ai-lead-finder-agent-activities) | 2026-10-15 |
| **List AI Lead Finder Agents** | List the AI Lead Finder Agents of the workspace, newest first. | `GET /api/v2/ai-agents/lead-finder` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/list-ai-lead-finder-agents) | 2026-10-15 |
| **List saved enrichment workflows** | Reusable AI-enrichment chains saved by the workspace, ready to apply to a Lead Finder Agent. | `GET /api/v2/ai-agents/lead-finder/enrichment-workflows` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/list-saved-enrichment-workflows) | 2026-10-15 |
| **Pause an AI Lead Finder Agent** | Pause an AI Lead Finder Agent. A paused agent stops topping up its campaign until resumed. | `POST /api/v2/ai-agents/lead-finder/{id}/pause` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/pause-an-ai-lead-finder-agent) | 2026-10-15 |
| **Resume an AI Lead Finder Agent** | Resume a paused AI Lead Finder Agent. The agent immediately checks whether its campaign needs a top-up. | `POST /api/v2/ai-agents/lead-finder/{id}/resume` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/resume-an-ai-lead-finder-agent) | 2026-10-15 |
| **Save an enrichment workflow** | Save an AI-enrichment chain as a named, workspace-wide reusable workflow. | `POST /api/v2/ai-agents/lead-finder/enrichment-workflows` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/save-an-enrichment-workflow) | 2026-10-15 |
| **Suggest audiences from a campaign** | Analyze the leads already in a campaign and suggest SuperSearch audiences that match them. Each suggestion returns a natural-language `query` plus… | `POST /api/v2/ai-agents/lead-finder/suggest-audience` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/suggest-audiences-from-a-campaign) | 2026-10-15 |
| **Update an AI Lead Finder Agent** | Update an AI Lead Finder Agent's settings. `on_exhaustion: fallback` requires fallback filters, either in this request or already stored. | `PATCH /api/v2/ai-agents/lead-finder/{id}` | [docs](https://developer.instantly.ai/api-reference/aileadfinderagent/update-an-ai-lead-finder-agent) | 2026-10-15 |

#### AI Sales Agent (19 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Approve an AI Sales Agent activity** | Approve a pending AI Sales Agent activity action. Approving a `recommend_autopilot` activity turns on autopilot for the agent. Returns 404 when… | `POST /api/v2/ai-agents/sales/{id}/activities/{activity_id}/approve` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/approve-an-ai-sales-agent-activity) | 2026-10-15 |
| **Approve multiple AI Sales Agent activities** | Approve multiple pending AI Sales Agent activity actions. `recommend_autopilot` activities are skipped: approve them one at a time. Returns 404… | `POST /api/v2/ai-agents/sales/{id}/activities/approve` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/approve-multiple-ai-sales-agent-activities) | 2026-10-15 |
| **Create an AI Sales Agent guidance rule** | Add a guidance rule the AI Sales Agent must follow when writing outreach. An agent can have at most 10 rules. Rules are stored as a single list,… | `POST /api/v2/ai-agents/sales/{id}/guidance-rules` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/create-an-ai-sales-agent-guidance-rule) | 2026-10-15 |
| **Create an AI Sales Agent** | Create a new AI Sales Agent. Provide `type` and `input` to extract business details from a website or pitch deck, or skip the scrape by setting… | `POST /api/v2/ai-agents/sales` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/create-an-ai-sales-agent) | 2026-10-15 |
| **Delete an AI Sales Agent guidance rule** | Delete a guidance rule. Rule ids are positional, so the remaining rules re-index after a deletion — re-fetch the list before acting on another… | `DELETE /api/v2/ai-agents/sales/{id}/guidance-rules/{rule_id}` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/delete-an-ai-sales-agent-guidance-rule) | 2026-10-15 |
| **Delete an AI Sales Agent** | Delete an AI Sales Agent. Returns the core fields of the deleted agent. Fails with a conflict while campaigns are still linked to the agent. | `DELETE /api/v2/ai-agents/sales/{id}` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/delete-an-ai-sales-agent) | 2026-10-15 |
| **Get AI Sales Agent analytics** | Get daily analytics (leads found, emails sent, replies, opportunities, total email activity) merged across all campaigns of the AI Sales Agent.… | `GET /api/v2/ai-agents/sales/{id}/analytics` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/get-ai-sales-agent-analytics) | 2026-10-15 |
| **Get AI Sales Agent lead activity summary** | Get aggregate counts and rates for lead activity across all campaigns of the AI Sales Agent. When `start_date` and `end_date` are omitted, the… | `GET /api/v2/ai-agents/sales/{id}/leads/activity/summary` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/get-ai-sales-agent-lead-activity-summary) | 2026-10-15 |
| **Get AI Sales Agent opportunity summary** | Get aggregated opportunity counts by status and a per-campaign breakdown for all campaigns of the AI Sales Agent. When `start_date` and `end_date`… | `GET /api/v2/ai-agents/sales/{id}/opportunities/summary` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/get-ai-sales-agent-opportunity-summary) | 2026-10-15 |
| **Get an AI Sales Agent** | Retrieve a single AI Sales Agent with its full configuration. | `GET /api/v2/ai-agents/sales/{id}` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/get-an-ai-sales-agent) | 2026-10-15 |
| **Get research sources for an AI Sales Agent lead** | Get research sources for an AI Sales Agent lead. | `GET /api/v2/ai-agents/sales/{id}/leads/{lead_id}/research` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/get-research-sources-for-an-ai-sales-agent-lead) | 2026-10-15 |
| **List AI Sales Agent activities** | List all activities for the AI Sales Agent. | `GET /api/v2/ai-agents/sales/{id}/activities` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/list-ai-sales-agent-activities) | 2026-10-15 |
| **List AI Sales Agent guidance rules** | List the guidance rules the AI Sales Agent follows when writing outreach. An agent has at most 10 rules, so the list is not paginated. | `GET /api/v2/ai-agents/sales/{id}/guidance-rules` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/list-ai-sales-agent-guidance-rules) | 2026-10-15 |
| **List AI Sales Agent lead activity** | Get per-lead event history (emails sent, opens, replies, clicks, bounces, opportunity status) for all campaigns of the AI Sales Agent. Leads are… | `GET /api/v2/ai-agents/sales/{id}/leads/activity` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/list-ai-sales-agent-lead-activity) | 2026-10-15 |
| **List AI Sales Agents** | List the AI Sales Agents of the workspace, newest first. | `GET /api/v2/ai-agents/sales` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/list-ai-sales-agents) | 2026-10-15 |
| **Reject an AI Sales Agent activity** | Reject a pending AI Sales Agent activity action. Returns 404 when the activity does not exist or is not pending. | `POST /api/v2/ai-agents/sales/{id}/activities/{activity_id}/reject` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/reject-an-ai-sales-agent-activity) | 2026-10-15 |
| **Reject multiple AI Sales Agent activities** | Reject multiple pending AI Sales Agent activity actions. `recommend_autopilot` activities are skipped: reject them one at a time. Returns 404 when… | `POST /api/v2/ai-agents/sales/{id}/activities/reject` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/reject-multiple-ai-sales-agent-activities) | 2026-10-15 |
| **Update an AI Sales Agent guidance rule** | Update the title or content of a guidance rule. Rules are stored as a single list, so concurrent writes to the same agent are last-write-wins —… | `PATCH /api/v2/ai-agents/sales/{id}/guidance-rules/{rule_id}` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/update-an-ai-sales-agent-guidance-rule) | 2026-10-15 |
| **Update an AI Sales Agent** | Update an AI Sales Agent, including its configuration. | `PATCH /api/v2/ai-agents/sales/{id}` | [docs](https://developer.instantly.ai/api-reference/aisalesagent/update-an-ai-sales-agent) | 2026-10-15 |

#### API Keys (3 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create api key** | Create api key. | `POST /api/v2/api-keys` | [docs](https://developer.instantly.ai/api-reference/apikey/create-api-key) | 2026-10-15 |
| **Delete api key** | Delete api key. | `DELETE /api/v2/api-keys/{id}` | [docs](https://developer.instantly.ai/api-reference/apikey/delete-api-key) | 2026-10-15 |
| **List api key** | List api key. | `GET /api/v2/api-keys` | [docs](https://developer.instantly.ai/api-reference/apikey/list-api-key) | 2026-10-15 |

#### Audit Logs (1 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **List audit log** | List audit log. | `GET /api/v2/audit-logs` | [docs](https://developer.instantly.ai/api-reference/auditlog/list-audit-log) | 2026-10-15 |

#### Background Jobs (2 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get background job** | Get background job. | `GET /api/v2/background-jobs/{id}` | [docs](https://developer.instantly.ai/api-reference/backgroundjob/get-background-job) | 2026-10-15 |
| **List background job** | List background job. | `GET /api/v2/background-jobs` | [docs](https://developer.instantly.ai/api-reference/backgroundjob/list-background-job) | 2026-10-15 |

#### Blocklist Entries (9 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Bulk create block list entry** | Bulk create block list entry. | `POST /api/v2/block-lists-entries/bulk-create` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/bulk-create-block-list-entry) | 2026-10-15 |
| **Bulk delete block list entry** | Bulk delete block list entry. | `POST /api/v2/block-lists-entries/bulk-delete` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/bulk-delete-block-list-entry) | 2026-10-15 |
| **Create block list entry** | Create block list entry. | `POST /api/v2/block-lists-entries` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/create-block-list-entry) | 2026-10-15 |
| **Delete all block list entries** | Delete all block list entries. | `DELETE /api/v2/block-lists-entries` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/delete-all-block-list-entries) | 2026-10-15 |
| **Delete block list entry** | Delete block list entry. | `DELETE /api/v2/block-lists-entries/{id}` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/delete-block-list-entry) | 2026-10-15 |
| **Download all block list entries as CSV** | Download all block list entries as CSV. | `GET /api/v2/block-lists-entries/download` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/download-all-block-list-entries-as-csv) | 2026-10-15 |
| **Get block list entry** | Get block list entry. | `GET /api/v2/block-lists-entries/{id}` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/get-block-list-entry) | 2026-10-15 |
| **List block list entry** | List block list entry. | `GET /api/v2/block-lists-entries` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/list-block-list-entry) | 2026-10-15 |
| **Patch block list entry** | Patch block list entry. | `PATCH /api/v2/block-lists-entries/{id}` | [docs](https://developer.instantly.ai/api-reference/blocklistentry/patch-block-list-entry) | 2026-10-15 |

#### Campaigns (19 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Activate(start), or resume a campaign** | Activate(start), or resume a campaign. | `POST /api/v2/campaigns/{id}/activate` | [docs](https://developer.instantly.ai/api-reference/campaign/activatestart-or-resume-a-campaign) | 2026-10-15 |
| **Add campaign variables** | Add campaign variables. | `POST /api/v2/campaigns/{id}/variables` | [docs](https://developer.instantly.ai/api-reference/campaign/add-campaign-variables) | 2026-10-15 |
| **Create campaign from shared one** | Create campaign from shared one. | `POST /api/v2/campaigns/{id}/from-export` | [docs](https://developer.instantly.ai/api-reference/campaign/create-campaign-from-shared-one) | 2026-10-15 |
| **Create campaign** | Create campaign. | `POST /api/v2/campaigns` | [docs](https://developer.instantly.ai/api-reference/campaign/create-campaign) | 2026-10-15 |
| **Delete campaign** | Delete campaign. | `DELETE /api/v2/campaigns/{id}` | [docs](https://developer.instantly.ai/api-reference/campaign/delete-campaign) | 2026-10-15 |
| **Duplicate campaign** | Duplicate campaign. | `POST /api/v2/campaigns/{id}/duplicate` | [docs](https://developer.instantly.ai/api-reference/campaign/duplicate-campaign) | 2026-10-15 |
| **Export campaign to JSON format** | Export campaign to JSON format. | `POST /api/v2/campaigns/{id}/export` | [docs](https://developer.instantly.ai/api-reference/campaign/export-campaign-to-json-format) | 2026-10-15 |
| **Get campaign sending status** | Returns sending status data explaining why a campaign may not be sending emails or is sending slower than expected. Note: Some fields may be… | `GET /api/v2/campaigns/{id}/sending-status` | [docs](https://developer.instantly.ai/api-reference/campaign/get-campaign-sending-status) | 2026-10-15 |
| **Get campaign steps analytics** | Get campaign steps analytics | `GET /api/v2/campaigns/analytics/steps` | [docs](https://developer.instantly.ai/api-reference/campaign/get-campaign-steps-analytics) | 2026-10-15 |
| **Get campaign** | Get campaign. | `GET /api/v2/campaigns/{id}` | [docs](https://developer.instantly.ai/api-reference/campaign/get-campaign) | 2026-10-15 |
| **Get campaign(s) analytics overview** | Get analytics overview for one or multiple campaigns. Specify the `id` field to get the analytics overview for a single campaign, or leave it… | `GET /api/v2/campaigns/analytics/overview` | [docs](https://developer.instantly.ai/api-reference/campaign/get-campaigns-analytics-overview) | 2026-10-15 |
| **Get campaign(s) analytics** | Get analytics for one or multiple campaigns. Specify the `id` field to get the analytics for a single campaign, or leave it empty to get the… | `GET /api/v2/campaigns/analytics` | [docs](https://developer.instantly.ai/api-reference/campaign/get-campaigns-analytics) | 2026-10-15 |
| **Get daily campaign analytics** | Get campaign daily analytics | `GET /api/v2/campaigns/analytics/daily` | [docs](https://developer.instantly.ai/api-reference/campaign/get-daily-campaign-analytics) | 2026-10-15 |
| **Get launched campaigns count** | Get launched campaigns count. | `GET /api/v2/campaigns/count-launched` | [docs](https://developer.instantly.ai/api-reference/campaign/get-launched-campaigns-count) | 2026-10-15 |
| **List campaign** (`list_campaigns`) | List campaign. | `GET /api/v2/campaigns` | [docs](https://developer.instantly.ai/api-reference/campaign/list-campaign) | 2026-10-15 |
| **Patch campaign** | Patch campaign. | `PATCH /api/v2/campaigns/{id}` | [docs](https://developer.instantly.ai/api-reference/campaign/patch-campaign) | 2026-10-15 |
| **Search campaigns by lead email** | Search campaigns by lead email. | `GET /api/v2/campaigns/search-by-contact` | [docs](https://developer.instantly.ai/api-reference/campaign/search-campaigns-by-lead-email) | 2026-10-15 |
| **Share a campaign** | Share a campaign. This allows other users to create new campaigns based on this campaign. The campaign is being shared for 7 days, after which… | `POST /api/v2/campaigns/{id}/share` | [docs](https://developer.instantly.ai/api-reference/campaign/share-a-campaign) | 2026-10-15 |
| **Stop(or pause) a campaign** | Stop(or pause) a campaign. | `POST /api/v2/campaigns/{id}/pause` | [docs](https://developer.instantly.ai/api-reference/campaign/stopor-pause-a-campaign) | 2026-10-15 |

#### Campaign Subsequences (11 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create campaign subsequence** | Create campaign subsequence. | `POST /api/v2/subsequences` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/create-campaign-subsequence) | 2026-10-15 |
| **Delete campaign subsequence** | Delete campaign subsequence. | `DELETE /api/v2/subsequences/{id}` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/delete-campaign-subsequence) | 2026-10-15 |
| **Duplicate a subsequence** | Duplicate a subsequence with the same trigger conditions | `POST /api/v2/subsequences/{id}/duplicate` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/duplicate-a-subsequence) | 2026-10-15 |
| **Get campaign subsequence** | Get campaign subsequence. | `GET /api/v2/subsequences/{id}` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/get-campaign-subsequence) | 2026-10-15 |
| **Get subsequence analytics summary** | Returns per-subsequence engagement totals (emails sent, unique opens, unique replies) for the subsequences of a campaign. | `GET /api/v2/subsequences/analytics` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/get-subsequence-analytics-summary) | 2026-10-15 |
| **Get subsequence sending status** | Returns sending status data explaining why a subsequence may not be sending emails or is sending slower than expected. Note: Some fields may be… | `GET /api/v2/subsequences/{id}/sending-status` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/get-subsequence-sending-status) | 2026-10-15 |
| **Get subsequence step and variant analytics** | Returns engagement metrics grouped by zero-based step and variant for one subsequence. Results include only activity from the requested… | `GET /api/v2/subsequences/{id}/analytics/steps` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/get-subsequence-step-and-variant-analytics) | 2026-10-15 |
| **List campaign subsequence** | List campaign subsequence. | `GET /api/v2/subsequences` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/list-campaign-subsequence) | 2026-10-15 |
| **Patch campaign subsequence** | Patch campaign subsequence. | `PATCH /api/v2/subsequences/{id}` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/patch-campaign-subsequence) | 2026-10-15 |
| **Pause a subsequence** | Pause a subsequence | `POST /api/v2/subsequences/{id}/pause` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/pause-a-subsequence) | 2026-10-15 |
| **Resume a paused subsequence** | Resume a paused subsequence | `POST /api/v2/subsequences/{id}/resume` | [docs](https://developer.instantly.ai/api-reference/campaignsubsequence/resume-a-paused-subsequence) | 2026-10-15 |

#### Company Lists (9 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create a company list build** | Create a company list build. | `POST /api/v2/supersearch-enrichment/company-lists` | [docs](https://developer.instantly.ai/api-reference/companylist/create-a-company-list-build) | 2026-10-15 |
| **Delete a terminal company list** | Delete a terminal company list. | `DELETE /api/v2/supersearch-enrichment/company-lists/{company_list_id}` | [docs](https://developer.instantly.ai/api-reference/companylist/delete-a-terminal-company-list) | 2026-10-15 |
| **Get company-list status** | Get company-list status. | `GET /api/v2/supersearch-enrichment/company-lists/{company_list_id}` | [docs](https://developer.instantly.ai/api-reference/companylist/get-company-list-status) | 2026-10-15 |
| **Get remote filter options for a catalog-backed company-list filter** | Get remote filter options for a catalog-backed company-list filter. | `GET /api/v2/supersearch-enrichment/company-lists/filter-options` | [docs](https://developer.instantly.ai/api-reference/companylist/get-remote-filter-options-for-a-catalog-backed-company-list-filter) | 2026-10-15 |
| **List company-list members** | List company-list members. | `GET /api/v2/supersearch-enrichment/company-lists/{company_list_id}/companies` | [docs](https://developer.instantly.ai/api-reference/companylist/list-company-list-members) | 2026-10-15 |
| **List company-list recipes** | List company-list recipes. | `GET /api/v2/supersearch-enrichment/company-lists/recipes` | [docs](https://developer.instantly.ai/api-reference/companylist/list-company-list-recipes) | 2026-10-15 |
| **List company-list sources** | List company-list sources. | `GET /api/v2/supersearch-enrichment/company-lists/sources` | [docs](https://developer.instantly.ai/api-reference/companylist/list-company-list-sources) | 2026-10-15 |
| **List company lists** | List company lists. | `GET /api/v2/supersearch-enrichment/company-lists` | [docs](https://developer.instantly.ai/api-reference/companylist/list-company-lists) | 2026-10-15 |
| **Rename a terminal company list** | Rename a terminal company list. | `PATCH /api/v2/supersearch-enrichment/company-lists/{company_list_id}` | [docs](https://developer.instantly.ai/api-reference/companylist/rename-a-terminal-company-list) | 2026-10-15 |

#### CRM Actions (2 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Delete phone number** | Remove a phone number from the organization. Provider cleanup is retried automatically if delayed. Deleting an unknown or already removed number… | `DELETE /api/v2/crm-actions/phone-numbers/{id}` | [docs](https://developer.instantly.ai/api-reference/crmactions/delete-phone-number) | 2026-10-15 |
| **List phone numbers** | Retrieve all phone numbers associated with the current organization. | `GET /api/v2/crm-actions/phone-numbers` | [docs](https://developer.instantly.ai/api-reference/crmactions/list-phone-numbers) | 2026-10-15 |

#### Custom Tags (6 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Assign or unassign tags to resources** | This can be used for both accounts and campaigns. Please check the `resource_type` field for more information. | `POST /api/v2/custom-tags/toggle-resource` | [docs](https://developer.instantly.ai/api-reference/customtag/assign-or-unassign-tags-to-resources) | 2026-10-15 |
| **Create custom tag** | Create custom tag. | `POST /api/v2/custom-tags` | [docs](https://developer.instantly.ai/api-reference/customtag/create-custom-tag) | 2026-10-15 |
| **Delete custom tag** | Delete custom tag. | `DELETE /api/v2/custom-tags/{id}` | [docs](https://developer.instantly.ai/api-reference/customtag/delete-custom-tag) | 2026-10-15 |
| **Get custom tag** | Get custom tag. | `GET /api/v2/custom-tags/{id}` | [docs](https://developer.instantly.ai/api-reference/customtag/get-custom-tag) | 2026-10-15 |
| **List custom tag** | List custom tag. | `GET /api/v2/custom-tags` | [docs](https://developer.instantly.ai/api-reference/customtag/list-custom-tag) | 2026-10-15 |
| **Patch custom tag** | Patch custom tag. | `PATCH /api/v2/custom-tags/{id}` | [docs](https://developer.instantly.ai/api-reference/customtag/patch-custom-tag) | 2026-10-15 |

#### Custom Tag Mappings (1 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **List custom tag mapping** | List custom tag mapping. | `GET /api/v2/custom-tag-mappings` | [docs](https://developer.instantly.ai/api-reference/customtagmapping/list-custom-tag-mapping) | 2026-10-15 |

#### DFY Email Account Orders (7 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Cancel dfy email accounts** | This endpoint will cancel the DFY email accounts based on the provided email addresses. Cancelling permanently deletes all Unibox emails and… | `POST /api/v2/dfy-email-account-orders/accounts/cancel` | [docs](https://developer.instantly.ai/api-reference/dfyemailaccountorder/cancel-dfy-email-accounts) | 2026-10-15 |
| **Check domains availability** | This endpoint will check the availability of the provided domains.. It will return a list of domains with their availability status. | `POST /api/v2/dfy-email-account-orders/domains/check` | [docs](https://developer.instantly.ai/api-reference/dfyemailaccountorder/check-domains-availability) | 2026-10-15 |
| **Generate similar available domains** | This endpoint will generate a list of similar AND available domains based on the provided domain.. It will return a maximum number of 67… | `POST /api/v2/dfy-email-account-orders/domains/similar` | [docs](https://developer.instantly.ai/api-reference/dfyemailaccountorder/generate-similar-available-domains) | 2026-10-15 |
| **Get pre-warmed up domains** | This endpoint will return a list of pre-warmed up domains available for order.<br/>These domains are set up and configured in advance, allowing… | `POST /api/v2/dfy-email-account-orders/domains/pre-warmed-up-list` | [docs](https://developer.instantly.ai/api-reference/dfyemailaccountorder/get-pre-warmed-up-domains) | 2026-10-15 |
| **List dfy email account order** | List dfy email account order. | `GET /api/v2/dfy-email-account-orders` | [docs](https://developer.instantly.ai/api-reference/dfyemailaccountorder/list-dfy-email-account-order) | 2026-10-15 |
| **List DFY ordered email accounts** | This endpoint will return a list of DFY email accounts ordered | `GET /api/v2/dfy-email-account-orders/accounts` | [docs](https://developer.instantly.ai/api-reference/dfyemailaccountorder/list-dfy-ordered-email-accounts) | 2026-10-15 |
| **Place a DFY email account order** | Place a Done-For-You (DFY) email account order for your workspace. | `POST /api/v2/dfy-email-account-orders` | [docs](https://developer.instantly.ai/api-reference/dfyemailaccountorder/place-a-dfy-email-account-order) | 2026-10-15 |

#### Domain Forwarding (3 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get domain forwarding** | Returns the stored web forwarding configuration for a domain ordered through Instantly. All fields except `domain` are null when no forwarding is… | `GET /api/v2/domains/{domain}/forwarding` | [docs](https://developer.instantly.ai/api-reference/domainforwarding/get-domain-forwarding) | 2026-10-15 |
| **Remove domain forwarding** | Removes web forwarding from a domain ordered through Instantly. This operation is idempotent: removing forwarding from a domain that has none… | `DELETE /api/v2/domains/{domain}/forwarding` | [docs](https://developer.instantly.ai/api-reference/domainforwarding/remove-domain-forwarding) | 2026-10-15 |
| **Set domain forwarding** | Sets web forwarding on a domain ordered through Instantly. The forwarding domain must be a valid domain different from the domain itself. Returns… | `PUT /api/v2/domains/{domain}/forwarding` | [docs](https://developer.instantly.ai/api-reference/domainforwarding/set-domain-forwarding) | 2026-10-15 |

#### Email (9 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Count unread emails** | Count unread emails. | `GET /api/v2/emails/unread/count` | [docs](https://developer.instantly.ai/api-reference/email/count-unread-emails) | 2026-10-15 |
| **Delete email** | Delete email. | `DELETE /api/v2/emails/{id}` | [docs](https://developer.instantly.ai/api-reference/email/delete-email) | 2026-10-15 |
| **Forward an email** | Forward an existing email to another recipient. You must specify the `reply_to_uuid` field, which represents the `id` of an existing email… | `POST /api/v2/emails/forward` | [docs](https://developer.instantly.ai/api-reference/email/forward-an-email) | 2026-10-15 |
| **Get email** | Get email. | `GET /api/v2/emails/{id}` | [docs](https://developer.instantly.ai/api-reference/email/get-email) | 2026-10-15 |
| **List email** | **Rate Limit:** This endpoint has a rate limit of 20 requests per minute, unlike other API endpoints. | `GET /api/v2/emails` | [docs](https://developer.instantly.ai/api-reference/email/list-email) | 2026-10-15 |
| **Mark all emails in a thread as read** | Mark all emails in a thread as read. | `POST /api/v2/emails/threads/{thread_id}/mark-as-read` | [docs](https://developer.instantly.ai/api-reference/email/mark-all-emails-in-a-thread-as-read) | 2026-10-15 |
| **Patch email** | Patch email. | `PATCH /api/v2/emails/{id}` | [docs](https://developer.instantly.ai/api-reference/email/patch-email) | 2026-10-15 |
| **Reply to an email** | Send a reply to an email. This endpoint can be used to send an email only as a reply to an existing email. In order to reply to an email, please… | `POST /api/v2/emails/reply` | [docs](https://developer.instantly.ai/api-reference/email/reply-to-an-email) | 2026-10-15 |
| **Send a test email** | Send a preview/test email without creating an email entity in Unibox. Rate limit: 10 requests per minute per workspace. | `POST /api/v2/emails/test` | [docs](https://developer.instantly.ai/api-reference/email/send-a-test-email) | 2026-10-15 |

#### Email Verification (2 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Check an email verification status** | Check an email verification status. | `GET /api/v2/email-verification/{email}` | [docs](https://developer.instantly.ai/api-reference/emailverification/check-an-email-verification-status) | 2026-10-15 |
| **Create email verification** | If an email takes longer than 10 seconds to verify, the endpoint will return the status as `pending`. In that case, you may use the… | `POST /api/v2/email-verification` | [docs](https://developer.instantly.ai/api-reference/emailverification/create-email-verification) | 2026-10-15 |

