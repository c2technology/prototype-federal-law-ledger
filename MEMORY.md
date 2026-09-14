# Project Memory

## Purpose

Federal Law Ledger reconstructs federal statutory history as a public, documentation-only Git repository.

## Durable decisions

- GitHub is the public remote and pull-request viewer.
- Important legislative facts live in tracked files and Git history.
- Each bill has one branch and one PR.
- Official revisions are commits on that branch.
- Enacted bills merge only after the PR adds the complete Public Law and applies every directed U.S. Code change.
- `main` represents consolidated effective statutory text after merged enactments.
- Effective temporary and uncodified provisions live under `effective/uncodified/`.
- No positive-law metadata is required for the prototype.
- The primary elected sponsor is the Git author; the repository maintainer/importer is the committer.
- Sponsors, cosponsors, and voters are identified by full name in human-facing documents.
- Stable IDs may supplement names but never replace them.
- Votes remain distinct from sponsorship.
- Aggregate procedures do not imply individual votes.
- Enacted and unsuccessful bills receive permanent tags.
- The project requires no application, database, API, custom UI, Git aliases, package installation, checksum system, signing system, or elaborate validation framework.
- Jim merges PRs.

## Source priorities

1. GovInfo and Statutes at Large.
2. OLRC U.S. Code and classification resources.
3. Congress.gov.
4. Official House, Senate, committee, presidential, and historical records.
5. Library of Congress historical collections.
6. Secondary public datasets only for explicitly documented gaps.

## Known limitation

Historical bill text, sponsors, revisions, and individual votes are not uniformly available back to 1789. Missing facts must be stated, not inferred.
