# InfinityNet ISP Ultimate 14.0 — AI NOC Intelligence

Developer: **خليل الخليل | Khalil Al Khalil**

## AI capabilities
- AI NOC Copilot for current network assessment.
- Root-cause hypotheses grounded in current incidents, Guardian events, outages, topology and telemetry.
- Safe recommended remediation steps; no direct destructive execution by the model.
- Action proposals are persisted separately and require approval.
- Supports local Ollama or OpenAI-compatible endpoints through environment variables.
- Deterministic local fallback when no external AI provider is configured or reachable.
- AI feedback loop (`useful`, `not_useful`, `wrong`) for future evaluation.
- Optional background AI worker for automatic incident analysis.

## API
- `POST /api/ai/analyze`
- `GET /api/ai/insights`
- `POST /api/ai/insights/{id}/feedback`
- `GET /api/ai/health`

All endpoints require `X-Admin-Token`.

## Safety
AI does not receive database credentials and is instructed not to invent facts. Sensitive-looking values are redacted before the AI context is assembled. Proposed high-impact actions remain approval-gated.
