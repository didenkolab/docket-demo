---
key: ACME-1
title: Fix login redirect loop
type: bug
status: Backlog
status_category: todo
priority: high
assignee: agent/claude
labels: []
created: 2026-08-30T18:37:28Z
updated: 2026-08-30T18:37:28Z
aliases: []
---

The login redirect loops when the session cookie is rejected but the form still succeeds.

Steps:

1. Sign in with an expired session
2. Watch `/login` bounce to `/` and back

See [[ACME-2 Session model]] for how sessions are meant to work.

## Acceptance

- [x] Reproduced
- [ ] Fixed

## Comments

**Dana Example · 2026-08-30 14:03** — Reproduced on staging. The cookie is set with the wrong
`SameSite`, so the browser drops it on the redirect.

**agent/claude · 2026-08-30 15:10** — Narrowed it to the session middleware. Fix is one line,
test is not.
