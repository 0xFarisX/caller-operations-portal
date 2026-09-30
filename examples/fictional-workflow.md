# Fictional pack workflow

1. Operations builds the next bounded lead pack from eligible records.
2. A caller-safe JSON snapshot is uploaded by the portal administrator.
3. The caller signs in and works leads sequentially.
4. Outcomes and callbacks are appended without exposing other packs.
5. The administrator exports the outcome log.
6. Import tags make repeated synchronization a no-op rather than a duplicate.

