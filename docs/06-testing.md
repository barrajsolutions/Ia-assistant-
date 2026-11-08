# Phase 6 — Test documentation (actual results, 2026-11-08)

| # | Test | Method | Result |
|---|---|---|---|
| T1 | Task extraction | Seeded 8 tasks in AI Tasks; queried by Status/Deadline in W1 manual run | ✅ Pass |
| T2 | Calendar retrieval | Google Calendar `list_events` Nov 8–22, America/Toronto | ✅ 25 events, recurring events expanded, correct EST offset (-05:00) after DST change |
| T3 | Briefing accuracy | Manual W1 run → CEO Reports « Daily briefing — Monday Nov 9 »; every fact cross-checked against source | ✅ Pass — found 3 real issues (TikTok errors, 0 scheduled posts, stale content calendar) |
| T4 | Voice: tomorrow's schedule | ElevenLabs LLM test BVM-1 | ✅ Pass (2 runs) |
| T5 | Voice: reminder request | BVM-2 | ✅ Pass (2 runs); run 1 time-statement inconsistency fixed by prompt |
| T6 | Voice: marketing summary, no invented numbers | BVM-3 | ✅ Pass (2 runs) |
| T7 | Voice: ambiguous task completion → clarification | BVM-4 | ✅ Pass (2 runs) |
| T8 | Voice: TTS-safe output | Inspection of run 1 | ❌ Arabizi found → fixed (Arabic script) → ✅ run 2 |
| T9 | Approval enforcement | Inspection: no tool used to create/schedule Metricool posts; Approvals DB untouched; registry forbids it; prompts forbid it | ✅ Pass (design + no writes made) |
| T10 | Marketing workflow preservation | Make scenarios 6824732/6828540 and data store 187388 read only; `lastEdit` unchanged (2026-10-29) | ✅ Pass |
| T11 | Make W6 blueprint | `validate_blueprint_schema` | ✅ Structurally valid. Module field validation needs the ElevenLabs keychain → at activation |
| T12 | Scheduled routines | `create_trigger` W1/W2/W5 | ⚠️ Created, but **no connectors attachable from API in this org** → paused |
| T13 | Reminder scheduling / postponement / duplicate prevention | Test task « TEST — reminder pipeline » (Reminder at Nov 9 10:00) | ⏳ Pending: runs at the first W2 sweep after you attach connectors. Expected: exactly one push, Reminder state → Sent, count 1, no repeat at 13:07 |
| T14 | Failure handling | Prompts: kill switch, `Integration unavailable`, partial runs | ⏳ Verify on first live runs (Automation Log) |
| T15 | Kill switch | Set registry row to Paused → run → expect « Skipped - paused » | ⏳ Run once after activation |
| T16 | Real phone call | — | ⛔ Not possible: no phone number (needs approval) |
| T17 | Lebanese speech recognition (ASR) on real voice | Browser test by Mohamad | ⏳ Task BFT-4 |

Credits used by tests: ≈ 500 ElevenLabs credits (8 text test turns). No calls placed. No purchases.
