# Instantly quote banks 4: Platform, API and integrations

Covers: API & Integrations, Instantly Platform How-To.

Verbatim lines from Instantly's public content (blog, help center, Academy, YouTube, X), each with its source date and public link. Use when you need exact wording or a citation; never paraphrase inside quotation marks. Topic notes are in `instantly-topics-4`.

## Quote bank: API & Integrations

Exact quotes from Instantly's public content (blog, help center, Academy, YouTube, X) on `api-and-integrations` (Instantly API v2, webhooks, MCP/SDK, CRM and automation integrations (HubSpot, Pipedrive, Salesforce, Zapier, Make), and how Instantly fits into an outbound tool stack.). Every quote was verified by substring match against the raw source; YouTube timestamps come from the caption (.vtt) cue where the quote starts. Each line shows the source date: newer guidance wins over older. Use these when you need exact wording. Do not paraphrase inside quotation marks.

Topic note: file `knowledge/instantly-topics-4.md` in this repo, section "Topic: API & Integrations"

1. "Use MCP when an AI agent needs to make decisions and take actions in real time. Use REST when you need to move large volumes of data reliably between systems."  
   — *MCP Server vs traditional API integration: which approach is right for your outreach stack?* (Blog, 2026-06-19) · [link](https://instantly.ai/blog/mcp-server-vs-api-integration/)
2. "Rather than treating MCP and REST as competing choices, the smart approach is to understand what each protocol does well and build a hybrid stack that uses both."  
   — *MCP Server vs traditional API integration: which approach is right for your outreach stack?* (Blog, 2026-06-19) · [link](https://instantly.ai/blog/mcp-server-vs-api-integration/)
3. "REST excels at high-volume, stateless services where you need predictable throughput and fine-grained control over individual records."  
   — *MCP Server vs traditional API integration: which approach is right for your outreach stack?* (Blog, 2026-06-19) · [link](https://instantly.ai/blog/mcp-server-vs-api-integration/)
4. "The rate limit is shared between API v2 and API v1, and it applies to the entire Workspace, even if it's using multiple API keys."  
   — *getting-started_rate-limit* (Developer docs, date unknown) · [link](https://developer.instantly.ai/getting-started/rate-limit)
5. "Make your handlers idempotent so retries do not double-process."  
   — *Instantly API & Webhooks: Custom integrations for advanced outreach* (Blog, 2025-10-09) · [link](https://instantly.ai/blog/api-webhooks-custom-integrations-for-outreach/)
6. "Use webhooks to push events to your systems in real time. The webhook guide lists event types, payloads, and setup steps."  
   — *Instantly API & Webhooks: Custom integrations for advanced outreach* (Blog, 2025-10-09) · [link](https://instantly.ai/blog/api-webhooks-custom-integrations-for-outreach/)
7. "Your mapping determines whether analytics and attribution are trustworthy. Use Email as the unique key, keep naming consistent, and capture campaign context."  
   — *Integrating Instantly with HubSpot: Streamlining cold email campaigns and lead sync* (Blog, 2025-09-05) · [link](https://instantly.ai/blog/integrating-instantly-ai-with-hubspot/)
8. "Real-time sync prevents your AI BDR from messaging active opportunities or opted-out contacts. One-way sync creates data silos where your AI tool sends emails to prospects who already became customers because it never received the "closed" signal from the CRM."  
   — *AI BDR and CRM integration: Connecting your sales stack for clean data flow* (Blog, 2026-07-13) · [link](https://instantly.ai/blog/ai-bdr-crm-integration/)
9. "Use email address as your primary unique identifier in HubSpot. In your Zapier or Make flow, always search by email first, update if found, and create only if no match exists."  
   — *AI BDR and CRM integration: Connecting your sales stack for clean data flow* (Blog, 2026-07-13) · [link](https://instantly.ai/blog/ai-bdr-crm-integration/)
10. "Every action an AI BDR takes, including sourcing a lead, enrolling them in a sequence, logging an open, and routing a reply, must map to a specific CRM object."  
   — *AI BDR and CRM integration: Connecting your sales stack for clean data flow* (Blog, 2026-07-13) · [link](https://instantly.ai/blog/ai-bdr-crm-integration/)
11. "Solving drift means treating the CRM as the single system of record and streaming every outbound event into it in real time."  
   — *AI sales agents for data integration: reliable CRM & workflow sync* (Blog, 2026-06-10) · [link](https://instantly.ai/blog/ai-sales-agents-data-integration-crm/)
12. "Apply "always update" only to fields that Instantly owns and is the most current source for: reply status, bounce flags, and outreach stage. For everything else, use "update if blank.""  
   — *How to integrate your AI SDR with your CRM: setup guide* (Blog, 2026-06-19) · [link](https://instantly.ai/blog/ai-sdr-crm-integration-guide/)
13. "A composable sales stack flips this model. You choose the best email engine, the best CRM, and the best enrichment source, then connect them through APIs, webhooks, or integration platforms."  
   — *How to integrate cold email and text messaging (SMS) for multi-channel sales outreach* (Blog, 2025-11-07) · [link](https://instantly.ai/blog/how-to-integrate-cold-email-text-messaging-sms/)
14. "Start with native or partner sync for core CRM logging, and add Zapier only for edge cases. This reduces points of failure and keeps data fidelity high, as argued in The revenue team’s integration guide."  
   — *Streamline Sales: Instantly.ai CRM integration for B2B lead flow* (Blog, 2025-09-12) · [link](https://instantly.ai/blog/crm-integration/)
15. "Use Zapier and Make to connect Instantly to thousands of tools, enrich data, and trigger actions based on real events like new replies, bounces, or booked meetings."  
   — *Instantly AI integrations: connect, automate, scale your outreach* (Blog, 2025-10-05) · [link](https://instantly.ai/blog/instantly-ai-integrations/)
16. "You can now connect HubSpot directly to Instantly Automations and enable two-way lead sync and automation between your CRM and outbound workflows."  
   — *HubSpot Integration in Automations* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/13342530-hubspot-integration-in-automations)
17. "You can connect your Pipedrive to Instantly to import leads, export SuperSearch leads, or build workflows in Automations."  
   — *How to connect Pipedrive to Instantly* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/8848881-how-to-connect-pipedrive-to-instantly)
18. "Instantly Automations links your CRM, inbox, ads, and every sales tool you use, then lets AI run the workflows between them."  
   — *Your Entire Sales Stack. Finally Connected.* (Product page, date unknown) · [link](https://instantly.ai/ai-agents/automations)
19. "Every contact update, deal stage change, reply, and meeting booked flows back into your CRM automatically. Your pipeline stays clean. Your reps stay selling."  
   — *Your Entire Sales Stack. Finally Connected.* (Product page, date unknown) · [link](https://instantly.ai/ai-agents/automations)
20. "The Instantly MCP server exposes the full Instantly V2 API as MCP tools. Every API endpoint is available as a tool your AI assistant can call."  
   — *mcp_tools* (Developer docs, date unknown) · [link](https://developer.instantly.ai/mcp/tools)
21. "Each MCP tool corresponds to a single API endpoint. Tool names follow the pattern `{action}_{resource}` — for example, `list_campaigns`, `create_lead`, or `get_campaign_analytics`."  
   — *mcp_tools* (Developer docs, date unknown) · [link](https://developer.instantly.ai/mcp/tools)
22. "You need every action the agent takes to land in your CRM as a clean, timestamped, attributable record, which is exactly what Instantly's AI agents deliver. Without that, your pipeline reports are fiction, no matter how capable your AI sales automation agent is."  
   — *AI sales agents for data integration: reliable CRM & workflow sync* (Blog, 2026-06-10) · [link](https://instantly.ai/blog/ai-sales-agents-data-integration-crm/)
23. "Bidirectional sync pushes CRM block lists back into Instantly automatically, so suppression records align between marketing ops and sales ops and reduce the risk of re-engaging a prospect who already asked to opt out."  
   — *Decision-maker prospecting automation: tools that integrate with your email and CRM* (Blog, 2026-05-15) · [link](https://instantly.ai/blog/decision-maker-prospecting-automation-tools/)
24. "if you have a team it's optional you can do it without it and then save here to add some automations if somebody books a meeting in your calendly you can have all the information coming to your slack"  
   — *Part 4 - Tools You Need - Cold Email Sales Masterclass* (YouTube, 2022-09-27) · [1:42](https://www.youtube.com/watch?v=5H5DRyxMKpY&t=102s)

## Instantly MCP server (added 2026-10-15)

25. "Instantly MCP Server is a connector that lets your AI assistants communicate directly with your Instantly account. Your AI can create campaigns, manage leads, pull analytics, and more."  
   — *Instantly MCP(Model Context Protocol)* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/12980002-instantly-mcp-model-context-protocol)
26. "The MCP server is free with your Instantly subscription. You just need an account with API access."  
   — *Instantly MCP(Model Context Protocol)* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/12980002-instantly-mcp-model-context-protocol)
27. "Most actions can be undone, and destructive actions like delete are clearly marked. The AI will typically confirm before taking major actions."  
   — *Instantly MCP(Model Context Protocol)* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/12980002-instantly-mcp-model-context-protocol)
28. "Send your API key in the `Authorization` header. This is the recommended method — it keeps your key out of server access logs and client history."  
   — *Authentication* (Developer docs, MCP, fetched 2026-10-15) · [link](https://developer.instantly.ai/mcp/authentication)
29. "Use this only if your MCP client cannot set custom headers. The key is part of the request URL, so it may be recorded in intermediary and server logs."  
   — *Authentication* (Developer docs, MCP, fetched 2026-10-15) · [link](https://developer.instantly.ai/mcp/authentication)
30. "The Instantly MCP server lets AI assistants like Claude and Cursor manage your Instantly workspace through natural language. Instead of writing API calls manually, describe what you want and the assistant executes the right operations for you."  
   — *Introduction* (Developer docs, MCP, fetched 2026-10-15) · [link](https://developer.instantly.ai/mcp/introduction)
31. "If the connection is working, the assistant calls the `list_accounts` tool and returns your accounts."  
   — *Quickstart* (Developer docs, MCP, fetched 2026-10-15) · [link](https://developer.instantly.ai/mcp/quickstart)
32. "Keep your API key secure. Never share MCP configuration files that contain your key."  
   — *Quickstart* (Developer docs, MCP, fetched 2026-10-15) · [link](https://developer.instantly.ai/mcp/quickstart)
33. "You can connect Instantly to ChatGPT to manage your Instantly tasks directly from ChatGPT without switching between platforms."  
   — *Instantly Plugin in ChatGPT* (Help center, modified 2026-10-14) · [link](https://help.instantly.ai/en/articles/17595989-instantly-plugin-in-chatgpt)
34. "The Instantly MCP is the bridge that turns a smart writing assistant into an active outbound system."  
   — *Connect the Instantly MCP* (Academy, 2026-03-19) · [link](https://instantly.ai/courses/connect-the-instantly-mcp)
35. "You can click Configure on the connector to review what permissions Claude has — read tools, write tools, and delete tools."  
   — *Connect the Instantly MCP* (Academy, 2026-03-19) · [link](https://instantly.ai/courses/connect-the-instantly-mcp)
36. "For most growth teams, the winning approach is a hybrid stack: REST and webhooks for bulk data pipelines, MCP for AI-driven campaign management and reply handling."  
   — *MCP Server vs traditional API integration: which approach is right for your outreach stack?* (Blog, 2026-06-19) · [link](https://instantly.ai/blog/mcp-server-vs-api-integration/)
37. "Traditional REST APIs remain the right choice for high-volume, stateless data syncing, such as pushing thousands of leads from a CRM."  
   — *MCP Server vs traditional API integration: which approach is right for your outreach stack?* (Blog, 2026-06-19) · [link](https://instantly.ai/blog/mcp-server-vs-api-integration/)
38. "Yes, Instantly fully supports running both simultaneously."  
   — *MCP Server vs traditional API integration: which approach is right for your outreach stack?* (Blog, 2026-06-19) · [link](https://instantly.ai/blog/mcp-server-vs-api-integration/)
39. "When creating a key for an MCP reporting bot, select only `campaigns:read` and `analytics:read`. Avoid the `all:all` scope, which grants unrestricted access."  
   — *Instantly MCP Server Privacy Guide: Security Risks & Best Practices* (Blog, 2026-02-24, modified 2026-07-26) · [link](https://instantly.ai/blog/instantly-mcp-server-privacy-guide-security-risks-best-practices/)
40. "Rotate API keys at least every 90 days."  
   — *Instantly MCP Server Privacy Guide: Security Risks & Best Practices* (Blog, 2026-02-24, modified 2026-07-26) · [link](https://instantly.ai/blog/instantly-mcp-server-privacy-guide-security-risks-best-practices/)
41. "Just shipped: the Instantly MCP Server connects AI assistants like Claude and Cursor directly to your"  
   — @InstantlyAI on X (2025-12-02) · [link](https://x.com/InstantlyAI/status/1995886921675854220)

---

## Quote bank: Instantly Platform How-To

Exact quotes from Instantly's public content (blog, help center, Academy, YouTube, X) on `instantly-platform-how-to` (Setting up and using Instantly campaigns, accounts, features, integrations, analytics, and workspaces.). Every quote was verified by substring match against the raw source; YouTube timestamps come from the caption (.vtt) cue where the quote starts. Each line shows the source date: newer guidance wins over older. Use these when you need exact wording. Do not paraphrase inside quotation marks.

Topic note: file `knowledge/instantly-topics-4.md` in this repo, section "Topic: Instantly Platform How-To"

1. "Reading dashboards for ten accounts is manageable. Reading dashboards for a hundred accounts takes hours. Asking Copilot to summarize status across a hundred accounts takes seconds."  
   — *Infra basics - getting started 8* (Academy lesson, 2026-01-19) · [link](https://instantly.ai/courses/infra-basics-getting-started-8)
2. "Copilot acts as your personal ops assistant. It can write campaigns for you, analyze performance, manage your infrastructure, and answer questions about your setup."  
   — *Welcome to Instantly* (Academy lesson, modified 2026-02-18) · [link](https://instantly.ai/get-started-with-instantly/lesson-1)
3. "Unibox aggregates all replies from all your inboxes into one place. And Analytics is where you track everything once it's live."  
   — *Welcome to Instantly* (Academy lesson, modified 2026-02-18) · [link](https://instantly.ai/get-started-with-instantly/lesson-1)
4. "You can enable the evergreen feature that automatically adds leads that fit within your search criteria to any running campaign."  
   — *Actionable Email Management Tips, Best Practices, and Tools* (Blog, 2024-10-11) · [link](https://instantly.ai/blog/email-management/)
5. "Webhooks are **real-time notifications** sent to your specified URL whenever certain events happen in your Instantly campaigns."  
   — *Webhooks* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/6261906-webhooks)
6. "Contacts can flow from HighLevel into Instantly, and key events in Instantly, such as positive replies or status changes, can automatically push leads back into HighLevel."  
   — *HighLevel Integration in Automations* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/13436125-highlevel-integration-in-automations)
7. "So that means that it will not surface leave that you already have in your workspace. That's really helpful because maybe you're reaching out to a specific market, you want to make sure you're not enriching the same lead more than once, spending credits on them, not reaching out to the same lead more than once, maybe in different campaigns."  
   — *Finding leads - Lesson 2 (lesson video)* (Academy lesson video, modified 2026-02-17) · [link](https://instantly.ai/courses/finding-leads-lesson-2)
8. "Instead of clicking through dashboards and drilling into individual accounts, you can simply ask questions and give instructions in natural language."  
   — *Infra basics - getting started 8* (Academy lesson, 2026-01-19) · [link](https://instantly.ai/courses/infra-basics-getting-started-8)
9. "The native integrations are primarily one-way. You can import lists from your CRM into Instantly, but to sync activities like opens, replies, and status changes back to the CRM, you'll need a more advanced setup."  
   — *How Instantly Connects Outsourced Sales to Your CRM for 99% Data Accuracy* (Blog, 2026-01-15) · [link](https://instantly.ai/blog/how-to-connect-outsourced-sales-crm/)
10. "Changing a lead's status is the quickest way to stop campaign emails while keeping the lead in your system."  
   — *How to Stop Sending to Specific Leads* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/7913412-how-to-stop-sending-to-specific-leads)
11. "You can import an existing campaign into another workspace without having to recreate it."  
   — *Importing Existing Campaigns from One Workspace to Another* (Help center, modified 2026-10-14) · [link](https://help.instantly.ai/en/articles/7908783-importing-existing-campaigns-from-one-workspace-to-another)
12. "A workspace group lets you organize multiple sub-workspaces under a single admin workspace."  
   — *Workspace Groups* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/10575905-workspace-groups)
13. "You can schedule your replies in Unibox to be sent on a specific date and time."  
   — *Schedule Replies in Unibox* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/7894683-schedule-replies-in-unibox)
14. "Send individual emails directly from the Leads tab without creating a full campaign - perfect for personal follow-ups and one-on-one communication."  
   — *Sending One-Off Emails Outside Campaigns* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/13923946-sending-one-off-emails-outside-campaigns)
15. "API Scopes allow for granular control over API keys and their usage"  
   — *API V2* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/10432807-api-v2)
16. "Once you insert the pixel code, test the status to check if the code/pixel has been added properly."  
   — *How to Set Up the Website Visitors Pixel* (Help center, modified 2026-10-14) · [link](https://help.instantly.ai/en/articles/9526841-how-to-set-up-the-website-visitors-pixel)
17. "you can add entire domains or specific email accounts they both work just fine you can enter them manually through Google Sheets or through CSV and uh yeah once you do it they appear here and you can select them you can delete them you can import new ones"  
   — *New Feature - In-built blocklist* (YouTube, 2023-03-07) · [1:09](https://www.youtube.com/watch?v=Z8VttoGz3CI&t=69s)
18. "By integrating Instantly directly with your CRM through native connectors or webhooks, you eliminate manual handoffs and prove your value through automated, real-time reporting."  
   — *How Instantly Connects Outsourced Sales to Your CRM for 99% Data Accuracy* (Blog, 2026-01-15) · [link](https://instantly.ai/blog/how-to-connect-outsourced-sales-crm/)
19. "Leads will be distributed evenly among the selected team members using a round-robin method."  
   — *Getting Started with the CRM Dashboard* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/9064602-getting-started-with-the-crm-dashboard)
20. "The blocklist tab is checked both during the uploading of lead data and throughout ongoing campaigns."  
   — *How to Stop Sending to Specific Leads* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/7913412-how-to-stop-sending-to-specific-leads)
21. "The Clean HTML feature removes unnecessary HTML tags from your email body while preserving your text formatting (color, size, etc.)."  
   — *Clean HTML features* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/6525904-clean-html-features)
22. "You can also specify the exact URL the visitor was detected on, and the Referrer - who brought the visitor to this page."  
   — *Slack for Website Visitor Alerts* (Help center, modified 2026-10-09) · [link](https://help.instantly.ai/en/articles/9527161-slack-for-website-visitor-alerts)
23. "you can also download the CSV pack and yeah like uh when I uploaded the list I only had the first name last name and the company website right but now I have all these extra bits of information available that I can use in the Outreach"  
   — *New Feature - Lead Enrichment* (YouTube, 2023-07-25) · [2:32](https://www.youtube.com/watch?v=YxFfqLbTY9Q&t=152s)
24. "so let's just pick this person here for example and all I have to do is just hit okay that email outside in the others tab is now with in the primary this will help you if you feel like something needs to be in the primary you can instantly move it and attach it within the campaign"  
   — *This NEW Tool Makes Inbox Management EASY* (YouTube, 2024-04-06) · [0:51](https://www.youtube.com/watch?v=lV7iT1CXeiM&t=51s)
