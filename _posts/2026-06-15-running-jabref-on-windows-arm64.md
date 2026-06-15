---
title: Running JabRef on Windows ARM64
tags: [setup, javafx, arm]
author: faneesh
---

Windows on ARM is becoming more common under the influence of Surface laptops, Copilot+ PCs and other devices shipping with ARM64 processors. But running Java desktop applications on these machines is still a challenge: JavaFX, which JabRef relies on for its user interface, does not yet provide official builds for Windows ARM64.

This post walks through how to run JabRef on a Windows ARM64 machine. Note that this is an **experimental setup**, not an officially supported configuration. The preview panel in particular will not work, because the WebKit component of JavaFX is not yet available for Windows ARM. Everything else such as the main interface, entry editor, search, groups, import/export runs fine.

The setup has two parts: build JavaFX from source for your machine, then configure JabRef to use it.

## Prerequisites

Before you begin, install the following :

* **JDK 25** - [Amazon Corretto 25](https://docs.aws.amazon.com/corretto/latest/corretto-25-ug/downloads-list.html) is recommended.
* **Visual Studio 2022 Community** with the "Desktop development with C++" workload - required to compile JavaFX's native components.
* **Git** - for cloning the repositories.
* **cmake**, **ninja**, and **ant** - required by the JavaFX build.

## 1. Build JavaFX from source

Clone the OpenJFX repository and add Marius Hanl's fork as a remote. His fork includes a small commit that fixes sources publishing, which is needed for IntelliJ to resolve JavaFX classes correctly.

```powershell
git clone https://github.com/openjdk/jfx.git
cd jfx
git remote add maran https://github.com/Maran23/jfx.git
git fetch maran local-dev
```

Cherry-pick the sources-publishing commit from his `local-dev` branch:

```powershell
git cherry-pick 9e9d43e8bb
```

Now build JavaFX and publish it to your local Maven repository:

```powershell
.\gradlew sdk -PCONF=Release -PMAVEN_PUBLISH=true -PMAVEN_VERSION=custom publishToMavenLocal
```

This takes around 6–8 minutes on average. The `-PMAVEN_VERSION=custom` flag labels the published artifacts as version `custom` - JabRef will reference this name in the next section.

When the build finishes, your local Maven repository (`%USERPROFILE%\.m2\repository\org\openjfx\`) will contain the JavaFX modules under the `custom` version, including the `-win.jar` classifier jars that hold the actual classes for your platform.

## 2. Configure JabRef to use your custom JavaFX

Clone JabRef:

```powershell
git clone https://github.com/JabRef/jabref.git
cd jabref
```

Four files need small edits to point JabRef at your locally built JavaFX.

**Set the JavaFX version to `custom`** in `versions/build.gradle.kts`:

```kotlin
val javafx = "custom"
```

**Add `mavenLocal()` as a repository** in `build-logic/src/main/kotlin/org.jabref.gradle.base.repositories.gradle.kts`. Add it as the first entry so Gradle checks your local Maven repository before remote sources:

```kotlin
repositories {
    mavenLocal()
    mavenCentral()
    // ... existing entries
}
```

**Register the Windows ARM64 target** in `build-logic/src/main/kotlin/org.jabref.gradle.base.dependency-rules.gradle.kts`. Find the section listing JavaFX targets and add the ARM64 line:

```kotlin
addJfxTarget(jfxModule, "win", OperatingSystemFamily.WINDOWS, MachineArchitecture.X86_64)
addJfxTarget(jfxModule, "win-aarch64", OperatingSystemFamily.WINDOWS, MachineArchitecture.ARM64)
```

**Configure the toolchain** in `gradle.properties` to point at your installed JDK 25 and disable auto-download (which currently fails on Windows ARM):

```properties
org.gradle.java.installations.paths=C:\\Program Files\\Amazon Corretto\\jdk25.0.3_9
org.gradle.java.installations.auto-download=false
```

Adjust the path if your Corretto installation is elsewhere.

## 3. Apply workarounds for ARM-specific issues

Two small code changes are needed because of current gaps in JavaFX support for Windows ARM.

**WebView graceful degradation.** JavaFX's WebKit component is not yet built for Windows ARM, so any attempt to create a `WebView` instance throws a `NoClassDefFoundError` at runtime. JabRef uses `WebView` in its preview panel and a few other places, and the resulting crash prevents the application from launching at all.

The fix is to make `WebViewStore` catch the error and return `null` instead, and have the components that use `WebView` (`PreviewViewer`, `AiSummaryShowingView`, `MainTableTooltip`) handle the null gracefully - showing a placeholder where the preview would have been.

The full set of changes is available on this branch on my fork: [`faneeshh/jabref:fix/webview-graceful-degradation`](https://github.com/faneeshh/jabref/tree/fix/webview-graceful-degradation).

You can either cherry-pick those commits onto your local working branch, or apply the same null-handling pattern manually to the files listed above.

You can either cherry-pick those commits onto your local working branch, or apply the same null-handling pattern manually to the files listed above.

**ThemeManager stub.** JabRef calls `Scene.getPreferences()` (a JavaFX 27 API used for syncing with the operating system's light/dark theme). Due to how JavaFX publishes its artifacts, this method is not visible on the compile classpath in this setup, even though it exists at runtime.

Comment out the three calls in `jabgui/src/main/java/org/jabref/gui/theme/ThemeManager.java` (around line 170):

```java
// if (Objects.equals(type, Theme.Type.LIGHT)) {
//     scene.getPreferences().setColorScheme(ColorScheme.LIGHT);
// } else if (Objects.equals(type, Theme.Type.DARK)) {
//     scene.getPreferences().setColorScheme(ColorScheme.DARK);
// } else {
//     scene.getPreferences().setColorScheme(null);
// }
```

This disables automatic theme syncing with the OS - JabRef will still respect manually selected themes from its preferences. This is a local workaround only; do not commit it upstream.

## 4. Run JabRef

From the `jabref` directory:

```powershell
.\gradlew :jabgui:run --no-configuration-cache
```

The first build takes a few minutes. Subsequent runs are faster.

When JabRef launches, the main window, entry table, entry editor, search, groups, and import/export all function normally. The preview panel will show a placeholder message instead of the usual rendered preview, because the WebKit component is unavailable on this platform.

## Current limitations on Windows ARM64

- **Preview panel** is not functional. This is the most visible limitation - features that depend on `WebView` (the entry preview, AI summary view, table tooltips) show placeholders or are skipped. This will be resolved once JavaFX provides a WebKit build for Windows ARM64.

- **Automatic OS theme syncing** is disabled by the local stub above.

- **No official JavaFX ARM64 build** means readers need to rebuild JavaFX themselves whenever they want to update to a newer version.

## Acknowledgments

Thanks to [Marius Hanl](https://github.com/Maran23) for sharing the JavaFX build configuration and guidance throughout this setup. Progress on official Windows ARM64 support for JavaFX is tracked upstream at [openjdk/jfx](https://github.com/openjdk/jfx) and until that lands, the approach above is the practical way to run JabRef on these machines.
