# Algonquin Digital Platform

Monorepo for the Algonquin Digital Platform. The platform is composed of five
connected systems with shared contracts and platform services:

```text
Algonquin Digital Platform
├── algonquin-cloud              AC Cloud — shared control plane and infrastructure
├── algonquin-ai                 AC AI — gateway, clients, models, and agents
├── algonquin-compute-fabric     ACF — campus compute and hardware fabric
├── algonquin-media-fabric       AC Media Fabric — image, video, 3D, and 4DGS
└── algonquin-fediverse          AC Fediverse — social, media, communities, blogs
```

`algonquin-digital-platform/` contains the cross-system architecture and
versioned contracts. `sandbox/` is local-only storage for models, datasets, and
experiments; it is intentionally not a product subsystem.

## Cross-system principles

- AC Cloud provides shared identity, service discovery, policy, storage,
  messaging, and observability.
- AC AI, ACF, and AC Media Fabric remain independently deployable systems.
- AC Fediverse owns ActivityPub federation; other systems integrate through
  explicit contracts rather than embedding federation logic everywhere.
- Every system supports spatial metadata and spatial-aware resources through the
  shared `contracts/spatial` definitions.
- Large artifacts and model weights stay outside Git.

## Repository map

| Path | Role |
|---|---|
| `algonquin-digital-platform/` | Umbrella architecture, governance, and shared contracts |
| `algonquin-cloud/` | Common platform control plane |
| `algonquin-ai/` | AI platform and gateway |
| `algonquin-compute-fabric/` | Compute inventory, scheduling, and runtimes |
| `algonquin-media-fabric/` | Media asset and generation pipelines |
| `algonquin-fediverse/` | ActivityPub applications and federation |
| `sandbox/` | Unversioned local models, data, and experiments |

## Current implementation posture

This is an architecture-first scaffold. Component directories establish ownership
boundaries; implementation technology is intentionally undecided. Build vertical
slices in dependency order, starting with AC Cloud foundations and the AC AI
gateway, while ACF, Media Fabric, and Fediverse develop against shared contracts.

See `algonquin-digital-platform/docs/architecture/` for the system map and
integration rules.
