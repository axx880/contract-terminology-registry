# Contract Terminology Registry v0.4.0

Date: 2026-10-07  
Status: VALID

## Purpose

Enable Object Reference Stage 4 Publish/Exchange for multiple consumers through a single owner-resolved TMC identifier.

## Added

- `CurrentTMCID` (`TERM-0067`) — the current TMC identifier after an accepted Object Reference merge/alias decision.
- Source `REF_STAGE4` documenting the provider/consumer architecture.

## Semantics

- `TMCID` remains the immutable issued identifier and traceability key.
- `CurrentTMCID` is used by consumers for current links, grouping and downstream exchange.
- With no alias, `CurrentTMCID = TMCID`.
- Multiple historical `TMCID` values may resolve to the same `CurrentTMCID`.
- Alias chains are forbidden by the Object Reference owner; consumers do not implement merge logic independently.

## Compatibility

This is additive. Existing active terms are not renamed or removed. Projects adopt v0.4.0 explicitly and pin the exact `DictionaryRevision`.

## Validation

- canonical JSON schema/custom invariants: PASS;
- Excel content synchronization / formula scan / OOXML integrity: PASS;
- final manifest pins the exact release files plus Rules/Skills commits;
- merge to `main` remains the final release action.
