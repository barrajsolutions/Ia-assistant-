# Architecture — Barrage AI Manager

Design rule: **smallest reliable architecture**. One "brain" (Claude scheduled runs) + Notion as the shared state + existing tools untouched. No new servers, no new paid platform.

```mermaid
flowchart LR
  subgraph EXISTING["Existing (unchanged)"]
    direction TB
    CC["Claude chat\n(content production)"] -->|HTML/CSS| MK["Make scenarios\n6824732 / 6828540"]
    MK --> HCTI["HTML/CSS to Image"]
    MK --> DS[("Make Data Store 187388")]
    CC -->|"after APPROUVÉ"| MC["Metricool brand 6941045"]
    CL["Cloudinary"] --> CC
    MC --> SOC["Instagram · Facebook · LinkedIn · TikTok"]
    LV["Lovable website\n+ leads table"]
    GC["Google Calendar\n…94@gmail.com"]
  end

  subgraph NEW["New: AI management layer"]
    direction TB
    W1["W1 Morning briefing\nweekdays 08:10"]
    W2["W2 Reminder sweep\n10:07 · 13:07 · 16:07"]
    W5["W5 Weekly CEO review\nFri 15:40"]
    HQ[("Notion AI HQ\nAI Tasks · CEO Reports · Automation Log\nAgent Registry + KILL SWITCH · Integrations")]
    VM["ElevenLabs\nBarrage Voice Manager"]
    PUSH["Push notification\n(Claude app)"]
  end

  subgraph GATED["Prepared — needs your approval"]
    MKR["Make W6 relay\n(blueprint in repo)"]
    TW["Twilio CA number"]
    IP["Your iPhone"]
  end

  W1 & W2 & W5 -->|read| GC
  W1 & W5 -->|read only| MC
  W5 -->|read only| MK
  W5 -->|"aggregate counts only"| LV
  W1 & W2 & W5 <-->|"read / write HQ only"| HQ
  W1 & W2 & W5 --> PUSH
  W1 & W2 -->|"read call outcomes"| VM
  W1 -.->|"voice script (when enabled)"| MKR
  MKR -.-> VM
  VM -.-> TW -.-> IP
```

## Why not Make for the manager?
| Need | Make (current free plan) | Claude scheduled tasks |
|---|---|---|
| Scheduled runs | 2 active scenarios max | unlimited routines (plan usage) |
| Notion / Calendar access | no connection exists; needs new OAuth | connectors already authorized |
| Reasoning (prioritize, summarize, Lebanese script) | needs paid AI modules | native |
| Cost | 0 until limits, then paid tier | 0 extra (existing Claude subscription) |

Make stays the execution engine for **content rendering** (unchanged) and is the proposed **voice-call relay** (W6) because a Make keychain can hold the ElevenLabs API key outside GitHub and the relay hard-codes the only allowed phone number.

## Workflow mapping (your 6 workflows)
| Requested | Implemented as | State |
|---|---|---|
| W1 Morning CEO briefing | Routine W1 + CEO Reports | Built, tested manually, paused until connectors attached |
| W2 Intelligent reminder manager | Routine W2 + AI Tasks reminder fields | Built, paused |
| W3 Marketing operations monitor | Folded into W1 (daily) and W5 (weekly) | Built |
| W4 AI Manager task coordinator | AI Tasks Owner/Status + W2 escalation + Automation Log | Built |
| W5 Weekly CEO review | Routine W5 (Fri 15:40) | Built, paused |
| W6 ElevenLabs voice calling | Agent configured + Make relay blueprint | Prototype; calling needs approval |

## Voice command flow (no live tools during a call — by design)
1. W1 writes the Voice script + today/tomorrow/marketing/open tasks into CEO Reports.
2. (After approval) W6 relay passes them as `dynamic_variables` to the outbound call.
3. During the call the agent **only confirms** instructions; it cannot change anything.
4. After the call, ElevenLabs extracts structured fields (`reminder_requests`, `task_completions`, `decisions`, `callback_request`).
5. The next W1/W2 run reconciles them into Notion (creates reminders, closes the exact confirmed task, never approves anything).

Trade-off: a "Zakkirne ba3d se3ten" request is applied at the next W2 sweep (max ~3 h delay) rather than instantly. Upgrade path (roadmap R4): a Make webhook tool for instant writes once the Make plan allows a 3rd active scenario.

## Security controls
- Kill switch row checked first by every run.
- Write scope limited to 5 HQ databases; content, calendar, Metricool, Make content scenarios are read-only.
- Lovable: aggregate SQL only.
- Voice agent: talks only to Mohamad; no audio recording; 30-day transcript retention; max 8 conversations/day, concurrency 1, no burst billing.
- No secrets in GitHub; API keys go in a Make keychain.
- Every run logged in Automation Log.
