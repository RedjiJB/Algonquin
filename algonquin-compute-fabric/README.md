# algonquin-compute-fabric

Parallel research and engineering workspace for the Algonquin Compute Fabric
(ACF). Its first milestone is hardware census and telemetry, not distributed
inference.

## Initial vertical slice

1. `acf-worker` registers an authorized machine.
2. The worker reports CPU, RAM, GPU, VRAM, operating system, network, and idle
   state.
3. The control API stores and serves the inventory.
4. The dashboard presents current and aggregate capacity.
5. Benchmarks validate reporting overhead and hardware capability.

This repository remains independent of `algonquin-ai` until the main platform's
Phase 9 merge point. Do not make the AI gateway depend on ACF during the early
research phases.

Within the full Algonquin Digital Platform, ACF is a general compute substrate for
AC AI, AC Media Fabric, AC Fediverse background work, and AC Cloud platform jobs.
Callers submit capability-based jobs; they do not select worker machines directly.

## Repository map

| Path | Responsibility |
|---|---|
| `worker/acf-worker/` | Cross-platform inventory and telemetry agent |
| `control-plane/api/` | Registration, inventory, health, and query API |
| `dashboard/` | Operator-facing capacity view |
| `benchmarks/` | Repeatable hardware and overhead measurements |
| `docs/` | Architecture, security boundaries, and research notes |
| `infrastructure/docker/` | Local development environment |
