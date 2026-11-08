# Test results (actual)

## Round 2 — 2026-11-08 (approved safe tests)
| # | Test | Where | Result | Evidence |
|---|---|---|---|---|
| R1 | Push notification reaches iPhone | Setup session → Claude app | ⏳ sent (test #1 16:42, #3 16:47); **awaiting Mohamad's confirmation** | PushNotification « Mobile push requested » |
| R2 | Push from a routine | Routine W2 manual fire | ⏳ sent (test #2 16:43); awaiting confirmation | Routine session cse_01BJ3ec8YpTDm8S4c7AgdoMJ called PushNotification |
| R3 | Connectors inside routines | Routine W2 manual fire | ❌ **None available** — routine found no Notion tools | Same session transcript |
| R4 | Kill switch fail-closed when Notion unreachable | Routine W2 | ✅ Stopped, 0 reads, 0 writes | Final reply « KILL SWITCH: run skipped (Notion unavailable…) » |
| R5 | Kill switch Paused → no execution | Setup session executing G0 | ✅ Read Status=Paused, wrote only the skip log, nothing else; restored Active | Automation Log « W2 skipped — KILL SWITCH TEST » |
| R6 | Reminder delivery | Setup session executing W2 logic | ✅ BFT-8 found due, updated Sent/Last reminded/count=1, one push | Log « W2 … 16:47 — REMINDER TEST » |
| R7 | Duplicate prevention | Second sweep 1 min later | ✅ 0 due → no push | Log « W2 … 16:48 — DUPLICATE TEST » |
| R8 | New-lead alert without PII | Lovable aggregate query | ✅ last 24 h: 0 rows; since Oct 1: quiz=1 (count only) | — |
| R9 | Notion rows-mode date filter | Setup session | ❌ **Bug found**: datetime filter returned 0 rows for a due reminder → prompts changed to filter by state and compare times explicitly | Log 16:47 details |
| R10 | TikTok PNG fix | Vendor docs | ✅ HCTI docs: `.jpg` extension converts on the fly. Live URL check blocked by session network | docs.htmlcsstoimage.com |
| R11 | Agent backup | ElevenLabs read | ✅ elevenlabs/backup/*.json + system prompt | version agtvrsn_9401m6ygjk4te5pb9rkskj23y6fz |

**Not yet proven inside a routine with real data** (needs connectors attached): kill switch Paused path, full W1 briefing, W2 reminder push, duplicate guard. These are the 3 activation tests in docs/08-activation.md.

## Round 1 — 2026-11-08
Manual W1 briefing from live data ✅ · Voice commands BVM-1..4 ✅ (2 runs each; Arabizi → Arabic script fixed) · Make W6 blueprint structurally valid ✅ · Content workflow untouched ✅.
