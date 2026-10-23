# Instantly tools catalog 3 of 5

This skill holds: Part 3, API v2 endpoint groups: CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification, AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members.

Rules: name the feature or endpoint, give its exact docs link and say "as of <date>"; suggest checking the live docs. Recommend only items listed in the `instantly-tools-*` skills; never invent a feature, endpoint, parameter, limit or plan. Always write API keys as `YOUR_API_KEY`; never ask for or repeat a real key.

Where the rest of the catalog lives:
- `instantly-tools-1`: Part 1 (product features and tools) and Part 2 (developer guides)
- `instantly-tools-2`: Part 3, API v2 endpoint groups: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists
- `instantly-tools-3`: Part 3, API v2 endpoint groups: CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification, AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members
- `instantly-tools-4`: Part 4, Instantly MCP server (what it is, MCP vs REST, setup by client, auth and scopes, tool count) plus MCP tools for: Email Accounts, Account Campaign Mapping, AI Deliverability Agent, AI Inbox Manager, AI Lead Finder Agent, AI Sales Agent, API Keys, Audit Logs, Background Jobs, Blocklist Entries, Campaigns, Campaign Subsequences, Company Lists, CRM Actions, Custom Tags, Custom Tag Mappings, DFY Email Account Orders, Domain Forwarding, Email, Email Verification
- `instantly-tools-5`: Part 4 continued, MCP tools for: AI Agent Items, Inbox Placement Analytics, Inbox Placement Blacklist and SpamAssassin Reports, Inbox Placement Tests, Leads, Lead Labels, Lead Lists, OAuth, SuperSearch and Enrichment, Webhooks, Webhook Events, Workspace, Workspace Billing, Workspace Group Members, Workspace Members

---

## Part 3: API v2 endpoints, continued (as documented 2026-10-15)


