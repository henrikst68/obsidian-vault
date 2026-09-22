---
date: '2026-09-22'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

# 🗓️ Collaboration Morning Brief — Tuesday, 22 September 2026

## 🔵 Microsoft Teams
- Microsoft is rolling out a **centralized resource management experience** for Teams chats and channels — pinning links, files, and messages below the header and organizing them into folders — replacing the old "In this chat/channel" panes, with worldwide rollout starting late September. Microsoft is introducing a more consistent way for users to access and manage important resources in Microsoft Teams chats and channels, letting users pin frequently used resources directly below the chat or channel header, pin multiple messages alongside other resources, and organize them into folders.
- The **Teams Admin Center's device management is being phased out** for Android Rooms, panels, and phones, with Microsoft targeting completion by end of September across all clouds — inventory, updates and health monitoring are moving to the Teams Rooms Pro Management Portal. The phased deprecation of device management in the Teams Admin Center began the week of 1 September, with inventory, updates, health and settings for Teams Rooms on Android, Teams phones, panels and SIP phones moving to the Teams Rooms Pro Management Portal.
- Entra **passwordless resource accounts** for Rooms (Windows and Android), panels and phones continue rolling out with a migration wizard and progress dashboard in the Pro Management Portal. Entra passwordless resource accounts for Rooms (Windows and Android), panels and phones are rolling out from August, with a migration wizard and progress dashboard in the Pro Management Portal, across worldwide, GCC and GCC High.

## 🤖 Copilot & AI in Teams
- **Facilitator** (the Teams meeting agent) now proactively runs a Copilot web search mid-meeting to resolve unanswered factual questions, posting answers directly to chat — a shift from purely prompt-driven AI, requiring Microsoft 365 Copilot Premium. The feature has slipped to a September rollout: when a factual question goes unanswered during a meeting, Facilitator can now run a Copilot web search and post the answer directly into the meeting chat without anyone asking it to; the capability requires Microsoft 365 Copilot Premium, has to be switched on manually for each meeting, and is designed to fire less than once per meeting.
- Answers appear for **all attendees, including external/cross-tenant guests** without Copilot licenses — worth a policy decision on default-on vs. per-meeting opt-in. Once Facilitator is enabled, its answers appear in the meeting chat for everyone present, including external and cross-tenant attendees who may not hold a Copilot licence themselves, so it's worth deciding as a matter of policy whether it should be on by default.
- Microsoft is opening an **official admin-centre route for third-party agents** (e.g. GitHub Copilot) into Teams, part of a broader push toward less manually-switched-on AI. Third-party agents such as GitHub Copilot get a proper home in the Teams admin centre, and Rooms devices are rebranded as intelligent spaces.

