# Knitting Calculator

Knitting Calculator is an open-source Kotlin Multiplatform library for calculating how to distribute increases and decreases evenly across a row of knitting.

The calculation engine is deliberately independent of any user interface. The same tested code can eventually power mobile and web apps, a command-line tool, or a public API.

## Project status

This project is in early development. It does not yet provide a stable API or a published package.

The first planned calculations are:

- Evenly spaced increases
- Evenly spaced decreases

## Platforms

The project is currently configured to compile for:

- JVM
- Android
- iOS devices using ARM64
- iOS simulators using ARM64
- Linux x64

Web support is planned.

## Project structure

The `calculator-library` module contains the shared calculation code:

```text
calculator-library/
+-- src/
    +-- commonMain/kotlin/    # Shared calculation code
    +-- commonTest/kotlin/    # Shared tests
```

Platform-specific source sets will be added only when a platform genuinely requires different code.

## Running the tests

Use the Gradle wrapper to run the JVM version of the shared test suite:

```shell
./gradlew jvmTest
```

Running the Android host tests locally requires an installed Android SDK and a machine-specific SDK path in `local.properties`:

```properties
sdk.dir=/absolute/path/to/Android/sdk
```

The `local.properties` file is ignored by Git because the SDK location differs between computers. Once it is configured, run:

```shell
./gradlew testAndroidHostTest
```

Tests for other targets can be run using their corresponding Gradle tasks on compatible hosts.

## Licence

Knitting Calculator is available under the [MIT License](LICENSE).
