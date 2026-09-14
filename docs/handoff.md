# Handoff

## Current state

- Final prototype requirements are in `SPECIFICATION.md`.
- Repository structure and lifecycle are in `docs/architecture.md`.
- Initial official-source reconnaissance is in `docs/sources.md`.
- No law or bill has been imported.
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

## Next working issue

Import the June 1, 1789 Oaths Act as the first complete enactment slice. Before writing its text:

1. inspect the exact Volume 1 pages;
2. identify its Statutes at Large citation;
3. identify supported House/Senate actions and vote evidence;
4. determine its Code/uncodified disposition from OLRC and subsequent official law;
5. write acceptance scenarios in the issue; and
6. open one bill branch/PR without inventing unavailable sponsors or votes.

## Recommended following issue

Research and select one small modern enacted law whose official record includes complete bill text, backers, chamber action, enactment, and a limited direct Code amendment. Selection should be a documented issue before import begins.

## Known risks

- Early bill-level records are incomplete.
- OCR from historical scans may require manual comparison with page images.
- Classification and subsequent repeal history may be more difficult than transcribing enacted text.
- A bill branch that stays open while other enactments merge may need to incorporate current `main` before its effective-state changes are finalized.

## Verification performed

- Specification citation mapping passed the grounded-citation checker.
- Repository scaffold files were reviewed for required paths and project constraints.
- Official source URLs were discovered through live web search on 2026-09-14.
