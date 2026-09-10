# Club / Team Structure

## Note on source inconsistency

The source planning conversation names the club's functional teams two
slightly different ways in two different places. Worth flagging so it doesn't
get carried forward inconsistently:

- Earlier framing: Platform Engineering, AI/ML, Cybersecurity & Privacy,
  UX/Accessibility, Education, Research, Operations/Partnerships
- Later framing (attached to the actual build roadmap): Platform Engineering,
  AI/ML, Applications, UX, Academic Technology, Security & Privacy,
  Distributed Systems → ACF

**Recommendation:** use the second one — it's the version tied to the actual
phased roadmap, and it explicitly places compute/distributed-systems work as
a sub-team rather than a separate club.

## Recommended structure

```text
ALGONQUIN AI CLUB

Platform Engineering     — gateway, identity, model router, infra
AI/ML                     — model evaluation, RAG, agents, benchmarking
Applications              — OpenWebUI/OpenCode forks, desktop/mobile clients
UX                        — design, accessibility
Academic Technology       — Brightspace integration, course tooling, faculty liaison
Security & Privacy        — policy engine, data classification, auth review
Distributed Systems       — sub-team, owns algonquin-compute-fabric workspace
```

## Why not two clubs immediately

Two brand-new clubs competing for the same small pool of interested students
splits membership before either has traction. Keep Distributed Systems as a
division of the AI Club. If it grows large enough on its own merits (it has a
scope well beyond AI — HPC, cloud/edge computing, clustering, storage,
virtualization, Kubernetes, distributed databases, research computing) it can
spin out into its own club later, with the relationship becoming:

```text
AI CLUB  ──consumes compute──▶  COMPUTE CLUB  ──builds infra──▶  Compute Fabric
```

## Positioning against existing College AI offerings

Algonquin already provides Microsoft Copilot and has an institutional AI
framework, an AI Assessment Scale, and an AWS-supported AI Accelerator Hub.
The Students' Association can reject a club that duplicates an existing
College/SA service, so the pitch should not be "an alternative to Copilot."
It should be: a student-built, open, local-first AI **engineering and
learning platform** — local model experimentation, APIs students can build
against without buying their own vendor credits, coding agents, AI
infrastructure training, and open-source engineering — that complements
rather than competes with the College's existing AI direction.
