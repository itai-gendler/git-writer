---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Conflicted files
  - Sync status
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
---

# A failed push retains the locally committed conflict resolution

Resolving all conflicts commits the result locally before pushing. Push failure is reported separately so a later sync can upload that resolution.
