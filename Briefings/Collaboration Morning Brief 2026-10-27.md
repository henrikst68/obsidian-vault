---
date: '2026-10-27'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

# 🗓️ Collaboration Morning Brief — Tuesday, 27 October 2026

## 🔵 Microsoft Teams
- Microsoft restored Teams service after an incident affecting US users on October 26, tracked as TM1526111, with automatic scaling returning the service to healthy levels. Downdetector had logged more than 3,000 user reports of problems at 8:45 a.m. PT during the disruption.
- Security researchers are warning of a recurring social-engineering pattern where threat actors use Teams' external chat creation feature to run impersonation scams, with Arctic Wolf Labs noting consistent use of throwaway tenants and "IT Support (Internal)" display names. Nearly 30–40% of cases abuse *.onmicrosoft.com, the fallback domain auto-generated when a Microsoft 365 tenant is created.
- Microsoft will deploy an AI security layer in Teams that reads conversation content to detect social-engineering attacks lacking traditional indicators like malicious links, detailed in Message Center post MC1519866 on October 21. Rollout is targeted to end by mid-November, with general availability expected worldwide between early and mid-December.

## 🤖 Copilot & AI in Teams
- Usage-based billing is now default on for new Microsoft 365 Copilot Business licenses, and existing Copilot offers are being renamed "(add-on)" beginning October 16, with SKUs available without a base-subscription prerequisite from December 1.
- Microsoft's October model refresh added new options to the Copilot selector — a model picker with Auto, Quick response, Think deeper and Advanced reasoning options now lists Sonnet 5.5 between Sonnet 5 and Opus 5.5, under usage-based billing, though GPT-6.1 Sol isn't yet visible.
- A new "Today" feature enters private preview in Copilot this month and is coming to Outlook and Teams, and invoking @Copilot in Teams now gives the whole team shared context and permissions of the channel, group chat or meeting.

## 🔗 Ecosystem & Integrations
- Dataverse for Teams environments can no longer be created starting November 15, 2026, with existing unupgraded environments suspended September 2027 and decommissioned October 2027 — relevant for any custom Teams apps built on low-code Dataverse.
- Copilot can now help build quick workflows for Teams chats and channels when key file changes or metadata updates occur in SharePoint, without needing triggers, actions or a separate Power Automate flow.
- Plugins now let Copilot in SharePoint work with systems such as GitHub, CRM systems, publishing platforms and internal tools, supporting read and write scenarios with human approval on bulk actions.

## Meetingroom Equipment
- Microsoft and Zoom jointly announced "Cross-Platform Meeting Connect," but this is a roadmap announcement, not a release — Microsoft gave no ship date, rollout schedule, device list or minimum software versions.
- Zoom confirmed Zoom Rooms will be able to join Teams meetings in the first half of 2027, with HDMI sharing, dual displays, 1080p video, rosters and read-only chat; its sensitivity labels already sync with Microsoft Purview for some customers.
- Zoom notes early limitations: the meeting will appear only on the room's first display, wired/wireless HDMI sharing won't be available initially, and web-client join is limited to single camera/mic/speaker rooms.

## 🌐 Broader Collaboration Landscape
- At Zoomtopia 2026, Zoom introduced a new Unified Context Layer and several AI-powered products designed to help businesses transform meeting context into deliverables. Search & Ask APIs now let users query Zoom's Unified Context Layer directly from Claude, GPT, Codex, Muse, MS Copilot, Gemini and Slackbot, available now.
- Native Zoom Rooms now run on Cisco hardware, with Teams interoperability following next year so customers can add Zoom to rooms without replacing existing equipment.
- Google's new Gmail "AI Inbox" view — suggested to-dos and topic summaries — is rolling out to paid Workspace plans in the US from October 2026, starting with Standard and Plus tiers.

## ⚡ Action Items & Things to Watch
- **Prep for Nov 15 deadline:** Audit any Teams apps built on Dataverse for Teams before new-environment creation is blocked.
- **Security review:** Brief helpdesk/security teams on the Teams "IT Support" impersonation scam pattern and the incoming AI phishing detection feature (targeted release begins early November).
- **Watch for dates:** Microsoft has not yet published a timeline or licensing tier for Cross-Platform Meeting Connect (Teams/Zoom room interop) — worth monitoring for Q1 2027 planning.

---
**Sources:**
- [GV Wire – Microsoft Teams Down for Thousands of Users](https://gvwire.com/2026/10/26/microsoft-teams-down-for-thousands-of-users-downdetector-reports/)
- [Cybersecurity News – Microsoft Investigation Teams Issue](https://cybersecuritynews.com/microsoft-investigation-teams-issue/)
- [The Hacker News – Attackers Use Microsoft Teams IT Support Scams](https://thehackernews.com/2026/10/attackers-use-microsoft-teams-it.html)
- [Tech Times – Microsoft Teams Adds AI That Reads Conversations](https://techtimes.com/articles/329521/20261027/microsoft-teams-adds-ai-that-reads-conversations-catch-phishing-no-malicious-links.htm)
- [BleepingComputer – Microsoft Teams AI-powered phishing detection](https://www.bleepingcomputer.com/news/microsoft/microsoft-teams-to-get-ai-powered-context-aware-phishing-detection/)
- [Microsoft Learn – Partner Center October 2026 announcements](https://learn.microsoft.com/en-us/partner-center/announcements/2026-october)
- [A Guide to Cloud – What's New
