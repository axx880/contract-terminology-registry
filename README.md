# Contract Terminology Registry

Central source of truth for terminology, MachineName, Russian display names, naming rules, and migration history across the project ecosystem.

Current registry version: **0.1.0**

## Canonical machine-readable source
- `data/terms.json`
- `data/naming-rules.json`
- `data/history.json`
- `data/sources.json`

Schemas are stored in `schema/`.

## User view
`exports/Contract_Terminology_Dictionary_v0.1.0.xlsx` is generated from the same canonical registry content and is not an independent source of truth.

## Versioning
- `RegistryVersion` uses semantic versioning.
- Exact `DictionaryRevision` for a consuming project is the Git commit SHA containing the registry state used by that project.
- `DictionaryVersion` and `DataContractVersion` are independent.

## Principles
1. Similar names are never unified automatically.
2. `ID` = stable identity; `Key` may be a local/composite technical key.
3. `Source<Entity>` = provenance coordinate (`SourceID`, `SourceFile`, `SourceSheet`, `SourceRow`).
4. `<Field>Source` = exact original field value.
5. `Canonical<Field>` = value from a shared approved reference registry.
6. `DCT_` is reserved for public cross-system machine contracts.
7. Specific contract names and project-specific role codes do not become global rules automatically.

## Change workflow
Review/decision → canonical JSON update → schema/custom validation → regenerate Excel → GFD/validation → branch → diff → PR → merge.
