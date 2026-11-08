# Cost comparison — what is free vs what needs spending

Current additional spending: **$0**. Nothing below has been purchased or activated.

> Price sources: official pages (elevenlabs.io, twilio.com) were **blocked by this session's network policy**, so figures come from web-search snippets of official and third-party pages (Nov 2026). Verify on the vendors' pricing pages before approving.

## Free (in place now)
| Item | Cost | Notes |
|---|---|---|
| AI Manager runs (Claude scheduled tasks W1/W2/W5) | $0 extra | Uses your existing Claude subscription usage (~19 runs/week). |
| Notion AI HQ | $0 | Existing workspace. |
| Google Calendar / Metricool / Lovable reads | $0 | Existing connectors, read-only. |
| ElevenLabs voice prototype (browser test) | existing credits | Text tests today used ≈ 500 credits total (8 runs). Browser voice tests consume agent minutes from your plan. |
| Push notifications | $0 | Claude app. |
| Make content workflow | $0 | Unchanged. |

## Requires approval / payment
| Item | Estimated cost | Status | Why |
|---|---|---|---|
| **Twilio account + Canadian local number** | ~1.15 USD/month (US local-number list price; CA price to confirm) | Needs approval (BFT-3) | ElevenLabs cannot place PSTN calls without an imported number. |
| Twilio outbound minutes to your iPhone | ~0.014 USD/min (third-party figure for US/Canada; confirm CA-mobile rate) | Needs approval | |
| ElevenLabs agent minutes | ~0.08 USD/min above included minutes (third-party sources); LLM billed separately but small (test turn ≈ 0.003 USD) | Depends on your plan (BFT-5) | Free tier reportedly ≈ 15 min/month; Starter (~6 USD/mo) ≈ 75 min. |
| HTML/CSS to Image Basic | 14 USD/month | Needs decision (BFT-2) | Free 50 images/month ≈ 8 carousels. |
| Make Core (optional, later) | paid tier | Not needed now | Only if you want instant voice-command writes (R4). |

## Estimated monthly cost once calling is on (estimate)
Assumptions: 22 weekday briefings × 2 min + ~10 reminder calls × 1 min = **~54 call-minutes/month**.

| Line | Low | High |
|---|---|---|
| Twilio number | 1.15 | 1.50 |
| Twilio minutes (54 × 0.014) | 0.76 | 1.50 |
| ElevenLabs minutes (if above plan) | 0 (covered by plan) | 4.32 (54 × 0.08) |
| **Total (USD/month)** | **≈ 2** | **≈ 7.5** |

Possible **$0 trial path** (to verify): a Twilio trial account comes with trial credit and can call **verified** numbers only (your own iPhone qualifies), with a short "trial account" message before each call. That would allow a real-call test without spending — still requires your approval to create the account.

## Not recommended
- A separate CRM: 1 lead so far; Notion + Lovable DB is enough. Re-evaluate at ~20 leads/month, and only with company-approved tools.
- Replacing Make or Metricool: both work; no business case.
