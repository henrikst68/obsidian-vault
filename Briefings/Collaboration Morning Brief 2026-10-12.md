---
date: '2026-10-12'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

Have enough to build a comprehensive briefing now.

# 🗓️ Collaboration Morning Brief — Monday, 12 October 2026

## 🔵 Microsoft Teams
- Microsoft is rolling out **third-party deepfake detection and impersonation protection** for Teams meetings, with certified providers sending synthetic audio/video detection signals to Teams, which then surfaces warnings and risk indicators to help users recognize potential impersonation attempts; worldwide GA is slated for November (Roadmap 573451/573157).
- A new **Czech-language report** (11 Oct) confirms the rollout timeline, noting Microsoft's own telemetry shows weekly fraudulent voice-call attempts via Teams had climbed to nearly ten times mid-2025 levels by late June, underscoring why these protections are landing now.
- **Teams Phone Agent** — an AI receptionist for business phone lines — is now generally available, charged with "usage-based billing through Copilot Credits … including call duration and the capabilities invoked", requiring Teams Phone, a resource account and a spending policy set up first.
- Admin housekeeping: users can now temporarily pause all notifications without changing existing settings, and Teams now supports audio/video offloading for town hall attendees on VDI endpoints (Azure Virtual Desktop, Windows 365, Citrix, Omnissa, AWS).

## 🤖 Copilot & AI in Teams
- **Copilot in SharePoint and OneDrive is now generally available**, one of the biggest releases of the month, alongside a new Copilot Chat experience in Teams and Outlook, more PowerPoint skills, new spending-policy controls, and a stack of new models.
- Microsoft confirmed usage-based billing will be enabled by default for new Microsoft 365 Copilot Business subscriptions purchased through CSP, beginning December 1, 2026 — pushed back a month from the original November date.
- Copilot's Teams-facing search gets smarter: it can now find meetings based on topics or keywords from meeting body, chat, and transcription, searching transcript text from meetings in the last two months.

## 🔗 Ecosystem & Integrations
- **Azure Communication Services is retiring** as a standalone product — Microsoft's CPaaS play, the Twilio compete — with no new sign-ups for the retiring services from 23 October 2026, a notable signal for anyone building custom voice/video on Azure.
- Admins have a hard deadline: Exchange Web Services is retiring, and Teams devices below the minimum version will lose calendar sync; Teams mobile needs iOS 8.9.0+/Android 1416+, with Google Workspace-to-Teams calendar sync unsupported from October.
- GitHub Copilot has formally joined Teams as an agent — users can @mention GitHub Copilot in a channel or meeting chat to start a coding-agent session that opens a PR, reflecting Microsoft's broader push on third-party agents inside Teams search and the admin center.

## Meeting Room Equipment
- **Logitech** unveiled its next MDEP-based Teams Rooms lineup on 8 October, headlined by Rally Bar 2, successor to Rally Bar and Rally Bar Mini, built on the Microsoft Device Ecosystem Platform, with built-in occupancy sensors feeding room-usage data to IT, plus Rally System 2 Pro, Rally Speaker 2 Pro/Max, Tap IP 2/Scheduler 2, and a new AV-over-IP approach called Logitech Link.
- **Neat and Shure** have both shipped new MDEP devices: Neat's Board 32, Pad Pro and Pad Gen 2 have been certified for Microsoft Teams Rooms, marking Neat's inclusion in Microsoft's Device Ecosystem Platform, while Shure's IntelliMix Bar Pro is now shipping as an all-in-one video bar for medium/large rooms.
- Teams Rooms on Windows app updates now flow **exclusively through the Pro Management Portal**, no longer via the Microsoft Store, and local PTZ camera control from the in-room console is rolling out this month.

