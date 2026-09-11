# Release Notes — Contract Terminology Registry v0.2.0

Date: 2026-09-11
Status: VALIDATED FOR MERGE

## Purpose

This release closes the Stage 1 terminology gate required by `axx880/object-reference-data` before implementation of the Reference Core public contracts.

## Added shared terms

- `ObjectShortName`
- `ObjectProjectName`
- `ObjectContractName`
- `LocationRoom`

All four terms are ACTIVE and scoped to `OBJECT_REFERENCE` in this release. Future consumers adopt them through their own project migration/contract workflow.

## Preserved boundaries

- `LocationID` and `SectionID` remain deferred.
- `Article`, `Manufacturer`, and `Unit` are not widened to `OBJECT_REFERENCE`; that is deferred to TMC Checkpoint B.
- No shared TMC formation-status enum is introduced.
- No shared MachineName for the optional section description is introduced.
- `HIST-0007 LocationRoom = EXCLUDED` remains historical evidence for an early JPR baseline and does not retroactively enable `LocationRoom` in JPR.

## Validation

Canonical JSON is validated against the current schemas and custom invariants. The Excel user view is regenerated from the same canonical data and is not an independent source of truth.
