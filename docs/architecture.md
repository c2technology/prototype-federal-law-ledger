# Architecture

## Current architecture

Federal Law Ledger is a static documentation repository. There is no runtime, database, parser, generator, or required installation.

```text
Official public sources
        |
        v
Bill branch + GitHub pull request
        |
        +-- bills/                 portable bill history and attribution
        +-- enacted/               complete Public Law after enactment
        +-- effective/usc/         applied consolidated Code changes
        +-- effective/uncodified/ effective non-Code provisions
        |
        v
Merged enactment on main or closed unmerged proposal
        |
        v
Permanent outcome tags + ordinary Git history
```

## Components

### Bill record

`bills/congress-{N}/{type}-{number}.md` records:

- title and status;
- full named sponsor and cosponsors;
- optional stable IDs beside names;
- official text-version history;
- named individual votes where recorded;
- aggregate actions where no individual tally exists;
- presidential action or unsuccessful outcome; and
- source URLs.

### Enacted law

`enacted/congress-{N}/public-law-{N}-{law-number}.md` contains the complete enacted Act and its identifying information.

Early enactments that predate modern Public Law numbering use a stable chapter-based path, such as `enacted/congress-001/chapter-001-oaths-act.md`.

### Effective U.S. Code

`effective/usc/title-{number}-{name}/section-{number}.md` contains consolidated statutory text. An enacted PR directly changes every affected file.

### Effective uncodified provisions

`effective/uncodified/congress-{N}/public-law-{N}-{law-number}.md` contains operative provisions from that law that have no ordinary Code-section destination. It does not duplicate the complete Act.

### People references

`people/members.md` and `people/presidents.md` provide name-first identity references and supplemental stable IDs as the corpus grows.

## Git lifecycle

1. Branch from current `main`.
2. Add the introduced bill record.
3. Add official revisions and actions as ordered commits.
4. If unsuccessful, close unmerged and tag the final commit.
5. If enacted, add the Public Law, apply all Code changes, update uncodified provisions, then merge and tag.

A bill branch may need to incorporate current `main` before enactment if other laws merged while it remained open. This keeps its effective-state changes based on the latest consolidated text.

## Authorship model

The primary elected sponsor is the Git author. The repository importer is the committer. Full backer and voter records remain in the tracked bill document because a single Git author field cannot represent every sponsor, cosponsor, or voter.

## Effective-date limitation

The prototype stores all Code modifications in the enacted law's PR and records delayed or conditional effective-date clauses prominently in the enacted and uncodified documents. It does not initially provide an as-of-date rendering engine.

## Deferred architecture

A static GitHub Pages browser may later provide search. It must consume repository files and must not become a separate source of legislative facts.
