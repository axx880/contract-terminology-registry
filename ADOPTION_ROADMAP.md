# Contract Terminology Adoption Roadmap

Status: ACTIVE
Date: 2026-09-09

Этот roadmap фиксирует порядок внедрения центрального `contract-terminology-registry` в существующие проекты экосистемы.

RegistryVersion сам по себе не меняется только из-за обновления roadmap. При каждом adoption-проекте используется актуальный `main` registry и фиксируется точный `DictionaryRevision`.

## Governance sources

Перед каждой migration/adoption задачей применять:

- `axx880/chatgpt-project-rules/main` → `PREFLIGHT.md` и `CONTRACT_TERMINOLOGY_RULES.md`;
- `axx880/agent-skills/main` → `skills/contract-terminology-integration-standard/SKILL.md`;
- актуальные domain standards конкретного проекта;
- canonical registry `data/*.json` из этого репозитория.

## Общий adoption cycle

Для каждого проекта:

1. зафиксировать текущую project baseline/schema;
2. зафиксировать `DictionaryVersion` и `DictionaryRevision` целевого registry;
3. собрать фактически используемые MachineName/IDs/display mappings;
4. сопоставить их с active terms и history;
5. классифицировать как `ACTIVE`, `LEGACY_MAPPED`, `NEW_SHARED`, `PROJECT_LOCAL` или `PROJECT_EXCEPTION`;
6. отсутствующие shared terms сначала утвердить в central registry;
7. спроектировать migration/compatibility конкретного проекта;
8. реализовать изменения project-specific schema/PQ/VBA/user layer;
9. выполнить применимые repository/workbook/runtime regression checks;
10. зафиксировать принятую project baseline и использованный DictionaryRevision.

## Порядок внедрения

### 1. `axx880/object-reference-data` — NEXT

Цель: построить Minimal Object References на уже утверждённой терминологии.

Ключевая граница:

- terminology registry определяет MachineName и смысл общих полей (`ObjectID`, `TMCID`, `Section` и др.);
- `object-reference-data` определяет реальные справочные значения, relationships, топологию и атрибуты;
- не создавать второй словарь определений терминов внутри reference-data;
- новые shared fields сначала сверять/добавлять в terminology registry.

Результат этапа должен дать устойчивый reference layer для следующих выгрузок.

### 2. `axx880/calculation-export-pq-vba` — PLANNED

Цель: привести DCT РАСЧЁТКИ к canonical MachineName и физически отделить raw DCT от русского USER_VIEW.

Особое внимание:

- legacy `Name` → `ItemName`;
- `NameSource` → `ItemNameSource`;
- `CalcGroupKey` остаётся доменным technical key и не становится `TMCID`;
- зафиксировать DictionaryVersion/Revision и DataContractVersion;
- не ломать принятую Stage 3 Candidate → Validate → Publish / Previous VALID архитектуру.

### 3. `axx880/jpr-ogbuz-pq` / ЖПР-Контроль — PLANNED

Цель: стабилизировать source identity и подготовить canonical terms для downstream Выгрузки ЖПР.

Особое внимание:

- `RowID` должен стать стабильным идентификатором записи, а не `ROW()`;
- физический номер строки при необходимости хранится как `SourceRow`;
- исходные/локальные/canonical item-name layers использовать только там, где они реально нужны;
- не вводить `SourceRowID` как новый canonical field.

### 4. `axx880/jpr-export-pq-vba` — PLANNED

Цель: мигрировать DCT_JPR_Install на canonical terminology после стабилизации источника.

Особое внимание:

- legacy `SourceRowID` → `RowID`;
- `MaterialID` → `TMCID`;
- `MaterialSourceName` → `ItemNameSource`;
- пересмотреть `RecordID` с учётом стабильного RowID;
- сохранить проверенную Stage 2 runtime architecture и не переписывать её без необходимости.

### 5. `axx880/purchase-export-pq-vba` — PLANNED

Цель: подготовить будущий публичный machine contract и убрать исторические локальные синонимы там, где это оправдано.

Особое внимание:

- `SheetName` → `SourceSheet`;
- `BaseQuantity` → `QuantityBase`;
- `ItemKey` пока сохраняется как local technical key и отдельно оценивается после внедрения TMCID;
- `ProjectID` не объединяется автоматически с `ObjectID`;
- существующий internal output не объявляется публичным DCT задним числом без отдельной migration задачи.

### 6. `axx880/object-analytics-global` / GLOBAL — PLANNED

Цель: потреблять уже нормализованные provider contracts и reference layer.

Правило: GLOBAL не должен становиться местом повторной нормализации терминов, которые обязаны быть исправлены у provider system.

### 7. `axx880/upo-object-workbook` и другие будущие системы — PLANNED

Цель: новые machine contracts сразу проектировать на canonical terminology без legacy migration, если система ещё не имеет принятого публичного schema contract.

## Change rule

Порядок может изменяться только осознанным project decision. Сам central registry не заставляет автоматически обновлять уже принятую систему: каждая migration выполняется отдельной задачей с собственной regression/acceptance точкой.
