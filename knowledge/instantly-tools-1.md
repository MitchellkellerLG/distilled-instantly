# Instantly tools catalog 1 of 5

This skill holds: Part 1 (product features and tools) and Part 2 (developer guides).

Rules: name the feature or endpoint, give its exact docs link and say "as of <date>"; suggest checking the live docs. Recommend only items listed in the `instantly-tools-*` skills; never invent a feature, endpoint, parameter, limit or plan. Always write API keys as `YOUR_API_KEY`; never ask for or repeat a real key.

Where the rest of the catalog lives:
- `instantly-tools-1`: Part 1 (product features and tools) and Part 2 (developer guides)
- `instantly-tools-2`: Part 3, API v2 endpoint groups: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists
- `instantly-tools-3`: Part 3, API v2 endpoint groups: CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification, AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members
- `instantly-tools-4`: Part 4, Instantly MCP server (what it is, MCP vs REST, setup by client, auth and scopes, tool count) plus MCP tools for: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists, CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification
- `instantly-tools-5`: Part 4 continued, MCP tools for: AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members

---

# TOOLS: Instantly features, tools and API endpoints

Reference catalog for recommending a specific named Instantly feature, tool or API endpoint. Built 2026-10-15 only from official Instantly sources: instantly.ai product pages, help.instantly.ai articles, and developer.instantly.ai (API v2 docs + OpenAPI spec `https://api.instantly.ai/openapi/api_v2.json`, spec version 2.0.0).

**Dates matter:** features, plans, limits and UI change. Each feature row shows the date of the source it came from (help-article modified date or product-page sitemap lastmod). API endpoints are as documented on 2026-10-15 (API v2). When recommending, name the feature or endpoint, link its docs URL, and say "as of <date>"; suggest checking the live docs for current behaviour. Never recommend an endpoint or feature that is not listed here.

Entries: 42 features/tools · 255 API v2 endpoints in 35 groups · 20 developer guides · Instantly MCP server (Part 4, files `knowledge/instantly-tools-4.md` and `knowledge/instantly-tools-5.md` in this repo: setup per client, auth, MCP vs REST, 255 MCP tools).

**AI assistant acting in an Instantly account by chat** (launch campaigns, add leads, pull stats from Claude, ChatGPT, Cursor, n8n): go to Part 4, Instantly MCP server (file `knowledge/instantly-tools-4.md` in this repo), first. App-to-app code: Part 3, API v2 (files `knowledge/instantly-tools-2.md` and `knowledge/instantly-tools-3.md` in this repo).

## Part 1: Product features and tools

