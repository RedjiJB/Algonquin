# ACF System Overview

The first ACF implementation is a hardware-census system:

```text
ACF Worker
    |
    v
register machine and report authorized inventory/idle state
    |
    v
ACF Control API
    |
    v
Dashboard
```

## Current scope

- Discover CPU, RAM, GPU, VRAM, operating system, and network capabilities.
- Report health and idle state with a stable machine identity.
- Store current inventory and surface aggregate capacity.
- Measure worker overhead and validate heterogeneous machines.

## Explicitly deferred

- Running arbitrary jobs
- Campus-wide deployment
- Preemption and scheduling
- Model caching
- Multi-node or heterogeneous distributed inference
- Integration as an `algonquin-ai` model-routing backend

Those capabilities require authorization, security design, and evidence from the
census prototype before they become implementation work.
