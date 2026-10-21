---
entities:
- entity: notebook
  shows:
  - Name
  - Remote URL
  - Username
  collects:
  - Name
  - Remote URL
  - Username
  - Password or token
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/edit_notebook/EditNotebookDialog.kt
---

# Edit notebook

The selected notebook’s name and remote connection.
