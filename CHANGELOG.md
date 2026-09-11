# Changelog

## 0.2.0 — 2026-09-11

Stage 1 terminology gate for `axx880/object-reference-data`.

### Added
- `ObjectShortName` — short object name for the object reference layer;
- `ObjectProjectName` — full object name according to project documentation;
- `ObjectContractName` — full object name according to contract documentation;
- `LocationRoom` — structured room/location component for `OBJECT_REFERENCE`.

### Changed
- `NR-007` location-family examples now include `LocationRoom`;
- all canonical registry payloads are versioned as `0.2.0`;
- regenerated user-readable Excel dictionary from the canonical JSON.

### Compatibility
- changes are additive for consumers pinned to registry `0.1.0`;
- historical `HIST-0007` remains an early JPR-specific exclusion and is not treated as a prohibition on the new `OBJECT_REFERENCE` scope;
- `Article`, `Manufacturer` and `Unit` are not widened to `OBJECT_REFERENCE` in this release; that decision remains deferred to the TMC integration checkpoint.

## 0.1.0 — 2026-09-09

Initial canonical registry release.

### Added
- canonical cross-project terminology registry;
- naming/prefix assignment rules;
- migration history for superseded, removed and excluded MachineName;
- JSON Schema validation;
- Excel user view generated from the same registry content.

### Key decisions
- `SourceRow` = physical source row number;
- `RowID` = stable record identity passed downstream;
- `SourceRowID` → superseded by `RowID`;
- `ItemName` = local/working item name;
- `ItemNameSource` = exact source value;
- `CanonicalItemName` = shared reference name;
- `TMCID` = canonical cross-system material identifier;
- `ItemKey` remains a local technical key until later migration.
