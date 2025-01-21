Attempt to use the rule LibraryCodeMustSpecifyReturnType in Android project.

Currently this is failing to detect non-compliant code.

Noted:
- Need to place Rule activation in 'style' section
- Need to run detektMain (to ge Type Resolution)
- Initially this detected non-compliance to Rule HasPlatformType (so I deactivated it), as shown below
- Using non-compliant example from https://detekt.dev/docs/rules/libraries#librarycodemustspecifyreturntype

1. With *LibraryCodeMustSpecifyReturnType active* and *HasPlatformType active*
```
$> ./gradlew detektMain --no-build-cache --rerun-tasks --no-configuration-cache

> Task :library-android:detektDebug
Property 'style>LibraryCodeMustSpecifyReturnType' is deprecated. Rule migrated to `libraries` ruleset plugin.

Get
/Users/alice/StudioProjects/DetektExampleRepo/library-kotlin/src/main/java/com/ncorti/kotlin/template/library/FactorialCalculator.kt:27:5: FUN has implicit platform type. Type must be declared explicitly. [HasPlatformType]
```


2. With *LibraryCodeMustSpecifyReturnType active* and HasPlatformType _inactive_
```
$> ./gradlew detektDebug --no-build-cache --rerun-tasks --no-configuration-cache
Type-safe project accessors is an incubating feature.

> Task :library-android:detektDebug
Property 'style>LibraryCodeMustSpecifyReturnType' is deprecated. Rule migrated to `libraries` ruleset plugin.

> Task :library-compose:detektDebug
Property 'style>LibraryCodeMustSpecifyReturnType' is deprecated. Rule migrated to `libraries` ruleset plugin.

> Task :app:detektDebug
Property 'style>LibraryCodeMustSpecifyReturnType' is deprecated. Rule migrated to `libraries` ruleset plugin.

BUILD SUCCESSFUL in 2s
58 actionable tasks: 58 executed
```
