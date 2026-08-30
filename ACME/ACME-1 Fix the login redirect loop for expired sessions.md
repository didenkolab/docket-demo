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
updated: 2026-08-30T23:03:27Z
aliases: []
tags: [area/auth, needs-review]
---

The redirect loops when the session cookie is rejected but the
form still succeeds.

> [!warning] Reproduces only on staging
> The production cookie has a different `SameSite`, so this cannot be seen locally.

> [!faq]- Why is this urgent?
> Everyone whose session expires overnight is locked out until they clear cookies.

See [[ACME-2 Session model]].

## Comments

**Dana Example · 2026-08-30 14:03** — Reproduced on staging. The cookie is set with the wrong
`SameSite`, so the browser drops it on the redirect.

**agent/claude · 2026-08-30 15:10** — Narrowed it to the session middleware. Fix is one line,
test is not.
