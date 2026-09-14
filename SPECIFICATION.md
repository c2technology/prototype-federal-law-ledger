# Federal Law Ledger — Prototype Specification

**Status:** Agreed design  
**Repository:** `prototype-federal-law-ledger`  
**Visibility:** Public  
**Format:** Documentation-only Git repository hosted on GitHub

## 1. Purpose

Federal Law Ledger will reconstruct federal statutory history in ordinary Git, beginning with the earliest federal enactments and proceeding chronologically.

The repository will make these facts inspectable without special software:

- what each bill proposed;
- how its official text changed;
- which elected officials officially backed it;
- how each named member voted when an individual tally exists;
- what aggregate procedure occurred when individual votes were not recorded;
- whether and how the measure became law;
- the complete enacted Public Law;
- every resulting change to the effective United States Code;
- every still-effective temporary or uncodified provision; and
- the exact state associated with enacted and failed bills.

The repository is an unofficial public-information project. It is not legal advice and does not replace official legal publications.

## 2. Core legal representation

### 2.1 Public Laws

The Statutes at Large is the chronological collection of laws enacted during each session of Congress.[1] A Public Law is the complete enacted Act; it is not itself a single U.S. Code entry.

The repository retains each complete enacted Public Law under `enacted/`.

### 2.2 United States Code

The U.S. Code organizes general and permanent federal law by subject.[2] A Public Law may create, amend, repeal, transfer, or redesignate one or many Code provisions. A Code section may therefore reflect changes made by several Public Laws.

The repository maintains the consolidated result of those changes under `effective/usc/`.

### 2.3 Uncodified provisions

Some enacted provisions are not placed in ordinary U.S. Code sections. OLRC classification may place provisions in statutory notes or leave them unclassified rather than making them ordinary Code sections.[3]

The repository keeps all still-effective temporary and uncodified provisions in a second document adjacent to the Code representation under `effective/uncodified/`. Examples include:

- reporting requirements;
- temporary programs;
- transition rules;
- one-time instructions;
- special applicability rules;
- effective-date provisions; and
- other operative provisions without an ordinary Code-section destination.

An uncodified provision remains law. “Uncodified” only describes where it appears relative to the subject-organized U.S. Code.

### 2.4 No positive-law metadata

The prototype will not add a `positive_law` field to titles, sections, or bills. The repository follows the existing U.S. Code title structure. Positive-law status remains legally meaningful background, but the prototype has no workflow requiring that fact to be duplicated as metadata.

## 3. Product rules

1. Every bill has one branch and one GitHub pull request.
2. Official bill revisions are ordered commits in that pull request.
3. The elected primary sponsor is the Git author.
4. The repository maintainer/importer is the Git committer.
5. The bill document names every official sponsor and cosponsor.
6. A stable identifier may accompany a person’s name as supplemental metadata, but never replaces the name in human-facing content.
7. Recorded votes name every member and that member’s recorded position.
8. Voice votes, unanimous consent, and other aggregate procedures are recorded without inventing individual positions.
9. A yea vote does not make a member a sponsor, cosponsor, or backer.
10. A failed, withdrawn, vetoed, pocket-vetoed, or lapsed bill remains a closed, unmerged PR.
11. When a bill becomes law, its PR adds the complete Public Law and applies every U.S. Code modification directed by that law.
12. The same enacted-law PR adds or updates all corresponding effective uncodified provisions.
13. If one Public Law changes several titles or sections, every affected file appears in that PR diff.
14. `main` represents the consolidated effective statutory state after each merged enacted-law PR.
15. Enacted and unsuccessful bills receive permanent tags.
16. The repository requires only ordinary files, Git, and GitHub’s normal PR interface.

## 4. Repository layout

```text
README.md
AGENTS.md
MEMORY.md
SPECIFICATION.md

enacted/
  congress-001/
    chapter-001-oaths-act.md
  congress-{number}/
    public-law-{congress}-{law-number}.md

effective/
  usc/
    title-001-general-provisions/
      section-{number}.md
    title-018-crimes-and-criminal-procedure/
      section-{number}.md
  uncodified/
    congress-{number}/
      public-law-{congress}-{law-number}.md

bills/
  congress-{number}/
    {bill-type}-{bill-number}.md

people/
  members.md
  presidents.md

docs/
  architecture.md
  conventions.md
  handoff.md
  sources.md
  decisions/
  findings/
```

### 4.1 Directory responsibilities

- `bills/` contains the portable bill record while the PR is open and after it closes.
- `enacted/` contains each complete law as enacted.
- `effective/usc/` contains consolidated Code text after applying enacted amendments.
- `effective/uncodified/` contains the still-effective provisions of each enacted law that have no ordinary Code-section destination.
- `people/` provides name-first identity references and optional stable identifiers.
- `docs/` records conventions, architecture, sources, decisions, findings, and handoff state.

