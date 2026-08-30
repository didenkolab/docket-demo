---
key: ACME-2
title: Session model
type: story
status: In review
status_category: doing
priority: normal
assignee: agent/claude
parent: "[[ACME-1 Fix the login redirect loop for expired sessions]]"
labels: ["[[auth]]", "[[design]]"]
created: 2026-08-30T18:37:28Z
updated: 2026-08-30T22:57:54Z
aliases: []
tags: [area/auth]
---

The session is currently a cookie and a hope: three places construct one, and each sets a
slightly different expiry. [[ACME-1 Fix the login redirect loop for expired sessions]] is the
second bug this month that comes out of that.

One type, constructed in one place, with the expiry as a field rather than a convention.

## Acceptance

- [ ] A session is created in exactly one function.
- [ ] Expiry is a field on the type, not a duration recomputed per call site.
- [ ] The redirect path reads the session rather than reconstructing it.

## Comments
