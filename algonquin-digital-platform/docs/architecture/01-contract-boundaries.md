# Contract Boundaries

## Shared identity

Every internal request carries one normalized subject identity plus service
identity. Human roles originate in the institutional identity system and are
mapped by AC Cloud's identity broker. Services authorize scopes locally.

## Shared events

Cross-system events use versioned envelopes with an event id, type, timestamp,
producer, subject, schema version, trace context, classification, and optional
spatial context. Consumers must tolerate additive fields and process events
idempotently.

## Spatial contract

Spatial data uses stable place/scene identifiers, coordinate-reference metadata,
precision, provenance, visibility, and retention classification. Public
federation never receives precise private location by default.

## ActivityPub contract

AC Fediverse owns HTTP signatures, actor discovery, inbox/outbox processing,
delivery, retries, remote-media handling, federation policy, and abuse controls.
Other ecosystems request publishing or attach approved objects through internal
APIs; they do not independently expose ActivityPub endpoints.

## Compute contract

ACF accepts declarative jobs describing resource requirements, artifacts,
isolation, preemption, locality, data classification, and result destinations.
Callers do not select individual worker machines.