### Sending & campaigns

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **Campaigns** | Campaigns send cold email sequences to leads, with follow-ups and campaign settings managed in Instantly. | Use campaigns when you want to run and manage outbound email outreach at scale. | [docs](https://help.instantly.ai/en/articles/6386134-how-to-create-a-campaign-complete-setup-guide) | 2026-10-09 |
| **Subsequences** | Subsequences add follow-up paths to a campaign. | Use subsequences when you want to continue or branch outreach after a lead’s actions. | [docs](https://help.instantly.ai/en/articles/7251329-subsequences) | 2026-10-09 |
| **Inbox Rotation** | Inbox Rotation assigns sending accounts to a campaign. | Use it when you want to distribute campaign sending across connected accounts. | [docs](https://help.instantly.ai/en/articles/7046484-inbox-rotation-assign-sending-accounts-to-a-campaign) | 2026-10-09 |
| **AI Sequence Writer** | AI Sequence Writer helps create email sequences for campaigns. | Use it when you need a starting sequence for a new campaign. | [docs](https://help.instantly.ai/en/articles/9394155-ai-sequence-writer) | 2026-10-09 |

### Analytics & testing

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **A/Z Testing** | A/Z Testing lets you create email variants to compare campaign messaging. | Use it when you want to test alternative email copy and see which performs better. | [docs](https://help.instantly.ai/en/articles/6661549-a-z-testing-how-to-create-email-variants) | 2026-10-09 |
| **Analytics & Report** | Analytics & Report provides reporting on campaign performance. | Use it when you want to review campaign results and understand performance. | [docs](https://help.instantly.ai/en/articles/6602310-analytics-report) | 2026-10-13 |
| **Opportunities in Campaign Analytics** | Campaign analytics can include opportunities data. | Use it when you want to evaluate campaigns by opportunities as well as sending metrics. | [docs](https://help.instantly.ai/en/articles/9160456-opportunities-in-campaign-analytics) | 2026-10-13 |

### Inbox & replies

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **Unibox** | Unibox brings campaign replies into one place so you can manage and respond to leads. | Use it when you need a shared view of prospect replies and a place to follow up. | [docs](https://help.instantly.ai/en/articles/6576561-how-to-manage-unibox-best-practices-for-replying-to-leads) | 2026-10-09 |
| **Unibox Reply Macros** | Reply macros let you reuse prepared responses in Unibox. | Use them when you want to respond to common prospect messages more quickly. | [docs](https://help.instantly.ai/en/articles/6752942-unibox-reply-macros) | 2026-10-09 |

### AI agents & Copilot

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **AI Inbox Manager** | AI Inbox Manager is an AI tool for managing inbox activity and replies. | Use it when you want AI assistance handling inbox work. | [docs](https://help.instantly.ai/en/articles/8693846-ai-inbox-manager) | 2026-10-09 |
| **AI Reply Agent** | AI Reply Agent responds to interested prospects, handles questions and objections, and can book meetings. | Use it when you want to respond to interested leads promptly and automate reply handling. | [docs](https://help.instantly.ai/en/articles/11774076-ai-reply-agent) · [more](https://instantly.ai/ai-agents/reply-agent) | 2026-10-09 |
| **AI Sales Agent** | AI Sales Agent finds leads, personalizes outreach, follows up, and books meetings automatically. | Use it when you want an agent to run prospecting and outreach from your business context. | [docs](https://help.instantly.ai/en/articles/14299661-ai-sales-agent) · [more](https://instantly.ai/ai-agents/sales-agent) | 2026-10-13 |
| **AI Lead Finder Agent** | AI Lead Finder Agent finds and adds prospects to a campaign when its active lead count falls below a set minimum. | Use it when you want a campaign automatically replenished with prospects. | [docs](https://help.instantly.ai/en/articles/16062161-lead-finder-agent) · [more](https://instantly.ai/ai-agents/lead-generation-agent) | 2026-10-09 |
| **AI Deliverability Agent** | AI Deliverability Agent monitors sending health and provides deliverability recommendations. | Use it when you need help monitoring and addressing sending health issues. | [docs](https://help.instantly.ai/en/articles/15549574-deliverability-ai-agent) · [more](https://instantly.ai/ai-agents) | 2026-10-09 |
| **AI SDR** | The AI SDR automates prospect sourcing, personalized outreach, follow-ups, and reply qualification. | Use it when you want to automate top-of-funnel sales development work. | [docs](https://instantly.ai/ai-agents/ai-sdr-agent) | 2026-09-11 |
| **AI BDR Agent** | AI BDR finds net-new accounts, launches personalized outbound, and flags genuine interest in replies. | Use it when you want to prospect new accounts and start outbound conversations across email and LinkedIn. | [docs](https://instantly.ai/ai-bdr) | 2026-09-21 |
| **Instantly AI & Copilot** | Copilot uses business context and prompts to help with outbound tasks such as finding leads and creating campaigns. | Use it when you want AI help planning or carrying out everyday outbound work. | [docs](https://help.instantly.ai/en/articles/11532420-instantly-ai-copilot) · [more](https://instantly.ai/copilot) | 2026-10-14 |

### Integrations & developer

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **Automations** | Automations connect tools and run workflows in response to events and conditions. | Use them when you want actions such as CRM updates or next steps to happen automatically across your sales stack. | [docs](https://help.instantly.ai/en/articles/12838955-automations) · [more](https://instantly.ai/ai-agents/automations) | 2026-10-09 |
| **Webhooks** | Webhooks let Instantly send or receive event-driven data for connected workflows. | Use webhooks when an external system needs to react to Instantly events or exchange workflow data. | [docs](https://help.instantly.ai/en/articles/6261906-webhooks) | 2026-10-09 |
| **API V2** | API V2 provides REST endpoints for working with Instantly data and workflows programmatically. | Use API V2 when building a direct integration, data pipeline, or custom product connection. | [docs](https://help.instantly.ai/en/articles/10432807-api-v2) · [more](https://instantly.ai/developers) | 2026-10-09 |
| **Instantly MCP** | Hosted MCP server at `https://mcp.instantly.ai/mcp` that lets AI assistants (Claude, ChatGPT plugin, Cursor, n8n, any MCP client) act in your Instantly workspace by chat, using API v2 tools. | Recommend it first when someone wants an AI assistant to launch campaigns, add leads, pull stats or reply by chat. Setup, auth and full tool list: Part 4 (files `knowledge/instantly-tools-4.md` and `knowledge/instantly-tools-5.md` in this repo). | [docs](https://developer.instantly.ai/mcp/quickstart) · [help](https://help.instantly.ai/en/articles/12980002-instantly-mcp-model-context-protocol) · [ChatGPT plugin](https://help.instantly.ai/en/articles/17595989-instantly-plugin-in-chatgpt) | 2026-10-15 |
| **Zapier Integration** | Zapier connects Instantly events and actions with other apps through automated workflows. | Use Zapier when you want to connect Instantly to an app using a documented Zap workflow. | [docs](https://help.instantly.ai/en/articles/7866145-zapier-integration) | 2026-10-09 |
| **Make.com automations** | The listed Make.com automations connect Instantly actions with services such as Pipedrive and HubSpot. | Use these workflows when you want to pass interested leads from Instantly into a supported CRM through Make.com. | [docs](https://help.instantly.ai/en/articles/9533763-automation-add-an-interested-lead-to-pipedrive-with-make-com) · [more](https://help.instantly.ai/en/articles/9533974-automation-add-an-interested-lead-to-hubspot-with-make-com) | 2024-06-27 |
| **HubSpot integration** | The HubSpot integration connects Instantly and HubSpot for CRM workflows and contact or lead syncing. | Use it when you want to connect outreach activity or leads with HubSpot. | [docs](https://help.instantly.ai/en/articles/8848886-how-to-connect-hubspot-to-instantly) · [more](https://help.instantly.ai/en/articles/13342530-hubspot-integration-in-automations) | 2026-10-09 |
| **Pipedrive integration** | The Pipedrive integration connects Instantly and Pipedrive for CRM workflows and lead handling. | Use it when you want to connect Instantly leads with Pipedrive. | [docs](https://help.instantly.ai/en/articles/8848881-how-to-connect-pipedrive-to-instantly) · [more](https://help.instantly.ai/en/articles/13645175-pipedrive-integration-in-automations) | 2026-10-09 |
| **Salesforce and HubSpot Integration via OutboundSync** | OutboundSync provides a Salesforce and HubSpot integration with Instantly. | Use it when you want to connect Instantly with Salesforce or HubSpot through OutboundSync. | [docs](https://help.instantly.ai/en/articles/10536090-salesforce-and-hubspot-integration-via-outboundsync) | 2026-10-09 |

### Leads & data

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **SuperSearch** | SuperSearch finds B2B leads using filters and supports lead enrichment. | Use it when you need to identify and import prospects that match your target audience. | [docs](https://help.instantly.ai/en/articles/11364248-supersearch) · [more](https://instantly.ai/b2b-lead-finder) | 2026-10-14 |
| **Waterfall Enrichment** | Waterfall Enrichment uses multiple providers to enrich lead data. | Use it when you want to enrich prospects with additional contact information. | [docs](https://help.instantly.ai/en/articles/11364341-waterfall-enrichment) | 2026-10-09 |
| **Email Verification** | Email verification checks whether email addresses are valid before outreach. | Use it when you want to clean a lead list and reduce bounces before sending. | [docs](https://help.instantly.ai/en/articles/6514690-how-to-verify-leads) · [more](https://instantly.ai/email-verification) | 2026-10-09 |
| **Website Visitors** | Website Visitors uses a pixel to identify visitor profiles and can send identified visitors into campaigns. | Use it when you want to find and follow up with potential buyers who visit your website. | [docs](https://help.instantly.ai/en/articles/9502519-getting-started-with-the-website-visitors-feature) · [more](https://instantly.ai/website-visitors) | 2026-10-12 |

### CRM & sales

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **CRM** | Instantly CRM manages outreach, pipeline, and closing activity, including calls, SMS, tasks, and email. | Use it when you want to manage sales conversations and pipeline activity in Instantly. | [docs](https://help.instantly.ai/en/articles/9064527-instantly-crm) · [more](https://instantly.ai/crm) | 2026-10-09 |
| **CRM Opportunities** | CRM Opportunities lets you manage opportunities in the CRM. | Use it when you need to track sales opportunities in your CRM pipeline. | [docs](https://help.instantly.ai/en/articles/9082317-crm-managing-opportunities) | 2026-10-13 |

### Deliverability & infrastructure

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **Email accounts** | The Email Accounts Dashboard lets you manage email accounts connected to Instantly. | Use it when you need to connect or manage sending accounts for campaigns. | [docs](https://help.instantly.ai/en/articles/11991261-getting-started-with-the-email-accounts-dashboard) · [more](https://instantly.ai/email-accounts) | 2026-10-13 |
| **Done-for-you Google Email Setup** | Instantly sets up Google email accounts and adds them to your Instantly account. | Use it when you want ready-to-use email accounts without handling setup yourself. | [docs](https://help.instantly.ai/en/articles/9361043-done-for-you-google-email-setup) · [more](https://instantly.ai/email-accounts) | 2026-10-15 |
| **Instantly AirMail Accounts** | AirMail Accounts are Instantly email accounts with a dedicated setup guide. | Use them when you want to set up Instantly AirMail accounts for sending. | [docs](https://help.instantly.ai/en/articles/14893942-instantly-airmail-accounts-setup) · [more](https://instantly.ai/airmail) | 2026-10-15 |
| **Email Warmup** | Email Warmup sends warmup emails to help build sending reputation for connected accounts. | Use it when you need to warm up sending accounts before or alongside campaigns. | [docs](https://help.instantly.ai/en/articles/5975330-how-to-enable-warmup) · [more](https://instantly.ai/email-warmup) | 2026-10-15 |
| **Inbox Placement** | Inbox Placement tests show whether emails land in the primary inbox, promotions, or spam. | Use it when you need to check where your campaign emails are landing and identify deliverability issues. | [docs](https://help.instantly.ai/en/articles/10147177-inbox-placement-feature) · [more](https://instantly.ai/inbox-placement) | 2026-10-09 |
| **Custom Tracking Domain (CTD)** | A Custom Tracking Domain lets you configure a domain for email tracking. | Use it when you want to configure a custom domain for tracking links in campaigns. | [docs](https://help.instantly.ai/en/articles/6984188-custom-tracking-domain-ctd) | 2026-10-09 |
| **Global Blocklist** | Global Blocklist stores entries that Instantly should block from outreach. | Use it when you need to prevent sending to specified email addresses or domains. | [docs](https://help.instantly.ai/en/articles/6192983-global-blocklist) | 2026-10-09 |

### Account & workspace

| Name | What it does | When we recommend it | Docs | As of |
|---|---|---|---|---|
| **Workspace Groups** | Workspace Groups organize workspaces and workspace group members. | Use them when you need to manage multiple workspaces as a group. | [docs](https://help.instantly.ai/en/articles/10575905-workspace-groups) | 2026-10-09 |
| **Manage Workspaces and Team Members** | Workspace management lets you manage workspaces and team members. | Use it when you need to organize team access across workspaces. | [docs](https://help.instantly.ai/en/articles/6718773-manage-workspaces-and-team-members) | 2026-10-09 |
| **Agency White Labeling** | Agency White Labeling provides white-labeling options for agencies. | Use it when you want to configure Instantly branding for an agency workspace. | [docs](https://help.instantly.ai/en/articles/8678006-agency-white-labeling) · [more](https://instantly.ai/agency) | 2026-10-09 |

## Part 2: Developer guides (developer.instantly.ai, fetched 2026-10-15)

- [Introduction](https://developer.instantly.ai/api-reference/introduction) (`api-reference`)
- [Schemas](https://developer.instantly.ai/api-reference/schemas/index) (`api-reference`)
- [Introduction](https://developer.instantly.ai/cli/introduction) (`cli`)
- [Quickstart](https://developer.instantly.ai/cli/quickstart) (`cli`)
- [Authorization](https://developer.instantly.ai/getting-started/authorization) (`getting-started`)
- [Getting Started](https://developer.instantly.ai/getting-started/getting-started) (`getting-started`)
- [Rate Limit](https://developer.instantly.ai/getting-started/rate-limit) (`getting-started`)
- [Slack channel](https://developer.instantly.ai/getting-started/slack-channel) (`getting-started`)
- [API v1 to v2 migration](https://developer.instantly.ai/guides/api-v1-migration) (`guides`)
- [OAuth connection flow](https://developer.instantly.ai/guides/oauth-connection-flow) (`guides`)
- [Webhook events](https://developer.instantly.ai/guides/webhook-events) (`guides`)
- [Workspace group](https://developer.instantly.ai/guides/workspace-group) (`guides`)
- [Introduction](https://developer.instantly.ai/index) (`start`)
- [Authentication](https://developer.instantly.ai/mcp/authentication) (`mcp`)
- [Introduction](https://developer.instantly.ai/mcp/introduction) (`mcp`)
- [Quickstart](https://developer.instantly.ai/mcp/quickstart) (`mcp`)
- [Available tools](https://developer.instantly.ai/mcp/tools) (`mcp`)
- [Quickstart](https://developer.instantly.ai/quickstart) (`start`)
- [Introduction](https://developer.instantly.ai/sdk/introduction) (`sdk`)
- [Quickstart](https://developer.instantly.ai/sdk/quickstart) (`sdk`)

