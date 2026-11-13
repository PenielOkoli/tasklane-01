# Tasklane — product brief

**Phase 1 · AI-Native Product Strategy & Frontend Architecture**

## Product purpose

Tasklane helps a small project team keep a shared task list moving. A person can ask for a task to be found, drafted, prioritized, or moved. AI can suggest a structured next step, while the person remains responsible for approving changes.

The product promise is: **AI can organize the work; people choose what changes.** Tasklane is a staged prototype, not an autonomous project manager.

## Target users and jobs

The first users are small product, design, engineering, or operations teams working on a launch or short project. A project lead needs one board to see and prioritize work. A contributor needs to understand the next useful action. Both may have rough requests that need to become clear tasks.

- When work feels scattered, I want one board showing what is next, in progress, and done.
- When I have a rough request, I want AI to find or draft a task so I spend less time formatting work.
- When AI suggests a change, I want to inspect the exact target and before/after values before saving it.
- When a suggestion is wrong or fails, I want to decline it, retry safely, or undo the last change.

## Scope and AI use cases

The first product iteration is one project board with read-only task search and proposed task creation, priority, status, and archive changes. The model may search and prepare one proposal. It cannot commit, approve its own proposal, contact people, or operate an external project system. Every write requires a person’s approval; archiving also requires typing `ARCHIVE`. The prototype uses fictional tasks and avoids confidential project data.

Search success means returned tasks match explicit filters and the board remains unchanged. A task suggestion succeeds when its fields are valid and reviewable. A priority or status suggestion succeeds when it targets an existing task and remains pending until approval. Errors must preserve the board and explain the next safe step.

Initial targets for later measurement: 18 of 20 scripted lookups identify the intended fixture; 100% of writes wait for approval; invalid or foreign task IDs produce no change; keyboard-only users can operate all core controls; p95 model response under 8 seconds in a small sample. These are targets, not measured results.

## Primary journey

1. A person opens the Spring launch board and scans To do, In progress, and Done.
2. They ask Tasklane to find a task or suggest one change.
3. The server validates the request and sends the model only necessary task fields.
4. A read-only search may run. A proposed change appears with its target and before/after values.
5. The person approves or declines. Archive requires `ARCHIVE` as an extra confirmation.
6. Tasklane records the result and offers undo for the latest approved change. Errors preserve the board.

## State and platform choices

The prototype keeps a bounded task board, current proposal, revision, and latest undo record in a short-lived session. Conversation text is not the source of truth. The validated board and proposal are authoritative. Durable shared storage and authentication are out of scope initially.

The initial implementation uses Groq through the Vercel AI SDK. Model access stays server-side; the React UI depends on typed application responses rather than provider-specific browser code. The provider can be swapped without redesigning the UI. No API key is exposed to the browser.

## Continuity

At the user's request, submissions 1–4 are being rebuilt as a coherent Tasklane sequence. Earlier repositories and deployments remain historical submissions; this resubmission series gets its own repositories and deployments.
