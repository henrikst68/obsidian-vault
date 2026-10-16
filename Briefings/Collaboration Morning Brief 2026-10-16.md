---
date: '2026-10-16'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

# 🗓️ Collaboration Morning Brief — Friday, 16 October 2026

## 🔵 Microsoft Teams
- Microsoft **paused rollout** of the improved external-chat file-sharing feature (paperclip/drag-and-drop), announcing on Oct 15: "We have decided not to move forward with this change at this time." Admins should hold off on related policy changes.
- The new **Muted and Meeting chat sections** in the chat list have slipped: the rollout timeline shifted from mid-October to early November 2026, lowering immediate urgency, per an Oct 15 Message Center update.
- **Copilot is leaving the Teams chat list** — from mid-October the Copilot app in the app bar becomes the only entry point, with conversations and deep links preserved.
- Microsoft is adding **deepfake/impersonation protection** to meetings, where Teams will surface "warnings and risk indicators" on deceptive participants and organisers, alongside new guest-invitation reporting and granular conditional access for sensitive meetings.

## 🤖 Copilot & AI in Teams
- Effective **today (Oct 16)**, existing Copilot subscriptions requiring a base M365 plan get renamed with an "(add-on)" suffix, e.g. Microsoft 365 Copilot (add-on); standalone (no base subscription) SKUs arrive Dec 1. No functional change, but admins relying on product names in scripts should switch to SKU IDs.
- A key admin deadline looms: the new **Advanced Package Uploads** setting defaults to "on" from **October 25**, after which users will automatically be able to upload advanced packages — a declarative agent with actions, or an MCP server — unless admins configure it first.
- Admins can now publish **Organization Skills**: admins can publish organizational skills through the Microsoft 365 admin center, and end users with skills assigned will see them tagged "Organization" in their skills list.

## 🔗 Ecosystem & Integrations
- **Azure Communication Services** is being retired as a standalone product; Teams-related interop (Teams Phone, video interop, Click-2-Call) is unaffected, but ACS Direct Routing, PSTN Direct Offer, Chat and Rooms are retiring as Microsoft refocuses on Teams, Dynamics 365 and Azure-native experiences.
- **Viva Insights** advanced reporting now covers Copilot Cowork adoption: analysts can query Consumption (credit usage) and Person (Cowork usage) data via the Consumption dashboard and Copilot dashboard, improving AI ROI visibility.
- **Power Platform Community Conference 2026** runs Oct 27–29 in Las Vegas, with Microsoft framing the event around agents, apps and automation on a single managed platform — worth calendaring if Henrik tracks Power Platform roadmap signals.

## 🖥️ Meeting Room Equipment
- Management of **Android-based Teams Rooms, panels and phones is moving from the Teams admin center to the Pro Management portal**, requiring Admin Agent 855+; Microsoft calls the new enrollment flow "an Autopilot-like, light-touch device enrollment and provisioning experience," though OEM readiness varies by vendor.
- **Exchange Web Services retirement** is forcing device updates — Teams Rooms on Android devices below the minimum build lose calendar sync, and Google Workspace-to-Teams calendar sync is unsupported from October.
- At **WebexOne 2026**, Cisco confirmed its room hardware is going multi-platform: native Zoom Rooms support on Cisco hardware reaches general availability in October, and RoomOS 27 adds native Google Meet in November, letting one device fleet run Webex, MTR, Zoom or Meet.

## 🌐 Broader Collaboration Landscape
- **Cisco (WebexOne 2026):** beyond multi-platform rooms, Cisco showcased cross-platform troubleshooting tools as AI agents move into the workplace, signalling a push toward vendor-agnostic meeting room strategies.
- **Google Workspace:** the "skills" rollout for Gemini and Workspace has slipped — rollouts are slightly delayed as Google works through reliability issues; Google Meet also adopted post-quantum cryptography this week.
- **Slack:** shipped shareable "Slackbot Skills," letting orgs create external links so skills can travel across orgs and be copied into another workspace, alongside a growing AI agent skill repository.

## ⚡ Action Items & Things to Watch
- **Before Oct 25:** Review and configure the Copilot "Advanced Package Uploads" admin setting — default is "All users" if left unattended.
- **Before Dec 1:** Audit PowerShell/licensing scripts referencing Copilot SKU names to use product/SKU IDs ahead of the add-on naming transition.
- **Monitor Message Center:** The external-chat file-sharing feature and chat-section reorganisation are both paused/delayed — watch for the next rollout announcement before updating training materials or DLP policies.
- **Infra check:** Confirm Teams Rooms on Android devices meet minimum builds ahead of the EWS retirement to avoid calendar sync breakage.

---
**Sources:**
- [Planet Technologies – Microsoft 365 Roadmap Updates, Oct 15 2026](https://go-planet.com/in-the-know/october-15-2026/)
- [Empowering.Cloud – Microsoft Teams Enterprise Update, October 2026](https://empowering.cloud/microsoft-teams-enterprise-update-october-2026/)
- [Empowering.Cloud – Microsoft Teams Enterprise Update, September 2026](https://empowering.cloud/microsoft-teams-enterprise-update-september-2026/)
- [Modern Workspace Pro – MC1479514: Teams Pauses External Chat File Sharing](https://mwpro.co.uk/blog/2026/10/15/mc1479514-microsoft-teams-pauses-rollout-of-improved-file-sharing-in-external-chats/)
- [Modern Workspace Pro – MC1269864: Muted & Meeting Chat Sections](https://mwpro.co.uk/blog/2026/10/15/mc1269864-microsoft-teams-adds-muted-and-meeting-chat-sections-and-replaces-meeting-chat-filter-2/)
- [pupuweb.com – MC1508148 Microsoft 365 Copilot Offer and Name Updates](https://pupuweb.com/mc1508148-microsoft-365-copilot-offer-and-name-updates/)
- [Partner Center Announcements – October 2026](https://learn.microsoft.com/en-us/partner-center/announcements/2026-october)
- [M365 Copilot Connection – Copilot's biggest October 2026 updates](https://m365copilotconnection.substack.com/p/copilots-biggest-october-2026-updates)
- [Microsoft Learn – Microsoft 365 Copilot Release Notes](https://learn.microsoft.com/en-us/microsoft-365/copilot/release-notes)
- [WWT – WebexOne 2026: Key Takeaways](https://wwt.com/blog/webexone-2026-key-takeaways-for-digital-workspace-and-employee-experience)
- [Google Workspace Updates Blog – 2026](https://workspaceupdates.googleblog.com/2026/)
- [Google Workspace Updates – Skills Rollout Update](https://workspaceupdates.googleblog.com/)
- [Releasebot – Slack Release Notes, October 2026](https://releasebot.io/updates/slack)
- [Dynamics Edge – Power Platform News, October 2026](https://www.dynamicsedge.com/power-platform-news-today-october-2025/)
