# Repository Instructions

## Read order

Before changing the repository, read:

1. `SPECIFICATION.md`
2. `README.md`
3. `MEMORY.md`
4. `docs/architecture.md`
5. `docs/sources.md`
6. `docs/handoff.md`
7. the relevant GitHub issue and bill branch history

## Source of truth

Use this priority order:

1. Official source documents linked from each bill or enacted-law document.
2. `SPECIFICATION.md` for agreed product behavior.
3. Tracked repository files and Git history for the portable project record.
4. GitHub PRs and issues for workflow and discussion.

GitHub-only comments, reviews, labels, or descriptions must not be the sole location of legislative facts needed after an ordinary clone.

## Bill and pull-request workflow

- Use one branch and one GitHub pull request per bill.
- Preserve official bill revisions as ordered commits on that branch.
- Keep bill text, named backers, votes, actions, outcomes, and source URLs in tracked documents.
- Failed, withdrawn, vetoed, pocket-vetoed, and lapsed measures close unmerged and receive the appropriate permanent tag.
- Do not merge PRs. Jim merges.

## Enacted-law contract

When a bill becomes law, its existing PR must:

1. add the complete enacted Public Law under `enacted/`;
2. apply every U.S. Code modification directed by that law under `effective/usc/`;
3. add or update its effective temporary and uncodified provisions under `effective/uncodified/`;
4. record the actual enactment mechanism and constitutional actor; and
5. include all supporting official source URLs.

The enacted-law document is not a substitute for editing the effective Code. If one law changes several titles or sections, every affected file must appear in that PR.

Before finalizing an enacted PR, incorporate current `main` if other enactments merged while the bill branch was open.

## Attribution and identity

- Use full human-readable names whenever referring to a sponsor, cosponsor, voter, President, or other person.
- The elected primary sponsor is the Git author for bill-branch commits.
- The repository importer or maintainer is the Git committer.
- List every supported sponsor and cosponsor in the tracked bill document.
- A stable identifier may appear beside a person's name for disambiguation, but never replaces the name.
- A yea vote does not make a member a sponsor, cosponsor, or backer.
- Do not create or use GitHub identities that impersonate elected officials.

## Votes and historical gaps

- Tie every officially recorded individual vote to the voter's full name and recorded position.
- For voice vote, unanimous consent, or another aggregate procedure without a member-level tally, record only the supported procedure and result.
- Never infer an individual's position from party, sponsorship, attendance, aggregate passage, or another person's vote.
- If a source does not identify a sponsor, revision, voter, or action, state that the checked sources do not identify it.
- Never fabricate or silently fill historical gaps.

## Evidence and neutrality

- Prefer GovInfo and Statutes at Large, OLRC, Congress.gov, official House and Senate records, and Library of Congress historical collections.
- Include source URLs in each bill and enacted-law document.
- Use secondary data only for a documented gap and label it accordingly.
- Keep descriptions of legislation, officials, votes, and outcomes politically neutral and factual.
- Do not represent this repository as an official legal publication or legal advice.

## Architecture and handoff

- Keep `docs/architecture.md` aligned with the repository.
- Update architecture documentation in the same commit whenever a change modifies directory structure, document contracts, source hierarchy, authorship rules, vote representation, effective-state handling, or PR/tag lifecycle.
- Record durable project decisions in `MEMORY.md` or `docs/decisions/`.
- Record source findings in `docs/findings/` and actionable follow-up in GitHub issues.
- Update `docs/handoff.md` before ending substantial work.

## Verification

No build or package installation is required. Before opening or updating a PR, run:

```bash
git diff --check
git status --short
git diff --stat main...HEAD
```

Then inspect the complete diff and verify:

- every factual claim has an identified source;
- names and vote positions match those sources;
- all Code changes directed by an enacted law are present;
- temporary and uncodified provisions are preserved when applicable;
- no unsupported individual votes or backers were introduced;
- architecture and handoff documentation remain accurate; and
- no unrelated files changed.

## Security

Never commit API keys, tokens, passwords, credentials, private keys, `.env` files, private data, production data, or personal device identifiers.
