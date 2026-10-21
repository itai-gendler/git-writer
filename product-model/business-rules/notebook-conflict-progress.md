---
appliesTo:
- type: entity
  id: notebook
  effect: changes
  facts:
  - Conflicted files
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
permits:
- actors:
  - writer
- unattended: true
---

# The conflict list changes through syncs and the Writer's version choices

A sync that stops on conflicts lists the conflicting files; each version the Writer keeps takes its file off the list, and a completed or aborted merge clears it.
