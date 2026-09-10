# Roles & Identity

## Role taxonomy

| Role | Who | Notes |
|---|---|---|
| `student` | Default identity for enrolled students | Standard quota |
| `faculty` | Instructors | May get course-management scopes later |
| `staff` | Non-teaching employees | Standard quota |
| `researcher` | Approved research projects | Larger quota, possibly higher compute trust tier |
| `club-developer` | AI Club members building on the platform | API/SDK access, elevated debugging visibility |
| `platform-operator` | People running the infrastructure | Admin over services, not over student data by default |
| `administrator` | Full institutional control | College-controlled, not individual club members, once in production |
| `guest/affiliate` | Anyone else with institutional access | Most restricted default scope |

## Entra groups (proposed)

```text
AC-AI-Users              — baseline access
AC-AI-Faculty            — faculty-specific features
AC-AI-Researchers        — elevated quota
AC-AI-Developers         — SDK/API access
AC-AI-Platform-Admins    — operational control
AC-AI-GPU-Priority       — priority scheduling on constrained compute
```

## Ownership boundary — important

Once this becomes a production, college-wide service, **the College — not
individual club members — owns the production identity, servers, secrets,
security policies, backups, and service continuity.** The club builds and
governs the platform's evolution; it should not be the sole entity with root
access to production once real student data is flowing through it. Get this
boundary agreed with ITS explicitly before the pilot-to-production transition
(Phase 3 → Phase 4 in the roadmap), not after.

## Multi-tenant note

If Algonquin's student/staff/faculty populations aren't all in one Entra
tenant, don't try to make the gateway understand every identity source
directly — put an identity broker in front of it (see
`docs/architecture/02-identity-sso.md`) so the gateway only ever sees one
normalized identity shape.
