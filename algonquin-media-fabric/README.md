# AC Media Fabric

Media production and delivery ecosystem for image, video, 3D, and 4DGS assets.
It owns asset lifecycle, metadata, rights, moderation, generation pipelines,
transcoding, delivery, and spatial media workflows. Compute capacity is consumed
through ACF/AC Cloud contracts; social publishing is consumed through AC
Fediverse contracts.

## Layout

- `apps/` — creator studio and administration clients
- `services/` — media API, registry, orchestration, metadata, delivery, moderation,
  and spatial services
- `pipelines/` — image, video, 3D, and 4DGS workflows
- `runtimes/` — pluggable generation and processing engines
- `connectors/` — cloud, compute, AI, and federated integrations
- `policies/` — safety, rights, and retention controls
