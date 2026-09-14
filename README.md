# Federal Law Ledger

Federal Law Ledger is a public, documentation-only Git repository for reconstructing federal statutory history from the earliest enactments forward.

Each bill is represented by a branch and GitHub pull request. If enacted, that same PR adds the complete Public Law, applies every directed U.S. Code change, and records effective uncodified provisions. Unsuccessful bills close unmerged and remain reachable through tags.

## Current status

Issue #1 imports the First Congress's first enacted law: **An Act to regulate the Time and Manner of administering certain Oaths**, approved June 1, 1789.

While the historical chronology is incomplete, `main` represents effective law at the latest imported enactment. It must not be read as a statement of present-day federal law.

## Core rules

- One branch and PR per bill.
- Official text revisions are ordered commits.
- The primary elected sponsor is the Git author; the maintainer/importer is the committer.
- Bill documents identify sponsors, cosponsors, and recorded voters by full name.
- Aggregate proceedings are recorded without invented individual votes.
- An enacted-law PR contains the complete Public Law and every resulting Code edit.
- Effective uncodified provisions live beside the Code representation under `effective/uncodified/`.
- `main` represents consolidated effective statutory text after merged enactments.
- Until the chronology reaches the present, `main` reflects the latest imported historical enactment rather than current-day law.
- Enacted and unsuccessful bills receive durable tags.
- Important facts remain available after an ordinary clone.

## Read first

1. [`SPECIFICATION.md`](SPECIFICATION.md) — agreed product requirements and acceptance criteria.
2. [`AGENTS.md`](AGENTS.md) — contribution, evidence, attribution, and verification rules.
3. [`docs/architecture.md`](docs/architecture.md) — repository structure and lifecycle.
4. [`docs/sources.md`](docs/sources.md) — official source inventory and known coverage limits.
5. [`MEMORY.md`](MEMORY.md) — durable project decisions and constraints.
6. [`docs/handoff.md`](docs/handoff.md) — current implementation state and next work.

## Use

No installation or custom command is required.

```bash
git clone https://github.com/c2technology/prototype-federal-law-ledger.git
cd prototype-federal-law-ledger
```

Inspect history with ordinary Git:

```bash
git log --graph --oneline --all
git diff <earlier-tag> <later-tag>
git blame <path>
```

## Source policy

Use official public sources first: GovInfo and the Statutes at Large, OLRC U.S. Code text and classification tables, Congress.gov, official House and Senate vote records, and Library of Congress historical collections. Record gaps instead of inferring missing sponsors, revisions, or votes.

See [`docs/sources.md`](docs/sources.md) for the initial verified source map.

## Legal notice

This is an unofficial documentation project. It does not provide legal advice and is not a substitute for official publications or professional legal research.
