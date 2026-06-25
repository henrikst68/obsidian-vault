---
date: '2026-06-25'
type: briefing
tags:
  - teams
  - microsoft365
  - collaboration
  - copilot
---
# 🗓️ Collaboration Morning Brief — Thursday, 25 June 2026

---

## 🔵 Microsoft Teams

- **Teams Live Events retires in 5 days (June 30).** After June 30 no new Live Events can be scheduled; existing ones continue through February 2027. Microsoft's recommended replacement is Teams Town Halls — if your org still runs Live Events, this needs immediate action.
- **Together mode is gone.** Microsoft completed the retirement of Together mode and custom scenes this month; gallery view is now the primary layout for all meetings.
- **macOS 13 (Ventura) devices will lose Teams desktop access.** Microsoft is enforcing macOS 14 (Sonoma) as the new minimum — affected users will lose access without warning at enforcement. Time to audit and upgrade.
- **Workplace Check-in via Wi-Fi now live.** A new opt-in feature lets managers see who is in the office based on company Wi-Fi detection. Off by default; tenants choose to enable, end users always retain the choice to decline.

---

## 🤖 Copilot & AI in Teams

- **Copilot Cowork is generally available as of June 16.** More than half of the Fortune 500 used it during the Frontier preview. Billing starts today via Copilot Credits (PayGo at $0.01/credit); Frontier-program tenants have a grace period until July 1. It runs on Anthropic Opus 4.8 and Sonnet 4.6, with a dedicated fine-tuned "Cowork 1" model coming soon. Cost management controls (spending limits at tenant/group/user level, usage alerts) are live.
- **Copilot features in Office apps now require a Copilot license.** Word, Excel, PowerPoint, and OneNote Copilot features are restricted to M365 Copilot USL holders from this month; Copilot Chat via the web remains broadly available.
- **Copilot Vision rolling out — analyses on-screen content during meetings.** Copilot can now read and summarise what a presenter is sharing on screen in real time. Review your AI governance policy before this lands: it may raise sensitivity concerns for confidential presentations.
- **In-meeting AI kill switch available.** Licensed organizers and presenters can toggle Meeting AI (Copilot, Facilitator, recap) off during live meetings — useful for HR, legal, or sensitive discussions.

---

## 🔗 Ecosystem & Integrations

- **Microsoft Facilitator AI Notes expanding to Teams Rooms for in-person meetings.** From June 2026, Teams Rooms on Windows will auto-generate AI notes, action items, and summaries for in-person sessions — even without remote participants. Review room policies and update signage for sensitive meeting spaces; align with legal and HR before rollout.
- **Power Platform backup retention slashed from 28 days to 7 days.** A quiet but high-risk change: Production environment backups now only go back one week. Any recovery need older than 7 days is no longer possible by default. Review BCDR strategies and third-party backup options immediately.
- **Nine new Copilot Cowork partner plugins now available:** Enosix, Harvey, LSEG, Miro, monday.com, Moodys, Morningstar, S&P Global Energy, and TeamsMaestro. Coming soon: Adobe, Atlassian, Box, Canva, Databricks, and others.

---

## 📽️ Meeting Room Equipment

- **MTR Windows update 5.6.137.0 released June 18.** This is the latest firmware for Teams Rooms on Windows — check your Pro Management Portal to ensure devices are updating to this release.
- **Human Interpreter Listening Mode coming to Teams Rooms on Windows** (June 2026 roadmap). Allows participants to listen to a live human interpreter during multilingual meetings — a useful addition for international or public-sector organisations.
- **Facilitator AI Notes in Teams Rooms** means in-person meetings in hardware-equipped rooms will be captured and summarised automatically for the first time, without any remote participant needed to trigger AI features.

---

## 🌐 Broader Collaboration Landscape

- **Slack's Agentforce 360 ("Slackbot as ultimate AI teammate") continues rollout.** Now available to Business+ and Enterprise+ customers since January 2026, Slackbot is evolving into a multi-agent orchestrator that can act across tools inside Slack channels — Salesforce's direct answer to Microsoft's agentic Teams push.
- **AI meeting assistants are now table stakes.** Real-time transcription, auto-generated summaries, and action-item extraction are no longer premium features across the industry — Zoom, Google Meet, Webex, and Teams all provide them at most price tiers. Differentiation is shifting to agent depth, cost controls, and compliance governance.
- **Microsoft positioned Copilot Cowork vs. Claude Cowork on cost.** Microsoft published internal testing claiming Copilot Cowork is 30–40% cheaper than Claude Cowork with a Microsoft 365 connector (both using Opus 4.8). The comparison methodology (internal Microsoft testing) warrants scrutiny, but it signals pricing competition between Anthropic's direct product and Microsoft's wrapper is now explicit.

---

## ⚡ Action Items & Things to Watch

- **⚠️ Act now: Teams Live Events retires June 30.** Five days left. Migrate any scheduled Live Events to Town Halls and brief internal event owners.
- **⚠️ Audit Power Platform environments.** The drop to 7-day backup retention is live — review Production environments storing critical data and update your BCDR docs and tooling before an incident forces the point.
- **👁️ Watch: Copilot Cowork billing and Frontier grace period.** If your org was in the Frontier program, billing kicks in July 1 — set spending limits and budget policies in the admin center before then. For new adopters, evaluate the credit estimator spreadsheet Microsoft published.

---

**Sources:**
- [What's New in Microsoft Teams – June 2026 (WheelHouse IT)](https://www.wheelhouseit.com/blog/whats-new-in-microsoft-teams-june-2026/)
- [Copilot Cowork is now generally available (Microsoft 365 Blog)](https://www.microsoft.com/en-us/microsoft-365/blog/2026/06/16/copilot-cowork-is-now-generally-available/)
- [June 2026 Top 10 M365 Message Center & Roadmap Updates (ChangePilot)](https://changepilot.cloud/blog/june-2026-top-10-microsoft-365-message-center-roadmap-updates)
- [Microsoft Teams Rooms MTR Update List: June 2026 (UC Lobby)](https://uclobby.com/2018/08/08/skype-room-systems-v2-update-list/)
- [June 2026 Microsoft 365 Update: Copilot Licensing & AI Recaps (Windows Forum)](https://windowsforum.com/threads/june-2026-microsoft-365-update-copilot-licensing-ai-recaps-teams-controls.426494/)
- [Slack turns Slackbot into 'the ultimate AI teammate' (No Jitter)](https://www.nojitter.com/digital-workplace/slack-turns-slackbot-into-the-ultimate-ai-teammate)
- [Microsoft Teams Will Pinpoint Employee Location (ad-hoc-news.de)](https://www.ad-hoc-news.de/boerse/news/ueberblick/microsoft-teams-will-pinpoint-employee-location-by-june-2026-as-workplace/69512797)
- [Teams Together Mode Retires June 2026 (TechRepublic)](https://www.techrepublic.com/article/news-microsoft-teams-together-mode-ends-june-2026/)
