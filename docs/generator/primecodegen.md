# PrimeCodeGen

[PrimeCodeGen](https://github.com/primelib/primecodegen) is a extension of the [OpenAPI Generator](https://openapi-generator.tech/) that provides additional features.

## Template Engine

Peble allows to use a `@pebvariable` hint to provide type information for all variables in the template (e.g. `t` is the root type for all variables in the template):

``` peb
{# @pebvariable name="t" type="io.github.primelib.primecodegen.core.domain.template.NitroGeneratorData" #}
package {{ t.apiPackage }};

{% include "./import.peb" with {"t": t, "imports": t.api.imports} %}
```

### Syntax

The Pebble syntax is easy to understand without knowing anything about the used template language.

Pebble templates are easier to read and write than the standard OpenAPI Generator templates, while also providing a high degree of flexibility around whitespace and formatting to generate clean code.

See this comparision between the default `mustache` and the `pebble` templates:

``` title="mustache"
@Headers({
{{#headerParams}}
    "{{baseName}}: {{=<% %>=}}{<%paramName%>}<%={{ }}=%>"{{^-last}},
    {{/-last}}{{/headerParams}}
  })
```

``` title="pebble"
{% if operation.hasHeaderParams %}
    @Headers({
{% for param in operation.headerParams %}
        "{{ param.baseName }}: {% if param.baseName == "Authorization" %}Bearer {% endif %}{% if param.vendorExtensions.getOrDefault("x-param-static", false) %}{{ param.defaultValue }}{% else %}{{ param.vendorExtensions.get("x-base-name") | wrapin("{", "}") }}{% endif %}"{% if not loop.last %}, {% endif %}{{ newline() }}
{% endfor %}
    })
{% endif %}
```

### IDE Plugins

- JetBrains: [https://plugins.jetbrains.com/plugin/9407-pebble](https://plugins.jetbrains.com/plugin/9407-pebble)1

## Template Registration

We provide a very flexible template registration system. You can register templates in the following ways:

```java
cfg.templateSpecs.add(PrimeTemplateSpec(
    description = "api interface for reactor",
    sourceTemplate = "api_main.peb",
    targetDirectory = apiFolder,
    targetFileName = "{mainClassName}ReactorApi.java",
    scope = TemplateScope.API,
    iterator = PrimeIterator.EACH_API,
    filter = { data -> true },
    transform = { data ->
        data.mainClassName = "${data.mainClassName}Reactor"
    }
))
```

- iterator: `ONCE_API`, `EACH_API`, `EACH_API_OPERATION`, `ONCE_MODEL`, `EACH_MODEL`, `ONCE_PROJECT`
- filter: dynamic filter to decide if the template should be executed (e.g. only for api operations with parameters)
- transform: dynamically transform data before the template is executed

This allows covering the following use-cases that are not possible with the standard OpenAPI Generator:

- filter templates based on the data (e.g. only generate a model file if the model has properties)
- generate a model file for each api operation that has parameters (e.g. `MyOperationRequest`)
- reuse the same template and transform data (e.g. wrap response types in `CompletableFuture<>`, ...)
