---
date: '2026-10-19'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

I have comprehensive data now. Let me compile the briefing.# 🗓️ Collaboration Morning Brief — Monday, 19 October 2026

## 🔵 Microsoft Teams
- Teams rolled out several admin-facing updates this month including the ability for users to temporarily pause all notifications to minimize interruptions without changing their existing notification settings, plus automatic recording and transcription for calls answered through Teams Call Queues, with recordings stored in SharePoint and accessible from call history.
- Microsoft confirmed it is introducing support for third-party deepfake detection solutions and impersonation protection in Teams meetings, with both changes reaching general availability in November after a worldwide rollout.
- An important license/billing change lands this week: beginning October 16, 2026, existing Microsoft 365 Copilot subscriptions requiring a qualifying base subscription will include "(add-on)" in their names, with standalone Copilot SKUs arriving December 1.
- Looking ahead, Teams event organizers and producers will be able to share videos directly from OneDrive during events, beginning in December — useful for town halls and large broadcasts.

## 🤖 Copilot & AI in Teams
- Teams-specific Copilot UX is being consolidated: from mid-October, the Copilot app in the app bar is the only entry point into Copilot within Teams, with conversations moving there.
- Microsoft is overhauling Copilot's commercial model — splitting Copilot into two billing tracks and rebuilding the app around a new Home screen, Code, and an always-on agent called Autopilot, meaning admins need to set spending policies before wider rollout.
- Governance just got more enterprise-ready: admins can now list up to 100 SharePoint Online sites as "authoritative content" in the Copilot control system, making Copilot and Search results more relevant and trustworthy. A related setting to review before Oct 25 will auto-enable users to upload advanced packages (declarative agents/MCP servers) unless disabled.

## 🔗 Ecosystem & Integrations
- Teams Phone Agent — an AI receptionist that sits in front of call queues, answers from knowledge bases and files, books appointments, and works in 60+ languages — is now generally available (billed via Copilot Credits usage).
- Microsoft is retiring Azure Communication Services as a standalone product; it will "prioritize deeply integrated communication experiences within Microsoft platforms, specifically Teams, Dynamics 365, and Azure, while working with leading CPaaS providers to fill gaps." Teams-interop services (Phone, Direct Routing extensibility) are unaffected.
- Power Platform is extending agent identity: agents retain user preferences and business-process context across cycles, so people stop restating the same context every time, with "agent refinements" coming to suggest workflow automation from repeated steps.

## Meetingroom Equipment
- Cisco used WebexOne 2026 to close out a multi-platform room strategy: RoomOS 27, due in November, adds native Google Meet support to Cisco hardware, so one device fleet can now boot into Webex, Microsoft Teams, Zoom or Google Meet, with native Zoom Rooms on Cisco hardware reaching general availability this month.
- Industry commentary notes Microsoft finished moving Teams Android device management into the Pro Management Portal, while Neat and Shure shipped new MDEP devices — relevant for anyone managing a mixed MTR fleet.
- Certified MTR hardware remains anchored around Logitech, Poly (HP), Yealink, Neat, Crestron and Jabra, with Teams Rooms Pro licensing priced at $40/room/month, required for Pro Portal management and Copilot features.

## 🌐 Broader Collaboration Landscape
- Google Workspace continues weekly feature drops: new Assured Controls rules in the Admin Console give admins a more granular, resource-centric way to enforce Access Management and Access Approvals policies on Drive files; separately, Gemini "skills" rollout to Workspace scheduled for Oct 19 has slipped slightly.
- Salesforce escalated its agentic push directly into Slack's territory: Salesforce introduced an AI outbound sales agent called Hunter, built on Agentforce, on 16 October 2026, launching with ZoomInfo and Demandbase as core data providers, and expanded its Docusign partnership so users can manage, generate, and track agreements natively inside Agentforce and Slack.
- Slack itself shipped a developer-facing update, with CLI 4.9.0 adding support for app-level token rotation, opting apps into rotating app-level tokens — a minor but notable security hygiene update for Slack app builders.

## ⚡ Action Items & Things to Watch
- Review the Copilot "advanced package uploads" admin setting before **October 25** — if left on default, users will automatically be able to upload declarative agents/MCP servers.
- Audit PowerShell/license-management scripts referencing Copilot product names before the **(add-on)** renaming fully lands (effective Oct 16) to avoid automation breakage.
- Watch Cisco's RoomOS 27 (Nov) and Zoom Rooms-on-Cisco GA — if Henrik's estate is multi-vendor, this changes room-hardware procurement flexibility ahead of Microsoft Ignite in November, where further Teams/Copilot announcements are expected.

---
**Sources:**
- [Windows Central – OneDrive video sharing in Teams events](https://www.windowscentral.com/microsoft/microsoft-teams/this-one-new-feature-is-enough-to-make-me-switch-back-to-microsoft-teams)
- [Releasebot – Microsoft Teams October 2026 release notes](https://releasebot.io/updates/microsoft/microsoft-teams)
- [Empowering.Cloud – Teams Enterprise Update October 2026](https://empowering.cloud/microsoft-teams-enterprise-update-october-2026/)
- [BleepingComputer – Teams deepfake detection](https://www.bleepingcomputer.com/news/security/microsoft-teams-to-add-third-party-deepfake-detection-impersonation-protection/)
- [PupuWeb – MC1508148 Copilot offer renaming](https://pupuweb.com/mc1508148-microsoft-365-copilot-offer-and-name-updates/)
- [m365copilotconnection Substack – Copilot's October 2026 updates](https://m365copilotconnection.substack.com/p/copilots-biggest-october-2026-updates)
- [changepilot.cloud – October 2026 M365 Updates](https://changepilot.cloud/blog/october-2026-microsoft-365-updates-copilot-billing-home-more)
- [PowerPlatStack – Power Platform Week in Review Oct 3–16](https://powerplatstack.substack.com/p/power-platform-week-in-review-oct)
- [UC Today – WebexOne 2026: Cisco Bets on AI](https://uctoday.com/webexone-2026-cisco-bets-on-ai-to-redefine-the-meeting-room)
- [UC Today – Cisco Goes Open at WebexOne 2026](https://uctoday.com/this-week-in-uc-c-cisco-goes-open-at-webexone-2026)
- [EPC Group – MTR Enterprise Deployment Guide 2026](https://www.epcgroup.net/microsoft-teams-rooms-enterprise-deployment-guide-2026)
- [Google Workspace Updates – Weekly Recap Oct 16](https://workspaceupdates.googleblog.com/)
- [Releasebot – Slack October 2026 updates](https://releasebot.io/updates/slack)
- [Yahoo Finance – Salesforce Unveils Hunter AI](https://finance.yahoo.com/technology/ai/articles/salesforce-crm-unveils-hunter-ai-042659534.html)
- [Jazz Security – AI controls in SaaS apps](https://jazz.security/dlp-explained/dlp-basics/how-to-control-ai-features-in-saas-apps/)
