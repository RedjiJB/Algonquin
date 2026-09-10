# ActivityPub Federation

AC Fediverse is the sole public ActivityPub security and interoperability edge.
Centralizing that boundary avoids five inconsistent implementations of HTTP
signatures, discovery, delivery, moderation, remote media, and abuse controls.

## Internal publication flow

```text
AC AI or AC Media Fabric
          |
          v
authenticated internal publication request
          |
          v
AC Fediverse policy + moderation + object mapping
          |
          v
local actor outbox
          |
          v
signed ActivityPub delivery
```

AC Cloud provides identity, secrets, events, and observability. ACF may process
background jobs. Neither exposes ActivityPub endpoints.

## Required controls before public federation

- HTTP signature and actor-key verification
- SSRF-resistant discovery and remote-media retrieval
- Durable inbox/outbox processing with idempotency and bounded retries
- Instance, actor, domain, and content federation policy
- Rate limits, abuse reporting, moderation, appeals, and audit trails
- Spatial precision reduction and private-location stripping
- Incident response, peer blocking, key rotation, and recovery procedures
