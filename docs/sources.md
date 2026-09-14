# Official Source Inventory

**Reconnaissance date:** 2026-09-14

This is the initial source map for building Federal Law Ledger. It favors official, public, source-of-truth material. Coverage limits are part of the data contract.

## 1. Enacted laws and Statutes at Large

### GovInfo — Statutes at Large

- Collection help: https://www.govinfo.gov/help/statute
- Browse collection: https://www.govinfo.gov/app/collection/STATUTE
- Bulk-data root: https://www.govinfo.gov/bulkdata

Use for:

- official chronological enacted law;
- Public and Private Law text;
- Statutes at Large citations;
- modern PDF and available USLM packages.

Verified finding: GovInfo describes the Statutes at Large as the permanent collection of laws and resolutions enacted during each congressional session, with coverage beginning in 1789. Its help page states that day-forward USLM is available from 2003.

### Library of Congress — early Statutes at Large

- First Congress guide: https://wwws.loc.gov/law/help/statutes-at-large/1st-congress.php
- Volumes 1–5 chronology: https://www.loc.gov/collections/united-states-statutes-at-large/articles-and-essays/vol1-5
- Volume 1 catalog record: https://www.loc.gov/item/llsl-v1
- First Congress PDF: https://tile.loc.gov/storage-services/service/ll/llsl/llsl-c1/llsl-c1.pdf

Use for:

- early enactments not covered by modern GovInfo USLM;
- page images and PDFs of Volume 1;
- chronological act titles, chapter numbers, and enactment dates.

Verified starting point: the Library of Congress chronology identifies Chapter 1, “An Act to regulate the Time and Manner of administering certain Oaths,” dated June 1, 1789, as the first listed public Act of the First Congress.

## 2. Effective U.S. Code and classification

### Office of the Law Revision Counsel

- U.S. Code downloads: https://uscode.house.gov/download/download.shtml
- Classification explanation: https://uscode.house.gov/about_classification.xhtml
- Classification tables: https://uscode.house.gov/classification/priortables.shtml
- Table III, Statutes at Large to Code: https://uscode.house.gov/table3/statutesatlargevolume1.htm
- Detailed Code guide: https://uscode.house.gov/detailed_guide.xhtml

Use for:

- current and prior-release U.S. Code text;
- title and section organization;
- mapping Public Law provisions to Code sections and notes;
- identifying amended, enacted, omitted, repealed, transferred, and note provisions.

Verified finding: OLRC publishes downloadable U.S. Code formats and classification tables. Table III provides bulk XML and act-level mappings between Statutes at Large provisions and the Code.

Project rule: OLRC classification is the preferred source for determining where an enacted provision belongs. The enacted Act remains preserved even when a provision is classified to a Code note or omitted from ordinary Code sections.

## 3. Bills, sponsors, cosponsors, versions, and actions

### Congress.gov

- Legislation: https://www.congress.gov/legislation
- Coverage dates: https://www.congress.gov/help/coverage-dates
- Legislation-text guide: https://www.congress.gov/help/legislation-text
- API: https://api.congress.gov/
- API documentation repository: https://github.com/LibraryOfCongress/api.congress.gov

Use for:

- bill identifiers and titles;
- sponsors and cosponsors;
- official actions;
- text-version links;
- amendments;
- law relationships;
- modern House vote links; and
- member identifiers.

Coverage warning: Congress.gov reports broad legislation metadata from the 93rd Congress forward, bill text in modern formats mainly from the 103rd Congress forward, and uneven or absent historical bill text for many earlier periods. Every import must state the detail actually available for its Congress.

API note: the Congress.gov API requires an API key. The documentation-only prototype does not require the API; public web and bulk sources can be used manually. Never commit an API key.

### GovInfo — Congressional Bills and Bill Status

- Congressional Bills help: https://www.govinfo.gov/help/bills
- Bill Status bulk data: https://www.govinfo.gov/bulkdata/BILLSTATUS
- Developer hub: https://www.govinfo.gov/developers

Use for:

- published bill text versions;
- enrolled text;
- structured bill-status actions; and
- bulk XML when later import work justifies it.

Verified coverage:

- GovInfo bill help states that all published bill versions are available from the 103rd Congress forward.
- GovInfo developer documentation lists Bill Status XML from the 108th Congress forward and Congressional Bill Text XML from the 113th Congress forward.

## 4. Votes

### Congress.gov vote guide

- https://www.congress.gov/help/votes-in-the-house-and-senate

Use for locating recorded floor votes and committee-report vote records. Congress.gov states that recorded floor votes appear in legislative actions and the Congressional Record, while committee votes often appear in committee reports.

### Clerk of the U.S. House

- Vote browser: https://clerk.house.gov/Votes
- Example machine-readable vote: https://clerk.house.gov/evs/2023/roll118.xml

Use for:

- House roll-call metadata;
- official totals; and
- individual member positions in available XML.

### U.S. Senate

- Vote browser: https://www.senate.gov/votes
- XML-source index: https://www.senate.gov/general/XML.htm

Use for:

- Senate roll-call metadata;
- official totals; and
- individual senator positions in available XML.

Repository rule: when the official proceeding is a voice vote, unanimous consent, or another method without an individual tally, record only the aggregate method and result.

## 5. Members and identity resolution

### Biographical Directory of the United States Congress

- https://bioguide.congress.gov/

### Congress.gov members

- https://www.congress.gov/members

Use for:

- full human-readable names;
- Bioguide identifiers;
- chamber, state, district, and service dates; and
- disambiguating people with similar names.

Names remain primary in every human-facing document. Identifiers are supplemental.

## 6. Presidential action

- Congress.gov process guide: https://www.congress.gov/legislative-process/presidential-action
- Public Law or bill action record for the specific measure.

Use for distinguishing:

- presidential signature;
- enactment without signature;
- veto;
- pocket veto; and
- congressional veto override.

The repository maintainer's technical GitHub merge is never presented as the constitutional actor.

## 7. Initial source plan

### First working import

For the June 1, 1789 Oaths Act:

1. Use the Library of Congress First Congress guide to establish chronology and locate the Act.
2. Use the Volume 1 scan/PDF for enacted text and Statutes at Large pagination.
3. Check OLRC Table III for later classification and disposition.
4. Check House and Senate journals or other official historical records for supported actions or votes.
5. State explicitly when no individual sponsor or vote evidence is available.

### First modern import

Choose a small Public Law with:

- an official introduced and enrolled bill text;
- a named sponsor and manageable cosponsor list;
- recorded or clearly aggregate chamber actions;
- a direct, reviewable U.S. Code amendment; and
- an OLRC classification-table entry.

Avoid selecting the modern example until its complete source chain has been checked.

## 8. Research findings and open questions

- The first enactment can be sourced now from the Library of Congress collection.
- Modern source coverage is much richer and can support the full bill/revision/backer/vote/enactment/Code-change model.
- Historical reconstruction will be uneven. Enacted text can often be recovered where bill revisions, named sponsors, or member-level votes cannot.
- OLRC classification tables are the key bridge between a Public Law and resulting Code files.
- A modern pilot law still needs to be selected based on source completeness and small diff size.
- The First Congress Oaths Act needs a source-level determination of what remained effective, what was superseded or repealed, and whether it has an ordinary current Code destination.
