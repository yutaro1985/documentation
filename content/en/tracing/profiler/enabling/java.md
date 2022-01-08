---
title: Enabling the Java Profiler
kind: Documentation
code_lang: java
type: multi-code-lang
code_lang_weight: 10
further_reading:
    - link: 'getting_started/profiler'
      tag: 'Documentation'
      text: 'Getting Started with Profiler'
    - link: 'tracing/profiler/search_profiles'
      tag: 'Documentation'
      text: 'Learn more about available profile types'
    - link: 'tracing/profiler/profiler_troubleshooting'
      tag: 'Documentation'
      text: 'Fix problems you encounter while using the profiler'
---

{{< site-region region="us5" >}}
<div class="alert alert-warning">
  The Continuous Profiler is not available for the Datadog {{< region-param key="dd_site_name" >}} site.
</div>
{{< /site-region >}}

## Requirements

The Datadog Profiler requires [JDK Flight Recorder][1]. The Datadog Profiler library is supported in OpenJDK 11+, Oracle JDK 11+, [OpenJDK 8 (version 8u262+)][2] and Azul Zulu 8+ (version 8u212+). It is not supported in OpenJ9 as it doesn't support the [JDK Flight Recorder][1].

All JVM-based languages, such as Java, Scala, Groovy, Kotlin, and Clojure are supported.

## Installation

1. Install the Datadog Agent or upgrade it to version [7.20.2][1]+ or [6.20.2][2]+ if needed.

2. The profiler and tracer are shipped together. Install or upgrade to version 0.55+ if needed:

    ```shell
    wget -O dd-java-agent.jar 'https://dtdg.co/latest-java-tracer'
    ```

3. Enable the profiler by setting `-Ddd.profiling.enabled` flag or `DD_PROFILING_ENABLED` environment variable to `true`. Specify `dd.service`, `dd.env`, and `dd.version` so you can filter and group your profiles across these dimensions:
   {{< tabs >}}
{{% tab "Command arguments" %}}

Invoke your service: 
```diff
java \
    -javaagent:dd-java-agent.jar \
    -Ddd.service=<YOUR_SERVICE> \
    -Ddd.env=<YOUR_ENVIRONMENT> \
    -Ddd.version=<YOUR_VERSION> \
    -Ddd.profiling.enabled=true \
    -XX:FlightRecorderOptions=stackdepth=256 \
    -jar <YOUR_SERVICE>.jar <YOUR_SERVICE_FLAGS>
```

{{% /tab %}}
{{% tab "Environment variables" %}}

```diff
export DD_SERVICE=<YOUR_SERVICE>
export DD_ENV=<YOUR_ENV>
export DD_VERSION=<YOUR_VERSION>
export DD_PROFILING_ENABLED=true
java \
    -javaagent:dd-java-agent.jar \
    -XX:FlightRecorderOptions=stackdepth=256 \
    -jar <YOUR_SERVICE>.jar <YOUR_SERVICE_FLAGS>
```

{{% /tab %}}
{{< /tabs >}}

    **Note**: The `-javaagent` argument needs to be before `-jar`, adding it as a JVM option rather than an application argument. For more information, see the [Oracle documentation][3]:

    ```shell
    # Good:
    java -javaagent:dd-java-agent.jar ... -jar my-service.jar -more-flags
    # Bad:
    java -jar my-service.jar -javaagent:dd-java-agent.jar ...
    ```

4. After a minute or two, you can visualize your profiles on the [Datadog APM > Profiling page][4].

## Enabling the allocation profiler

In dd-java-agent v0.84.0+ and Java 15 and lower, the allocation profiler is opt-in because it can use excessive CPU in allocation-heavy applications. This isn't common, so you may want to try it in a staging environment to see if it affects your application. To enable it, see [Enabling the allocation profiler][5].

## Configuration

You can configure the profiler using the following environment variables:

| Environment variable                             | Type          | Description                                                                                      |
| ------------------------------------------------ | ------------- | ------------------------------------------------------------------------------------------------ |
| `DD_PROFILING_ENABLED`                           | Boolean       | Alternate for `-Ddd.profiling.enabled` argument. Set to `true` to enable profiler.               |
| `DD_PROFILING_ALLOCATION_ENABLED`                | Boolean       | Alternate for `-Ddd.profiling.allocation.enabled` argument. Set to `true` to enable the allocation profiler. It requires the profiler to be enabled already. |
| `DD_ENV`                                         | String        | The [environment][6] name, for example: `production`. |
| `DD_SERVICE`                                     | String        | The [service][6] name, for example, `web-backend`. |
| `DD_VERSION`                                     | String        | The [version][6] of your service. |
| `DD_TAGS`                                        | String        | Tags to apply to an uploaded profile. Must be a list of `<key>:<value>` separated by commas such as: `layer:api, team:intake`.  |

## Not sure what to do next?

The [Getting Started with Profiler][7] guide takes a sample service with a performance problem and shows you how to use Continuous Profiler to understand and fix the problem.

## Further Reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: https://docs.oracle.com/javacomponents/jmc-5-4/jfr-runtime-guide/about.htm
[2]: /tracing/profiler/profiler_troubleshooting/#java-8-support
[3]: https://docs.oracle.com/javase/7/docs/technotes/tools/solaris/java.html
[4]: https://app.datadoghq.com/profiling
[5]: /tracing/profiler/profiler_troubleshooting/#enabling-the-allocation-profiler
[6]: /getting_started/tagging/unified_service_tagging
[7]: /getting_started/profiler/
