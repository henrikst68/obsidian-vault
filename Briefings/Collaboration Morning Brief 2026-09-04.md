---
date: '2026-09-04'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

# 🗓️ Collaboration Morning Brief — Friday, 4 September 2026

## 🔵 Microsoft Teams
- Microsoft has largely resolved the multi-day Microsoft 365 outage that began August 31: Microsoft now tracks this outage under MO1465074 and says the incident also affects OneDrive for Business and SharePoint Online, Microsoft Teams, Microsoft Purview, and Microsoft Defender XDR, with the root cause traced to a core authentication configuration used by multiple Microsoft 365 services. As of September 2, 48 hours after the outage began, all Microsoft 365 services have been recovered except Exchange Online, Universal Print, OneDrive for Business, and SharePoint Online — worth confirming Teams/Exchange are fully stable in your tenant today.
- Teams Rooms is rolling out **IntelliFrame people labels**: Microsoft Teams Rooms on Windows will introduce IntelliFrame people labels to identify in-room participants by name and show contact cards for remote attendees, enhancing hybrid meetings. The feature rolls out worldwide in September 2026, requires Teams Rooms Pro licenses, supports voice and face recognition enrollment.

## 🤖 Copilot & AI in Teams
- Latest Copilot release notes show two navigation/UX upgrades: Copilot Notebooks can now be opened from the Microsoft 365 app launcher with a streamlined navigation pane, reducing time spent on navigation, and Copilot Chat is now available from the side pane when using Copilot Search, letting users engage with Copilot without switching pages or losing context.
- Governance shift for developers: the GitHub Copilot harness for building autonomous agents is now generally available and moves to paid billing starting September 1, 2026 — flag this for any teams using agent-building harnesses.

## 🔗 Ecosystem & Integrations
- Admins should note the GitHub Copilot harness billing change above also ties into the broader tenant-wide agent management across multiple tenants, and billing changes for GitHub Copilot harness-built agents beginning in September 2026.
- Nothing new on SharePoint/Viva/Power Platform in the last 48 hours beyond incremental Copilot admin control updates noted above.

## Meetingroom Equipment
- **Action needed for legacy MTR hardware**: Microsoft's Teams certification for first-gen HP Poly Studio X30, X50, X70, G7500, TC8 and the original Neat Bar and Neat Board ends 3 September 2026 — along with a handful of devices from Logitech, DTEN, Yealink and EPOS. Rooms do not switch off that day and Teams keeps working, backed by two more years of Microsoft support, but new certification guarantees stop.
- Affected models specifically include Logitech Rally Bar Huddle (VR0034), Logitech Dock Flex (VR0035, Teams panel), DTEN Mate Touch Console (Gen1), and Yealink RoomPanel Plus — worth an inventory check if Henrik manages room fleets.
- IntelliFrame (see Teams section above) is the key new hardware-side feature to plan for on Teams Rooms Pro-licensed Windows devices this month.

## 🌐 Broader Collaboration Landscape
- Google Workspace pushed two updates this week: a gradual rollout of Gemini response customization in Drive, Chat, Gmail, Sheets, and Slides starting September 2, 2026, and four new Workspace Studio Flows automation steps — Move Drive file, Copy Drive file, Send a Chat reply, and Reply to email — giving end users greater control over document and cross-channel automation.
- Google also began widening cross-platform meeting interoperability: improvements to Google Calendar make it easier to join third-party video meetings including Microsoft Teams, Zoom, and Cisco Webex, with rollout starting August 27, 2026 — relevant for any mixed-vendor meeting environments Henrik supports.

## ⚡ Action Items & Things to Watch
- Confirm Exchange Online/SharePoint/Teams are fully stable in your tenant post-outage (MO1465074) and check Microsoft's forthcoming post-incident review.
- Audit any first-gen Poly/Neat/Logitech/DTEN/Yealink room devices against the September 3 certification cut-off list — no forced downtime, but plan hardware refresh cycles now.
- If your org builds custom agents via GitHub Copilot harness, review budget impact of the new paid billing model effective September 1.

---
**Sources:**
- [BleepingComputer – Massive Microsoft 365 outage causes auth issues, service failures](https://www.bleepingcomputer.com/news/microsoft/microsoft-exchange-online-outage-causes-email-failures-auth-issues/)
- [Cyber Defense Magazine – Microsoft Investigates Service Disruption Affecting Core M365 Apps](https://www.cyberdefensemagazine.com/microsoft-investigates-service-disruption-affecting-core-m365-apps/)
- [HANDS ON Teams – What's new for Microsoft Teams, July 2026](https://teams.handsontek.net/2026/08/03/whats-new-microsoft-teams-july-2026/)
- [Releasebot – Microsoft Release Notes, September 2026](https://releasebot.io/updates/microsoft)
- [Hubsite365 – Microsoft Copilot: August 2026 Updates](https://www.hubsite365.com/en-ww/crm-pages/microsoft-copilot-catch-up-new-features-and-changes-in-august-2026.htm)
- [MAV Reality – Is Your HP Poly or Neat Meeting Room Losing Certification?](https://www.mavreality.com/guides/poly-neat-teams-certification)
- [Google Workspace Updates blog (2026)](https://workspaceupdates.googleblog.com/2026/)
- [Google Workspace Updates – Improving Google Calendar's interoperability with third-party video conferencing](https://workspaceupdates.googleblog.com/2026/08/improving-google-calendars-interoperability-with-third-party-video-conferencing-solutions.html?m=1)
