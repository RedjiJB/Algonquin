# Repository Layout (target, full platform)

This is the eventual full layout for the main-track platform once it's past
the prototype stage. Not all of it should be built now — see "what to build
first" below.

```text
algonquin-ai/
│
├── apps/
│   ├── webui/               # OpenWebUI downstream fork
│   ├── code/                # OpenCode downstream fork
│   └── admin/
│
├── services/
│   ├── gateway/              # MAIN SERVICE — build first
│   ├── identity/             # build second
│   ├── model-router/         # build third
│   ├── policy/
│   ├── usage/
│   ├── files/
│   ├── rag/
│   └── telemetry/
│
├── inference/
│   ├── general/
│   ├── code/
│   ├── embeddings/
│   └── rerank/
│
├── sdk/
│   ├── python/
│   ├── typescript/
│   └── cli/
│
├── infrastructure/
│   ├── docker/
│   ├── kubernetes/
│   ├── terraform/
│   └── monitoring/
│
├── policies/
│   ├── model-registry/
│   ├── routing/
│   ├── quotas/
│   └── data-classification/
│
└── docs/
    ├── architecture/
    ├── security/
    ├── privacy/
    ├── governance/
    └── operations/
```

## What to build first

Only three of these folders matter for the first vertical slice:

1. `services/gateway/` — the gateway itself
2. `apps/webui/` — a thin OpenWebUI fork pointed at the gateway
3. `apps/code/` — a thin OpenCode fork pointed at the gateway

`services/identity/` and `services/model-router/` can start as code *inside*
the gateway service and get extracted later once there's a real reason to run
them independently (separate scaling needs, separate team ownership). Don't
pre-split services that don't have a concrete reason to be separate yet — it
just adds deployment and networking overhead for no benefit at this stage.

`sdk/`, `inference/`, `rag/`, `files/`, `telemetry/`, and everything under
`policies/` are Phase 4+ concerns (see `05-roadmap-phases.md`). Creating empty
folders for them now is fine; putting real code in them now is premature.

## Note on OpenWebUI/OpenCode forks

Keep these as thin downstream forks, not hard forks:

```text
upstream/open-webui  →  algonquin/open-webui
upstream/opencode    →  algonquin/opencode
```

This keeps upstream security fixes mergeable. Resist the urge to restyle
deeply before the gateway/identity/routing design is settled — those three
determine whether this becomes a real platform or just another OpenWebUI
deployment, and restyling first means redoing UI work once the backend
contract changes.