Base: `https://api.instantly.ai`. Auth: Bearer API key with the listed scopes (see [Authorization](https://developer.instantly.ai/getting-started/authorization) and [Rate Limit](https://developer.instantly.ai/getting-started/rate-limit)).

### CRM Actions (`crmactions`, 2)

**When to use:** Use this group to list phone numbers or delete a phone number.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Delete phone number](https://developer.instantly.ai/api-reference/crmactions/delete-phone-number) | `DELETE /api/v2/crm-actions/phone-numbers/{id}` | crm_actions:delete, crm_actions:all, all:delete, all:all | Remove a phone number from the organization. Provider cleanup is retried automatically if delayed. Deleting an unknown or already removed number returns 404. A  |
| [List phone numbers](https://developer.instantly.ai/api-reference/crmactions/list-phone-numbers) | `GET /api/v2/crm-actions/phone-numbers` | crm_actions:read, crm_actions:all, all:read, all:all | Retrieve all phone numbers associated with the current organization. |

### Custom Tags (`customtag`, 6)

**When to use:** Use this group to create and manage custom tags and assign them to resources.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Assign or unassign tags to resources](https://developer.instantly.ai/api-reference/customtag/assign-or-unassign-tags-to-resources) | `POST /api/v2/custom-tags/toggle-resource` |  | This can be used for both accounts and campaigns. Please check the `resource_type` field for more information. |
| [Create custom tag](https://developer.instantly.ai/api-reference/customtag/create-custom-tag) | `POST /api/v2/custom-tags` | custom_tags:create, custom_tags:all, all:create, all:all | Requires one of the following scopes: `custom_tags:create`, `custom_tags:all`, `all:create`, `all:all` |
| [Delete custom tag](https://developer.instantly.ai/api-reference/customtag/delete-custom-tag) | `DELETE /api/v2/custom-tags/{id}` | custom_tags:delete, custom_tags:all, all:delete, all:all | Requires one of the following scopes: `custom_tags:delete`, `custom_tags:all`, `all:delete`, `all:all` |
| [Get custom tag](https://developer.instantly.ai/api-reference/customtag/get-custom-tag) | `GET /api/v2/custom-tags/{id}` | custom_tags:read, custom_tags:all, all:read, all:all | Requires one of the following scopes: `custom_tags:read`, `custom_tags:all`, `all:read`, `all:all` |
| [List custom tag](https://developer.instantly.ai/api-reference/customtag/list-custom-tag) | `GET /api/v2/custom-tags` | custom_tags:read, custom_tags:all, all:read, all:all | Requires one of the following scopes: `custom_tags:read`, `custom_tags:all`, `all:read`, `all:all` |
| [Patch custom tag](https://developer.instantly.ai/api-reference/customtag/patch-custom-tag) | `PATCH /api/v2/custom-tags/{id}` | custom_tags:update, custom_tags:all, all:update, all:all | Requires one of the following scopes: `custom_tags:update`, `custom_tags:all`, `all:update`, `all:all` |

### Custom Tag Mappings (`customtagmapping`, 1)

**When to use:** Use this group to list custom tag mappings.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [List custom tag mapping](https://developer.instantly.ai/api-reference/customtagmapping/list-custom-tag-mapping) | `GET /api/v2/custom-tag-mappings` | custom_tag_mappings:read, custom_tag_mappings:all, all:read, all:all | Requires one of the following scopes: `custom_tag_mappings:read`, `custom_tag_mappings:all`, `all:read`, `all:all` |

### DFY Email Account Orders (`dfyemailaccountorder`, 7)

**When to use:** Use this group to check domains and place or manage done-for-you email account orders.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Cancel dfy email accounts](https://developer.instantly.ai/api-reference/dfyemailaccountorder/cancel-dfy-email-accounts) | `POST /api/v2/dfy-email-account-orders/accounts/cancel` | dfy_email_account_orders:delete, dfy_email_account_orders:all, all:delete, all:all | This endpoint will cancel the DFY email accounts based on the provided email addresses. Cancelling permanently deletes all Unibox emails and conversations assoc |
| [Check domains availability](https://developer.instantly.ai/api-reference/dfyemailaccountorder/check-domains-availability) | `POST /api/v2/dfy-email-account-orders/domains/check` | dfy_email_account_orders:create, dfy_email_account_orders:all, all:create, all:all | This endpoint will check the availability of the provided domains.. It will return a list of domains with their availability status. |
| [Generate similar available domains](https://developer.instantly.ai/api-reference/dfyemailaccountorder/generate-similar-available-domains) | `POST /api/v2/dfy-email-account-orders/domains/similar` | dfy_email_account_orders:create, dfy_email_account_orders:all, all:create, all:all | This endpoint will generate a list of similar AND available domains based on the provided domain.. It will return a maximum number of 67 suggestions per extensi |
| [Get pre-warmed up domains](https://developer.instantly.ai/api-reference/dfyemailaccountorder/get-pre-warmed-up-domains) | `POST /api/v2/dfy-email-account-orders/domains/pre-warmed-up-list` | dfy_email_account_orders:read, dfy_email_account_orders:all, all:read, all:all | This endpoint will return a list of pre-warmed up domains available for order.<br/>These domains are set up and configured in advance, allowing for quick deploy |
| [List dfy email account order](https://developer.instantly.ai/api-reference/dfyemailaccountorder/list-dfy-email-account-order) | `GET /api/v2/dfy-email-account-orders` | dfy_email_account_orders:read, dfy_email_account_orders:all, all:read, all:all | Requires one of the following scopes: `dfy_email_account_orders:read`, `dfy_email_account_orders:all`, `all:read`, `all:all` |
| [List DFY ordered email accounts](https://developer.instantly.ai/api-reference/dfyemailaccountorder/list-dfy-ordered-email-accounts) | `GET /api/v2/dfy-email-account-orders/accounts` | dfy_email_account_orders:read, dfy_email_account_orders:all, all:read, all:all | This endpoint will return a list of DFY email accounts ordered |
| [Place a DFY email account order](https://developer.instantly.ai/api-reference/dfyemailaccountorder/place-a-dfy-email-account-order) | `POST /api/v2/dfy-email-account-orders` | dfy_email_account_orders:create, dfy_email_account_orders:all, all:create, all:all | Place a Done-For-You (DFY) email account order for your workspace. |

### Domain Forwarding (`domainforwarding`, 3)

**When to use:** Use this group to retrieve, set, or remove domain forwarding.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Get domain forwarding](https://developer.instantly.ai/api-reference/domainforwarding/get-domain-forwarding) | `GET /api/v2/domains/{domain}/forwarding` | dfy_email_account_orders:read, dfy_email_account_orders:all, all:read, all:all | Returns the stored web forwarding configuration for a domain ordered through Instantly. All fields except `domain` are null when no forwarding is configured. |
| [Remove domain forwarding](https://developer.instantly.ai/api-reference/domainforwarding/remove-domain-forwarding) | `DELETE /api/v2/domains/{domain}/forwarding` | dfy_email_account_orders:delete, dfy_email_account_orders:all, all:delete, all:all | Removes web forwarding from a domain ordered through Instantly. This operation is idempotent: removing forwarding from a domain that has none configured succeed |
| [Set domain forwarding](https://developer.instantly.ai/api-reference/domainforwarding/set-domain-forwarding) | `PUT /api/v2/domains/{domain}/forwarding` | dfy_email_account_orders:update, dfy_email_account_orders:all, all:update, all:all | Sets web forwarding on a domain ordered through Instantly. The forwarding domain must be a valid domain different from the domain itself. Returns a conflict err |

### Email (`email`, 9)

**When to use:** Use this group to list, read, reply to, forward, and manage emails.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Count unread emails](https://developer.instantly.ai/api-reference/email/count-unread-emails) | `GET /api/v2/emails/unread/count` | emails:read, emails:all, all:read, all:all | Requires one of the following scopes: `emails:read`, `emails:all`, `all:read`, `all:all` |
| [Delete email](https://developer.instantly.ai/api-reference/email/delete-email) | `DELETE /api/v2/emails/{id}` | emails:delete, emails:all, all:delete, all:all | Requires one of the following scopes: `emails:delete`, `emails:all`, `all:delete`, `all:all` |
| [Forward an email](https://developer.instantly.ai/api-reference/email/forward-an-email) | `POST /api/v2/emails/forward` | emails:create, emails:all, all:create, all:all | Forward an existing email to another recipient. You must specify the `reply_to_uuid` field, which represents the `id` of an existing email returned by the `/ema |
| [Get email](https://developer.instantly.ai/api-reference/email/get-email) | `GET /api/v2/emails/{id}` | emails:read, emails:all, all:read, all:all | Requires one of the following scopes: `emails:read`, `emails:all`, `all:read`, `all:all` |
| [List email](https://developer.instantly.ai/api-reference/email/list-email) | `GET /api/v2/emails` | emails:read, emails:all, all:read, all:all | **Rate Limit:** This endpoint has a rate limit of 20 requests per minute, unlike other API endpoints. |
| [Mark all emails in a thread as read](https://developer.instantly.ai/api-reference/email/mark-all-emails-in-a-thread-as-read) | `POST /api/v2/emails/threads/{thread_id}/mark-as-read` | emails:update, emails:all, all:update, all:all | Requires one of the following scopes: `emails:update`, `emails:all`, `all:update`, `all:all` |
| [Patch email](https://developer.instantly.ai/api-reference/email/patch-email) | `PATCH /api/v2/emails/{id}` | emails:update, emails:all, all:update, all:all | Requires one of the following scopes: `emails:update`, `emails:all`, `all:update`, `all:all` |
| [Reply to an email](https://developer.instantly.ai/api-reference/email/reply-to-an-email) | `POST /api/v2/emails/reply` | emails:create, emails:all, all:create, all:all | Send a reply to an email. This endpoint can be used to send an email only as a reply to an existing email. In order to reply to an email, please specify the `re |
| [Send a test email](https://developer.instantly.ai/api-reference/email/send-a-test-email) | `POST /api/v2/emails/test` | emails:create, emails:all, all:create, all:all | Send a preview/test email without creating an email entity in Unibox. Rate limit: 10 requests per minute per workspace. |

### Email Verification (`emailverification`, 2)

**When to use:** Use this group to create email verification checks and retrieve their status.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Check an email verification status](https://developer.instantly.ai/api-reference/emailverification/check-an-email-verification-status) | `GET /api/v2/email-verification/{email}` | email_verifications:read, email_verifications:all, all:read, all:all | Requires one of the following scopes: `email_verifications:read`, `email_verifications:all`, `all:read`, `all:all` |
| [Create email verification](https://developer.instantly.ai/api-reference/emailverification/create-email-verification) | `POST /api/v2/email-verification` | email_verifications:create | If an email takes longer than 10 seconds to verify, the endpoint will return the status as `pending`. In that case, you may use the `/email-verification/:email` |

### AI Agent Items (`engageitem`, 2)

**When to use:** Use this group to list or bulk-delete AI agent items.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Bulk delete AI agent items](https://developer.instantly.ai/api-reference/engageitem/bulk-delete-ai-agent-items) | `POST /api/v2/agent-items/bulk-delete` | all:delete, all:all | Requires one of the following scopes: `all:delete`, `all:all` |
| [List AI agent items](https://developer.instantly.ai/api-reference/engageitem/list-ai-agent-items) | `GET /api/v2/agent-items` | all:read, all:all | Requires one of the following scopes: `all:read`, `all:all` |

### Inbox Placement Analytics (`inboxplacementanalytics`, 5)

**When to use:** Use this group to retrieve inbox placement analytics and deliverability insights.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Get inbox placement analytics stats by date](https://developer.instantly.ai/api-reference/inboxplacementanalytics/get-inbox-placement-analytics-stats-by-date) | `POST /api/v2/inbox-placement-analytics/stats-by-date` | inbox_placement_analytics:read, inbox_placement_analytics:all, all:read, all:all | Provides a time series representing the distribution of emails sent to inbox, spam, or category folders for scheduled inbox placement tests. |
| [Get inbox placement analytics](https://developer.instantly.ai/api-reference/inboxplacementanalytics/get-inbox-placement-analytics) | `GET /api/v2/inbox-placement-analytics/{id}` | inbox_placement_analytics:read, inbox_placement_analytics:all, all:read, all:all | Requires one of the following scopes: `inbox_placement_analytics:read`, `inbox_placement_analytics:all`, `all:read`, `all:all` |
| [List inbox placement analytics](https://developer.instantly.ai/api-reference/inboxplacementanalytics/list-inbox-placement-analytics) | `GET /api/v2/inbox-placement-analytics` | inbox_placement_analytics:read, inbox_placement_analytics:all, all:read, all:all | Requires one of the following scopes: `inbox_placement_analytics:read`, `inbox_placement_analytics:all`, `all:read`, `all:all` |
| [Retrieve inbox placement analytics deliverability insights](https://developer.instantly.ai/api-reference/inboxplacementanalytics/retrieve-inbox-placement-analytics-deliverability-insights) | `POST /api/v2/inbox-placement-analytics/deliverability-insights` | inbox_placement_analytics:read, inbox_placement_analytics:all, all:read, all:all | Provides deliverability insights for a specific inbox placement test |
| [Retrieve inbox placement analytics stats by test id](https://developer.instantly.ai/api-reference/inboxplacementanalytics/retrieve-inbox-placement-analytics-stats-by-test-id) | `POST /api/v2/inbox-placement-analytics/stats-by-test-id` | inbox_placement_analytics:read, inbox_placement_analytics:all, all:read, all:all | Provides aggregated inbox, spam and category counts for specified test IDs |

### Inbox Placement Blacklist and SpamAssassin Reports (`inboxplacementblacklistandspamassassinreport`, 2)

**When to use:** Use this group to retrieve inbox placement blacklist and SpamAssassin reports.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Get inbox placement blacklist and spamassassin report](https://developer.instantly.ai/api-reference/inboxplacementblacklistandspamassassinreport/get-inbox-placement-blacklist-and-spamassassin-report) | `GET /api/v2/inbox-placement-reports/{id}` | inbox_placement_reports:read, inbox_placement_reports:all, all:read, all:all | Requires one of the following scopes: `inbox_placement_reports:read`, `inbox_placement_reports:all`, `all:read`, `all:all` |
| [List inbox placement blacklist and spamassassin report](https://developer.instantly.ai/api-reference/inboxplacementblacklistandspamassassinreport/list-inbox-placement-blacklist-and-spamassassin-report) | `GET /api/v2/inbox-placement-reports` | inbox_placement_reports:read, inbox_placement_reports:all, all:read, all:all | Requires one of the following scopes: `inbox_placement_reports:read`, `inbox_placement_reports:all`, `all:read`, `all:all` |

### Inbox Placement Tests (`inboxplacementtest`, 6)

**When to use:** Use this group to create, inspect, and manage inbox placement tests.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Create inbox placement test](https://developer.instantly.ai/api-reference/inboxplacementtest/create-inbox-placement-test) | `POST /api/v2/inbox-placement-tests` | inbox_placement_tests:create, inbox_placement_tests:all, all:create, all:all | Requires one of the following scopes: `inbox_placement_tests:create`, `inbox_placement_tests:all`, `all:create`, `all:all` |
| [Delete inbox placement test](https://developer.instantly.ai/api-reference/inboxplacementtest/delete-inbox-placement-test) | `DELETE /api/v2/inbox-placement-tests/{id}` | inbox_placement_tests:delete, inbox_placement_tests:all, all:delete, all:all | Requires one of the following scopes: `inbox_placement_tests:delete`, `inbox_placement_tests:all`, `all:delete`, `all:all` |
| [Get ESP options](https://developer.instantly.ai/api-reference/inboxplacementtest/get-esp-options) | `GET /api/v2/inbox-placement-tests/email-service-provider-options` |  | Provides a list of available email service providers for inbox placement tests. |
| [Get inbox placement test](https://developer.instantly.ai/api-reference/inboxplacementtest/get-inbox-placement-test) | `GET /api/v2/inbox-placement-tests/{id}` | inbox_placement_tests:read, inbox_placement_tests:all, all:read, all:all | Requires one of the following scopes: `inbox_placement_tests:read`, `inbox_placement_tests:all`, `all:read`, `all:all` |
| [List inbox placement test](https://developer.instantly.ai/api-reference/inboxplacementtest/list-inbox-placement-test) | `GET /api/v2/inbox-placement-tests` | inbox_placement_tests:read, inbox_placement_tests:all, all:read, all:all | Requires one of the following scopes: `inbox_placement_tests:read`, `inbox_placement_tests:all`, `all:read`, `all:all` |
| [Patch inbox placement test](https://developer.instantly.ai/api-reference/inboxplacementtest/patch-inbox-placement-test) | `PATCH /api/v2/inbox-placement-tests/{id}` | inbox_placement_tests:update, inbox_placement_tests:all, all:update, all:all | Requires one of the following scopes: `inbox_placement_tests:update`, `inbox_placement_tests:all`, `all:update`, `all:all` |

### Leads (`lead`, 13)

**When to use:** Use this group to create, update, move, assign, and remove leads.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Add leads in bulk to a campaign or list](https://developer.instantly.ai/api-reference/lead/add-leads-in-bulk-to-a-campaign-or-list) | `POST /api/v2/leads/add` | leads:create, leads:all, all:create, all:all | Adds up to 1000 leads to either a campaign or a list. You must provide a `campaign_id` or a `list_id`, but not both. The endpoint validates emails, checks again |
| [Bulk assign leads to organization users](https://developer.instantly.ai/api-reference/lead/bulk-assign-leads-to-organization-users) | `POST /api/v2/leads/bulk-assign` |  | Bulk assign leads to organization users |
| [Create lead](https://developer.instantly.ai/api-reference/lead/create-lead) | `POST /api/v2/leads` | leads:create, leads:all, all:create, all:all | Requires one of the following scopes: `leads:create`, `leads:all`, `all:create`, `all:all` |
| [Delete lead](https://developer.instantly.ai/api-reference/lead/delete-lead) | `DELETE /api/v2/leads/{id}` | leads:delete, leads:all, all:delete, all:all | Requires one of the following scopes: `leads:delete`, `leads:all`, `all:delete`, `all:all` |
| [Delete leads in bulk](https://developer.instantly.ai/api-reference/lead/delete-leads-in-bulk) | `DELETE /api/v2/leads` | leads:delete, leads:all, all:delete, all:all | Delete multiple leads from a campaign or list based on filters. You must provide either `campaign_id` or `list_id`. Optionally filter by status or specific IDs. |
| [Get lead](https://developer.instantly.ai/api-reference/lead/get-lead) | `GET /api/v2/leads/{id}` | leads:read, leads:all, all:read, all:all | Requires one of the following scopes: `leads:read`, `leads:all`, `all:read`, `all:all` |
| [List leads](https://developer.instantly.ai/api-reference/lead/list-leads) | `POST /api/v2/leads/list` | leads:read, leads:all, all:read, all:all | This endpoint is a POST endpoint, instead of GET - a deviation from the REST APIs standards we’re following because of the complex arguments it accepts, which w |
| [Merge two leads](https://developer.instantly.ai/api-reference/lead/merge-two-leads) | `POST /api/v2/leads/merge` | leads:update, leads:all, all:update, all:all | Merge two leads |
| [Move a lead to a subsequence](https://developer.instantly.ai/api-reference/lead/move-a-lead-to-a-subsequence) | `POST /api/v2/leads/subsequence/move` | leads:update, leads:all, all:update, all:all | Move a lead to a subsequence |
| [Move leads to a campaign or list](https://developer.instantly.ai/api-reference/lead/move-leads-to-a-campaign-or-list) | `POST /api/v2/leads/move` | leads:update, leads:all, all:update, all:all | Move leads to a different campaign or list. This endpoint will return a background job that will process the move. The job will be processed in the background a |
| [Patch lead](https://developer.instantly.ai/api-reference/lead/patch-lead) | `PATCH /api/v2/leads/{id}` | leads:update, leads:all, all:update, all:all | Requires one of the following scopes: `leads:update`, `leads:all`, `all:update`, `all:all` |
| [Remove a lead from a subsequence](https://developer.instantly.ai/api-reference/lead/remove-a-lead-from-a-subsequence) | `POST /api/v2/leads/subsequence/remove` | leads:update, leads:all, all:update, all:all | Remove a lead from a subsequence |
| [Update the interest status of a lead](https://developer.instantly.ai/api-reference/lead/update-the-interest-status-of-a-lead) | `POST /api/v2/leads/update-interest-status` |  | Update the interest status of a lead |

### Lead Labels (`leadlabel`, 6)

**When to use:** Use this group to manage lead labels and test AI reply label predictions.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Create lead label](https://developer.instantly.ai/api-reference/leadlabel/create-lead-label) | `POST /api/v2/lead-labels` | lead-labels:create, lead-labels:all, all:create, all:all | Requires one of the following scopes: `lead-labels:create`, `lead-labels:all`, `all:create`, `all:all` |
| [Delete lead label](https://developer.instantly.ai/api-reference/leadlabel/delete-lead-label) | `DELETE /api/v2/lead-labels/{id}` | lead-labels:delete, lead-labels:all, all:delete, all:all | Requires one of the following scopes: `lead-labels:delete`, `lead-labels:all`, `all:delete`, `all:all` |
| [Get lead label](https://developer.instantly.ai/api-reference/leadlabel/get-lead-label) | `GET /api/v2/lead-labels/{id}` | lead-labels:read, lead-labels:all, all:read, all:all | Requires one of the following scopes: `lead-labels:read`, `lead-labels:all`, `all:read`, `all:all` |
| [List lead label](https://developer.instantly.ai/api-reference/leadlabel/list-lead-label) | `GET /api/v2/lead-labels` | lead-labels:read, lead-labels:all, all:read, all:all | Requires one of the following scopes: `lead-labels:read`, `lead-labels:all`, `all:read`, `all:all` |
| [Patch lead label](https://developer.instantly.ai/api-reference/leadlabel/patch-lead-label) | `PATCH /api/v2/lead-labels/{id}` | lead-labels:update, lead-labels:all, all:update, all:all | Requires one of the following scopes: `lead-labels:update`, `lead-labels:all`, `all:update`, `all:all` |
| [Test AI reply label prediction](https://developer.instantly.ai/api-reference/leadlabel/test-ai-reply-label-prediction) | `POST /api/v2/lead-labels/ai-reply-label` | lead-labels:read, lead-labels:all, all:read, all:all | Returns the AI-predicted lead label for a reply text. This simulates how AI auto-tagging would label an incoming reply for testing custom labels and description |

### Lead Lists (`leadlist`, 6)

**When to use:** Use this group to manage lead lists and retrieve verification statistics.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Create lead list](https://developer.instantly.ai/api-reference/leadlist/create-lead-list) | `POST /api/v2/lead-lists` | lead_lists:create, lead_lists:all, all:create, all:all | Requires one of the following scopes: `lead_lists:create`, `lead_lists:all`, `all:create`, `all:all` |
| [Delete lead list](https://developer.instantly.ai/api-reference/leadlist/delete-lead-list) | `DELETE /api/v2/lead-lists/{id}` | lead_lists:delete, lead_lists:all, all:delete, all:all | Requires one of the following scopes: `lead_lists:delete`, `lead_lists:all`, `all:delete`, `all:all` |
| [Get lead list](https://developer.instantly.ai/api-reference/leadlist/get-lead-list) | `GET /api/v2/lead-lists/{id}` | lead_lists:read, lead_lists:all, all:read, all:all | Requires one of the following scopes: `lead_lists:read`, `lead_lists:all`, `all:read`, `all:all` |
| [Get verification statistics for a lead list](https://developer.instantly.ai/api-reference/leadlist/get-verification-statistics-for-a-lead-list) | `GET /api/v2/lead-lists/{id}/verification-stats` |  | Get verification statistics for a lead list |
| [List lead list](https://developer.instantly.ai/api-reference/leadlist/list-lead-list) | `GET /api/v2/lead-lists` | lead_lists:read, lead_lists:all, all:read, all:all | Requires one of the following scopes: `lead_lists:read`, `lead_lists:all`, `all:read`, `all:all` |
| [Patch lead list](https://developer.instantly.ai/api-reference/leadlist/patch-lead-list) | `PATCH /api/v2/lead-lists/{id}` | lead_lists:update, lead_lists:all, all:update, all:all | Requires one of the following scopes: `lead_lists:update`, `lead_lists:all`, `all:update`, `all:all` |

### OAuth (`oauth`, 3)

**When to use:** Use this group to initialize Google or Microsoft OAuth and check session status.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Get oauth session status](https://developer.instantly.ai/api-reference/oauth/get-oauth-session-status) | `GET /api/v2/oauth/session/status/{sessionId}` |  | Poll this endpoint to check the OAuth session result. Works for both Google and Microsoft OAuth sessions. Returns pending while waiting, success with account de |
| [Initialize google oauth](https://developer.instantly.ai/api-reference/oauth/initialize-google-oauth) | `POST /api/v2/oauth/google/init` |  | Creates an OAuth session and returns the Google authorization URL. The user should be redirected to auth_url to complete the OAuth flow. Poll the status endpoin |
| [Initialize microsoft oauth](https://developer.instantly.ai/api-reference/oauth/initialize-microsoft-oauth) | `POST /api/v2/oauth/microsoft/init` |  | Creates an OAuth session and returns the Microsoft authorization URL. The user should be redirected to auth_url to complete the OAuth flow. Poll the status endp |

### SuperSearch and Enrichment (`supersearchenrichment`, 18)

**When to use:** Use this group to search for leads and manage enrichment workflows and provider lookups.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Count leads from supersearch](https://developer.instantly.ai/api-reference/supersearchenrichment/count-leads-from-supersearch) | `POST /api/v2/supersearch-enrichment/count-leads-from-supersearch` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | Count the number of leads matching a SuperSearch query without enriching them. This endpoint is intended to estimate lead availability before running an enrichm |
| [Create AI enrichment](https://developer.instantly.ai/api-reference/supersearchenrichment/create-ai-enrichment) | `POST /api/v2/supersearch-enrichment/ai` | supersearch_enrichments:create, supersearch_enrichments:all, all:create, all:all | Create an AI enrichment for a resource (list or campaign) |
| [Create an enrichment](https://developer.instantly.ai/api-reference/supersearchenrichment/create-an-enrichment) | `POST /api/v2/supersearch-enrichment/` |  | Create an enrichment for a specific resource (list or campaign). This is the main endpoint for adding enrichments to resources. The enrichments are automaticall |
| [Delete a saved search](https://developer.instantly.ai/api-reference/supersearchenrichment/delete-a-saved-search) | `DELETE /api/v2/supersearch-enrichment/saved-searches/{id}` | supersearch_enrichments:delete, supersearch_enrichments:all, all:delete, all:all | Requires one of the following scopes: `supersearch_enrichments:delete`, `supersearch_enrichments:all`, `all:delete`, `all:all` |
| [Enrich leads from supersearch](https://developer.instantly.ai/api-reference/supersearchenrichment/enrich-leads-from-supersearch) | `POST /api/v2/supersearch-enrichment/enrich-leads-from-supersearch` |  | Add leads from SuperSearch to a list and enrich them. A list is automatically created if no list is provided. |
| [Facet keywords for a signal category](https://developer.instantly.ai/api-reference/supersearchenrichment/facet-keywords-for-a-signal-category) | `POST /api/v2/supersearch-enrichment/signal-keywords-facet` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | Return the top matching keyword tokens for a given signal category and keyword field, aggregated from the last 90 days of signal data. Powers the Signals filter |
| [Get a saved search](https://developer.instantly.ai/api-reference/supersearchenrichment/get-a-saved-search) | `GET /api/v2/supersearch-enrichment/saved-searches/{id}` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | Requires one of the following scopes: `supersearch_enrichments:read`, `supersearch_enrichments:all`, `all:read`, `all:all` |
| [Get AI enrichment for resource](https://developer.instantly.ai/api-reference/supersearchenrichment/get-ai-enrichment-for-resource) | `GET /api/v2/supersearch-enrichment/ai/{resource_id}/in-progress` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | Get the AI enrichment for a specific resource |
| [Get enrichment for resource](https://developer.instantly.ai/api-reference/supersearchenrichment/get-enrichment-for-resource) | `GET /api/v2/supersearch-enrichment/{resource_id}` |  | Get the enrichment for a specific resource |
| [Get enrichment history](https://developer.instantly.ai/api-reference/supersearchenrichment/get-enrichment-history) | `GET /api/v2/supersearch-enrichment/history/{resource_id}` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | Retrieve the enrichment history for a specific resource |
| [List saved searches](https://developer.instantly.ai/api-reference/supersearchenrichment/list-saved-searches) | `GET /api/v2/supersearch-enrichment/saved-searches` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | List the workspace's saved SuperSearch queries, newest first. |
| [Preview leads from supersearch](https://developer.instantly.ai/api-reference/supersearchenrichment/preview-leads-from-supersearch) | `POST /api/v2/supersearch-enrichment/preview-leads-from-supersearch` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | Preview the leads matching a SuperSearch query without enriching them |
| [Returns the full integration provider registry](https://developer.instantly.ai/api-reference/supersearchenrichment/returns-the-full-integration-provider-registry) | `GET /api/v2/supersearch-enrichment/integrations/providers` | supersearch_enrichments:read, supersearch_enrichments:all, all:read, all:all | Returns every data-provider integration with its available lookup actions, per-action credit cost, and whether the requesting workspace has connected its own pr |
| [Run a single integration lookup action synchronously](https://developer.instantly.ai/api-reference/supersearchenrichment/run-a-single-integration-lookup-action-synchronously) | `POST /api/v2/supersearch-enrichment/integrations/run` | supersearch_enrichments:create, supersearch_enrichments:all, all:create, all:all | Executes one lookup action for a single record with literal inputs and returns the provider payload inline, under the action's output column. |
| [Run enrichment for resource](https://developer.instantly.ai/api-reference/supersearchenrichment/run-enrichment-for-resource) | `POST /api/v2/supersearch-enrichment/run` |  | Run all enrichments associated with a resource for a list of leads or for all the leads that haven't been enriched yet |
| [Save a search](https://developer.instantly.ai/api-reference/supersearchenrichment/save-a-search) | `POST /api/v2/supersearch-enrichment/saved-searches` | supersearch_enrichments:create, supersearch_enrichments:all, all:create, all:all | Save a SuperSearch query for reuse. `search_filters` uses the same shape as the count, preview and enrich endpoints. |
| [Update a saved search](https://developer.instantly.ai/api-reference/supersearchenrichment/update-a-saved-search) | `PATCH /api/v2/supersearch-enrichment/saved-searches/{id}` | supersearch_enrichments:update, supersearch_enrichments:all, all:update, all:all | Rename a saved search and/or replace its filters. |
| [Update enrichment settings for resource](https://developer.instantly.ai/api-reference/supersearchenrichment/update-enrichment-settings-for-resource) | `PATCH /api/v2/supersearch-enrichment/{resource_id}/settings` | supersearch_enrichments:create, supersearch_enrichments:all, all:create, all:all | Update auto-update and skip settings for a SuperSearch enrichment tied to a specific resource |

### Webhooks (`webhook`, 8)

**When to use:** Use this group to configure, test, pause, and manage webhooks and available event types.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Create webhook](https://developer.instantly.ai/api-reference/webhook/create-webhook) | `POST /api/v2/webhooks` | webhooks:create, webhooks:all, all:create, all:all | Requires one of the following scopes: `webhooks:create`, `webhooks:all`, `all:create`, `all:all` |
| [Delete webhook](https://developer.instantly.ai/api-reference/webhook/delete-webhook) | `DELETE /api/v2/webhooks/{id}` | webhooks:delete, webhooks:all, all:delete, all:all | Requires one of the following scopes: `webhooks:delete`, `webhooks:all`, `all:delete`, `all:all` |
| [Get webhook](https://developer.instantly.ai/api-reference/webhook/get-webhook) | `GET /api/v2/webhooks/{id}` | webhooks:read, webhooks:all, all:read, all:all | Requires one of the following scopes: `webhooks:read`, `webhooks:all`, `all:read`, `all:all` |
| [List available event types](https://developer.instantly.ai/api-reference/webhook/list-available-event-types) | `GET /api/v2/webhooks/event-types` |  | Get all available webhook event types including custom labels |
| [List webhooks](https://developer.instantly.ai/api-reference/webhook/list-webhooks) | `GET /api/v2/webhooks` |  | List all webhooks for the workspace with optional filters |
| [Patch webhook](https://developer.instantly.ai/api-reference/webhook/patch-webhook) | `PATCH /api/v2/webhooks/{id}` | webhooks:update, webhooks:all, all:update, all:all | Requires one of the following scopes: `webhooks:update`, `webhooks:all`, `all:update`, `all:all` |
| [Resume a webhook](https://developer.instantly.ai/api-reference/webhook/resume-a-webhook) | `POST /api/v2/webhooks/{id}/resume` | webhooks:update, webhooks:all, all:update, all:all | Resume a webhook that was disabled due to repeated delivery failures |
| [Test a webhook](https://developer.instantly.ai/api-reference/webhook/test-a-webhook) | `POST /api/v2/webhooks/{id}/test` |  | Send a test payload to a webhook URL to verify it is working |

### Webhook Events (`webhookevent`, 4)

**When to use:** Use this group to inspect webhook events and event aggregates over time.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Get overview aggregates for webhook events by date](https://developer.instantly.ai/api-reference/webhookevent/get-overview-aggregates-for-webhook-events-by-date) | `GET /api/v2/webhook-events/summary-by-date` |  | Get overview aggregates for webhook events by Date for charts |
| [Get overview aggregates for webhook events](https://developer.instantly.ai/api-reference/webhookevent/get-overview-aggregates-for-webhook-events) | `GET /api/v2/webhook-events/summary` |  | Get overview aggregates for webhook events including success/failure rates |
| [Get webhook event](https://developer.instantly.ai/api-reference/webhookevent/get-webhook-event) | `GET /api/v2/webhook-events/{id}` | webhook_events:read, webhook_events:all, all:read, all:all | Requires one of the following scopes: `webhook_events:read`, `webhook_events:all`, `all:read`, `all:all` |
| [List webhook event](https://developer.instantly.ai/api-reference/webhookevent/list-webhook-event) | `GET /api/v2/webhook-events` | webhook_events:read, webhook_events:all, all:read, all:all | Requires one of the following scopes: `webhook_events:read`, `webhook_events:all`, `all:read`, `all:all` |

### Workspace (`workspace`, 8)

**When to use:** Use this group to retrieve or update workspace settings, ownership, and agency domain configuration.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Cancel Current Workspace Removal](https://developer.instantly.ai/api-reference/workspace/cancel-current-workspace-removal) | `DELETE /api/v2/workspaces/current/schedule-for-removal` | workspaces:delete, workspaces:all, all:delete, all:all | Requires one of the following scopes: `workspaces:delete`, `workspaces:all`, `all:delete`, `all:all` |
| [Change workspace owner](https://developer.instantly.ai/api-reference/workspace/change-workspace-owner) | `POST /api/v2/workspaces/current/change-owner` | workspaces:update, workspaces:all, all:update, all:all | Requires one of the following scopes: `workspaces:update`, `workspaces:all`, `all:update`, `all:all` |
| [Delete organization agency domain](https://developer.instantly.ai/api-reference/workspace/delete-organization-agency-domain) | `DELETE /api/v2/workspaces/current/whitelabel-domain` | workspaces:update, workspaces:all, all:update, all:all | Requires one of the following scopes: `workspaces:update`, `workspaces:all`, `all:update`, `all:all` |
| [Get organization verified agency domain information](https://developer.instantly.ai/api-reference/workspace/get-organization-verified-agency-domain-information) | `GET /api/v2/workspaces/current/whitelabel-domain` | workspaces:read, workspaces:all, all:read, all:all | Requires one of the following scopes: `workspaces:read`, `workspaces:all`, `all:read`, `all:all` |
| [Get workspace](https://developer.instantly.ai/api-reference/workspace/get-workspace) | `GET /api/v2/workspaces/current` | workspaces:read, workspaces:all, all:read, all:all | Get your current workspace details. Note that this endpoint doesn't require any parameters. It will return the workspace based on the API key sent in the header |
| [Patch workspace](https://developer.instantly.ai/api-reference/workspace/patch-workspace) | `PATCH /api/v2/workspaces/current` | workspaces:update, workspaces:all, all:update, all:all | Update your current workspace details. Note that this endpoint doesn't require any parameters. It will update the workspace based on the API key sent in the hea |
| [Schedule Current Workspace Removal](https://developer.instantly.ai/api-reference/workspace/schedule-current-workspace-removal) | `POST /api/v2/workspaces/current/schedule-for-removal` | workspaces:delete, workspaces:all, all:delete, all:all | Schedule the current workspace to be removed in 24 hours. |
| [Set the agency domain for the workspace](https://developer.instantly.ai/api-reference/workspace/set-the-agency-domain-for-the-workspace) | `POST /api/v2/workspaces/current/whitelabel-domain` | workspaces:update, workspaces:all, all:update, all:all | Requires one of the following scopes: `workspaces:update`, `workspaces:all`, `all:update`, `all:all` |

### Workspace Billing (`workspacebilling`, 2)

**When to use:** Use this group to retrieve workspace plan and subscription details.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Get workspace plan details](https://developer.instantly.ai/api-reference/workspacebilling/get-workspace-plan-details) | `GET /api/v2/workspace-billing/plan-details` | workspace_billing:read, workspace_billing:all, all:read, all:all | Requires one of the following scopes: `workspace_billing:read`, `workspace_billing:all`, `all:read`, `all:all` |
| [Get workspace subscription details](https://developer.instantly.ai/api-reference/workspacebilling/get-workspace-subscription-details) | `GET /api/v2/workspace-billing/subscription-details` | workspace_billing:read, workspace_billing:all, all:read, all:all | Requires one of the following scopes: `workspace_billing:read`, `workspace_billing:all`, `all:read`, `all:all` |

### Workspace Group Members (`workspacegroupmember`, 5)

**When to use:** Use this group to manage members and inspect the current admin workspace for workspace groups.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Create workspace group member](https://developer.instantly.ai/api-reference/workspacegroupmember/create-workspace-group-member) | `POST /api/v2/workspace-group-members` | workspace_group_members:create, workspace_group_members:all, all:create, all:all | This endpoint allows you to send an invitation for a sub workspace to join the admin workspace. The sub workspace will be added as a sub workspace of the admin  |
| [Delete workspace group member](https://developer.instantly.ai/api-reference/workspacegroupmember/delete-workspace-group-member) | `DELETE /api/v2/workspace-group-members/{id}` | workspace_group_members:delete, workspace_group_members:all, all:delete, all:all | Requires one of the following scopes: `workspace_group_members:delete`, `workspace_group_members:all`, `all:delete`, `all:all` |
| [Get the current workspace admin workspace](https://developer.instantly.ai/api-reference/workspacegroupmember/get-the-current-workspace-admin-workspace) | `GET /api/v2/workspace-group-members/admin` |  | Get the details of the admin workspace of the current workspace |
| [Get workspace group member](https://developer.instantly.ai/api-reference/workspacegroupmember/get-workspace-group-member) | `GET /api/v2/workspace-group-members/{id}` | workspace_group_members:read, workspace_group_members:all, all:read, all:all | Requires one of the following scopes: `workspace_group_members:read`, `workspace_group_members:all`, `all:read`, `all:all` |
| [List workspace group member](https://developer.instantly.ai/api-reference/workspacegroupmember/list-workspace-group-member) | `GET /api/v2/workspace-group-members` | workspace_group_members:read, workspace_group_members:all, all:read, all:all | Requires one of the following scopes: `workspace_group_members:read`, `workspace_group_members:all`, `all:read`, `all:all` |

### Workspace Members (`workspacemember`, 5)

**When to use:** Use this group to create, update, list, and remove workspace members.

| Endpoint | Method + path | Scopes | What it does |
|---|---|---|---|
| [Create workspace member](https://developer.instantly.ai/api-reference/workspacemember/create-workspace-member) | `POST /api/v2/workspace-members` | workspace_members:create, workspace_members:all, all:create, all:all | Requires one of the following scopes: `workspace_members:create`, `workspace_members:all`, `all:create`, `all:all` |
| [Delete workspace member](https://developer.instantly.ai/api-reference/workspacemember/delete-workspace-member) | `DELETE /api/v2/workspace-members/{id}` | workspace_members:delete, workspace_members:all, all:delete, all:all | Requires one of the following scopes: `workspace_members:delete`, `workspace_members:all`, `all:delete`, `all:all` |
| [Get workspace member](https://developer.instantly.ai/api-reference/workspacemember/get-workspace-member) | `GET /api/v2/workspace-members/{id}` | workspace_members:read, workspace_members:all, all:read, all:all | Requires one of the following scopes: `workspace_members:read`, `workspace_members:all`, `all:read`, `all:all` |
| [List workspace member](https://developer.instantly.ai/api-reference/workspacemember/list-workspace-member) | `GET /api/v2/workspace-members` | workspace_members:read, workspace_members:all, all:read, all:all | Requires one of the following scopes: `workspace_members:read`, `workspace_members:all`, `all:read`, `all:all` |
| [Patch workspace member](https://developer.instantly.ai/api-reference/workspacemember/patch-workspace-member) | `PATCH /api/v2/workspace-members/{id}` | workspace_members:update, workspace_members:all, all:update, all:all | Requires one of the following scopes: `workspace_members:update`, `workspace_members:all`, `all:update`, `all:all` |

