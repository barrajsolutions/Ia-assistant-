# Status & roadmap

## ✅ Completed
- Full audit of Make, Metricool, Notion, Google Calendar, ElevenLabs, Lovable, GitHub (docs/01-audit.md).
- Notion **BARRAGE FINANCE — AI HEADQUARTERS** under Centre d'affaires: 10 sections, 5 new databases (AI Tasks, Automation Log, AI Agent Registry with kill switch, CEO Reports, Integrations Status); reuses existing Approvals, Calendrier de contenu, Idées, Outils et coûts.
- 8 audit tasks + 14 integration statuses + 8 agent registry rows seeded.
- First real **Morning briefing** (Mon Nov 9) generated from live data and logged.
- ElevenLabs agent reused and configured as **Barrage Voice Manager**; privacy hardened; 4 command tests pass.
- AI Manager prompts W1/W2/W5 written (manager/prompts) and created as Claude scheduled tasks.
- Make W6 voice-call relay blueprint (validated), cost comparison, website review.

## ⏳ Pending — waiting on you
| ID | Action | Effort |
|---|---|---|
| A1 | **Attach connectors to the 3 routines and switch them on** (see docs/08-activation.md) | 5 min |
| BFT-4 | Test the voice agent in the browser, score dialect 1–5 | 10 min |
| BFT-1 | OK/no to JPEG export for TikTok | reply |
| BFT-2 | HTML/CSS to Image: stay free or Basic 14 USD | reply |
| BFT-3 | Approve or decline Twilio (trial first?) | reply |
| BFT-5 | Read ElevenLabs plan/minutes in dashboard | 2 min |
| BFT-6 | Approve any website item L1–L6 | reply |
| — | Schedule videos #6–#10 in Metricool (planned this week, none queued) | your content session |

## ⛔ Blocked
- Real outbound calls — no phone number (approval + small spend).
- Routines' data access — connectors must be attached in the claude.ai UI (API not permitted for this org).
- Salesforce — company policy (by design).
- Lead→appointment conversion — bookings live in company Teams; not measurable without L3.
- Lovable ↔ GitHub link — not exposed to this session.

## Roadmap (prioritized)
| # | Item | Depends on | Cost |
|---|---|---|---|
| R1 | Turn on W1/W2/W5; watch Automation Log for 1 week; tune noise | A1 | $0 |
| R2 | Fix TikTok JPEG in content production; clean stale Calendrier de contenu rows | BFT-1 | $0 |
| R3 | Twilio trial → 1 supervised call → enable 08:30 weekday call | BFT-3, BFT-4 | $0 trial, then ≈ 2–7.5 USD/mo |
| R4 | Instant voice commands (ElevenLabs webhook tool → Make → Notion) | R3, Make slot | $0–Make Core |
| R5 | UTM links everywhere + new-lead alert (aggregate) | BFT-6 | $0 |
| R6 | Self-serve Microsoft Bookings + appointment KPI | company approval | $0 |
| R7 | Monthly cost review in W5 (Outils et coûts) | — | $0 |
