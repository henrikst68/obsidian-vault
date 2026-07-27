---
date: '2026-07-27'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

Now I have enough to compile the briefing.

# 🗓️ Collaboration Morning Brief — Monday, 27 July 2026

## 🔵 Microsoft Teams
- **Post-incident review published on last week's outage:** Microsoft's preliminary Post Incident Review confirmed the July 23 outage was triggered during routine device maintenance in Azure's West US region, where a bug in the request conversion system incorrectly marked additional network devices as part of the maintenance event. Teams chat functionality was degraded, including images not loading, alongside SharePoint and OneDrive issues; a final PIR is expected in early August.
- **New Teams admin center agent governance is rolling out:** Administrators can now manage Teams Core agents, such as Facilitator, from a dedicated experience in the Teams admin center, controlling agent availability and settings for the whole org, specific users, or groups — with Teams Core agents available by default to licensed users.
- **Device management consolidation:** Admins can now use the Pro Management portal to monitor device health, manage inventory, and access analytics for Windows and Android devices, with management of Android-based Teams Rooms, panels, and phones moving from the Teams admin center to the Pro Management portal.
- **User-reported security signals live:** Users can now report suspicious external users directly within Teams, with reports surfaced in the Teams admin center so admins can investigate potentially risky interactions.

## 🤖 Copilot & AI in Teams
- **Meeting AI opt-out nearing full rollout:** Microsoft's in-meeting toggle letting organizers turn off Copilot, Facilitator, and Recap mid-meeting is completing its GA rollout this month — General Availability began in mid-July and is expected to complete by the end of July 2026, appearing across Windows, macOS, mobile, and web.
- **New frontier models added to Copilot:** Two new frontier models — OpenAI's GPT-5.6 and Anthropic's Claude Sonnet 5 — arrived in Copilot this month, alongside Copilot Notebooks turning notes into Word, Excel or PowerPoint outputs.
- **OpenAI-operated model rollout for tenants:** eligible commercial tenants become enabled for all users from 24 July 2026 unless admins select "No users" under Copilot → Settings → AI providers operating as Microsoft subprocessors — worth a governance check this week.

## 🔗 Ecosystem & Integrations
- **Agent Store governance expands:** Customers can now submit agents built in Agent Builder to the Agent Store under "Built by your org," after admin review and approval in the Microsoft 365 Admin Center — a governed flow enabling organizations to share validated agents at scale.
- **Teams Phone multi-line now GA:** Microsoft Teams Phone user multi-line lets admins assign up to 10 phone numbers to a single Teams Phone user.
- **Recording compliance tightened:** Teams meeting recordings can now automatically inherit the meeting's sensitivity label when admins enable label inheritance, so a "Confidential" meeting's MP4 recording can carry the same label for consistent access controls.

## Meeting Room Equipment
- **MTR hardware landscape stable, EOL notice issued:** Yealink confirmed the MVC800 II was discontinued for sale on Jul 12 2021 and will reach End-of-Life status on Jul 12 2026 — customers should plan migration.
- **Certified vendor ecosystem unchanged:** Current certified MTR hardware vendors remain Poly, Yealink, Logitech, Jabra, Crestron, and Neat, with tiering guidance noting medium rooms typically use Poly Studio X70, Yealink MeetingBar A40 or Logitech Rally Bar, while large rooms lean on Crestron Flex, Poly G85-T or Neat Bar Pro.

## 🌐 Broader Collaboration Landscape
- **Salesforce makes Slack the default collaboration layer:** As of Summer '26, any new Salesforce org in Enterprise or Unlimited edition comes with a Slack workspace already built and configured, with no separate purchase or setup — the collaboration layer arrives with the CRM. For organisations already running Microsoft Teams or Zoom as their primary UC platform, Salesforce is not asking them to switch.
- **Slack adds MCP-based agent connectivity:** Slack added the Slackbot MCP client, now generally available, letting teams search, act, and share live results from tools like Salesforce, Canva, Linear, and Zoom right in Slack.
- **Zoom pushes cross-platform AI notes:** Zoom's AI Companion can now take notes across third-party meeting platforms like Google Meet, Microsoft Teams, and WebEx, intensifying the AI-assistant competition across vendors.

## ⚡ Action Items & Things to Watch
1. **Review the Azure/M365 outage RCA** when Microsoft's final Post Incident Review lands (expected early August) and reassess business continuity fallback plans for Teams/SharePoint dependency risk.
2. **Audit the new OpenAI-subprocessor default** in Copilot settings before/after the 24 July auto-enablement date if your tenant hasn't explicitly opted out.
3. **Check Teams Core agent default-on governance** in the new Teams admin center experience — confirm whether Facilitator and other built-in agents should remain enabled by default for your org.

---
**Sources:**
- [BleepingComputer – Microsoft blames massive Microsoft 365 outage on maintenance bug](https://www.bleepingcomputer.com/news/microsoft/microsoft-blames-massive-microsoft-365-outage-on-maintenance-bug/)
- [Vertu – Microsoft Teams Outage: July 2026 Incident](https://vertu.com/ai-tools/microsoft-teams-outage-july-2026-azure-incident)
- [TechTimes – Microsoft 365 Outage: Azure Maintenance Bug](https://www.techtimes.com/articles/321568/20260725/microsoft-365-outage-azure-maintenance-bug-wiped-ip-routes-taking-down-teams-hours.htm)
- [Releasebot – Microsoft Teams Updates July 2026](https://releasebot.io/updates/microsoft/microsoft-teams)
- [Releasebot – Microsoft Copilot Updates July 2026](https://releasebot.io/updates/microsoft/microsoft-copilot)
- [Microsoft Learn – Release Notes for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/release-notes)
- [A Guide to Cloud & AI – What's New in Microsoft 365 Copilot July 2026](https://www.aguidetocloud.com/blog/microsoft-365-copilot-july-2026-updates/)
- [IT Trip – Microsoft Teams Release Notes: July 2026 Admin Changes](https://en.ittrip.xyz/ms-office/teams/teams-release-notes)
- [Windows Latest – Microsoft caves after Teams AI backlash](https://www.windowslatest.com/2026/07/05/microsoft-caves-after-teams-ai-backlash-will-let-you-turn-off-copilot-facilitator-and-recap-mid-meeting/)
- [Yealink – MVC800 II EOL Notice](https://www.yealink.com/en/product-detail/microsoft-teams-rooms-mvc800II)
- [EPC Group – Microsoft Teams Rooms Enterprise Deployment Guide 2026](https://www.epcgroup.net/microsoft-teams-rooms-enterprise-deployment-guide-2026)
- [UC Today – Salesforce Summer '26: Slack Is Now the Default](https://www.uctoday.com/unified-communications/salesforce-summer-26-slack-is-now-the-default-for-every-new-customer-heres-what-that-changes/)
- [Releasebot – Slack Release Notes July 2026](https://releasebot.io/updates/slack)
- [Zoom – What's New at Zoom](https://www.zoom.com/en/products/whats-new/)
