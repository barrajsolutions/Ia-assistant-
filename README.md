# Barrage AI Manager

AI management layer for **Barrage Finance** (Quebec). It coordinates the existing tools — it does **not** replace the Claude → Make → Metricool content workflow, the Lovable website, or company systems (Salesforce is never connected).

| Folder | Content |
|---|---|
| `docs/01-audit.md` | What exists, what works, what's missing/blocked |
| `docs/02-architecture.md` | Diagram + design decisions |
| `docs/03-cost-comparison.md` | Free vs paid, monthly estimate |
| `docs/04-voice-manager.md` | ElevenLabs Barrage Voice Manager config, tests, call activation |
| `docs/05-lovable-review.md` | Website conversion & tracking recommendations |
| `docs/06-testing.md` | Test results |
| `docs/07-status-and-roadmap.md` | Completed / pending / blocked + roadmap |
| `docs/08-activation.md` | Turn the routines on, emergency pause |
| `manager/config.yaml` | IDs, schedules, reminder rules (no secrets) |
| `manager/prompts/` | The AI Manager's workflows (W1, W2, W5) + guardrails |
| `make/blueprints/` | Importable Make W6 voice-call relay (inactive until approved) |

**Control center:** Notion → Barraj Finance — Centre d'affaires → **BARRAGE FINANCE — AI HEADQUARTERS**.

**Rules:** no publishing, scheduling, purchases, client contact, production changes or calls without Mohamad's explicit approval · no client data · no secrets in this repo · every run logged · kill switch in the AI Agent Registry.
