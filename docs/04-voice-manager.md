# Barrage Voice Manager (ElevenLabs)

**Agent:** `agent_7101m69hm0k8fp5a9aq3mae6hc4x` — your existing « Mohamad - Personal Assistant (Arabic) », renamed and reconfigured (no new agent created).

## Try it now (free of telephony, uses agent minutes)
Open on your iPhone: `https://elevenlabs.io/app/talk-to?agent_id=agent_7101m69hm0k8fp5a9aq3mae6hc4x`
(or ElevenLabs dashboard → Agents → Barrage Voice Manager → Test AI agent). It runs on **TEST DATA** placeholders until the AI Manager feeds real data on a real call.

Say, one at a time:
1. «Shu 3ande bokra?»
2. «Zakkirne ba3d se3ten ta e2ra el report taba3 HTML to Image»
3. «Shu 3emelna bel marketing hal osbou3?»
4. «Khalles hal task taba3 el decision» (should ask you which one)
5. «Parle-moi en français» then «What do I have tomorrow?»

Then write a 1–5 score for Lebanese dialect and voice quality in Notion task BFT-4.

## Configuration applied
| Setting | Value |
|---|---|
| Name / tags | Barrage Voice Manager / Barrage Finance, Personal, Voice Manager |
| Language | Arabic (`ar`) default; built-in **language detection** on (switches to French/English) |
| Output | Lebanese colloquial in **Arabic script** (Arabizi removed — TTS mispronounces it) |
| First message | «مرحبا محمد، أنا الـ Barrage Voice Manager. عندك دقيقة؟» |
| Voice / TTS | existing voice `cjVigY5qzO86Huf0OWal`, `eleven_v4_turbo` (unchanged) |
| LLM | `deepseek-v41-flash` (unchanged; cheapest, passed tests) |
| Timezone | America/Toronto (current time injected) |
| Dynamic variables | `call_reason`, `briefing`, `tomorrow_schedule`, `marketing_week`, `open_tasks` |
| Data collection (post-call) | `reminder_requests`, `task_completions`, `decisions`, `callback_request`, `call_outcome`, `language_used` |
| Evaluation | no invented facts · confirmed before done · Lebanese dialect |
| Voicemail | detection on; leaves a 1-line Arabic message |
| Privacy | **audio recording OFF**, audio deleted, transcripts kept 30 days (needed for reconciliation) |
| Limits | concurrency 1, max 8 conversations/day, burst billing off |
| Phone numbers | **none** — outbound calling not possible yet |

Guardrails in the prompt: talks only to Mohamad; ends call if someone else answers; no financial advice; never approves/publishes/buys; never mentions client data; confirms the exact task ID before "done"; < 5 min calls.

## Test results (text simulation, no telephony)
| Test | Run 1 (Arabizi) | Run 2 (Arabic script) | Notes |
|---|---|---|---|
| BVM-1 « Shu 3ande bokra? » | ✅ | ✅ | Correct 2 items. Run 2 literally translated a French title ("ton plus grand actif" → «تون أكبر أصل»). |
| BVM-2 « Zakkirne ba3d se3ten » | ✅ | ✅ | Run 1 said "arba3 w tletin (4:20)" — inconsistent; run 2 gave a single clean time. |
| BVM-3 Marketing this week | ✅ | ✅ | No invented metrics. |
| BVM-4 « Khalles hal task » (ambiguous) | ✅ | ✅ | Asked which task. Run 2 drifted partly to MSA («موعده», «نوفمبر»). |

Suites: `suite_0201m6ygh41afjmrj24vyv91xeqf`, `suite_4901m6ygjr21e9fb3znj7gdwr1c5`. **Not yet tested:** real speech recognition of Lebanese dialect, voice quality on a phone line, latency on PSTN — these need your browser test (BVM-4 task) and then a real call.

## Real call architecture (prepared, not active)
```
W1 routine (08:10) → CEO Reports voice script
      → Make W6 relay (webhook 2998526, blueprint in make/blueprints/)
      → POST https://api.elevenlabs.io/v1/convai/twilio/outbound-call
           { agent_id, agent_phone_number_id, to_number (fixed), conversation_initiation_client_data.dynamic_variables }
      → Twilio Canadian number → your iPhone (~08:30)
      → post-call data collection → reconciled by W1/W2 into Notion
```
Retry rule (in `manager/config.yaml`): 1 retry after 15 min on no-answer, then push notification; max 3 calls/day; quiet hours 20:00–08:00; weekends only for P1.

## Activation steps (only after you approve BFT-3)
1. Create a Twilio account (trial first if you want $0 testing) and buy/verify one Canadian number.
2. ElevenLabs → Agents → Phone Numbers → Import Twilio number (Account SID + Auth Token entered **by you** in the ElevenLabs UI) → assign to Barrage Voice Manager. Note the `phone_number_id`.
3. Make → Keys → add an API Key keychain named `ElevenLabs` (header `xi-api-key`).
4. Import `make/blueprints/W6-voice-call-relay.blueprint.json`, set the webhook to 2998526, the keychain, `agent_phone_number_id` and your iPhone number in E.164. Leave scenario **inactive**.
5. One supervised test call (you on the line), then set `outbound_calling_enabled: true` in `manager/config.yaml`, switch the Registry row to Active and I update W1/W2 prompts to call the relay.
Note: activating W6 uses Make's 1st active-scenario slot (content scenarios are inactive between runs, so the 2-slot limit still fits).
