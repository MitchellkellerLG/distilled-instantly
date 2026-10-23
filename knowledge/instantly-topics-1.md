# Instantly topic notes 1: Sending foundations

Covers: Deliverability, Email Infrastructure, Compliance & Privacy.

Part of the Instantly education-voice bot. Follow `instantly-voice` for how to speak. Exact quotes for these topics are in `instantly-quotes-1`. Named features, endpoints and docs links are in the `instantly-tools-*` skills. Every claim below carries its source date; newest guidance wins.

## Topic: Deliverability

## Overview

Instantly teaches that inbox placement comes from sender reputation, authentication, sending patterns, list quality, and recipient behavior working together over time. Warmup and monitoring can help you spot problems and build healthier sending habits, but no single setting guarantees inbox placement.

## Sender reputation and inbox placement

Mailbox providers assess signals from the sender, message, recipient, and recipient behavior. Replies, deletions, and spam reports can all affect sender reputation.

> "There is no single setting that guarantees inbox placement. Deliverability is the result of many signals working together over time."
>
> **Source:** [link](https://instantly.ai/blog/improve-email-deliverability/) · blog, 2026-08-11

> "Do people reply? Do they delete without reading? Do they hit spam? Every one of those micro signals builds or erodes your sender reputation."
>
> **Source:** [link](https://instantly.ai/infrastructure-lectures/infrastructure-lecture-4) · academy-video, modified 2026-02-04

## Warmup and sending pace

Instantly recommends building trust gradually. Sudden volume spikes, bounces, or complaints can look like abuse, so keep warmup active and increase campaign volume cautiously.

> "If you send hundreds of cold emails on day one, providers get suspicious – even if everything else is set up right. Warm up your accounts to build trust slowly."
>
> **Source:** [link](https://help.instantly.ai/en/articles/6222401-how-to-ensure-your-emails-get-delivered-and-avoid-spam-filters) · help, modified 2026-10-13

> "Sudden spikes, high bounces, and complaints look like abuse. Providers throttle, bulk, or block senders who trigger those patterns."
>
> **Source:** [link](https://instantly.ai/blog/what-is-slow-ramp-warmup/) · blog, 2025-09-23

## Bounce prevention and recovery

Instantly recommends verifying contacts, suppressing hard bounces, and investigating sustained increases. A bounce pattern across one company domain may point to a broader domain or mail-routing issue.

> "A rising bounce rate can indicate problems with list quality, sending infrastructure, or both. Monitor bounce rate throughout your campaigns and investigate sustained increases early."
>
> **Source:** [link](https://instantly.ai/blog/improve-email-deliverability/) · blog, 2026-08-11

> "A single bounce from a CEO domain is noise. Ten bounces from addresses at the same company domain in one week points to a domain-level block, a decommissioned company, or a misconfigured MX record."
>
> **Source:** [link](https://instantly.ai/blog/troubleshoot-invalid-ceo-emails/) · blog, 2026-05-25

## Content and spam filtering

Instantly teaches that filtering considers content alongside formatting, authentication, warmup, and reputation. Use neutral, specific subject lines and test changes before scaling.

> "The fix isn't memorizing a word list. It's a system: neutral language, clean formatting, technical warmup, and A/Z testing before you scale."
>
> **Source:** [link](https://instantly.ai/blog/cold-email-subject-lines-that-trigger-spam-filters-what-to-avoid/) · blog, 2026-03-23

> "A clean domain with a strong sender reputation gives you more tolerance on the vocabulary layer. A burned domain with no warmup history gets flagged even on neutral subject lines."
>
> **Source:** [link](https://instantly.ai/blog/cold-email-subject-lines-that-trigger-spam-filters-what-to-avoid/) · blog, 2026-03-23

## Placement testing and monitoring

Instantly recommends testing placement after warming a domain and periodically during active campaigns. Recurring tests can surface spam placement or low deliverability early enough to investigate.

> "Run a test after warming up a new domain, and again periodically during active campaigns; deliverability isn't static, and catching a shift early beats diagnosing a tanked campaign later."
>
> **Source:** [link](https://instantly.ai/blog/how-to-get-emails-out-of-promotions/) · blog, 2026-02-03

> "Automated recurring tests help you keep track of your email performance over time and send alerts if problems like spam placement or low deliverability happen."
>
> **Source:** [link](https://help.instantly.ai/en/articles/10147177-inbox-placement-feature) · help, modified 2026-10-09

## Related topics

- `email-infrastructure` (file `knowledge/instantly-topics-1.md` in this repo) — Authentication and provider setup affect deliverability.
- `list-building-and-targeting` (file `knowledge/instantly-topics-2.md` in this repo) — Contact quality and list hygiene help prevent bounces.
- `testing-and-performance` (file `knowledge/instantly-topics-3.md` in this repo) — Placement tests and monitoring help identify changes.
- `sequences-and-follow-ups` (file `knowledge/instantly-topics-2.md` in this repo) — Sending patterns and campaign volume affect reputation.

## Go deeper

- **Exact wording:** file `knowledge/instantly-quotes-1.md` in this repo, section "Quote bank: Deliverability" (22 verified quotes with timestamps).
- **Best public sources** (point people to these live pages when the note and quote bank are not enough):

1. [How Warm-Up Works and Why it's Important](https://help.instantly.ai/en/articles/5975329-how-warm-up-works-and-why-it-s-important)
2. [Warmup Health Score](https://help.instantly.ai/en/articles/13939939-warmup-health-score)
3. [Handling bounces and invalid emails from CEO lists: troubleshooting and recovery](https://instantly.ai/blog/troubleshoot-invalid-ceo-emails/)
4. [Mastering Cold Email Inbox Rotation: Strategies, Throttling, and Monitoring for 100+ Accounts](https://instantly.ai/blog/inbox-rotation/)
5. [How to Improve Email Deliverability: Best Practices for Better Inbox Placement](https://instantly.ai/blog/improve-email-deliverability/)
6. [How to Avoid the Gmail Promotions Tab with Email Warmup](https://instantly.ai/blog/gmail-promotions/)
7. [Cold Email Subject Lines That Trigger Spam Filters: What to Avoid](https://instantly.ai/blog/cold-email-subject-lines-that-trigger-spam-filters-what-to-avoid/)
8. [How to clean your B2B email list: removing bounces, invalid addresses, and dead leads](https://instantly.ai/blog/clean-b2b-email-list-bounces-invalid-addresses/)

---

## Topic: Email Infrastructure

## Overview

Instantly teaches that email infrastructure is a sending capacity system: domains, inboxes, DNS authentication, providers, and sending limits work together. Its guidance covers setting up authenticated domains, distributing sending across accounts, and managing capacity without overloading individual inboxes. Product-feature details below are dated to the cited sources.

## Domains and inboxes

Instantly teaches that dedicated, brand-aligned alternate domains help protect a primary domain’s reputation. Its sources differ on how many accounts to use per domain: an October 9, 2026 help article recommends three to five; older guidance recommends one to two inboxes per domain. Choose the newer guidance.

> "If you run cold outreach campaigns from your primary domain, you’re running the risk of permanently damaging your sending reputation."
>
> **Source:** [link](https://instantly.ai/blog/how-to-set-up-an-email-domain/) · blog, 2024-06-28

> "Use alternate domains and governed sequences to protect your primary brand domain."
>
> **Source:** [link](https://instantly.ai/blog/done-for-you-email-accounts/) · blog, 2025-10-03

## DNS authentication

Instantly teaches that MX, SPF, DKIM, and DMARC each have a role in routing, authentication, and handling failed checks. Configure SPF and DKIM first, then allow them to authenticate messages for at least 48 hours before enabling DMARC, per the help article modified October 9, 2026.

> "All four DNS records work together to ensure your emails are delivered and trusted: * **MX**: Routes incoming emails to your inbox * **SPF**: Authorizes which servers can send on your behalf * **DKIM**: Adds a digital signature to verify authenticity * **DMARC**: Provides authentication policy and instructions"
>
> **Source:** [link](https://help.instantly.ai/en/articles/6222192-how-to-set-up-dns-records-mx-spf-dkim-dmarc-and-domain-forwarding) · help, modified 2026-10-09

> "**Important:** Make sure you set up DKIM and SPF before setting up DMARC. DKIM and SPF should be authenticating messages for at least 48 hours before turning on DMARC."
>
> **Source:** [link](https://help.instantly.ai/en/articles/6222192-how-to-set-up-dns-records-mx-spf-dkim-dmarc-and-domain-forwarding) · help, modified 2026-10-09

## SPF records

Instantly teaches that a hostname should have one SPF record. Add other sending services to that record rather than publishing a second one, which can cause authentication to fail.

> "Exactly one SPF record per hostname (domain or subdomain). Start with your primary sender include and add other services."
>
> **Source:** [link](https://instantly.ai/blog/spf-dkim-and-dmarc-deliverability/) · blog, 2025-09-09

## Sending providers

Instantly teaches that users can connect third-party SMTP services while using their email provider’s IMAP for receiving. ESP Matching is an Instantly feature described in help content modified October 9, 2026; it can reduce throughput while waiting for a matching account.

> "You can connect SendGrid, Mailgun, Amazon SES, and other SMTP providers to Instantly by combining SMTP from these services with IMAP from your email provider."
>
> **Source:** [link](https://help.instantly.ai/en/articles/7878219-how-to-connect-sendgrid-mailgun-and-other-smtp-providers) · help, modified 2026-10-09

> "ESP Matching may reduce your sending volume, as the campaign will wait for a matched account to become available before sending."
>
> **Source:** [link](https://help.instantly.ai/en/articles/7044069-email-service-providers-matching) · help, modified 2026-10-09

## Rotation and redundancy

Instantly teaches that rotating sends across inboxes and domains spreads volume and risk. Its Inbox Rotation feature distributes campaign sends across connected accounts, according to an August 20, 2026 blog post.

> "Inbox rotation means spreading your daily sending across several inboxes and domains. This helps you: * Avoid spam triggers tied to volume * Protect any single inbox or domain from getting flagged * Send more without hurting deliverability"
>
> **Source:** [link](https://instantly.ai/blog/how-to-set-outreach-email-accounts/) · blog, 2025-07-09

> "Instantly's Inbox Rotation distributes sends across all connected accounts within a campaign automatically. No single inbox fires more than 30 campaign emails per day, which keeps individual account volume below the threshold that triggers ISP scrutiny."
>
> **Source:** [link](https://instantly.ai/blog/deliverability-first-email-vs-sales-engagement/) · blog, 2026-08-20

## Safe sending capacity

Instantly teaches that adding inboxes and domains is the safer way to increase throughput. Its October 15, 2026 help guidance caps pre-warmed accounts at 20–25 emails per day; older advice allowing up to 50 per day is superseded. AirMail mailboxes have a separate maximum of 20 campaign emails per account per day, per help content modified October 10, 2026.

> "The safest throughput plan is to add more inboxes and domains rather than pushing a single inbox too hard."
>
> **Source:** [link](https://instantly.ai/blog/done-for-you-email-accounts/) · blog, 2025-10-03

> "**Instantly AirMail mailboxes:** You can adjust daily campaign limits for AirMail mailboxes as needed, up to the maximum of 20 emails per account per day."
>
> **Source:** [link](https://help.instantly.ai/en/articles/6248612-account-and-campaign-limits) · help, modified 2026-10-10

## Related topics

- `deliverability` (file `knowledge/instantly-topics-1.md` in this repo) — Authentication and sending volume affect whether messages are trusted and delivered.
- `sequences-and-follow-ups` (file `knowledge/instantly-topics-2.md` in this repo) — Campaign sending uses connected accounts and rotation.
- `scaling-and-agencies` (file `knowledge/instantly-topics-3.md` in this repo) — More domains and inboxes expand sending capacity.

## Go deeper

- **Exact wording:** file `knowledge/instantly-quotes-1.md` in this repo, section "Quote bank: Email Infrastructure" (25 verified quotes with timestamps).
- **Best public sources** (point people to these live pages when the note and quote bank are not enough):

1. [Connecting GoDaddy Domain to Google Workspace Tutorial](https://www.youtube.com/watch?v=s_Pfm95-4pA&t=209s) at 3:29
2. [How to Transfer Domains Between Email Providers](https://help.instantly.ai/en/articles/8065134-how-to-transfer-domains-between-email-providers)
3. [How to set up SPF and DKIM for cPanel email accounts](https://help.instantly.ai/en/articles/7973225-how-to-set-up-spf-and-dkim-for-cpanel-email-accounts)
4. [SPF, DMARC and DKIM: Namecheap & Google Workspace accounts](https://help.instantly.ai/en/articles/6492915-spf-dmarc-and-dkim-namecheap-google-workspace-accounts)
5. [SPF, DMARC and DKIM: GoDaddy & Google Workspace](https://help.instantly.ai/en/articles/6491557-spf-dmarc-and-dkim-godaddy-google-workspace)
6. [How to Set Up DNS Records (MX, SPF, DKIM, DMARC) and Domain Forwarding](https://help.instantly.ai/en/articles/6222192-how-to-set-up-dns-records-mx-spf-dkim-dmarc-and-domain-forwarding)
7. [What Is BIMI & Why is it Essential For Email Marketing?](https://instantly.ai/blog/what-is-bimi/)
8. [Understanding The Role Of SMTP TLS In Cold Email Campaigns](https://instantly.ai/blog/smtp-tls/)

---

## Topic: Compliance & Privacy

## Overview

Instantly teaches that compliant outreach starts with a documented legal basis, responsibly sourced contact data, and opt-outs that are honored across sending tools. Its guidance also emphasizes collecting only necessary information, being transparent about tracking, and adapting practices to the recipient’s jurisdiction. Product settings can support these practices, but the sender remains responsible for following applicable laws.

## Legal basis and jurisdiction

Instantly teaches teams to document why they may contact each person and to apply rules according to where recipients are located. Requirements differ by jurisdiction, so list review and campaign practices should account for those differences.

> "You need three pillars for B2B cold email compliance: a documented legal basis (usually Legitimate Interest for GDPR-covered outreach), clean data sourcing from vendors who can prove lawful collection, and airtight opt-out management that syncs across every tool your team uses."
>
> **Source:** [link](https://instantly.ai/blog/b2b-email-list-privacy-consent-legitimate-interest/) · blog, 2026-04-22

> "Segment your contact lists by jurisdiction before launching any sequence. Apply CASL-level consent standards to Canadian contacts, GDPR legitimate interest documentation to EU contacts, and CAN-SPAM opt-out requirements universally."
>
> **Source:** [link](https://instantly.ai/blog/executive-email-collection-compliance/) · blog, 2026-05-25

## Sourcing and documenting contact data

Instantly teaches that teams should be able to show where contact data came from and the basis for using it. A contact’s permission to hear from one organization does not automatically extend to another.

> "For each contact list, verify the data source and confirm that the collection method and legal basis are documented, so you can demonstrate compliance if a data subject or regulator asks where the data came from."
>
> **Source:** [link](https://instantly.ai/blog/ai-bdr-security-compliance/) · blog, 2026-07-13

> "A contact who agreed to receive communications from one company has not agreed to receive communications from yours. Before importing any community-sourced data: run a real-time verification pass, check for catch-all domain configurations, and remove any contact where the role start date predates your import by more than 90 days."
>
> **Source:** [link](https://instantly.ai/blog/ai-bdr-data-sources-explained/) · blog, 2026-07-13

## Data minimization and privacy

Instantly teaches teams to limit personal data to what outreach needs and to consider what tracking collects. Its March 2026 tracking guidance recommends reply- and meeting-based measurement as a way to reduce pixel-related data collection.

> "GDPR Article 5(1)(c) requires that personal data be "adequate, relevant and limited to what is necessary." This principle of data minimization means that for cold outreach, you should collect only name, work email, job title, and company."
>
> **Source:** [link](https://instantly.ai/blog/executive-email-collection-compliance/) · blog, 2026-05-25

> "When you shift to reply-based measurement, you resolve much of the compliance tension around tracking. Measuring replies and meetings rather than pixel loads reduces the volume of PII you collect, lowers your exposure under GDPR's data minimization principle, and delivers a materially better prospect experience."
>
> **Source:** [link](https://instantly.ai/blog/email-tracking-privacy-and-compliance-the-sales-leaders-guide-to-gdpr-and-ccpa/) · blog, 2026-03-23

## Sender identity and unsubscribe

Instantly teaches that commercial emails should identify the sender accurately and make it possible to unsubscribe. Its help article, modified 2026-10-09, says supported providers receive a one-click unsubscribe option in email headers.

> "Your message must clearly identify the sender, provide a valid physical mailing address and either a phone number or email address, and include a functioning unsubscribe mechanism."
>
> **Source:** [link](https://instantly.ai/blog/reminder-email-compliance-gdpr-can-spam-casl-guide/) · blog, 2026-02-24

> "The unsubscribe link will be added to email headers for one-click unsubscribe by supported email providers."
>
> **Source:** [link](https://help.instantly.ai/en/articles/8860388-list-unsubscribe) · help, modified 2026-10-09

## Suppression and opt-out handling

Instantly teaches that opt-outs should be handled promptly and consistently across campaigns and tracking. Its guidance describes automated suppression and global block lists as ways to help prevent further contact.

> "When a contact opts out, suppress them from all sends and all tracking data collection at the same time. Your platform should automate this suppression without requiring manual intervention."
>
> **Source:** [link](https://instantly.ai/blog/email-tracking-privacy-and-compliance-the-sales-leaders-guide-to-gdpr-and-ccpa/) · blog, 2026-03-23

> "The best systems automate opt-out recording so that when a recipient unsubscribes, they are added to a global block list, removed from active sequences, and logged with a timestamp. Manual opt-out tracking is fragile at scale and will fail an audit."
>
> **Source:** [link](https://instantly.ai/blog/ai-sales-agent-security-compliance/) · blog, 2026-06-09

## Website visitor consent and responsibility

Instantly teaches that using Website Visitor ID involves privacy responsibilities, including obtaining affirmative consent before deploying cookies or similar technologies. Its help guidance, modified 2026-03-06, states that customers are responsible for compliant collection and use of personal information.

> "Obtains affirmative consent from visitors before deploying cookies or similar technologies."
>
> **Source:** [link](https://help.instantly.ai/en/articles/9503008-instantly-ai-website-visitor-id-legal-compliance-onboarding) · help, modified 2026-03-06

> "Ultimately, it is your responsibility to ensure that you are collecting and using personal information in compliance with all applicable laws and regulations."
>
> **Source:** [link](https://help.instantly.ai/en/articles/9503008-instantly-ai-website-visitor-id-legal-compliance-onboarding) · help, modified 2026-03-06

## Related topics

- `deliverability` (file `knowledge/instantly-topics-1.md` in this repo) — Clean lists and honored opt-outs support sustainable sending.
- `list-building-and-targeting` (file `knowledge/instantly-topics-2.md` in this repo) — Contact sourcing, verification, and jurisdiction-aware targeting affect compliance.
- `testing-and-performance` (file `knowledge/instantly-topics-3.md` in this repo) — Reply-based measurement can reduce reliance on tracking pixels.
- `instantly-platform-how-to` (file `knowledge/instantly-topics-4.md` in this repo) — Unsubscribe and blocklist settings help operationalize opt-out handling.

## Go deeper

- **Exact wording:** file `knowledge/instantly-quotes-1.md` in this repo, section "Quote bank: Compliance & Privacy" (22 verified quotes with timestamps).
- **Best public sources** (point people to these live pages when the note and quote bank are not enough):

1. [Instantly.ai Website Visitor ID Legal Compliance Onboarding](https://help.instantly.ai/en/articles/9503008-instantly-ai-website-visitor-id-legal-compliance-onboarding)
2. [Reminder Email Compliance: GDPR, CAN SPAM & CASL Guide](https://instantly.ai/blog/reminder-email-compliance-gdpr-can-spam-casl-guide/)
3. [GDPR Email Marketing: How to Scale While Staying Compliant](https://instantly.ai/blog/gdpr-email-marketing/)
4. [Compliance and privacy when collecting executive email addresses: GDPR, CCPA, and beyond](https://instantly.ai/blog/executive-email-collection-compliance/)
5. [Email Tracking Privacy and Compliance: GDPR, CCPA, and Data Protection Obligations](https://instantly.ai/blog/email-tracking-privacy-and-compliance-the-sales-leaders-guide-to-gdpr-and-ccpa/)
6. [Email Marketing Laws: Keeping Cold Email Campaigns Compliant](https://instantly.ai/blog/email-marketing-laws/)
7. [AI sales agent security compliance: what sales leaders need to know](https://instantly.ai/blog/ai-sales-agent-security-compliance/)
8. [Global Blocklist](https://help.instantly.ai/en/articles/6192983-global-blocklist)
