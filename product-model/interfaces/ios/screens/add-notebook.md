---
entities:
- entity: notebook
  collects:
  - Name
  - Remote URL
  - Username
  - Password or token
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/create_notebook/CreateNotebookDialog.kt
---

# Add notebook

Create a notebook or clone one from a remote repository, in storage the app manages.
