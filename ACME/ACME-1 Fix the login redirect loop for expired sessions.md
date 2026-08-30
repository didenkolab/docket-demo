---
key: ACME-1
title: Fix the login redirect loop for expired sessions
type: bug
status: In progress
status_category: doing
priority: urgent
assignee: dana
labels: ["[[auth]]", "[[regression]]"]
created: 2026-08-30T18:37:28Z
updated: 2026-08-30T19:04:01Z
aliases: []
---

The redirect loops when the session cookie is rejected but the
form still succeeds.

See [[ACME-2 Session model]].

## Comments

**Dana Example · 2026-08-30 14:03** — Reproduced on staging. The cookie is set with the wrong
`SameSite`, so the browser drops it on the redirect.

**agent/claude · 2026-08-30 15:10** — Narrowed it to the session middleware. Fix is one line,
test is not.
