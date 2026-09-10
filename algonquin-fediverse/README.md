# AC Fediverse

Federated social and publishing ecosystem built around ActivityPub. It owns
actors, inbox/outbox processing, federation, moderation, search, notifications,
and the user-facing Social, Photos, Video, Communities, and Blogs experiences.

## Layout

- `apps/` — social, photos, video, communities, blogs, and administration
- `services/` — ActivityPub gateway, actors, inbox/outbox, federation, moderation,
  media proxy, search, notifications, and spatial support
- `contracts/` — protocol and spatial integration definitions
- `connectors/` — AC Cloud, AI, compute, and media integrations
- `policies/` — federation, moderation, privacy, and retention controls
