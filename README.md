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

## Linting and formatting

The project uses [ktlint](https://ktlint.github.io/ktlint/latest/) to check and format Kotlin source files and Gradle Kotlin scripts. The project's formatting rules are defined in `.editorconfig`.

Check the project for formatting violations:

```shell
./gradlew ktlintCheck
```

Automatically fix violations that ktlint can correct:

```shell
./gradlew ktlintFormat
```

Some violations, such as incorrectly named files, cannot be fixed automatically. Review any changes made by `ktlintFormat`, then run `ktlintCheck` again before committing.

### Linting GitHub Actions workflows

GitHub Actions workflows are checked with [actionlint](https://github.com/rhysd/actionlint), which catches problems such as syntax errors, invalid expressions, and incorrect action inputs. CI runs actionlint automatically for every pull request targeting `main` and every push to `main`.

If you change a file in `.github/workflows`, run actionlint locally before pushing your branch. This provides faster feedback and avoids waiting for CI to find errors that can be caught on your machine.

On macOS, install actionlint with Homebrew:

```shell
brew install actionlint
```

Installation instructions for other platforms are available in the [actionlint documentation](https://github.com/rhysd/actionlint/blob/main/docs/install.md).

Run actionlint from the project root:

```shell
actionlint
```

The project deliberately does not install a pre-commit hook. This keeps local development unobtrusive while still combining a documented local check with an automatic CI check. If the project later needs stronger local automation, a managed pre-commit hook can be added.

## Licence

Knitting Calculator is available under the [MIT License](LICENSE).
