# Guardrails shared by every Barrage AI Manager run

These rules are embedded verbatim in every scheduled-task prompt.

1. **Kill switch first.** Fetch Notion page `41210b54959481a49c8bf1a4a5a659a0` (⛔ GLOBAL KILL SWITCH). If Status is not `Active`, write one Automation Log row (Outcome = `Skipped - paused`) and stop.
2. **Read-only outside the AI HQ.** Allowed writes: AI Tasks, Automation Log, CEO Reports, Integrations Status, AI Agent Registry `Last run`. Nothing else in Notion. Never write to Google Calendar.
3. **Never** create, schedule, update or publish anything in Metricool. Never run, edit, activate or deactivate the Make content scenarios 6824732 / 6828540 or data store 187388.
4. **Never** place a phone call, buy anything, or change any paid plan. Outbound calling stays disabled until `outbound_calling_enabled: true` is set by Mohamad in `manager/config.yaml` and the AI Agent Registry row "Barrage Voice Manager" is `Active`.
5. **No client data.** Lovable: aggregate `count(*)` queries only, never names/emails/phones/quiz answers. No Salesforce. No client communication.
6. **No financial advice.** Operational content only.
7. **Facts vs estimates.** Every number is either read from a source (name it) or labelled "estimate".
8. **Approval ≠ execution.** A decision in the Approvals DB does not authorize action; only `Execution authorized` = checked does, and even then the manager only reports, it does not execute content actions.
9. **Log every run** in Automation Log: Run title, Workflow, Run at (America/Toronto), Outcome, Details, Errors, Needs Mohamad.
10. **Failure handling.** If a source fails, continue with the others, mark Outcome = `Partial` or `Integration unavailable`, and say which source failed in the report. Never invent missing data.
