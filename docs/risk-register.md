# Risk register

| Risk | Likelihood / impact | Mitigation | Evidence or follow-up |
|---|---|---|---|
| Model proposes the wrong task or value | Medium / Medium | Show target and before/after values; require approval; allow decline and undo | Module 5 approval tests and live review |
| Malformed or unexpected tool input | Medium / High | Strict schema and server-side validation; fail closed | Invalid-input and boundary tests |
| Prompt injection in task content | Medium / High | Treat content as data; restrict tools and scope; model cannot approve | Adversarial tests in security milestone |
| API key reaches browser | Low / High | Server-only variable; no public prefix; inspect client bundle | Deployment configuration and bundle check |
| Accidental archive | Medium / Medium | Preview, typed `ARCHIVE`, server confirmation, undo | Archive gate test and walkthrough |
| Session replay or concurrent updates | Medium / Medium | Short expiry, authenticated cookie, serial UI; move to server-side store before multi-user use | Persistence milestone |
| Provider outage or slow response | Medium / Medium | Visible progress, cancel/error, preserve board, retry and manual controls | Simulated failure and provider checks |
| Confidential task data sent to model | Low / High | Fictional sample data; minimum field transfer; avoid sensitive content | Review payload before production |
| AI suggestions treated as guaranteed truth | Medium / Medium | Label proposals; require human decision; measure quality | Evaluation milestone |
