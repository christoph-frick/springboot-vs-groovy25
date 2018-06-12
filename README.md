# Springboot2, Gradle, Groovy 2.5 failing

**SOLVED: see below**

This repo is to show, that Groovy 2.5 does not work with Springboot2

```
FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':compileGroovy'.
> org/codehaus/groovy/ast/MethodCallTransformation

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 1s
```

## Solution

From https://github.com/spring-projects/spring-boot/issues/13444

Don't override the groovy dep via Gradle deps but change the version configured from Springboots dep management:

``` groovy
ext['groovy.version'] = '2.5.0'
```

Details about customizing versions: https://docs.spring.io/spring-boot/docs/2.0.2.RELEASE/gradle-plugin/reference/html/#managing-dependencies-customizing

List of all defined/managed versions: https://github.com/spring-projects/spring-boot/tree/v2.0.2.RELEASE/spring-boot-project/spring-boot-dependencies/pom.xml
