---
date: '2026-08-18'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---

# 🗓️ Collaboration Morning Brief — Tuesday, 18 August 2026

## 🔵 Microsoft Teams
- Microsoft is retiring Teams Live Chat about 18 months after launch, with the service fully retired on October 5 when customer messages stop reaching Teams; new setups were already blocked on August 6.
- A new **Report** button is rolling out to combat AI deepfake meetings — it lets users report a security issue during a meeting so IT/security teams can intervene, with full availability expected in August 2026.
- Admin-facing changes are landing fast: management of Android-based Teams Rooms, Teams panels, and Teams phones is moving from the Teams admin center to the Pro Management portal for a more consistent, secure experience, alongside a new Organization Trust Score that automates evaluation of apps and agents for security, privacy, and compliance.
- Governance tightening continues: Teams will require owner approval for users joining private teams via join codes starting late August 2026, though public teams are unaffected.

## 🤖 Copilot & AI in Teams
- Big consumer-side cutover **today**: Deep Research is being retired in the Copilot app for consumers starting August 18, 2026, and Podcasts is being retired from Copilot and will no longer be available after August 18, 2026 — Group Chats will also be collapsed into 1:1 conversations.
- Governance flag for enterprise admins: Microsoft closed out FY26 with 30 million Copilot seats and Azure up 43%, and OpenAI quietly became a subprocessor in Microsoft 365, with the toggle auto-enabled unless already opted out — worth checking tenant settings.
- Copilot is evolving beyond chat: eight new features landed in August, including integration of advanced AI models like GPT-5.6 and Claude that dynamically adapt to tasks such as generating reports or summaries, plus a new Cowork integration allowing teams to create custom automated workflows.

## 🔗 Ecosystem & Integrations
- Critical security alert: researchers disclosed CVE-2026-55040 (CVSS 9.1), a SharePoint flaw allowing entry as any user including an administrator with no valid account, affecting SharePoint Server Subscription Edition, 2019, and 2016 — patch/mitigate urgently if you run on-prem SharePoint.
- Slack (main Teams-chat rival for interoperability planning) shipped a major admin update: 12 new capabilities including agents in DMs, Slackbot-generated slides and dashboards, Google Docs as a Workflow Builder source, and adjustable AI content safety filters, with a FedRAMP support-data decision due August 19, 2026.
- Microsoft is also standing up a new certification programme for Teams Phone voice agents, signalling deeper AI-agent integration into telephony.

## Meetingroom Equipment
- Certification cliff approaching: Microsoft's Teams certification for first-gen HP Poly Studio X30, X50, X70, G7500, TC8 and the original Neat Bar and Neat Board ends 3 September 2026, alongside several Logitech, DTEN, Yealink and EPOS models — rooms keep working but lose certification guarantees.
- Not all devices are affected — Logitech Rally Bar, Rally Bar Mini, Tap IP and RoomMate, plus DTEN Mate Gen2 and Yealink RoomPanel/RoomPanel E2 all run through to 15 August 2028, so an audit against your specific SKUs is worthwhile before any panic-buying.
- Current MTR hardware guidance still lists Poly, Yealink, Logitech, Jabra, Crestron, and Neat as the certified hardware vendors for enterprise deployments.

## 🌐 Broader Collaboration Landscape
- Zoom security scare: a now-fixed Zoom screen-sharing bug let call participants hijack each other's devices, discovered in fewer than 20 prompts using a public AI tool — a reminder to review "join before host" and screen-share permissions across vendors, not just Teams.
- Competitive landscape remains fragmented rather than consolidating: Slack, Microsoft Teams, Zoom Team Chat, Cisco Webex, and Google Chat remain the five dominant enterprise messaging platforms, each anchored to a different primary use case and buyer.
- Enterprises are increasingly opting for interoperability layers instead of migration — the strongest enterprises are giving up on standardizing on a single chat platform, letting different functions pick different tools while a federation layer keeps conversations joined up.

## ⚡ Action Items & Things to Watch
- **Today's deadline:** If your org or users rely on Copilot consumer Group Chats, Podcasts, or Deep Research, confirm data/content has been exported before the August 18 cutover.
- **Security priority:** Assess exposure to CVE-2026-55040 (SharePoint) and review Zoom screen-share/join settings tenant-wide.
- **Hardware planning:** Run a Teams Rooms device audit against the September 3, 2026 certification expiry list (Poly/Neat/Logitech/Yealink first-gen units) to avoid last-minute replacement scrambles.
- **Governance:** Verify the OpenAI-as-subprocessor toggle setting in your M365 tenant and the EU Data Boundary wording change flagged this month.

---
**Sources:**
- [The Register – Microsoft tosses Teams Live chat into its feature graveyard](https://www.theregister.com/applications/2026/08/07/microsoft-tosses-teams-live-chat-into-its-feature-graveyard/5284634)
- [Windows Latest – Teams fighting AI deepfake meetings with Report button](https://www.windowslatest.com/2026/08/04/microsoft-teams-is-fighting-ai-deepfake-meetings-with-a-new-report-button-rolling-out-august-2026/)
- [Releasebot – Microsoft Teams Updates August 2026](https://releasebot.io/updates/microsoft/microsoft-teams)
- [HANDS ON Teams – What's new for Microsoft Teams, July 2026](https://teams.handsontek.net/2026/08/03/whats-new-microsoft-teams-july-2026/)
- [Microsoft Support – Updates to Copilot and the Microsoft 365 Copilot app](https://support.microsoft.com/en-us/microsoft-365-copilot/learning/changes-microsoft-copilot-app)
- [Empowering.Cloud – Microsoft 365 Enterprise Update August 2026](https://empowering.cloud/microsoft-365-ai-workplace-update-august-2026/)
- [Geeky Gadgets – Microsoft 365 Copilot Features: August 2026 Updates](https://www.geeky-gadgets.com/microsoft-365-copilot-features-august-2026/)
- [TechManiacs – AI Security Daily Briefing, August 12, 2026](https://techmaniacs.com/2026/08/12/ai-security-daily-briefing-august-12-2026/)
- [Vantage Point – Slack August 2026 Admin Updates](https://vantagepoint.io/blog/sf/slack-august-2026-admin-updates)
- [Releasebot – Slack Release Notes August 2026](https://releasebot.io/updates/slack)
- [SyncRivo – Slack vs Teams vs Zoom vs Webex vs Google Chat 2026](https://syncrivo.ai/en/resources/slack-vs-teams-vs-zoom-vs-webex)
- [SyncRivo – 15 Slack Alternatives Enterprises Choose in 2026](https://syncrivo.
