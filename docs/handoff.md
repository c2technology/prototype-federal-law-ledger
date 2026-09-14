# Handoff

## Current state

- Final prototype requirements are in `SPECIFICATION.md`.
- Repository structure and lifecycle are in `docs/architecture.md`.
- Initial official-source reconnaissance is in `docs/sources.md`.
- Issue #1 implements the first bill and enacted-law slice for the June 1,
  1789 Oaths Act.
- The effective-state frontier is June 1, 1789. The Act's five substantive
  sections are under `effective/uncodified/` because the United States Code
  did not yet exist.
- No runtime, package installation, or build is required.
- Repository contribution and agent instructions are in `AGENTS.md`.

## Verified resources

The initial source map includes:

- GovInfo Statutes at Large and bulk data;
- Library of Congress early Statutes at Large and the First Congress chronology;
- OLRC U.S. Code downloads, classification tables, and Table III;
- Congress.gov bill, member, vote, coverage, and API resources;
- GovInfo Congressional Bills and Bill Status bulk XML;
- Clerk of the House vote pages/XML;
- Senate vote pages/XML; and
- Congress.gov presidential-action guidance.

## First imported enactment

- Bill record: `bills/congress-001/house-bill-oaths-act.md`.
- Enacted law: `enacted/congress-001/chapter-001-oaths-act.md`.
- Historical effective state:
  `effective/uncodified/congress-001/chapter-001-oaths-act.md`.
- Source and disposition review:
  `docs/findings/1789-oaths-act-source-review.md`.
- The checked sources identify a five-member House preparation committee but
  no modern-style primary sponsor, cosponsors, bill number, complete version
  sequence, or member-level passage votes. Those gaps are explicit in the
  bill and enacted-law records.
- Later research establishes that Revised Statutes §5596 repealed the
  original Act in 1874 and that sections 2 and 3 have later statutory
  descendants. Those future changes are documented but are not projected
  backward into the June 1, 1789 effective tree.

## Recommended following issue

Issue #2 should research and select one small modern enacted law whose official record includes complete bill text, backers, chamber action, enactment, and a limited direct Code amendment.

## Known risks

- Early bill-level records are incomplete.
- OCR from historical scans may require manual comparison with page images.
- Classification and subsequent repeal history may be more difficult than transcribing enacted text.
- A bill branch that stays open while other enactments merge may need to incorporate current `main` before its effective-state changes are finalized.

## Verification performed

- Specification citation mapping passed the grounded-citation checker.
- Repository scaffold files were reviewed for required paths and project constraints.
- Official source URLs were discovered through live web search on 2026-09-14.
- The complete five-section Act was compared with the official page images
  for 1 Stat. 23–24, including the printed `[House of]` brackets.
- OLRC Table III and later official codification/repeal sources were checked
  for the Act's current disposition.
