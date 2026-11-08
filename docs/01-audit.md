# Phase 1 — Existing System Audit (verified 2026-11-08)

Every row below was checked live through a connected tool unless marked otherwise. Nothing in the existing content workflow was modified.

Legend: ✅ Existing & working (tested) · 🟡 Exists, not verified · ⬜ Missing · ⛔ Blocked by permissions · 💲 Requires approval or payment

| Component | Status | Evidence (what was actually checked) |
|---|---|---|
| Make — Carrousel scenario 6824732 | ✅ | On-demand, inactive between runs, 9 executions, 0 errors. Modules: 5× HTML/CSS to Image → Data Store. |
| Make — Citation scenario 6828540 | ✅ | On-demand, 10 executions, 0 errors. |
| Make — Data Store 187388 « Carrousels Barraj Finance » | ✅ | 8 records (latest 2026-11-03 « maladies graves »). |
| Make — connections | ✅ | HCTI-Barraj finance (used by both scenarios), Make AI Provider, Placid (unused). **No Notion, no Google Calendar, no ElevenLabs connection.** |
| Make — webhook 2998526 « Barrage Finance - Claude » | 🟡 | Enabled, API-key protected, attached to no scenario. |
| Make — plan | 💲 | Free: 1,000 credits/month, **max 2 active scenarios** (from Notion « Outils et coûts »). Too small to host 5+ scheduled workflows. |
| Make — team « Mohamad's space » (3317844) | ✅ | Empty. |
| HTML/CSS to Image | 💲 | Free tier 50 images/month; ~30 used on Oct 29. Basic = 14 USD/month (from Outils et coûts). |
| Claude ↔ Metricool connector | ✅ | Brand 6941045 « barrajfinance » (IG, FB, LinkedIn, TikTok). Read scheduled/published posts OK. |
| Metricool → TikTok photo posts | ❌ Failing | 5 posts Nov 2–7 in ERROR: *« The 'image/png' type is not allowed, use 'image/jpeg' or 'image/webp' »*. |
| Metricool scheduled queue | ⚠️ | **0 posts scheduled Nov 8–22**, while Google Calendar plans videos #6–#15 (Nov 9–20). |
| Make → Metricool | ⛔/💲 | Make's Metricool module needs Metricool Advanced (noted in Outils et coûts). Claude's connector is **not** callable from Make. |
| Cloudinary | 🟡 | No connector in this session; documented in Notion (account cblonrgl). Not needed by the manager. |
| Notion | ✅ | « Barraj Finance — Centre d'affaires » hub with Approvals, Calendrier de contenu, Idées de contenu, Outils et coûts. « My Tasks » (Home) is an empty template without a queryable data source. |
| Notion — Calendrier de contenu | ⚠️ | Not updated since Nov 1; 6 past rows still « Programmé ». |
| Google Calendar | ✅ | `mohamadbarraj94@gmail.com` (America/Toronto) + Canadian holidays. 25 events Nov 8–22 read. Note: calendar account (…94) ≠ Notion/Make account (…27). |
| ElevenLabs — agents | ✅ | 3 agents: « Mohamad - Personal Assistant (Arabic) » (reused → Barrage Voice Manager), « Léa » website widget, « Receptionist (Multilingual) ». 0 custom tools, 0 secrets listed. |
| ElevenLabs — phone numbers / Twilio | ⬜ | **0 phone numbers**. No Twilio or SIP trunk imported. |
| ElevenLabs — plan, minutes, quota | 🟡 | Not exposed by the connector. Must be read in the dashboard (task BFT-5). |
| ElevenLabs — privacy | ⚠️→✅ | Agent was recording audio with unlimited retention; changed to no audio, 30-day transcripts. |
| Lovable website « Conseiller Securite Financiere » | ✅ | Published, bilingual FR/EN, TanStack Start + Lovable Cloud (Supabase). 13 service pages, quiz, booking form (Teams), privacy page. |
| Lovable — lead storage | ✅ | Table `leads` (source quiz/booking, topic, UTM, consent). **1 lead total** (week of Oct 26, quiz). |
| Lovable — lead notification | ⬜ | Server function only inserts the row; **no email/notification** to you. |
| Lovable — analytics | ✅ | Oct 30–Nov 8: 30 visitors, 32 pageviews, 87% mobile, **100% « Direct »** source, 1 lead. |
| Lovable — GitHub integration | 🟡 | Not exposed by the Lovable connector; no Lovable repo is visible to this session. |
| GitHub | ✅ | `barrajsolutions/ia-assistant-` was empty; now holds this system's docs/prompts/blueprints. No new repository created. |
| Salesforce (company) | ⛔ | Not connected, by policy. Not needed: at 1 lead, Notion + Lovable DB is sufficient; no separate CRM recommended now. |
| Claude scheduled tasks (routines) | ✅/⚠️ | Created (W1, W2, W5) but **this org cannot attach connectors to them via API** → paused until you attach connectors in the claude.ai routines UI. |

## Key operational findings
1. **TikTok photo posts fail silently** — 5 failures in one week.
2. **This week's content isn't scheduled** — 10 planned videos, 0 queued in Metricool.
3. **Leads are not notified** — a booking request could sit unseen.
4. **Website traffic has no attribution** — 100% « Direct »; Instagram bio link has no UTM.
5. **Make free plan cannot host the manager** — 2 active scenarios max; and it has no Notion/Calendar access. The manager therefore runs on Claude scheduled tasks, which already have these connectors, at no extra cost.
6. **Voice calling needs a phone number** — ElevenLabs does not provide PSTN numbers; a Twilio (or SIP) number must be imported.
