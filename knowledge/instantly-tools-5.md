# Instantly tools catalog 5 of 5

This skill holds: Part 4 continued, MCP tools for: AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members.

Rules: name the feature or endpoint, give its exact docs link and say "as of <date>"; suggest checking the live docs. Recommend only items listed in the `instantly-tools-*` skills; never invent a feature, endpoint, parameter, limit or plan. Always write API keys as `YOUR_API_KEY`; never ask for or repeat a real key.

Where the rest of the catalog lives:
- `instantly-tools-1`: Part 1 (product features and tools) and Part 2 (developer guides)
- `instantly-tools-2`: Part 3, API v2 endpoint groups: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists
- `instantly-tools-3`: Part 3, API v2 endpoint groups: CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification, AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members
- `instantly-tools-4`: Part 4, Instantly MCP server (what it is, MCP vs REST, setup by client, auth and scopes, tool count) plus MCP tools for: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists, CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification
- `instantly-tools-5`: Part 4 continued, MCP tools for: AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members

---

## Part 4: Instantly MCP server, every MCP tool continued (as of 2026-10-15)

Tool names follow `{action}_{resource}`. Names confirmed in our docs: `list_accounts`, `list_campaigns`, `create_lead`, `get_campaign_analytics`. For the rest, refer to the tool by what it does and let the client show its exact name. Scopes per tool are the ones listed for its endpoint in Part 3 (files `knowledge/instantly-tools-2.md` and `knowledge/instantly-tools-3.md` in this repo).

