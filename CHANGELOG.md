# Changelog

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
