# System Overview

## Core principle

**OpenWebUI and OpenCode never talk to model providers directly.** Both are clients
of one shared backend: the Algonquin AI Gateway. Every other client (mobile, a
future desktop app, third-party SDKs, LMS integrations) is a client of the same
gateway. This is the single most important architectural decision in the whole
project — get this wrong and you end up with N independent integrations instead
of one platform.

```text
OpenWebUI ─┐
OpenCode ──┤
Mobile ────┤
Python SDK ┤
JS SDK ────┤──→ Algonquin AI Gateway → everything else
Brightspace┤
VS Code ───┘
```

## High-level layout

```text
                    ALGONQUIN AI
                         │
              ai.algonquincollege.com
                         │
            ┌────────────┴────────────┐
            │                         │
       Web / Mobile              Developer Access
            │                         │
   Customized OpenWebUI       Customized OpenCode
            │                         │
            └────────────┬────────────┘
                         │
                 ALGONQUIN AI API
                     / GATEWAY
                         │
       ┌─────────────────┼──────────────────┐
       │                 │                  │
   Identity          Policy/Quota       AI Services
     Layer              Layer              Layer
       │                 │                  │
 Entra ID SSO       RBAC / DLP       Models / RAG / Tools
 OIDC / OAuth       Rate limits      Agents / Search
 Device Login       Budgets          Embeddings / Code
       │                 │                  │
       └─────────────────┼──────────────────┘
                         │
                   MODEL ROUTER
                         │
         ┌───────────────┴──────────────┐
         │                              │
   ALGONQUIN ON-PREM              CLOUD OVERFLOW
     GPU CLUSTER                     PROVIDERS
         │                              │
  vLLM / inference              Azure / AWS / other
  Local open models             approved providers
         │                              │
         └──────────────┬───────────────┘
                        │
                 DATA PLATFORM
                        │
       PostgreSQL / Redis / Object Storage
       Vector DB / telemetry / audit / backups
```

## The two APIs

| API | Purpose |
|---|---|
| OpenAI-compatible (`/v1/...`) | Lets OpenWebUI, OpenCode, and any existing OpenAI-compatible tooling integrate with zero custom client code |
| Algonquin-native (`/ac/v1/...`) | Institution-specific functionality that doesn't fit OpenAI's API shape: `me`, `usage`, `files`, `knowledge`, `tools`, `courses`, `policies`, `agents`, `projects` |

## Why not "just deploy OpenWebUI with a plugin"

Because the differentiator isn't the chat UI, it's what sits behind it: SSO as
the identity root, policy-aware local/cloud routing, quotas, auditability, and
an API surface students can build against without needing their own vendor API
keys. OpenWebUI and OpenCode are two interfaces into that platform — not the
platform itself.
