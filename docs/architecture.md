# Architecture

The portal runs separately from the private intelligence application. An
administrator exports a bounded, caller-safe pack and uploads it to a dedicated
PostgreSQL/PGlite store. Signed sessions expose caller or administrator routes.
Callers record append-only outcomes; administrators export those outcomes for
idempotent import into the private system.

The portal never receives the complete customer database, mailbox corpus or
blocked-account lists.

