# Android Build Time Optimizer

An IntelliJ IDEA / Android Studio plugin for Android Gradle build-time checks and one-click configuration tweaks.

The plugin helps Android developers inspect project build configuration, add Gradle optimization flags, and detect source-layout patterns that can make builds slower.

## Features

- Apply all supported optimizations from a single IDE menu action.
- Add or adjust common `gradle.properties` flags for Android build features, Jetifier, Gradle daemon, non-transitive `R` classes, parallel execution, and configuration cache.
- Update Android `debug` build type settings in `build.gradle` / `build.gradle.kts`:
  - `crunchPngs false`;
  - `minifyEnabled false`;
  - `shrinkResources false`.
- Highlight `gradle.properties` values that may slow builds down and offer quick fixes.
- Report modules that mix Java and Kotlin source files in the same source tree.

## Installation

Download the plugin JAR from [`jars/`](jars/) and install it manually:

`Settings/Preferences` > `Plugins` > `Install Plugin from Disk...`

Then select the downloaded JAR file and restart the IDE if requested.

## Usage

Open an Android project's `gradle.properties`, `build.gradle`, or `build.gradle.kts` file.

Use the main menu:

`Android Build Time Optimizer` > `Optimize All`

Or apply one optimization at a time:

`Android Build Time Optimizer` > `Optimizations`

After applying changes, review the generated Gradle edits before committing them. Some build features should only be disabled when the project does not use them.

## Inspections

The plugin includes an inspection for modules that contain both Java and Kotlin files.

To configure it:

`Preferences` > `Editor` > `Inspections` > `Android Build Time Optimizer` > `Mixed Java and Kotlin sources in one module`

## Build from Source

```bash
./gradlew buildPlugin
```

The plugin artifact will be generated under `build/distributions/`.

## Demo

[<img src="https://img.youtube.com/vi/ioheOYLuvAE/maxresdefault.jpg" width="50%">](https://youtu.be/ioheOYLuvAE)

## Notes

This plugin edits Gradle files using text-based rules. Always review the resulting diff and run a local build after applying optimizations.
