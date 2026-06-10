# gradle-conventions-android

> Gradle convention plugins for modern Android Compose projects — apply one line, get a sane Kotlin + Compose + lint baseline.

[![Status](https://img.shields.io/badge/status-in%20development-orange)](#roadmap)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![JitPack](https://img.shields.io/badge/JitPack-coming%20soon-lightgrey)](#install)

## Why

Modern Android projects with Kotlin DSL repeat the same setup in every module: `compileSdk`, `minSdk`, Kotlin compiler options, Compose enablement, Java toolchain, lint config. Convention plugins centralize this so each module's `build.gradle.kts` becomes a 3-line apply instead of a 30-line copy-paste.

This repo ships three plugins designed to work together:

| Plugin ID | Apply to | Sets up |
| --- | --- | --- |
| `dev.hidev.android.app` | `:app` module | Android application defaults + Kotlin + lint |
| `dev.hidev.android.library` | Any `:core:*` / `:feature:*` module | Android library defaults + Kotlin + lint |
| `dev.hidev.android.compose` | Any module using Compose | BOM, compiler flags, runtime check |

## Install *(coming soon)*

Once published via JitPack, in your root `settings.gradle.kts`:

```kotlin
pluginManagement {
    repositories {
        google()
        mavenCentral()
        gradlePluginPortal()
        maven("https://jitpack.io")
    }
}
```

Then in your module `build.gradle.kts`:

```kotlin
plugins {
    id("dev.hidev.android.library")
    id("dev.hidev.android.compose")
}
```

That's it — no manual `compileSdk`, no Compose compiler boilerplate.

## What you get out of the box

- **`compileSdk` / `minSdk` / `targetSdk`** pinned to project-wide constants
- **Java 17 toolchain** + Kotlin JVM target alignment
- **Compose** enabled with the right compiler flags (no manual `compose = true` + extension version dance)
- **Kotlin warnings as errors** (configurable)
- **Lint baseline** + reasonable defaults
- **Unit test config** that doesn't fight you

## Roadmap

- [ ] v0.1 — Scaffold + README *(this commit)*
- [ ] v0.2 — `android-library` plugin minimum viable
- [ ] v0.3 — `android-app` plugin
- [ ] v0.4 — `android-compose` plugin
- [ ] v0.5 — JitPack publish + first real consumer (android-template-base)
- [ ] v1.0 — Docs site + examples

## Part of the `android-template-base` ecosystem

This is repo #1 of a planned set:

- [gradle-conventions-android](https://github.com/duonglkh/gradle-conventions-android) *(this repo)*
- [android-versioncat-stack](https://github.com/duonglkh/android-versioncat-stack)
- [android-template-base](https://github.com/duonglkh/android-template-base) — the showcase scaffold
- compose-theme-kit · compose-onboarding · compose-locale-switcher · compose-settings · compose-error-states · compose-permission · connectivity-flow · datastore-prefs-kit

See [duonglkh.github.io](https://duonglkh.github.io/#projects) for the full roster.

## License

MIT © 2026 Hung Duong
