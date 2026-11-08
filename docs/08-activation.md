# Safe activation — exact steps

All 3 routines are **paused** and currently have **no connectors** (verified by a test run). Nothing runs until you finish these steps.

## A. Before anything (account checks, 5 min)
1. **claude.ai → Settings → Usage** (or Billing): note your plan (Pro / Max) and its routine/scheduled-task daily limit if shown. Confirm **Extra usage = OFF**.
2. **iPhone → Settings → Notifications → Claude**: Allow, Lock Screen + Banners on. Confirm you received the test pushes of Nov 8 (#1, #2 « W2 reminder sweep did not run… », #3 « BFT-8 TEST »).
3. **ElevenLabs → Subscription**: confirm plan; usage-based billing OFF.

## B. Attach connectors (claude.ai → Code → Routines → open each routine → Connectors)
| Routine | Attach |
|---|---|
| Barrage AI Manager — W1 Morning briefing | Notion, Google Calendar, Metricool, Lovable |
| Barrage AI Manager — W2 Reminder sweep | Notion, Google Calendar, Lovable |
| Barrage AI Manager — W5 Weekly CEO review | Notion, Google Calendar, Metricool, Lovable (Make optional) |
Do **not** enable yet. If the routine screen has no connector option, stop and tell me (fallback below).

## C. Three proof runs — do them on Saturday or Sunday (no scheduled runs → stays ≤ 3 runs/day)
1. **Kill switch test** — Notion → AI Agent Registry → « ⛔ GLOBAL KILL SWITCH » → Status **Paused**. Open W2 → **Run now**.
   Pass = Automation Log gets « W2 skipped » (Outcome *Skipped - paused*), push « KILL SWITCH: run skipped », **no** BFT-8 change.
   Then set the kill switch back to **Active**.
2. **Briefing test** — W1 → **Run now**.
   Pass = new CEO Reports « Daily briefing — … », one Automation Log row « W1 … », push « Barrage briefing … ».
3. **Reminder test** — W2 → **Run now**.
   Pass = push « Barrage reminders: BFT-8 TEST — reminder pipeline », BFT-8 Reminder state = *Sent*, count = 1.
   Duplicate guard = the next scheduled W2 (Monday 12:07) must **not** remind BFT-8 again.
Send me « tests done » — I will read the Automation Log and routine transcripts and confirm pass/fail with evidence before you enable.

## D. Enable (only after C passes)
Enable W1, W2, W5 in the routines page. Schedules: W1 Mon–Fri 08:10 · W2 Mon–Thu 12:07 & 16:07 · W5 Fri 15:40 (also does Friday's reminders). Max 3 runs/day.

## Emergency pause
Notion kill switch → Paused (all runs stop at their first step) — or disable the routines in claude.ai.

## Fallback if routines cannot get connectors
Open the Claude app each morning and paste the W1 prompt from `manager/prompts/W1-morning-briefing.md` (this chat already has the connectors). Same output, manual trigger, $0.