Important legislative facts must be committed to the repository. GitHub PR descriptions, comments, reviews, and labels may improve presentation but are not the only copy of a fact needed after an ordinary clone.

## 5. Bill document

Each bill has one human-readable Markdown document. A representative structure is:

```markdown
---
congress: 000
bill: H.R. 0000
status: introduced
primary_sponsor:
  name: Full Name
  bioguide_id: A000000
cosponsors:
  - name: Full Name
    bioguide_id: B000000
base_commit: <git-object-id>
sources:
  - <official-source-url>
---

# H.R. 0000 — Bill title

## Backers

- Full Name — sponsor
- Full Name — cosponsor

## Revisions

- Introduced text — date — source
- House-reported text — date — source
- Enrolled text — date — source

## House vote

| Member | State | Party | Vote |
|---|---|---|---|
| Full Name | State | Party | Yea |
| Full Name | State | Party | Nay |

Result: Passed, with the official totals and source.

## Senate action

Passed by unanimous consent. Individual positions were not recorded.

## Presidential action

Signed by President Full Name on YYYY-MM-DD.

## Sources

- <official-source-url>
```

All names and statuses must come from cited public records. If a historical source does not identify a sponsor, voter, revision, or other fact, the document states that the available record does not identify it.

## 6. Git authorship

The elected primary sponsor—the bill’s main official backer—is the Git author for commits on the bill branch:

```text
Author: Full Name <stable-local-address>
Committer: Repository Maintainer <maintainer-address>
```

The local address exists to make Git identity consistent; it does not imply that the elected official owns an email account, GitHub account, or repository account.

The bill document remains the complete attribution record and includes:

- primary sponsor by full name;
- every cosponsor by full name;
- each person’s official role;
- optional stable IDs next to names; and
- source links.

“Backer” means an elected official recorded as a sponsor or cosponsor. It does not assert that the official personally drafted every word.

## 7. Vote representation

Official recorded floor votes are tied to each named voter. Congress.gov notes that recorded floor votes appear in legislative actions and the Congressional Record, while committee votes may appear in committee reports.[4]

Allowed member-level values include the exact categories supplied by the source, normalized only where repository conventions explicitly define the mapping. Typical values are:

- Yea;
- Nay;
- Present;
- Not voting; and
- Paired, where recorded.

For an aggregate procedure, record only what the source supports:

```text
Passed by voice vote. Individual positions were not recorded.
```

or:

```text
Passed by unanimous consent. Individual positions were not recorded.
```

The repository never infers individual positions from aggregate passage.

## 8. Pull-request lifecycle

### 8.1 Open a bill

Create:

```text
branch: bill/{congress}/{bill-type}-{bill-number}
file:   bills/congress-{congress}/{bill-type}-{bill-number}.md
PR:     one PR from that branch to main
```

The initial commit records the introduced bill text, named official backers, and sources available at that stage.

### 8.2 Add revisions

Each official version becomes an ordered commit on the same branch, for example:

```text
Introduce bill
Apply committee-reported revision
Apply House amendment
Apply Senate amendment
Apply conference agreement
Record enrolled text
```

The final bill document lists the versions and source links. Git history preserves their order and diffs.

### 8.3 Record votes and actions

Votes and legislative actions are committed to the bill document as they occur. Member-level votes list names and positions. Aggregate actions state their procedure and result.

### 8.4 Enact the law

After the measure becomes law, the same PR must:

1. update the bill status to enacted;
2. add the complete enacted Public Law under `enacted/`;
3. apply every Code amendment directed by the Public Law under `effective/usc/`;
4. add or update every effective uncodified provision under `effective/uncodified/`;
5. record the enactment mechanism and constitutional actor; and
6. add the final source links.

Federal enactment may occur by presidential signature, without signature, or by congressional override of a veto.[5] The tracked document records the actual mechanism. The GitHub user who technically merges the PR is only the repository maintainer and must not be represented as the President or Congress.

### 8.5 Close an unsuccessful bill

If a bill fails, is withdrawn, is vetoed without override, is pocket-vetoed, or lapses:

- record the supported outcome and sources in the bill document;
- close the PR without merging;
- tag its final branch commit; and
- leave `main`, `enacted/`, and `effective/` unchanged.

## 9. Enacted-law PR contract

An enacted-law PR is incomplete unless it includes the law and all its applied effects.

Conceptual diff:

```text
M  bills/congress-{N}/{type}-{number}.md
A  enacted/congress-{N}/public-law-{N}-{law-number}.md
M  effective/usc/title-{T}-{title-name}/section-{S}.md
M  effective/usc/title-{U}-{title-name}/section-{R}.md
A  effective/uncodified/congress-{N}/public-law-{N}-{law-number}.md
```