## 🌐 Broader Collaboration Landscape
- **Cisco's WebexOne 2026** (5–8 Oct, Austin) was the week's biggest ecosystem story: Cisco unveiled Claude Managed Agents inside Webex, letting AI agents join spaces, meetings and calls to carry out multi-step tasks across Webex and outside apps, plus an OpenAI "dots" integration via MCP.
- Cisco's new **RoomOS 27** (due November) completes a four-platform play: native Google Meet support on Cisco hardware, so one device fleet can now boot into Webex, Microsoft Teams, Zoom or Google Meet, with native Zoom Rooms reaching general availability this month too.
- Analyst take from Metrigy's Irwin Lazar frames this as an industry-wide pattern: "We've seen similar efforts by Slack, with Claude Tag, and with Zoom via ZoomMate" — every major vendor is now racing to embed third-party AI agents directly into their collaboration surface.

## ⚡ Action Items & Things to Watch
- **Decide on deepfake/impersonation protection rollout** (GA November) — review certified providers and licensing implications before it lands in your tenant.
- **Audit Teams Rooms hardware** against the EWS retirement and Android 10/11 certification cutoffs; older devices lose calendar sync and certification without an upgrade path.
- **Watch Microsoft Ignite (November)** — multiple vendor roadmaps (Teams Phone, Copilot billing, intelligent spaces) are explicitly holding announcements for the event.

---
**Sources:**
- [BetaNews – Microsoft Teams will soon support third-party deepfake protection](https://betanews.com/article/microsoft-teams-will-soon-support-third-party-deepfake-protection/)
- [BleepingComputer – Microsoft Teams to add third-party deepfake detection](https://www.bleepingcomputer.com/news/security/microsoft-teams-to-add-third-party-deepfake-detection-impersonation-protection/)
- [Planet Technologies – Microsoft 365 Roadmap Updates, Oct 8 2026](https://go-planet.com/in-the-know/october-8-2026/)
- [Empowering.Cloud – Microsoft Teams Enterprise Update, October 2026](https://empowering.cloud/microsoft-teams-enterprise-update-october-2026/)
- [Empowering.Cloud – Microsoft Teams Enterprise Update, September 2026](https://empowering.cloud/microsoft-teams-enterprise-update-september-2026/)
- [m365copilotconnection.substack.com – Copilot's biggest October 2026 updates](https://m365copilotconnection.substack.com/p/copilots-biggest-october-2026-updates)
- [Microsoft Learn – Partner Center October 2026 announcements](https://learn.microsoft.com/en-us/partner-center/announcements/2026-october)
- [Releasebot – Microsoft Copilot Updates, October 2026](https://releasebot.io/updates/microsoft/microsoft-copilot)
- [Microsoft Learn – Teams admin release notes](https://learn.microsoft.com/en-us/officeupdates/teams-admin)
- [UC Today – This Week in UC&C: Cisco Goes Open at WebexOne 2026](https://uctoday.com/this-week-in-uc-c-cisco-goes-open-at-webexone-2026)
- [UC Today – WebexOne 2026: Cisco Bets on AI to Redefine the Meeting Room](https://uctoday.com/webexone-2026-cisco-bets-on-ai-to-redefine-the-meeting-room)
- [Startup Fortune – Cisco turns Webex into an AI agent workspace with Claude built in](https://startupfortune.com/cisco-turns-webex-into-an-ai-agent-workspace-with-claude-built-in)
- [ComputerWorld – Cisco brings collaborative agents and Claude into Webex chats](https://computerworld.com/article/4231779/cisco-brings-collaborative-agents-and-claude-into-webex-chats.html)
- [AV Interactive – Three Neat devices achieve Microsoft Teams certification](https://www.avinteractive.com/news/products/three-neat-devices-achieve-microsoft-teams-certification-29-09-2026/)
- [UC Today – This Week in UC&C: Teams Rooms Get a New Operating Model](https://uctoday.com/this-week-in-uc-c-teams-rooms-get-a-new-operating-model)
- [WindowsForum – Shure IntelliMix Bar Pro Ships for Teams Rooms](https://windowsforum.com/news/shure-intellimix-bar-pro-ships-for-teams-rooms-mdep-lifecycle-and-management-guide.446580/)
- [WN24.cz – Microsoft Teams začne varovat před falešnými účastníky](https://wn24.cz/microsoft-teams-zacne-varovat-pred-falesnymi-ucastniky)
