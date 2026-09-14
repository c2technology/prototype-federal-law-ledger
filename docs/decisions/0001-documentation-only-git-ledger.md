# Decision 0001 — Documentation-only Git ledger

**Status:** Accepted  
**Date:** 2026-09-14

## Decision

Represent federal bills, enactments, effective U.S. Code changes, and uncodified provisions through ordinary tracked documents and Git history hosted on GitHub.

## Consequences

- One bill branch and PR carries its revisions and outcome.
- An enacted PR adds the complete Public Law and applies all directed Code edits.
- Unsuccessful bills close unmerged and receive outcome tags.
- No application, database, API, custom Git tooling, package installation, checksum system, or signing system is required.
- Historical gaps are documented rather than inferred.