If the Public Law directs that words be struck, those words disappear from the relevant Code file. If it directs that text be inserted, that text appears at the directed location. Replacements, repeals, transfers, redesignations, and changes across multiple titles are reflected in the same PR.

The enacted-law file is not a substitute for editing the effective Code.

### 9.1 Delayed effective dates

The enactment PR still includes every Code modification directed by the Public Law, as required by this project’s bill-as-PR model. Any delayed, conditional, or staged effective-date rule must be reproduced prominently in the enacted-law document and the adjacent uncodified document so readers do not mistake enactment date for operative date.

The prototype does not attempt a date-sensitive rendering engine. A future iteration may add historical as-of-date trees if ordinary Git history and explicit effective-date documentation prove insufficient.

### 9.2 Uncodified sidecar

The sidecar does not duplicate the complete Public Law. It contains the provisions from that law that remain operative but do not appear as ordinary Code sections.

When a later law changes, repeals, satisfies, or expires one of those provisions, that later law’s PR updates the corresponding uncodified document. Git history and enactment tags preserve its prior state.

If an enacted law contains no such provisions, it does not require an empty sidecar file. The PR or enacted-law document states that no separate uncodified provisions were identified.

## 10. Tags and comparisons

### 10.1 Enacted measures

Tag the enacted merge commit:

```text
bill/{congress}/{bill-type}-{bill-number}/enacted
public-law/{congress}-{law-number}
```

Show exactly what one enacted PR introduced relative to its first parent:

```bash
git diff public-law/{congress}-{law-number}^1 public-law/{congress}-{law-number}
```

Compare the consolidated repository state at two enacted laws:

```bash
git diff public-law/{earlier} public-law/{later}
```

### 10.2 Unsuccessful measures

Tag the final unmerged bill commit:

```text
bill/{congress}/{bill-type}-{bill-number}/failed
bill/{congress}/{bill-type}-{bill-number}/withdrawn
bill/{congress}/{bill-type}-{bill-number}/vetoed
bill/{congress}/{bill-type}-{bill-number}/pocket-vetoed
bill/{congress}/{bill-type}-{bill-number}/lapsed
```

Record the base commit in the bill document. Compare the proposed final state with its base using ordinary Git:

```bash
git diff <base-commit> bill/{congress}/{bill-type}-{bill-number}/{outcome}
```

Tags keep the exact final proposal reachable even if the remote PR branch is later deleted.

## 11. Source policy

Prefer source-of-truth public records in this order:

1. GovInfo slip laws and Statutes at Large;
2. OLRC U.S. Code text and classification tables;
3. Congress.gov bill records, text versions, actions, and roll calls;
4. official House, Senate, committee, presidential, and historical records;
5. Library of Congress historical collections; and
6. reputable secondary datasets only to fill documented gaps.

The Statutes at Large begins with the First Congress in 1789.[1][7] Congress.gov coverage is substantially more complete for recent Congresses than for early congressional history, so historical backer, revision, and vote data will be uneven.[6]

Each bill and enacted-law document includes the URLs used for its text and metadata. The project does not require checksums, cryptographic signatures, downloaded source archives, or elaborate automated validation.

When reliable sources disagree or leave a gap, document the conflict or absence. Do not silently choose a politically convenient interpretation and do not infer unsupported names, votes, or legislative actions.

## 12. Historical limitations

The repository aims to begin with the earliest enactments, but it cannot promise modern bill-level detail for every historical law. Source availability varies by period.[6]

For each unavailable fact:

- retain the enacted text that can be sourced;
- say what is unavailable;
- identify the sources checked when useful; and
- never fabricate a sponsor, cosponsor, revision, vote, or presidential action.

The absence of an individual tally must remain distinguishable from an affirmative vote by every member.

## 13. Non-goals

The prototype will not initially provide:

- an application or database;
- a custom web interface;
- an API;
- Git aliases or custom Git commands;
- a package installation or build step;
- cryptographic verification or signing;
- automated legal interpretation;
- a date-sensitive statutory rendering engine;
- official legal authority;
- rankings or political scores;
- inferred votes or backers;
- GitHub accounts impersonating elected officials; or
- an expectation that lawmakers use the repository.

A later static GitHub Pages browser may add full-text search after the repository itself is useful through ordinary files and Git.

## 14. Initial delivery iterations

### Iteration 1 — First federal enactment

Import the First Congress’s first enacted law, “An Act to regulate the Time and Manner of administering certain Oaths,” approved June 1, 1789, using the available Statutes at Large and historical sources.[7]

Acceptance focus:

- complete enacted-law document;
- correct chronological placement;
- no invented sponsor or individual votes;
- effective and uncodified representation appropriate to that law; and
- a tagged merge commit.

### Iteration 2 — Small modern enacted law

