# radian-mesh-failure-forge

`radian-mesh-failure-forge` explores distributed systems with a small SQL codebase and local fixtures. The technical goal is to implement an SQL distributed systems project for failure resource planning, using capacity fixtures and allocation and spill reports.

## Project Rationale

The project exists to keep a narrow engineering decision visible and testable. For this repo, that decision is how quorum health and replica lag should influence a review result.

## Radian Mesh Failure Forge Review Notes

`recovery` and `baseline` are the cases worth reading first. They show the optimistic and cautious ends of the fixture.

## Feature Set

- `fixtures/domain_review.csv` adds cases for quorum health and lease drift.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/radian-mesh-failure-walkthrough.md` walks through the case spread.
- The SQL code includes a review path for `membership churn` and `quorum health`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## Architecture

The fixture data drives the tests. The code stays thin, while `metadata/domain-review.json` and `config/review-profile.json` explain what each case is meant to protect.

The SQL checks add a separate view over the domain review fixture.

## Usage

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Test Command

The verifier is intentionally local. It should fail if the fixture score math, lane assignment, or language-specific test drifts.

## Next Improvements

The fixture set is small enough to audit by hand. The next useful expansion is malformed input coverage, not extra surface area.
