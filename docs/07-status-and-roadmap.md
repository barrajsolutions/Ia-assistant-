# Status & roadmap ($0 architecture) — 2026-11-08

## Working now
- Notion AI HQ (tasks, reports, log, registry + kill switch, integrations).
- AI Manager logic: kill switch, reminders, duplicate guard, new-lead counts — tested in the setup session.
- Routine safety: a real routine run failed closed when it could not reach Notion.
- Push notifications: sent from session and from a routine (receipt to be confirmed by Mohamad).
- Voice Manager prototype (browser), backed up.

## Needs Mohamad
1. Confirm test pushes arrived on iPhone.
2. Check Claude plan / Extra usage OFF; ElevenLabs usage billing OFF.
3. Attach connectors to the 3 routines; run the 3 proof runs (docs/08-activation.md).
4. Approve TikTok `.jpg` link fix (BFT-1).
5. Schedule videos #6–#10 (none queued in Metricool).
6. Optional: browser voice test (BFT-4).

## Blocked
- Routines without connectors (owner UI action).
- Real phone calls — no free permanent option (future, needs approval).
- Calendar-based reminders — not approved.
- Lead→appointment conversion — bookings in company Teams.
- Salesforce — company policy.

## Roadmap
| # | Item | Cost |
|---|---|---|
| R1 | Activation + 1 week monitoring of Automation Log | $0 |
| R2 | TikTok `.jpg` fix after approval; clean stale Calendrier rows | $0 |
| R3 | UTM links in bios (manual, no site change) | $0 |
| R4 | If push proves unreliable: Gmail self-email digest via existing Gmail connector (needs approval) | $0 |
| F1 | Future: real calls via Twilio (approval + spend) | paid |