Select a modern law that directly changes one or more U.S. Code sections.

Acceptance focus:

- bill branch and PR;
- official revisions as commits;
- full named backer list;
- named member votes where recorded;
- complete enacted Public Law;
- all directed Code edits in the same PR;
- uncodified sidecar where needed; and
- enacted tags.

### Iteration 3 — Modern unsuccessful bill

Select a failed or lapsed bill with useful revision or vote history.

Acceptance focus:

- proposed changes remain unmerged;
- final bill state is tagged;
- votes and outcome are documented; and
- effective law on `main` is unchanged.

### Iteration 4 — Chronological expansion

Continue from the First Congress forward, keeping each iteration small enough to review source fidelity and Git history.

## 15. Acceptance criteria

```gherkin
Feature: Represent federal legislation as inspectable Git history

  Scenario: Open a bill pull request
    Given a bill has an official introduced version
    When the bill is added to the ledger
    Then it has one branch and one pull request
    And its primary elected sponsor is the Git author
    And its bill document names every known sponsor and cosponsor

  Scenario: Preserve official bill revisions
    Given a bill has multiple official text versions
    When its pull request is updated
    Then each version is represented by an ordered commit
    And the versions and source links are listed in the bill document

  Scenario: Apply an enacted law to the Code
    Given a bill becomes a Public Law
    And the Public Law modifies one or more U.S. Code provisions
    When its pull request is completed
    Then the complete Public Law is added under enacted
    And every directed Code modification is applied under effective/usc
    And all affected titles and sections appear in that pull request diff

  Scenario: Preserve uncodified provisions
    Given a Public Law contains operative provisions without an ordinary Code-section destination
    When its pull request is completed
    Then those provisions appear in the law's effective/uncodified sidecar
    And the sidecar does not replace the complete enacted-law document

  Scenario: Avoid unnecessary uncodified files
    Given a Public Law contains no identified effective uncodified provisions
    When its pull request is completed
    Then no empty sidecar is required
    And the absence is stated in the pull request or enacted-law document

  Scenario: Name every recorded voter
    Given an official source provides a member-level vote
    When the vote is documented
    Then every recorded member is shown by full name
    And each member's recorded position is shown

  Scenario: Preserve an aggregate procedure
    Given the official proceeding provides no member-level tally
    When the action is documented
    Then the aggregate procedure and result are stated
    And no individual position is inferred

  Scenario: Distinguish backing from voting
    Given a member voted yea but was not a sponsor or cosponsor
    When the bill document is reviewed
    Then the member appears in the vote record
    And the member does not appear as a backer

  Scenario: Preserve an unsuccessful bill
    Given a bill fails, is withdrawn, is vetoed without override, is pocket-vetoed, or lapses
    When its pull request is closed
    Then it remains unmerged
    And its final commit receives the applicable outcome tag
    And main is unchanged

  Scenario: Inspect one enacted law
    Given an enacted Public Law tag
    When the tag is diffed against its first parent
    Then the diff shows the enacted-law document
    And the diff shows every effective Code change in that PR
    And the diff shows its uncodified additions or updates when applicable

  Scenario: Work from an ordinary clone
    Given a user clones the repository
    When GitHub-specific metadata is unavailable
    Then the user can still inspect bill text, revisions, backers, votes, outcomes, enacted laws, effective Code, uncodified provisions, and tags
```

## 16. Prototype completion definition

The first prototype milestone is complete when the repository contains and demonstrates:

1. one sourced First Congress enactment;
2. one modern enacted bill whose PR applies real Code changes;
3. one unsuccessful modern bill retained as a closed, tagged, unmerged proposal;
4. full named backer records for the chosen modern examples;
5. individual named vote records where officially available;
6. accurate aggregate-procedure records where no individual tally exists;
7. enacted and failed-bill tags that support ordinary `git diff` inspection;
8. aligned `README.md`, `AGENTS.md`, `MEMORY.md`, `SPECIFICATION.md`, `docs/architecture.md`, and `docs/handoff.md`; and
9. no dependency beyond normal Git, files, and GitHub’s standard PR view.

## Sources

[1] https://www.govinfo.gov/help/statute — United States Statutes at Large
[2] https://uscode.house.gov/detailed_guide.xhtml — Detailed Guide to the United States Code
[3] https://uscode.house.gov/about_classification.xhtml — United States Code Classification
[4] https://www.congress.gov/help/votes-in-the-house-and-senate — Votes in the House and Senate
[5] https://www.congress.gov/legislative-process/presidential-action — Presidential Action
[6] https://www.congress.gov/help/coverage-dates — Congress.gov Coverage Dates
[7] https://www.loc.gov/collections/united-states-statutes-at-large/articles-and-essays/vol1-5 — United States Statutes at Large, Volumes 1–5
