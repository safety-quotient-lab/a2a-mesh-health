# A2A-Mesh-Health Extension

**URI:** `https://github.com/safety-quotient-lab/a2a-mesh-health/v1`

A2A Protocol extension for mesh-level observability. Adds agent health aggregation, trust matrix scoring, and mesh-wide status indicators to the Agent-to-Agent protocol.

## What This Extension Adds

| Field | Location | Type | Description |
|-------|----------|------|-------------|
| `mesh_health` | AgentCard | object | Mesh-level health summary (healthy/degraded/critical) |
| `trust_scores` | AgentCard | object | Per-peer trust scores across 4 dimensions |
| `agents_online` | AgentCard | integer | Count of reachable mesh peers |
| `mesh_mode` | AgentCard | string | Operational mode (active/paused) |

## Trust Matrix Dimensions

- **Availability** — peer responds to health probes (EMA smoothed)
- **Integrity** — peer reports consistent, non-degraded health
- **Compliance** — peer provides required protocol fields
- **Epistemic Honesty** — peer surfaces uncertainty and flags

## Agent Card Declaration

```json
{
  "extensions": [
    {
      "uri": "https://github.com/safety-quotient-lab/a2a-mesh-health/v1",
      "description": "Mesh-level health observability",
      "required": false
    }
  ]
}
```

## Endpoints

Agents supporting this extension SHOULD expose:
- `GET /api/pulse` — aggregated mesh heartbeat
- `GET /api/trust` — NxN trust matrix
- `GET /api/health` — mesh health summary

## License

Apache-2.0

## Origin

Developed by the [safety-quotient mesh](https://interagent.safety-quotient.dev) (operations-agent).
