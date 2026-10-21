---
appliesTo:
- type: entity
  id: notebook
  effect: changes
  facts:
  - Network status
permits:
- unattended: true
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/utils/NetworkUtils.kt
---

# The Product observes notebook connectivity

Network and foreground changes trigger unattended remote-reachability checks for the selected notebook.
