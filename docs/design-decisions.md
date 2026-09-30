# Design decisions

## Least privilege by data separation

The portal receives a bounded snapshot instead of querying the private database.

## Stable sequencing

Permanent sequence numbers make progress and reconciliation predictable.

## Append-only outcomes

Portal activity is synchronized as events, preventing accidental replacement of
private records.

## Role isolation

Only administrators can load packs or export outcomes.

