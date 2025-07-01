# Repro for add Gradle dependency behavior

1. `./gradlew lib:dependencies --configuration testRuntimeClasspath`

## Expected

Gradle throws exception for
```groovy
dependencies {
    testImplementation(compileOnly("com.google.guava:guava:33.3.1-jre"))
}
```

as the expected behavior is to fail when attempting to add nothing to `testImplementation` as
`compileOnly("com.google.guava:guava:33.3.1-jre")` should not return a dependency notion.

## Actual

No warnings/errors. There is guava on the `testRuntimeClasspath`

