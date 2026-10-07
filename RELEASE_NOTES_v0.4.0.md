# Contract Terminology Registry v0.4.0

Date: 2026-10-07  
Status: RELEASE CANDIDATE — validation pending

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

## Release gate

Before merge to `main` as VALID:
1. validate canonical JSON and invariants;
2. regenerate and validate `exports/Contract_Terminology_Dictionary_v0.4.0.xlsx`;
3. update the registry manifest with final hashes/sizes and Rules/Skills commits;
4. review branch diff and merge through PR.
