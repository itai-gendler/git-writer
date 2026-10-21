---
scope: Notebook lifecycle, Markdown editing, file organization, repository connections, synchronization and conflict
  recovery across desktop, Android and iOS.
method: Static tracing from product text and app entry points through UI actions, persistence and both Git implementations.
covered:
- description: Notebook registration, activation and connection code.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/
  - shared/src/commonMain/kotlin/dev/jotalac/core/data/ActiveNotebookManager.kt
- description: Markdown editor, file hierarchy, local file operations and image handling code.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/feature/editor/
  - shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/
  - shared/src/commonMain/kotlin/dev/jotalac/core/utils/FileUtils.kt
- description: Synchronization orchestration, conflict recovery and platform Git implementations.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/feature/git_sync/
  - shared/src/jvmAndAndroidMain/kotlin/dev/jotalac/feature/git_sync/
  - shared/src/iosMain/kotlin/dev/jotalac/feature/git_sync/
- description: App entry points, preferences and settings surfaces.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/App.kt
  - shared/src/commonMain/kotlin/dev/jotalac/core/data/UserSettingsManager.kt
  - shared/src/commonMain/kotlin/dev/jotalac/feature/settings/
  - desktopApp/src/main/kotlin/dev/jotalac/main.kt
  - androidApp/src/main/kotlin/dev/jotalac/MainActivity.kt
  - shared/src/iosMain/kotlin/dev/jotalac/MainViewController.kt
- description: Connectivity status and desktop spelling integration.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/core/utils/NetworkUtils.kt
  - shared/src/jvmMain/kotlin/dev/jotalac/feature/editor/ui/spellcheck/
- description: Notebook-root image reference resolution.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/core/utils/ImageLoaderConfig.kt
exclusions:
- description: Build, release and native-library packaging code; no end-user product behavior.
  paths:
  - .github/
  - gradle/
  - tools/
  - proguard/
  - build.gradle.kts
  - shared/build.gradle.kts
- description: Rendering styles, visual resources and window decoration; presentation implementation.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/core/ui/
  - shared/src/commonMain/composeResources/
  - desktopApp/src/main/kotlin/dev/jotalac/window/
- description: Database schema and dependency wiring; implementation structure.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/core/database/
  - shared/src/commonMain/kotlin/dev/jotalac/core/di/
  - shared/schemas/
unmapped:
- description: Android home-screen widget and its launch selection; secondary surface outside the core notebook
    workflow.
  paths:
  - androidApp/src/main/kotlin/dev/jotalac/widget/
  - shared/src/androidMain/kotlin/dev/jotalac/feature/widget/
- description: Plain-text clipboard handling in the editor; a host editing convenience outside the core workflows.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/core/utils/ClipboardUtils.kt
- description: Platform image zoom and trackpad gesture details; secondary image-viewing interactions beyond opening
    images.
  paths:
  - shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/ZoomableImage.kt
  - shared/src/commonMain/kotlin/dev/jotalac/feature/editor/platform/TrackpadPinchZoom.kt
limitations:
- description: Keeping the deleted side of a conflict in the desktop and Android Git adapter, whose outcome the
    source alone does not establish; only the iOS deletion path has a scenario.
  paths:
  - shared/src/jvmAndAndroidMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.jvm.kt
---

# Coverage


