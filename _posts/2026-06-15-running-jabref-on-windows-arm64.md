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

Clone the OpenJFX repository:

```powershell
git clone https://github.com/openjdk/jfx.git
cd jfx
```

Build JavaFX and publish it to your local Maven repository:

```powershell
.\gradlew -PMAVEN_PUBLISH=true sdk publishJavafxPublicationToMavenLocal
```

This takes around 6–8 minutes on average.

When the build finishes, your local Maven repository (`%USERPROFILE%\.m2\repository\org\openjfx\`) will contain the freshly built JavaFX modules for Windows ARM64.

## 2. Configure JabRef to use your custom JavaFX

Clone JabRef (with submodules):

```powershell
git clone --recurse-submodules https://github.com/JabRef/jabref.git
cd jabref
```

Thanks to [JabRef #16000](https://github.com/JabRef/jabref/pull/16000), no file edits are needed. Two Gradle properties handle everything:

```powershell
.\gradlew -PjavafxVersion=+ -PuseMavenLocal=true :jabgui:run --no-configuration-cache
```

* `-PjavafxVersion=+` tells Gradle to use the latest JavaFX version found locally instead of the version pinned in `versions/build.gradle.kts`.
* `-PuseMavenLocal=true` lets Gradle resolve dependencies from your local Maven repository, where your custom JavaFX was just published.

The first build takes a few minutes but subsequent runs are faster.

## 3. Apply workarounds for ARM-specific issues

Some code changes are needed because of current gaps in JavaFX support for Windows ARM.

**WebView graceful degradation.** JavaFX's WebKit component is not yet built for Windows ARM, so any attempt to create a `WebView` instance throws a `NoClassDefFoundError` at runtime. JabRef uses `WebView` in its preview panel and a few other places, and the resulting crash prevents the application from launching at all.

The fix is to make `WebViewStore` catch the error and return `null` instead, and have the components that use `WebView` (`PreviewViewer`, `AiSummaryShowingView`, `MainTableTooltip`) handle the null gracefully - showing a placeholder where the preview would have been.

The full set of changes is available on this branch on my fork: [`faneeshh/jabref:fix/webview-graceful-degradation`](https://github.com/faneeshh/jabref/tree/fix/webview-graceful-degradation).

You can either cherry-pick those commits onto your local working branch, or apply the same null-handling pattern manually to the files listed above.

## Current limitations on Windows ARM64

- **Preview panel** is not functional. This is the most visible limitation - features that depend on `WebView` (the entry preview, AI summary view, table tooltips) show placeholders or are skipped. This will be resolved once JavaFX provides a WebKit build for Windows ARM64.

- **No official JavaFX ARM64 build** means readers need to rebuild JavaFX themselves whenever they want to update to a newer version.

## Acknowledgments

Thanks to [Marius Hanl](https://github.com/Maran23) for sharing the JavaFX build configuration and guidance throughout this setup. Progress on official Windows ARM64 support for JavaFX is tracked upstream at [JDK-8351905](https://bugs.openjdk.org/browse/JDK-8351905) and until that lands, the approach above is the practical way to run JabRef on these machines.
