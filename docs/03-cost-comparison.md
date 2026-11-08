# Cost — $0 additional-cost architecture

**Budget rule (owner decision, 2026-11-08): $0 additional spend.** Only existing subscriptions and their included capabilities. No new paid services, upgrades, or trials that require payment details.

## Active dependencies — all $0 extra
| Component | Uses | Limit that matters | Fits? |
|---|---|---|---|
| Claude routines W1/W2/W5 | Existing Claude subscription | Daily routine-run cap (reported 5/day Pro, 15/day Max; one report of 3/day) + normal usage limits | ✅ Lean schedule = **max 3 runs/day** (Mon–Thu: W1 + 2×W2; Fri: W1 + W5) |
| Push notifications | Claude app | — | ✅ |
| Notion AI HQ | Existing workspace | SQL query mode limited on non-Business plans | ✅ Routines use rows mode only |
| Google Calendar | Existing account, read-only | — | ✅ |
| Metricool | Existing connector, read-only | — | ✅ |
| Lovable | Existing project, aggregate `count(*)` + analytics reads | Reads don't use Lovable message credits | ✅ |
| ElevenLabs Voice Manager | Existing plan, browser link only | Plan's included minutes/credits (check dashboard) | ✅ if used occasionally |
| Make | Not used by the manager | 1,000 credits, 2 active scenarios | ✅ unchanged |
| HTML/CSS to Image | Unchanged content workflow; `.jpg` link = on-the-fly conversion of existing image | Free 50 images/month | ✅ (whether `.jpg` conversion counts as a new render is unverified — watch the HCTI dashboard) |

Measured: one routine run that stopped at the kill switch reported ≈ 0.09 USD *list-price equivalent* of model usage — this is drawn from the subscription allowance, **not billed**, unless "extra usage" is enabled on the Claude account.

## Usage/cost risks to watch
1. **Claude "extra usage" setting** — if enabled, runs beyond plan limits could be billed. Must be OFF (manual check).
2. **Routine daily cap** — manual "Run now" tests count toward the cap; do activation tests on a day with no scheduled runs.
3. **ElevenLabs** — browser voice tests consume plan minutes; usage-based billing must be OFF (manual check).
4. **HCTI free quota** — content volume can exceed 50 images/month; the manager reports usage weekly.

## Future possibilities (NOT active, NOT dependencies)
| Option | Cost | Notes |
|---|---|---|
| Real outbound phone calls via Twilio number + ElevenLabs | ≈ 1.15 USD/mo number + ≈ 0.014 USD/min (secondary sources) + ElevenLabs minutes beyond plan | Only option for true PSTN calls. Requires explicit owner approval. |
| Twilio free trial (no card, ≈ 15 USD credit, 30 days, verified numbers only, trial message before calls) | $0 for 30 days | Temporary test only; ElevenLabs compatibility with trial numbers unverified. Requires owner approval. |
| HTML/CSS to Image Basic | 14 USD/mo | Only if volume > 50 images/month. |
| Make paid tier | paid | Only for instant voice-command writes. |
