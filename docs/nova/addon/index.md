**This guide is not beginner-friendly! Making Nova addons requires a lot of knowledge about Kotlin, the Spigot API, Maven and Gradle.**

## Prerequisites

### IntelliJ

Even though Eclipse does have Kotlin support via a plugin, it's not the best option. We recommend using [IntelliJ](https://www.jetbrains.com/idea/)
to make addons.

### GitHub

This guide uses a GitHub repo template so having a GitHub account is recommended. You can also install [GitHub Desktop](https://desktop.github.com/)
if you don't want to use git commands.

## Setting up your project

You can now create a new repo using our addon template [here](https://github.com/xenondevs/Nova-Addon-Template/generate).
After creating the new repo and cloning it, make sure to edit the following files:

### src/main/kotlin

Change the package name to your own.

### settings.gradle.kts

Change `rootProject.name` to your addon id.

### build.gradle.kts

Change `group` to your group.  
Change `version` to your version.

In the `addon` task, set `main` to your addon main class.

## Adding dependencies

If your addon requires dependencies that need to be present at runtime, add them under the `nova` configuration:

```kotlin title="build.gradle.kts dependencies { }"
nova("commons-net:commons-net:3.8.0")
```

## Building

To build, run
```bash title="Build with Gradle"
gradlew addonJar -PoutDir="<Path to your addons directory here>"
```

## Enabling dev mode

To enable dev mode, add the `NovaDev` argument using `-DNovaDev`.  
This allows you to bypass some restrictions like using addons that require a different version of Nova and
enables general-purpose debugging functionality.

## KDoc

The generated KDoc for Nova can be found on [here](https://nova.dokka.xenondevs.xyz/).