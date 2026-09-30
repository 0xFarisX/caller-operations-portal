# Caller Operations Portal

**A restricted contractor portal that exposes only the assigned lead pack and returns structured outcomes to a private intelligence system.**

`Next.js` · `TypeScript` · `PostgreSQL/PGlite` · `Signed Sessions` · `Least Privilege`

## At a glance

| | |
|---|---|
| **Business problem** | External callers needed operational context without access to the private customer database |
| **Primary users** | Contract callers and a portal administrator |
| **System role** | Distribute bounded work, capture outcomes and return them safely |
| **Data boundary** | One assigned pack plus the caller's own outcomes |
| **Control model** | Role-specific sessions, separate storage and append-only outcome exchange |

## The problem

Giving a contractor direct access to an internal intelligence platform exposes
far more customer data than the job requires. Static spreadsheets reduce access
but create version conflicts, lost callbacks and inconsistent outcome tracking.

I designed a deliberately separate portal that carries only the minimum data
needed to complete assigned calls.

## How it works

```mermaid
flowchart LR
    A[Private intelligence system] --> B[Build bounded lead pack]
    B --> C[Caller-safe JSON export]
    C --> D[Admin upload]
    D --> E[(Separate portal database)]
    E --> F[Caller sequence]
    F --> G[Outcome and callback log]
    G --> H[Admin outcome export]
    H --> I[Idempotent import into private system]
```

## Core capabilities

- Builds permanent, sequential lead assignments in bounded packs
- Exports only caller-safe fields and limited context
- Stores portal data separately from the internal database
- Provides distinct caller and administrator roles
- Uses signed, expiring HTTP-only sessions
- Applies login throttling without revealing configuration state
- Supports chunked administrative uploads for large packs
- Guides callers through a sequential queue
- Records outcomes, notes, callbacks and attempt history
- Automatically marks repeatedly unanswered records as exhausted
- Exports an append-only outcome log
- Imports outcomes idempotently into the private system

## Technology stack

| Layer | Technology |
|---|---|
| Application | Next.js and React |
| Language | TypeScript |
| Data | PostgreSQL or embedded PGlite |
| Authentication | Environment-backed roles and HMAC-signed cookies |
| Deployment mode | Separate portal-only runtime |
| Integration | JSON pack and outcome exchange |

## Key design decisions

1. Separate the contractor portal from the intelligence database.
2. Export bounded snapshots rather than providing live internal access.
3. Preserve permanent sequence numbers across pack updates.
4. Use append-only, idempotent outcome synchronization.
5. Give callers and administrators different permissions and interfaces.

## My contribution

I defined the least-privilege data boundary, designed the pack and outcome
exchange, specified caller and administrator workflows, and directed the
AI-assisted implementation of the portal.

## Further documentation

- [Architecture](docs/architecture.md)
- [Capabilities](docs/capabilities.md)
- [Design decisions](docs/design-decisions.md)
- [Evidence boundaries](docs/evidence.md)
- [Fictional pack example](examples/fictional-workflow.md)

## Public repository boundary

This case study excludes lead packs, customer context, passwords, session keys,
production databases, deployment secrets and original private source code.

