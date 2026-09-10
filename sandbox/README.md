# Local Sandbox

Shared local storage for artifacts that should not live in the ecosystem Git
repositories.

- `models/` — model files and manifests
- `datasets/` — datasets and manifests
- `media-assets/` — source and generated media
- `object-storage/` — local object-store data
- `caches/` — model, package, and pipeline caches
- `experiments/` — temporary experiments and result manifests
- `federation-fixtures/` — controlled ActivityPub interoperability fixtures
- `spatial/` — local spatial datasets and captures
- `runtime-data/` — databases, queues,, logs, queues, and other mutable state

This directory is intentionally not a Git repository. Each product repository's
ignore rules also exclude common large-artifact formats and runtime-data paths.
