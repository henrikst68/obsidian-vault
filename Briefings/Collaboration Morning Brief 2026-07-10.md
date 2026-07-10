---
date: '2026-07-10'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

# 🗓️ Collaboration Morning Brief — Friday, 10 July 2026

## 🔵 Microsoft Teams
- Microsoft's July 2026 Partner Center update confirms the Copilot specialization is officially renamed the **Microsoft 365 Copilot specialization**, with the renamed specialization introducing updates across performance, skilling, and validation requirements, with the performance requirement shifting to account-only for paid monthly active usage growth.
- New licensing guardrails landed for **Agent 365**: effective June 1, Microsoft introduced an expanded set of license prerequisites for new Agent 365 purchases, intended to ensure customers have the foundational security, identity, compliance, and management capabilities required to support core Agent 365 functionality.
- Teams service health remains largely stable — StatusGator's latest 24-hour check showed Teams operational, though a regression has been reported on the Microsoft Graph API teams/channels endpoint, where creating a Shared Channel via Application Permissions returns an HTTP 500 error — worth flagging to any team using Graph automation for channel provisioning.
- Admins should note the default captioning change rolling out: Microsoft is updating the default profanity filter setting for live captions from On to Off across Teams meetings, calls, events, and Microsoft Teams Rooms devices to improve accessibility and align with EU requirements.

## 🤖 Copilot & AI in Teams
- **Copilot Cowork has gone GA** this month — described as the headline release among 40+ Microsoft 365 Copilot updates for July 2026.
- Transparency controls are expanding: Microsoft has enabled the ability to add watermarks for AI-generated content in Microsoft 365 Copilot, providing additional transparency about content generated or altered using AI, controlled via a policy setting for visual or audio watermarks.
- Model choice continues to broaden, with Microsoft 365 Copilot expanding model choice to Claude Opus 4.8, designed for complex, multi-step and long-running work with stronger instruction following and smarter tool selection, alongside GPT-5.2 already available in Copilot Chat for faster reasoning and coding support.

## 🔗 Ecosystem & Integrations
- SMB licensing shift: as of July 1, Microsoft 365 Business with Copilot SKUs, previewed in the June 1 price list, are now generally available, turning a successful promotional motion into a permanent, predictable offer.
- Teams Rooms Pro Management portal gained a **room builder tool**, described as a user-friendly, visually engaging tool to help IT managers design and configure Teams Rooms traditional, signature, and flex meeting spaces, simplifying device and license selection.
- Competitive pressure on Microsoft's collaboration stack continues via Salesforce, where Slack now ships by default with new CRM orgs — a dynamic still reshaping IT procurement conversations (see Broader Landscape below).

## Meetingroom Equipment
- New BYOD device monitoring: admins can now proactively manage peripherals in BYOD rooms and desks via Pro Management portal reports that flag if devices are faulty, undetectable, missing, or moved, requiring a Teams Shared Devices license.
- Fresh hardware certifications from June's roundup include Biamp Ceiling Tile Mic w/ Configurable DSP for Medium, Large and Extra-Large Rooms, plus Logitech Rally Bar Mini/Huddle and Vision Express Desk Mount options for Teams Rooms on Android.
- Post-InfoComm 2026 momentum continues with **IntelliFrame people labels**, where IntelliFrame now identifies each person in the room and places their name alongside them so remote participants always know who's speaking, plus expanded Facilitator agent skills for room readiness checks.

## 🌐 Broader Collaboration Landscape
- **Slack** shipped a major update: the Slackbot MCP client is now generally available, connecting apps and shared channels through one conversational workspace, with a partner ecosystem of 20+ apps including Salesforce, Canva, Linear, and Zoom — a direct competitive move against Copilot's agent/connector strategy.
- **Cisco Webex** is tightening its platform lifecycle: starting with version 46.7 released July 7, 2026, Webex officially ends support for iOS 17 and iPadOS 17.
- The **Salesforce–Slack** integration continues reshaping the market: from Summer '26, any new Salesforce Enterprise or Unlimited org gets a Slack workspace automatically created and configured, with Salesforce channels connecting CRM records directly to Slack conversations by default.

## ⚡ Action Items & Things to Watch
- **Flag the Graph API shared-channels bug** (HTTP 500 on App-Context channel creation) to any internal dev/automation teams before it disrupts provisioning workflows.
- **Review Agent 365 licensing** — new purchases now require Microsoft 365 E5 or equivalent prerequisites; confirm this doesn't block planned pilots.
- **Watch Copilot Cowork's GA rollout and usage-based billing** setup in the admin center, since Frontier customers needed billing configured by June 30 to avoid disruption.

---
**Sources:**
- [Partner Center July 2026 announcements – Microsoft Learn](https://learn.microsoft.com/en-us/partner-center/announcements/2026-july)
- [Microsoft 365 Copilot Release Notes – Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/copilot/release-notes)
- [Microsoft 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap)
- [Microsoft Copilot Updates — July 2026 (40+ Features) – YouTube](https://www.youtube.com/watch?v=hFlBYtI7q7o)
- [Microsoft Teams Updates by Microsoft – July 2026 – Releasebot](https://releasebot.io/updates/microsoft/microsoft-teams)
- [Release notes for Microsoft Teams – Office release notes – Microsoft Learn](https://learn.microsoft.com/en-us/officeupdates/teams-admin)
- [What's New in Microsoft Teams | June 2026 – InfoComm Edition – Microsoft Community Hub](https://techcommunity.microsoft.com/blog/microsoftteamsblog/what%E2%80%99s-new-in-microsoft-teams--june-2026-%E2%80%93-infocomm-edition/4531968)
- [Neowin – New features Microso
