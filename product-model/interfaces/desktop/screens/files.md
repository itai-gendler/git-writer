---
entities:
- entity: notebook
  shows:
  - Name
  - Active
- entity: note
  shows:
  - Name
  - Path
  collects:
  - Name
- entity: folder
  shows:
  - Name
  - Path
  collects:
  - Name
- entity: image
  shows:
  - Name
  - Path
  collects:
  - Name
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarContent.kt
---

# Notebook files

The active notebook’s folders, notes and images.