#### AI Agent Items (2 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Bulk delete AI agent items** | Bulk delete AI agent items. | `POST /api/v2/agent-items/bulk-delete` | [docs](https://developer.instantly.ai/api-reference/engageitem/bulk-delete-ai-agent-items) | 2026-10-15 |
| **List AI agent items** | List AI agent items. | `GET /api/v2/agent-items` | [docs](https://developer.instantly.ai/api-reference/engageitem/list-ai-agent-items) | 2026-10-15 |

#### Inbox Placement Analytics (5 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get inbox placement analytics stats by date** | Provides a time series representing the distribution of emails sent to inbox, spam, or category folders for scheduled inbox placement tests. | `POST /api/v2/inbox-placement-analytics/stats-by-date` | [docs](https://developer.instantly.ai/api-reference/inboxplacementanalytics/get-inbox-placement-analytics-stats-by-date) | 2026-10-15 |
| **Get inbox placement analytics** | Get inbox placement analytics. | `GET /api/v2/inbox-placement-analytics/{id}` | [docs](https://developer.instantly.ai/api-reference/inboxplacementanalytics/get-inbox-placement-analytics) | 2026-10-15 |
| **List inbox placement analytics** | List inbox placement analytics. | `GET /api/v2/inbox-placement-analytics` | [docs](https://developer.instantly.ai/api-reference/inboxplacementanalytics/list-inbox-placement-analytics) | 2026-10-15 |
| **Retrieve inbox placement analytics deliverability insights** | Provides deliverability insights for a specific inbox placement test | `POST /api/v2/inbox-placement-analytics/deliverability-insights` | [docs](https://developer.instantly.ai/api-reference/inboxplacementanalytics/retrieve-inbox-placement-analytics-deliverability-insights) | 2026-10-15 |
| **Retrieve inbox placement analytics stats by test id** | Provides aggregated inbox, spam and category counts for specified test IDs | `POST /api/v2/inbox-placement-analytics/stats-by-test-id` | [docs](https://developer.instantly.ai/api-reference/inboxplacementanalytics/retrieve-inbox-placement-analytics-stats-by-test-id) | 2026-10-15 |

#### Inbox Placement Blacklist and SpamAssassin Reports (2 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get inbox placement blacklist and spamassassin report** | Get inbox placement blacklist and spamassassin report. | `GET /api/v2/inbox-placement-reports/{id}` | [docs](https://developer.instantly.ai/api-reference/inboxplacementblacklistandspamassassinreport/get-inbox-placement-blacklist-and-spamassassin-report) | 2026-10-15 |
| **List inbox placement blacklist and spamassassin report** | List inbox placement blacklist and spamassassin report. | `GET /api/v2/inbox-placement-reports` | [docs](https://developer.instantly.ai/api-reference/inboxplacementblacklistandspamassassinreport/list-inbox-placement-blacklist-and-spamassassin-report) | 2026-10-15 |

#### Inbox Placement Tests (6 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create inbox placement test** | Create inbox placement test. | `POST /api/v2/inbox-placement-tests` | [docs](https://developer.instantly.ai/api-reference/inboxplacementtest/create-inbox-placement-test) | 2026-10-15 |
| **Delete inbox placement test** | Delete inbox placement test. | `DELETE /api/v2/inbox-placement-tests/{id}` | [docs](https://developer.instantly.ai/api-reference/inboxplacementtest/delete-inbox-placement-test) | 2026-10-15 |
| **Get ESP options** | Provides a list of available email service providers for inbox placement tests. | `GET /api/v2/inbox-placement-tests/email-service-provider-options` | [docs](https://developer.instantly.ai/api-reference/inboxplacementtest/get-esp-options) | 2026-10-15 |
| **Get inbox placement test** | Get inbox placement test. | `GET /api/v2/inbox-placement-tests/{id}` | [docs](https://developer.instantly.ai/api-reference/inboxplacementtest/get-inbox-placement-test) | 2026-10-15 |
| **List inbox placement test** | List inbox placement test. | `GET /api/v2/inbox-placement-tests` | [docs](https://developer.instantly.ai/api-reference/inboxplacementtest/list-inbox-placement-test) | 2026-10-15 |
| **Patch inbox placement test** | Patch inbox placement test. | `PATCH /api/v2/inbox-placement-tests/{id}` | [docs](https://developer.instantly.ai/api-reference/inboxplacementtest/patch-inbox-placement-test) | 2026-10-15 |

#### Leads (13 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Add leads in bulk to a campaign or list** | Adds up to 1000 leads to either a campaign or a list. You must provide a `campaign_id` or a `list_id`, but not both. The endpoint validates… | `POST /api/v2/leads/add` | [docs](https://developer.instantly.ai/api-reference/lead/add-leads-in-bulk-to-a-campaign-or-list) | 2026-10-15 |
| **Bulk assign leads to organization users** | Bulk assign leads to organization users | `POST /api/v2/leads/bulk-assign` | [docs](https://developer.instantly.ai/api-reference/lead/bulk-assign-leads-to-organization-users) | 2026-10-15 |
| **Create lead** (`create_lead`) | Create lead. | `POST /api/v2/leads` | [docs](https://developer.instantly.ai/api-reference/lead/create-lead) | 2026-10-15 |
| **Delete lead** | Delete lead. | `DELETE /api/v2/leads/{id}` | [docs](https://developer.instantly.ai/api-reference/lead/delete-lead) | 2026-10-15 |
| **Delete leads in bulk** | Delete multiple leads from a campaign or list based on filters. You must provide either `campaign_id` or `list_id`. Optionally filter by status or… | `DELETE /api/v2/leads` | [docs](https://developer.instantly.ai/api-reference/lead/delete-leads-in-bulk) | 2026-10-15 |
| **Get lead** | Get lead. | `GET /api/v2/leads/{id}` | [docs](https://developer.instantly.ai/api-reference/lead/get-lead) | 2026-10-15 |
| **List leads** | This endpoint is a POST endpoint, instead of GET - a deviation from the REST APIs standards we’re following because of the complex arguments it… | `POST /api/v2/leads/list` | [docs](https://developer.instantly.ai/api-reference/lead/list-leads) | 2026-10-15 |
| **Merge two leads** | Merge two leads | `POST /api/v2/leads/merge` | [docs](https://developer.instantly.ai/api-reference/lead/merge-two-leads) | 2026-10-15 |
| **Move a lead to a subsequence** | Move a lead to a subsequence | `POST /api/v2/leads/subsequence/move` | [docs](https://developer.instantly.ai/api-reference/lead/move-a-lead-to-a-subsequence) | 2026-10-15 |
| **Move leads to a campaign or list** | Move leads to a different campaign or list. This endpoint will return a background job that will process the move. The job will be processed in… | `POST /api/v2/leads/move` | [docs](https://developer.instantly.ai/api-reference/lead/move-leads-to-a-campaign-or-list) | 2026-10-15 |
| **Patch lead** | Patch lead. | `PATCH /api/v2/leads/{id}` | [docs](https://developer.instantly.ai/api-reference/lead/patch-lead) | 2026-10-15 |
| **Remove a lead from a subsequence** | Remove a lead from a subsequence | `POST /api/v2/leads/subsequence/remove` | [docs](https://developer.instantly.ai/api-reference/lead/remove-a-lead-from-a-subsequence) | 2026-10-15 |
| **Update the interest status of a lead** | Update the interest status of a lead | `POST /api/v2/leads/update-interest-status` | [docs](https://developer.instantly.ai/api-reference/lead/update-the-interest-status-of-a-lead) | 2026-10-15 |

#### Lead Labels (6 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create lead label** | Create lead label. | `POST /api/v2/lead-labels` | [docs](https://developer.instantly.ai/api-reference/leadlabel/create-lead-label) | 2026-10-15 |
| **Delete lead label** | Delete lead label. | `DELETE /api/v2/lead-labels/{id}` | [docs](https://developer.instantly.ai/api-reference/leadlabel/delete-lead-label) | 2026-10-15 |
| **Get lead label** | Get lead label. | `GET /api/v2/lead-labels/{id}` | [docs](https://developer.instantly.ai/api-reference/leadlabel/get-lead-label) | 2026-10-15 |
| **List lead label** | List lead label. | `GET /api/v2/lead-labels` | [docs](https://developer.instantly.ai/api-reference/leadlabel/list-lead-label) | 2026-10-15 |
| **Patch lead label** | Patch lead label. | `PATCH /api/v2/lead-labels/{id}` | [docs](https://developer.instantly.ai/api-reference/leadlabel/patch-lead-label) | 2026-10-15 |
| **Test AI reply label prediction** | Returns the AI-predicted lead label for a reply text. This simulates how AI auto-tagging would label an incoming reply for testing custom labels… | `POST /api/v2/lead-labels/ai-reply-label` | [docs](https://developer.instantly.ai/api-reference/leadlabel/test-ai-reply-label-prediction) | 2026-10-15 |

#### Lead Lists (6 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create lead list** | Create lead list. | `POST /api/v2/lead-lists` | [docs](https://developer.instantly.ai/api-reference/leadlist/create-lead-list) | 2026-10-15 |
| **Delete lead list** | Delete lead list. | `DELETE /api/v2/lead-lists/{id}` | [docs](https://developer.instantly.ai/api-reference/leadlist/delete-lead-list) | 2026-10-15 |
| **Get lead list** | Get lead list. | `GET /api/v2/lead-lists/{id}` | [docs](https://developer.instantly.ai/api-reference/leadlist/get-lead-list) | 2026-10-15 |
| **Get verification statistics for a lead list** | Get verification statistics for a lead list | `GET /api/v2/lead-lists/{id}/verification-stats` | [docs](https://developer.instantly.ai/api-reference/leadlist/get-verification-statistics-for-a-lead-list) | 2026-10-15 |
| **List lead list** | List lead list. | `GET /api/v2/lead-lists` | [docs](https://developer.instantly.ai/api-reference/leadlist/list-lead-list) | 2026-10-15 |
| **Patch lead list** | Patch lead list. | `PATCH /api/v2/lead-lists/{id}` | [docs](https://developer.instantly.ai/api-reference/leadlist/patch-lead-list) | 2026-10-15 |

#### OAuth (3 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get oauth session status** | Poll this endpoint to check the OAuth session result. Works for both Google and Microsoft OAuth sessions. Returns pending while waiting, success… | `GET /api/v2/oauth/session/status/{sessionId}` | [docs](https://developer.instantly.ai/api-reference/oauth/get-oauth-session-status) | 2026-10-15 |
| **Initialize google oauth** | Creates an OAuth session and returns the Google authorization URL. The user should be redirected to auth_url to complete the OAuth flow. Poll the… | `POST /api/v2/oauth/google/init` | [docs](https://developer.instantly.ai/api-reference/oauth/initialize-google-oauth) | 2026-10-15 |
| **Initialize microsoft oauth** | Creates an OAuth session and returns the Microsoft authorization URL. The user should be redirected to auth_url to complete the OAuth flow. Poll… | `POST /api/v2/oauth/microsoft/init` | [docs](https://developer.instantly.ai/api-reference/oauth/initialize-microsoft-oauth) | 2026-10-15 |

#### SuperSearch and Enrichment (18 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Count leads from supersearch** | Count the number of leads matching a SuperSearch query without enriching them. This endpoint is intended to estimate lead availability before… | `POST /api/v2/supersearch-enrichment/count-leads-from-supersearch` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/count-leads-from-supersearch) | 2026-10-15 |
| **Create AI enrichment** | Create an AI enrichment for a resource (list or campaign) | `POST /api/v2/supersearch-enrichment/ai` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/create-ai-enrichment) | 2026-10-15 |
| **Create an enrichment** | Create an enrichment for a specific resource (list or campaign). This is the main endpoint for adding enrichments to resources. The enrichments… | `POST /api/v2/supersearch-enrichment/` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/create-an-enrichment) | 2026-10-15 |
| **Delete a saved search** | Delete a saved search. | `DELETE /api/v2/supersearch-enrichment/saved-searches/{id}` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/delete-a-saved-search) | 2026-10-15 |
| **Enrich leads from supersearch** | Add leads from SuperSearch to a list and enrich them. A list is automatically created if no list is provided. | `POST /api/v2/supersearch-enrichment/enrich-leads-from-supersearch` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/enrich-leads-from-supersearch) | 2026-10-15 |
| **Facet keywords for a signal category** | Return the top matching keyword tokens for a given signal category and keyword field, aggregated from the last 90 days of signal data. Powers the… | `POST /api/v2/supersearch-enrichment/signal-keywords-facet` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/facet-keywords-for-a-signal-category) | 2026-10-15 |
| **Get a saved search** | Get a saved search. | `GET /api/v2/supersearch-enrichment/saved-searches/{id}` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/get-a-saved-search) | 2026-10-15 |
| **Get AI enrichment for resource** | Get the AI enrichment for a specific resource | `GET /api/v2/supersearch-enrichment/ai/{resource_id}/in-progress` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/get-ai-enrichment-for-resource) | 2026-10-15 |
| **Get enrichment for resource** | Get the enrichment for a specific resource | `GET /api/v2/supersearch-enrichment/{resource_id}` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/get-enrichment-for-resource) | 2026-10-15 |
| **Get enrichment history** | Retrieve the enrichment history for a specific resource | `GET /api/v2/supersearch-enrichment/history/{resource_id}` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/get-enrichment-history) | 2026-10-15 |
| **List saved searches** | List the workspace's saved SuperSearch queries, newest first. | `GET /api/v2/supersearch-enrichment/saved-searches` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/list-saved-searches) | 2026-10-15 |
| **Preview leads from supersearch** | Preview the leads matching a SuperSearch query without enriching them | `POST /api/v2/supersearch-enrichment/preview-leads-from-supersearch` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/preview-leads-from-supersearch) | 2026-10-15 |
| **Returns the full integration provider registry** | Returns every data-provider integration with its available lookup actions, per-action credit cost, and whether the requesting workspace has… | `GET /api/v2/supersearch-enrichment/integrations/providers` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/returns-the-full-integration-provider-registry) | 2026-10-15 |
| **Run a single integration lookup action synchronously** | Executes one lookup action for a single record with literal inputs and returns the provider payload inline, under the action's output column. | `POST /api/v2/supersearch-enrichment/integrations/run` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/run-a-single-integration-lookup-action-synchronously) | 2026-10-15 |
| **Run enrichment for resource** | Run all enrichments associated with a resource for a list of leads or for all the leads that haven't been enriched yet | `POST /api/v2/supersearch-enrichment/run` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/run-enrichment-for-resource) | 2026-10-15 |
| **Save a search** | Save a SuperSearch query for reuse. `search_filters` uses the same shape as the count, preview and enrich endpoints. | `POST /api/v2/supersearch-enrichment/saved-searches` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/save-a-search) | 2026-10-15 |
| **Update a saved search** | Rename a saved search and/or replace its filters. | `PATCH /api/v2/supersearch-enrichment/saved-searches/{id}` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/update-a-saved-search) | 2026-10-15 |
| **Update enrichment settings for resource** | Update auto-update and skip settings for a SuperSearch enrichment tied to a specific resource | `PATCH /api/v2/supersearch-enrichment/{resource_id}/settings` | [docs](https://developer.instantly.ai/api-reference/supersearchenrichment/update-enrichment-settings-for-resource) | 2026-10-15 |

#### Webhooks (8 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create webhook** | Create webhook. | `POST /api/v2/webhooks` | [docs](https://developer.instantly.ai/api-reference/webhook/create-webhook) | 2026-10-15 |
| **Delete webhook** | Delete webhook. | `DELETE /api/v2/webhooks/{id}` | [docs](https://developer.instantly.ai/api-reference/webhook/delete-webhook) | 2026-10-15 |
| **Get webhook** | Get webhook. | `GET /api/v2/webhooks/{id}` | [docs](https://developer.instantly.ai/api-reference/webhook/get-webhook) | 2026-10-15 |
| **List available event types** | Get all available webhook event types including custom labels | `GET /api/v2/webhooks/event-types` | [docs](https://developer.instantly.ai/api-reference/webhook/list-available-event-types) | 2026-10-15 |
| **List webhooks** | List all webhooks for the workspace with optional filters | `GET /api/v2/webhooks` | [docs](https://developer.instantly.ai/api-reference/webhook/list-webhooks) | 2026-10-15 |
| **Patch webhook** | Patch webhook. | `PATCH /api/v2/webhooks/{id}` | [docs](https://developer.instantly.ai/api-reference/webhook/patch-webhook) | 2026-10-15 |
| **Resume a webhook** | Resume a webhook that was disabled due to repeated delivery failures | `POST /api/v2/webhooks/{id}/resume` | [docs](https://developer.instantly.ai/api-reference/webhook/resume-a-webhook) | 2026-10-15 |
| **Test a webhook** | Send a test payload to a webhook URL to verify it is working | `POST /api/v2/webhooks/{id}/test` | [docs](https://developer.instantly.ai/api-reference/webhook/test-a-webhook) | 2026-10-15 |

#### Webhook Events (4 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get overview aggregates for webhook events by date** | Get overview aggregates for webhook events by Date for charts | `GET /api/v2/webhook-events/summary-by-date` | [docs](https://developer.instantly.ai/api-reference/webhookevent/get-overview-aggregates-for-webhook-events-by-date) | 2026-10-15 |
| **Get overview aggregates for webhook events** | Get overview aggregates for webhook events including success/failure rates | `GET /api/v2/webhook-events/summary` | [docs](https://developer.instantly.ai/api-reference/webhookevent/get-overview-aggregates-for-webhook-events) | 2026-10-15 |
| **Get webhook event** | Get webhook event. | `GET /api/v2/webhook-events/{id}` | [docs](https://developer.instantly.ai/api-reference/webhookevent/get-webhook-event) | 2026-10-15 |
| **List webhook event** | List webhook event. | `GET /api/v2/webhook-events` | [docs](https://developer.instantly.ai/api-reference/webhookevent/list-webhook-event) | 2026-10-15 |

#### Workspace (8 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Cancel Current Workspace Removal** | Cancel Current Workspace Removal. | `DELETE /api/v2/workspaces/current/schedule-for-removal` | [docs](https://developer.instantly.ai/api-reference/workspace/cancel-current-workspace-removal) | 2026-10-15 |
| **Change workspace owner** | Change workspace owner. | `POST /api/v2/workspaces/current/change-owner` | [docs](https://developer.instantly.ai/api-reference/workspace/change-workspace-owner) | 2026-10-15 |
| **Delete organization agency domain** | Delete organization agency domain. | `DELETE /api/v2/workspaces/current/whitelabel-domain` | [docs](https://developer.instantly.ai/api-reference/workspace/delete-organization-agency-domain) | 2026-10-15 |
| **Get organization verified agency domain information** | Get organization verified agency domain information. | `GET /api/v2/workspaces/current/whitelabel-domain` | [docs](https://developer.instantly.ai/api-reference/workspace/get-organization-verified-agency-domain-information) | 2026-10-15 |
| **Get workspace** | Get your current workspace details. Note that this endpoint doesn't require any parameters. It will return the workspace based on the API key sent… | `GET /api/v2/workspaces/current` | [docs](https://developer.instantly.ai/api-reference/workspace/get-workspace) | 2026-10-15 |
| **Patch workspace** | Update your current workspace details. Note that this endpoint doesn't require any parameters. It will update the workspace based on the API key… | `PATCH /api/v2/workspaces/current` | [docs](https://developer.instantly.ai/api-reference/workspace/patch-workspace) | 2026-10-15 |
| **Schedule Current Workspace Removal** | Schedule the current workspace to be removed in 24 hours. | `POST /api/v2/workspaces/current/schedule-for-removal` | [docs](https://developer.instantly.ai/api-reference/workspace/schedule-current-workspace-removal) | 2026-10-15 |
| **Set the agency domain for the workspace** | Set the agency domain for the workspace. | `POST /api/v2/workspaces/current/whitelabel-domain` | [docs](https://developer.instantly.ai/api-reference/workspace/set-the-agency-domain-for-the-workspace) | 2026-10-15 |

#### Workspace Billing (2 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Get workspace plan details** | Get workspace plan details. | `GET /api/v2/workspace-billing/plan-details` | [docs](https://developer.instantly.ai/api-reference/workspacebilling/get-workspace-plan-details) | 2026-10-15 |
| **Get workspace subscription details** | Get workspace subscription details. | `GET /api/v2/workspace-billing/subscription-details` | [docs](https://developer.instantly.ai/api-reference/workspacebilling/get-workspace-subscription-details) | 2026-10-15 |

#### Workspace Group Members (5 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create workspace group member** | This endpoint allows you to send an invitation for a sub workspace to join the admin workspace. The sub workspace will be added as a sub workspace… | `POST /api/v2/workspace-group-members` | [docs](https://developer.instantly.ai/api-reference/workspacegroupmember/create-workspace-group-member) | 2026-10-15 |
| **Delete workspace group member** | Delete workspace group member. | `DELETE /api/v2/workspace-group-members/{id}` | [docs](https://developer.instantly.ai/api-reference/workspacegroupmember/delete-workspace-group-member) | 2026-10-15 |
| **Get the current workspace admin workspace** | Get the details of the admin workspace of the current workspace | `GET /api/v2/workspace-group-members/admin` | [docs](https://developer.instantly.ai/api-reference/workspacegroupmember/get-the-current-workspace-admin-workspace) | 2026-10-15 |
| **Get workspace group member** | Get workspace group member. | `GET /api/v2/workspace-group-members/{id}` | [docs](https://developer.instantly.ai/api-reference/workspacegroupmember/get-workspace-group-member) | 2026-10-15 |
| **List workspace group member** | List workspace group member. | `GET /api/v2/workspace-group-members` | [docs](https://developer.instantly.ai/api-reference/workspacegroupmember/list-workspace-group-member) | 2026-10-15 |

#### Workspace Members (5 tools)

| Tool | What it does | Endpoint | Docs | As of |
|---|---|---|---|---|
| **Create workspace member** | Create workspace member. | `POST /api/v2/workspace-members` | [docs](https://developer.instantly.ai/api-reference/workspacemember/create-workspace-member) | 2026-10-15 |
| **Delete workspace member** | Delete workspace member. | `DELETE /api/v2/workspace-members/{id}` | [docs](https://developer.instantly.ai/api-reference/workspacemember/delete-workspace-member) | 2026-10-15 |
| **Get workspace member** | Get workspace member. | `GET /api/v2/workspace-members/{id}` | [docs](https://developer.instantly.ai/api-reference/workspacemember/get-workspace-member) | 2026-10-15 |
| **List workspace member** | List workspace member. | `GET /api/v2/workspace-members` | [docs](https://developer.instantly.ai/api-reference/workspacemember/list-workspace-member) | 2026-10-15 |
| **Patch workspace member** | Patch workspace member. | `PATCH /api/v2/workspace-members/{id}` | [docs](https://developer.instantly.ai/api-reference/workspacemember/patch-workspace-member) | 2026-10-15 |
