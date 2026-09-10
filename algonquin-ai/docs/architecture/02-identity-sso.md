# Identity & SSO

Microsoft Entra ID is the root of identity — Algonquin already uses Microsoft
auth/MFA for major services, and OpenWebUI already supports Microsoft OAuth
with Entra role mapping.

## Browser login flow

```text
User
 │
 ▼
ai.algonquincollege.com
 │
 ▼
Microsoft Entra ID
 │
 ├── MFA
 ├── Algonquin account
 └── institutional authorization
 │
 ▼
Algonquin AI Identity Service
 │
 ▼
short-lived AI session
```

## If Algonquin has multiple identity domains/tenants

Put a broker between Entra and the gateway so the gateway never has to care how
someone originally authenticated:

```text
Students ──────┐
Staff ─────────┤
Faculty ───────┤
Affiliates ────┤
               ▼
        Identity Broker
               │
               ▼
       Algonquin AI Gateway
```

## OpenCode's SSO story

OpenCode's normal flow expects a pasted API key. Replace that with:

```text
$ ac-code login

Opening your browser...
  Microsoft → Algonquin SSO → Authentication successful

Signed in as: student@algonquinlive.com
Plan: Student
Models: 8 available
```

For headless/terminal environments without a browser, use OAuth device
authorization (`ac-code login` prints a URL + short code to enter elsewhere).
Store the resulting token in the OS credential/keychain store, not a plaintext
config file. Keep tokens short-lived; OpenCode talks only to
`https://api.ai.algonquincollege.com` after login, never to a provider directly.

## Role taxonomy

```text
student
faculty
staff
researcher
club-developer
platform-operator
administrator
guest/affiliate
```

## Entra groups (proposed)

```text
AC-AI-Users
AC-AI-Faculty
AC-AI-Researchers
AC-AI-Developers
AC-AI-Platform-Admins
AC-AI-GPU-Priority
```

See `docs/governance/roles-and-identity.md` for how these map to permissions.
