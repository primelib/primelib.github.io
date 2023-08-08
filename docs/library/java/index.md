# Java

## Introduction

Clients are generated with the [prime-client-java-feign](../template/java-feign.md) template.
The generated code makes use of some interfaces to support extension modules.

## Libraries

| Name | Description | Version | Javadoc |
| ---- | ---------------------------- | ------- | ------- |
| [io.github.primelib:jira4j-rest-v2](https://github.com/primelib/jira4j) | JIRA REST | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/jira4j-rest-v2)](https://central.sonatype.com/artifact/io.github.primelib/jira4j-rest-v2) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/jira4j-rest-v2/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/jira4j-rest-v2) |
| [io.github.primelib:jira4j-rest-v3](https://github.com/primelib/jira4j) | JIRA REST | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/jira4j-rest-v3)](https://central.sonatype.com/artifact/io.github.primelib/jira4j-rest-v3) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/jira4j-rest-v3/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/jira4j-rest-v3) |
| [io.github.primelib:confluence4j-rest-v1](https://github.com/primelib/confluence4j) | Confluence REST | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/confluence4j-rest-v1)](https://central.sonatype.com/artifact/io.github.primelib/confluence4j-rest-v1) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/confluence4j-rest-v1/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/confluence4j-rest-v1) |
| [io.github.primelib:confluence4j-rest-v2](https://github.com/primelib/confluence4j) | Confluence REST | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/confluence4j-rest-v2)](https://central.sonatype.com/artifact/io.github.primelib/confluence4j-rest-v2) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/confluence4j-rest-v2/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/confluence4j-rest-v2) |
| [io.github.primelib:pagerduty4j-events-v2](https://github.com/primelib/pagerduty4j) | [PagerDuty Events](https://pagerduty.com/) | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/pagerduty4j-events-v2)](https://central.sonatype.com/artifact/io.github.primelib/pagerduty4j-events-v2) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/pagerduty4j-events-v2/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/pagerduty4j-events-v2) |
| [io.github.primelib:pagerduty4j-rest](https://github.com/primelib/pagerduty4j) | [PagerDuty REST](https://pagerduty.com/) | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/pagerduty4j-rest)](https://central.sonatype.com/artifact/io.github.primelib/pagerduty4j-rest) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/pagerduty4j-rest/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/pagerduty4j-rest) |
| [io.github.primelib:prometheus4j](https://github.com/primelib/prometheus4j) | Prometheus API | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/prometheus4j)](https://central.sonatype.com/artifact/io.github.primelib/prometheus4j) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/prometheus4j/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/prometheus4j) |
| [io.github.primelib:webmethodsapigateway4j](https://github.com/primelib/webmethodsapigateway4j) | Prometheus API | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/webmethodsapigateway4j)](https://central.sonatype.com/artifact/io.github.primelib/webmethodsapigateway4j) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/webmethodsapigateway4j/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/webmethodsapigateway4j) |
| [io.github.primelib:perspective4j](https://github.com/primelib/perspective4j) | [perspectiveapi.com](https://perspectiveapi.com/) | [![Maven Central](https://img.shields.io/maven-central/v/io.github.primelib/perspective4j)](https://central.sonatype.com/artifact/io.github.primelib/perspective4j) | [![javadoc](https://javadoc.io/badge2/io.github.primelib/perspective4j/javadoc.svg)](https://javadoc.io/doc/io.github.primelib/perspective4j) |

## Extensions

The source code for java extensions is available on [GitHub](https://github.com/primelib/primecodegen-lib-java).

### Reslience4J

The `Reslience4J` extension will decorate api invocations with various features. (e.g. CircuitBreaker, RateLimiter, Retry, Bulkhead, ...)

`implementation("io.github.primelib.primecodegenlib.java:feign-resilience4j")`

``` java
ApiName client = ApiNameFactory.create(spec -> {
    ...
    spec.registerExtension(new Resilience4JExtension());
    ...
});
```

### Blackbird

The `BlackbirdExtension` will add `jackson-blackbird` to the Jackson ObjectMapper used by the Feign Client.

`implementation("io.github.primelib.primecodegenlib.java:feign-blackbird")`

``` java
ApiName client = ApiNameFactory.create(spec -> {
    ...
    spec.registerExtension(new BlackbirdExtension());
    ...
});
```
