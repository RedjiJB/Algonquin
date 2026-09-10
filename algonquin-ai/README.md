# algonquin-ai

AC AI subsystem of the **Algonquin Digital Platform**: identity-aware AI access,
gateway and model routing, OpenWebUI/OpenCode integration, academic capabilities,
agents, SDKs, inference adapters, and web/desktop/mobile clients.

**Status:** pre-code scaffold. The architecture and governance documents are the
current source of truth; component directories mark ownership boundaries but do
not imply that implementation choices or service extraction are settled.

## Sibling workspace

Distributed campus compute (turning idle lab machines into an opportunistic
inference/compute pool) lives in a **separate** workspace, `algonquin-compute-fabric`,
not in this one. The two tracks develop in parallel and only integrate at Phase 9
(see `docs/architecture/05-roadmap-phases.md`). Keeping them separate means the
AI product doesn't get blocked by distributed-systems R&D, and the compute work
doesn't inherit the AI platform's security/compliance surface before it's ready to.

The complete ecosystem also includes sibling repositories for AC Cloud, AC Media
Fabric, AC Fediverse, and the umbrella cross-platform architecture. Integrations
use versioned APIs and contracts; AC AI never reads a sibling system's private
database or imports its internal code.

## How to read this workspace

| Folder | Contents |
|---|---|
| `docs/architecture/` | The technical design: gateway, identity/SSO, model routing, repo layout, phased roadmap |
| `docs/governance/` | The club/org taxonomy, identity & role model, agent action-risk levels |
| `docs/decisions/` | Architecture Decision Records (ADRs) — why things were decided a particular way |

## First vertical slice (target for the earliest working prototype)

1. `ac-ai-gateway` — the one service everything else depends on
2. Basic user authentication (dev-auth is fine before Entra is wired up)
3. One local model behind it
4. OpenAI-compatible API surface (`/v1/chat/completions`, `/v1/models`, etc.)
5. Customized OpenWebUI pointed at the gateway (never at a model provider directly)
6. OpenCode fork pointed at the same gateway
7. A basic usage/logging dashboard
8. Hardware-census prototype — lives in `algonquin-compute-fabric`, not here

If steps 1–7 work reliably, the rest of the roadmap is additive, not a rewrite.
