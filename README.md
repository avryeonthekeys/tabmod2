# Tab Disable - Fabric 26.2

A tiny client-side Fabric mod for Minecraft Java Edition 26.2 that prevents the vanilla TAB player list overlay from rendering.

## Requirements

- Minecraft Java Edition 26.2
- Fabric Loader 0.19.3 or newer
- Java/JDK 25

Fabric API is **not required**.

## Build

This source archive intentionally does not bundle Gradle's binary wrapper JAR.

### Easiest: IntelliJ IDEA

1. Install JDK 25.
2. Install IntelliJ IDEA Community Edition.
3. Extract this project.
4. Open the extracted folder in IntelliJ IDEA.
5. When IntelliJ asks, import/sync the Gradle project.
6. Set the Gradle JVM to JDK 25 if needed.
7. Open the Gradle tool window and run `build`, or use a terminal with a local Gradle 9.x installation and run `gradle build`.
8. The finished mod JAR will be under `build/libs/`.

### Alternative: use the official Fabric project generator

Generate a Minecraft 26.2 Fabric project, then copy this project's `src`, `build.gradle`, `gradle.properties`, and `settings.gradle` over the generated project. The generated template includes `gradlew`, `gradlew.bat`, and `gradle/wrapper/gradle-wrapper.jar`. Then run:

Windows:

    .\\gradlew.bat build

macOS/Linux:

    ./gradlew build

The installable JAR will be under `build/libs/`.

## Install

1. Install Fabric Loader for Minecraft 26.2 in the Minecraft Launcher.
2. Copy the final `tab-disable-1.0.0.jar` into your Minecraft `mods` folder.
3. Launch the Fabric 26.2 profile.
4. Join a world/server and hold TAB. The vanilla player-list overlay should not appear.

## What it changes

The mod injects at the beginning of `PlayerTabOverlay.extractRenderState(...)` and cancels that method. It is client-only and does not change server packets or other players' clients.

## Build online with GitHub Actions (no local Gradle required)

1. Create a new empty GitHub repository.
2. Upload the **contents of this project folder** to the repository root (not the outer ZIP itself).
3. Open the repository's **Actions** tab.
4. Open **Build Fabric Mod** and choose **Run workflow**. A push to `main`/`master` also triggers it automatically.
5. When the workflow finishes, open that workflow run and download the `tab-disable-1.0.0` artifact.
6. Extract the downloaded artifact ZIP. Inside is `tab-disable-1.0.0.jar` — that is the actual Fabric mod file.
