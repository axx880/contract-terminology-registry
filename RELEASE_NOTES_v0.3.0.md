# Contract Terminology Registry v0.3.0

Date: 2026-09-16  
Status: RELEASE CANDIDATE — Excel user view validation pending

## Purpose

Enable the Object Reference Stage 3 TMC Registry / Checkpoint B public contract without introducing new shared MachineName.

## Scope changes

The following existing ACTIVE terms are widened to `OBJECT_REFERENCE`:

- `Article` (`TERM-0004`);
- `Unit` (`TERM-0005`);
- `Manufacturer` (`TERM-0006`).

Their semantic meaning remains unchanged. `TMCID`, `ObjectID`, `Section` and `CanonicalItemName` already cover the required Object Reference semantics and are unchanged by this release.

## Compatibility

This is an additive terminology release:

- no active MachineName is removed or renamed;
- no legacy mapping changes;
- consumers pinned to `0.2.0` remain valid;
- projects adopt `0.3.0` explicitly and pin the exact `DictionaryRevision`.

## Dependent project

`axx880/object-reference-data` Stage 3 / Checkpoint B uses the following `DCT_ORD_TMC` fields:

`TMCID, ObjectID, Section, CanonicalItemName, Article, Manufacturer, Unit`.

## Release gate

Before merge to `main` as a VALID registry release:

1. validate all four canonical JSON payloads against their schemas and custom invariants;
2. regenerate `exports/Contract_Terminology_Dictionary_v0.3.0.xlsx` from canonical data;
3. verify Excel content synchronization, ZIP integrity and formula-error scan;
4. update `manifest/registry-manifest.json` with final SHA-256/size evidence and current Rules/Skills commits;
5. review branch diff and merge through PR.
