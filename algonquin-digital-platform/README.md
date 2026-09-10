# Algonquin Digital Platform

Umbrella architecture and contract repository for the Algonquin Digital
Platform. This repository contains the system context, ownership boundaries,
governance, security requirements, and shared contracts used by AC Cloud, AC AI,
ACF, AC Media Fabric, and AC Fediverse.

It intentionally contains no deployable product service. Product implementations
live in the sibling repositories under the workspace root.

## Shared contract domains

- `contracts/identity/` — normalized identities and roles
- `contracts/events/` — cross-system event envelopes
- `contracts/activitypub/` — federation-facing protocol contracts
- `contracts/spatial/` — spatial and temporal-spatial metadata
- `contracts/ai/` — model and inference references
- `contracts/compute/` — jobs, capacity, and worker references
- `contracts/media/` — assets, renditions, and media metadata