## 🔗 Ecosystem & Integrations
- **Copilot Cowork** (agentic, multi-step task execution across M365) continues expanding partner plugin support — nine live partner plugins now (Enosix, Harvey, LSEG, Miro, monday.com, Moody's, Morningstar, S&P Global Energy, TeamsMaestro) with eight more coming, plus billing now active for usage. Billing for Copilot Cowork begins today; nine new partner plugins are available now, eight are coming soon, including Enosix, Harvey, LSEG, Miro, monday.com, Moodys, Morningstar, S&P Global Energy, and TeamsMaestro.
- **Viva Connections Home Experience 3.0** reached general availability, adding a compact card variant and multi-source news feed — relevant for intranet/Teams integration teams. Viva Connections Home Experience 3.0 is GA — update your ACE manifests to support the compact card variant and take advantage of the multi-source news feed.
- **Google Calendar** now offers easier one-click joining for Teams, Zoom, and Webex meetings cross-platform, rolling out from 10 September. Google is introducing improvements to Google Calendar that make it easier to join third-party video meetings, including Microsoft Teams, Zoom, and Cisco Webex, when collaborating across different calendar and email clients.

## Meetingroom Equipment
- **First-gen HP Poly and Neat devices** (Studio X30/X50/X70, G7500, TC8, original Neat Bar/Board, plus some Logitech/DTEN/Yealink/EPOS models) lost fresh Teams certification guarantees as of 3 September 2026, though existing rooms keep working with two more years of Microsoft support. Microsoft's Teams certification for first-gen HP Poly Studio X30, X50, X70, G7500, TC8 and the original Neat Bar and Neat Board ends 3 September 2026, along with devices from Logitech, DTEN, Yealink and EPOS — rooms don't switch off, backed by two more years of Microsoft support, but new certification guarantees stop.
- **Cisco's "Devices for Zoom Rooms"** program reached general availability this month, letting Cisco hardware run as certified Zoom Rooms devices — expanding cross-platform hardware flexibility for enterprises running mixed UC stacks. As of September 2026, Cisco hardware is certified as a Device for Zoom Rooms, with general availability expected September 2026 following public beta starting June 2026.

## 🌐 Broader Collaboration Landscape
- **Slack** shipped a major AI-focused monthly update centred on code channels, new Agent/Slackbot workspaces, and tighter Salesforce/Seismic/Workflow Builder integration, aiming to keep human and agent collaboration in shared context. Slack released a major monthly update centered on AI collaboration, bringing code channels, new Agent and Slackbot workspaces, deeper research, and tighter connections to Salesforce, Seismic, Lists, and Workflow Builder — connecting AI work already happening across teams to the conversation.
- **Zoom** continues building out workflow automation (ZoomMate), including workspace-reservation triggers/actions and admin controls restricting which automation nodes are available per user group. Users with a Zoom Workspace license can build automated workflows using workspace reservation action nodes, and account owners/admins can now define which workflow action nodes and triggers are available to specific user groups.
- Analysts continue to frame Teams vs. rivals along familiar lines: Teams' channel-based structure suits M365-native orgs but can feel heavy for guests and smaller teams, while Google Meet/Webex remain lighter-weight alternatives for cross-org calls. Teams uses a channel structure that keeps video calls in context with related conversations and files, but guests joining a Teams call for the first time often struggle with the sign-in flow.

## ⚡ Action Items & Things to Watch
- **Audit Teams Rooms device inventory now** — Teams Admin Center device management for Android Rooms/panels/phones is being fully deprecated by 30 September; pull inventory and confirm ops teams have Pro Management Portal access before the cutover.
- **Review Facilitator's proactive web-search behaviour** ahead of wider rollout — decide organisational policy on default-on vs. per-meeting activation, especially for meetings with external/unlicensed guests.
- **Check meeting room hardware fleet** against the newly-lapsed certification list (first-gen Poly/Neat/Logitech/DTEN/Yealink/EPOS devices) — no immediate disruption, but plan refresh cycles ahead of the 2028 support horizon.

---
**Sources:**
- [UC Today – Microsoft Teams and Copilot updates for September 2026](https://uctoday.com/microsoft-teams-copilot-whats-new-in-september-2026)
- [Empowering.Cloud – Microsoft Teams Enterprise Update, September 2026](https://empowering.cloud/microsoft-teams-enterprise-update-september-2026/)
- [Message Center Archive – MC1473153](https://mc.merill.net/message/MC1473153)
- [Akshara Technologies – Microsoft 365 September 2026 Updates](https://www.aksharatech.com/blog-posts/microsoft-365-september-2026-updates)
- [SharePoint Stuff – Microsoft Roadmap Roundup, 14 September 2026](https://sharepointstuff.com/2026/09/14/microsoft-roadmap-roundup-14-september-2026/)
- [Releasebot – Microsoft Copilot Updates, September 2026](https://releasebot.io/updates/microsoft/microsoft-copilot)
- [MAV Reality – HP Poly and Neat Gen1 Teams Certification](https://www.mavreality.com/guides/poly-neat-teams-certification)
- [Webex Blog – Extending the Agentic Workplace to Every Meeting Platform](https://blog.webex.com/collaboration/infocomm-2026-extending-agentic-workplace-every-meeting-platform/)
- [Google Workspace Updates – August 2026](https://workspaceupdates.googleblog.com/2026/08/)
- [Releasebot – Zoom Release Notes, September 2026](https://releasebot.io/updates/zoom)
- [Releasebot – Slack Release Notes, September 2026](https://releasebot.io/updates/slack)
- [Redmondmag – Microsoft Makes Copilot Cowork Generally Available Worldwide](https://redmondmag.com/articles/2026/06/16/microsoft-makes-copilot-cowork-generally-available-worldwide.aspx)
