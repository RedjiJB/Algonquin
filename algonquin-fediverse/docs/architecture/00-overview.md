# AC Fediverse Overview

```text
apps -> shared product services -> durable inbox/outbox
                                  -> ActivityPub gateway
                                  -> remote federation

media -> AC Media Fabric
AI assistance -> AC AI
shared platform -> AC Cloud
background work -> ACF
```

Only the ActivityPub gateway communicates with remote servers. Internal products
and ecosystems publish through authenticated internal APIs and versioned events.
