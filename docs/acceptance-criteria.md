# Acceptance criteria

These are targets for implementation and evaluation, not results already measured.

- A visitor understands the board stages and assistant role.
- Search is read-only and returns tasks matching supplied filters.
- A proposed change identifies its target and before/after values.
- No mutation occurs before a person's approval.
- Archive requires exact `ARCHIVE` confirmation.
- Invalid, missing, expired, stale, or foreign-session inputs fail closed.
- Loading, provider failure, success, decline, retry, and undo are clear.
- Core interactions work by keyboard and status changes are announced.
- No model key or session secret appears in client code or browser responses.
- Prompts and model output are untrusted; logs are bounded and omit credentials.
- Lookup precision, latency, and valid proposal rates are measured before quality claims.
