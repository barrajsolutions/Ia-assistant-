# Activation — turn the AI Manager on (5 minutes)

The 3 routines exist but are **paused** because this organization does not allow attaching connectors to routines through the API. Do this once:

1. Open **claude.ai → Code → Routines** (scheduled tasks).
2. For each routine below, open it → **Connectors** → add the listed connectors → Save → **Enable**.

| Routine | ID | Schedule (America/Toronto) | Connectors to attach |
|---|---|---|---|
| Barrage AI Manager — W1 Morning briefing | `trig_01D2LN29gCGkgXRYi6yD8UJe` | Mon–Fri 08:10 | Notion, Google Calendar, Metricool, ElevenLabs |
| Barrage AI Manager — W2 Reminder sweep | `trig_0151qVLiVjnmemQ5YgNHRqDf` | Mon–Fri 10:07, 13:07, 16:07 | Notion, Google Calendar, ElevenLabs |
| Barrage AI Manager — W5 Weekly CEO review | `trig_019dBQweBcyF7zDJg5FGsu8r` | Fri 15:40 | Notion, Google Calendar, Metricool, Make, ElevenLabs, Lovable |

3. Optional: press **Run now** on W2 — it should push « TEST — reminder pipeline » once (test T13) and write an Automation Log row.

If the routines UI does not offer connectors for scheduled runs, tell me in chat; fallback is running "W1" manually from the Claude app each morning (same prompt, same result).

## Emergency pause
Notion → AI HEADQUARTERS → AI Agent Registry → « ⛔ GLOBAL KILL SWITCH » → Status = **Paused**. Or disable the routines in claude.ai.
