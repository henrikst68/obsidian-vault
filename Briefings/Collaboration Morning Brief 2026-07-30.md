---
date: '2026-07-30'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

Now I have enough fresh material, including yesterday's Q4 FY26 earnings. Let me compile the briefing.

# 🗓️ Collaboration Morning Brief — Thursday, 30 July 2026

## 🔵 Microsoft Teams
- Fallout continues from the July 23 Azure West US incident that caused connectivity failures and latency for Azure and Microsoft cloud services between 14:44 and 19:41 UTC, traced to a bug in a maintenance-request conversion system that removed more network routes than intended; Teams chat and file access were among the visible symptoms.
- Admins should note the new July release: Teams Phone Call Transfer Improvements plus sensitivity label inheritance for meeting recordings, letting confidential labels automatically carry over to recorded files.
- UC Today reports Teams is getting a dedicated Meeting Recap app this month, with guidance on what IT teams need to do before it arrives.
- Microsoft has centralized device oversight: the Pro Management portal now lets admins monitor device health, manage inventory and access analytics for Windows and Android Teams devices, moving Android-based Teams Rooms, panels and phones management out of the Teams admin center.

## 🤖 Copilot & AI in Teams
- In yesterday's FY26 Q4 earnings, Nadella confirmed Microsoft 365 Copilot reached over 30 million paid seats, up from over 20 million in April, with GitHub Copilot now at 50 million users.
- Copilot Cowork (agentic task automation across M365 apps) is now GA worldwide, running on Anthropic models including Opus 4.8 and Sonnet 4.6, with GPT 5.5 in Frontier and a new Cowork 1 model expected soon; new partner plugins from Miro, monday.com, LSEG and others are live.
- July's release notes add governance controls, including watermarks for AI-generated video/audio content, controlled via a Microsoft 365 policy setting, and OpenAI-operated models becoming enabled by default for eligible commercial tenants from 24 July unless admins opt out.

## 🔗 Ecosystem & Integrations
- Microsoft's Agent 365 launch brings third-party agents natively into Teams: Miro, a visual collaboration platform, now integrates boards directly into Teams so users can create and collaborate on visual content without leaving Microsoft 365; Lucid diagrams and Manus workflow automation are also pre-integrated.
- Purview/compliance tightening continues alongside Teams: sensitivity labels can now follow meeting recordings end-to-end, closing a compliance gap where only the meeting invite was protected while the recording carried no such controls.
- CSP partners should note new bundled SKUs — Microsoft 365 Business Standard with Copilot and Business Premium with Copilot — giving Business-tier customers an integrated path to Copilot without separate subscriptions.

## Meetingroom Equipment
- Certified MTR hardware remains concentrated among Poly, Yealink, Logitech, Jabra, Crestron and Neat, with device management increasingly consolidated in Teams Rooms Pro.
- HP Poly has pushed a new AI-capable compute hub: the AI-powered HP Poly Studio Room Compute, designed to upgrade Teams Rooms with dedicated processing, PoE and top-tier security.
- Vendor differentiation persists by use-case: Logitech leads on flexibility and broad platform certification, Poly on premium performance, Yealink on cost/integration balance, and Neat on Zoom-native deployment — relevant for Henrik's room-standardization decisions.

## 🌐 Broader Collaboration Landscape
- Salesforce's Summer '26 release now ships every new Enterprise and Unlimited org with a fully provisioned Slack workspace by default, replacing Chatter and positioning Slack as the default collaboration layer across Agentforce, Sales Cloud and Service Cloud — a direct competitive play against Teams in CRM-adjacent workflows.
- Zoom continues its AI-first pivot: AI Companion on web now pulls from Zoom Chat messages (up to 90 days) as context, so decisions made in chat last week can surface automatically in later answers, alongside self-serve custom meeting-summary templates.
- Security researchers flag Teams as an active attack vector: initial access broker KongTuke has moved to Microsoft Teams for social engineering attacks, taking as little as five minutes to gain persistent access to corporate networks — worth flagging to Henrik's security team.

## ⚡ Action Items & Things to Watch
- Review tenant exposure to the July 23 Azure West US incident and confirm Teams/SharePoint service health commitments before Microsoft's final post-incident review lands.
- Decide on Copilot Cowork governance (billing, model access, spending limits) given its rapid GA rollout and rising adoption (30M+ paid Copilot seats company-wide).
- Assess Slack's new default-provisioning in Salesforce orgs against your Teams-first policy — clarify guidance for business units running Salesforce Enterprise/Unlimited.
- Brief security/helpdesk teams on the KongTuke Teams-based social engineering technique targeting external collaboration features.

---
**Sources:**
- [Vertu – Microsoft Teams Outage: July 2026 Incident](https://vertu.com/ai-tools/microsoft-teams-outage-july-2026-azure-incident)
- [BleepingComputer – Microsoft 365 outage affects Teams, SharePoint](https://www.bleepingcomputer.com/news/microsoft/microsoft-365-outage-affects-teams-sharepoint-and-other-services/)
- [BleepingComputer – Latest Microsoft Teams news](https://www.bleepingcomputer.com/tag/microsoft-teams/)
- [UC Today – Microsoft Teams Meeting Recap App](https://www.uctoday.com/tag/microsoft-teams/)
- [IT Trip – Teams Release Notes July 2026](https://en.ittrip.xyz/ms-office/teams/teams-release-notes)
- [Releasebot – Microsoft Teams Updates July 2026](https://releasebot.io/updates/microsoft/microsoft-teams)
- [Microsoft Investor Relations – FY26 Q4 Press Release](https://www.microsoft.com/en-us/investor/earnings/fy-2026-q4/press-release-webcast)
- [CNBC – Microsoft Q4 Earnings Report 2026](https://www.cnbc.com/2026/07/29/microsoft-msft-q4-earnings-report-2026.html)
- [Office365ITPros – FY26 Q4 Microsoft Results](https://office365itpros.com/2026/07/30/fy26-q4-microsoft-results/)
- [Redmondmag – Copilot Cowork GA](https://redmondmag.com/articles/2026/06/16/microsoft-makes-copilot-cowork-generally-available-worldwide.aspx)
- [Microsoft Learn – Copilot Release Notes](https://learn.microsoft.com/en-us/microsoft-365/copilot/release-notes)
- [A Guide to Cloud & AI – Copilot July 2026 Updates](https://www.aguidetocloud.com/blog/microsoft-365-copilot-july-2026-updates/)
- [Microsoft Learn – Agent 365 Third-Party Agents](https://learn.microsoft.com/en-us/microsoft-agent-365/third-party-agents)
- [Cloud Factory Group – M365 Pricing & Packaging Update](https://blog.cloudfactorygroup.com/posts/microsoft-365-pricing-packaging-update-effective-july-1-2026-what-every-csp-partner-must-know)
- [EPC Group – Microsoft Teams Rooms Deployment Guide 2026](https://www.epcgroup.net/microsoft-teams-rooms-enterprise-deployment-guide-2026)
- [323.tv – HP Poly Studio Room Compute](https://www.323.tv/2026/06/30/meet-the-new-poly-studio-room-compute-ai-powered-hub-for-microsoft-teams-rooms/)
- [UC Today – Meeting Room Technology Vendors 2026](https://www.uctoday.com/devices-workspace-tech/meeting-room-technology-vendors-2026/)
- [UC Today – Salesforce Summer '26: Slack Default](https://www.uctoday.com/unified-communications/salesforce-summer-26-slack-is-now-the-default-for-every-new-customer-heres-what-that-changes/)
- [Zoom – What's New at Zoom](https://www.zoom.com/en/products/whats-new/)
