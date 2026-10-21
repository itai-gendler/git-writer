---
entities:
- entity: note
  shows:
  - Name
  - Content
  collects:
  - Content
- entity: image
  shows:
  - Name
  - Content
- entity: notebook
  shows:
  - Name
  - Open files
  - Active file
  - Sync status
  - Network status
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreen.kt
---

# Editor

The selected file, its editable Markdown or image content, open file selections, and synchronization status.
