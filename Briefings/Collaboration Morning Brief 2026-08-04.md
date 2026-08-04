---
date: '2026-08-04'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

# 🗓️ Collaboration Morning Brief — Tuesday, 4 August 2026

## 🔵 Microsoft Teams
- The Teams engineering team's July 31 "What's New in Teams" update notes the team is continuing to innovate in Teams to help people collaborate with people and AI to get work done, following on from InfoComm 2026 coverage the prior month.
- Microsoft is rolling out **expanded presenter visibility** in "Manage what attendees see": beginning late August 2026, users will be able to drag and resize the presenter panel, allowing more presenters to be displayed at once.
- A cross-tenant audit change is coming: starting late August 2026, Microsoft Teams will share Meeting Participant Detail audit records with all participating tenants for their own users in cross-tenant meetings, enhancing audit visibility while maintaining data boundaries.
- Admins now have a new external-bot control policy in the Teams Admin Center — the "Manage external bots and their access to meetings" policy can be assigned to individual users or specific groups, addressing concerns about AI note-taking bots joining meetings uninvited.

## 🤖 Copilot & AI in Teams
- Copilot Chat's Context IQ now supports SharePoint List grounding: users can search for and select specific SharePoint Lists to ground their prompts, improving relevance and accuracy, supporting M365 security and compliance policies. Copilot responses are also gaining inline rich images from files and meetings for better comprehension.
- Governance is expanding for Agent 365: managers can now access Agent 365 data through the Agent Dashboard in Copilot Analytics (Insights) to understand activity across all registered agents, rolling out through August 2026.
- Worth flagging for IT planning: Microsoft 365 Apps on Windows 10 continue receiving security updates until October 10, 2028, but feature updates and Copilot support phase out by update channel — the Current Channel feature cutoff is Version 2608, expected in August 2026.

## 🔗 Ecosystem & Integrations
- Purview governance is broadening beyond Microsoft's own stack: Microsoft Purview Data Loss Prevention and Information Protection auto-labeling capabilities now extend to non-Microsoft connected apps (e.g., Google Workspace, Box, Dropbox, Salesforce, ServiceNow, AWS, and Cisco Webex).
- A unified app/agent governance model is in development: admins using the Microsoft 365 admin center and Teams admin center will be able to apply app and agent installation changes once and have them consistently enforced across Teams, Outlook, and Microsoft 365 Copilot.
- SharePoint/OneDrive auto-labeling capacity is scaling up, with Microsoft increasing the maximum auto-labeling capacity for SharePoint and OneDrive from 100,000 up to 500,000 files per tenant per day.

## Meetingroom Equipment
Nothing significant in the past 48 hours. Background context: Yealink and Logitech continue to hold near-parity MTR certification versus each other, with ongoing market debate over Yealink's aggressive pricing challenging incumbents Poly and Logitech — but no fresh announcements this cycle.

## 🌐 Broader Collaboration Landscape
- Salesforce's Summer '26 release continues to reshape the CRM/collaboration boundary: from June 15, any new Salesforce org in Enterprise or Unlimited edition comes with a Slack workspace already built and configured — no separate purchase or setup, with the collaboration layer arriving alongside the CRM. This directly pressures Teams' incumbency in Salesforce-heavy accounts.
- Enterprise messaging reliability is under scrutiny industry-wide, with analysts noting uptime SLAs vary dramatically across enterprise messaging platforms, with a full 2026 comparison of contractual SLAs versus actual measured uptime now circulating among procurement teams.
- Webex continues to lean on its security credentials against Zoom, holding a US Defense Information Systems Agency (DISA) Provisional Authority at Level 5 while Zoom has DISA Level 4 clearance — a differentiator often cited in competitive enterprise evaluations.

## ⚡ Action Items & Things to Watch
- **Post-Incident Review pending:** Microsoft's Post-Incident Review for the July 23, 2026 Microsoft 365 outage that knocked out Teams, SharePoint, OneDrive, and Copilot Chat for nearly five hours after an Azure maintenance automation bug removed IP routes is expected imminently — worth reviewing once published for resilience-planning implications.
- **Windows 10 fleets:** Confirm which devices are still on Windows 10, as Copilot/feature updates for Microsoft 365 Apps begin phasing out by channel starting with Version 2608 this month.
- **Governance rollouts:** Track the new cross-tenant audit record sharing and unified app/agent installation policies landing in Teams/M365 admin centers over the next few weeks — relevant for compliance and security teams.

---
**Sources:**
- [Microsoft Teams Blog – Microsoft Community Hub](https://techcommunity.microsoft.com/category/microsoftteams/blog/microsoftteamsblog)
- [Microsoft Teams: Expanded presenter visibility – M365 Admin](https://m365admin.handsontek.net/microsoft-teams-expanded-presenter-visibility-manage-attendees-see/)
- [Microsoft Teams: Meeting Participant Detail audit records – M365 Admin](https://m365admin.handsontek.net/microsoft-teams-meeting-participant-detail-audit-records-will-available-participating-non-organizer-tenants/)
- [Introducing smarter bot protection in Microsoft Teams meetings – Microsoft Community Hub](https://techcommunity.microsoft.com/blog/microsoftteamsblog/introducing-smarter-bot-protection-in-microsoft-teams-meetings/4531375)
- [Microsoft Release Notes – Releasebot](https://releasebot.io/updates/microsoft)
- [Microsoft 365 Upcoming Changes & New Features – Active Directory Pro](https://activedirectorypro.com/microsoft-365-upcoming-changes-new-features/)
- [This Week in Microsoft, Security & AI: August 3, 2026 – Covenant Tech](https://covenant-tech.net/blog/this-week-in-microsoft-security-ai-august-3-2026/)
- [Salesforce Summer '26: Slack Is Now the Default – UC Today](https://www.uctoday.com/unified-communications/salesforce-summer-26-slack-is-now-the-default-for-every-new-customer-heres-what-that-changes/)
- [Enterprise Messaging SLA Comparison – SyncRivo Blog](https://syncrivo.ai/en/blog/enterprise-messaging-sla-comparison-slack-teams-zoom-2026)
- [The 8 best Zoom alternatives in 2026 – Zapier](https://zapier.com/blog/best-zoom-alternatives/)
- [Microsoft 365 Outage: Azure Maintenance Bug – Tech Times](https://www.techtimes.com/articles/321568/20260725/microsoft-365-outage-azure-maintenance-bug-wiped-ip-routes-taking-down-teams-hours.htm)
- [Microsoft 365 outage affects Teams, SharePoint – BleepingComputer](https://www.bleepingcomputer.com/news/microsoft/microsoft-365-outage-affects-teams-sharepoint-and-other-services/)
- [Microsoft Teams status – StatusGator](https://statusgator.com/services/microsoft-teams)
