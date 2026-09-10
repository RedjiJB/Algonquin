# AC Cloud

Shared platform control plane for the Algonquin Digital Platform. AC Cloud
provides normalized identity, service discovery, policy distribution, storage,
messaging, secrets integration, observability, and cross-system events. It does
not own AI, compute, media, or social-domain behavior.

## Layout

- `services/` — shared APIs and control-plane services
- `platform/` — infrastructure abstractions and operational dependencies
- `connectors/` — explicit integrations with the other ecosystems
- `apps/` — operator and developer portals
- `infrastructure/` — local and future production deployment assets
