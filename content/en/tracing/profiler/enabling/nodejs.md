---
title: Enabling the Node.js Profiler
kind: Documentation
code_lang: nodejs
type: multi-code-lang
code_lang_weight: 50
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

<div class="alert alert-warning">
Datadog Node.js Profiler is currently in public beta. Datadog recommends evaluating the profiler in a non-sensitive environment before deploying in production.
</div>

## Requirements

The Datadog Profiler requires at least Node.js 12, but Node.js 16 or higher is recommended. **If you use a version of Node.js earlier than 16, some applications see tail latency spikes every minute when starting the next profile.**

## Installation

1. Install the Datadog Agent or upgrade it to version [7.20.2][1]+ or [6.20.2][2]+ if needed.

2. The profiler and tracer are shipped together. Install or upgrade to version 1.5.1+ if needed: `npm install --save dd-trace@latest`.

3. Enable the profiler:

   {{< tabs >}}
{{% tab "Environment variables" %}}

```shell
export DD_PROFILING_ENABLED=true
export DD_ENV=prod
export DD_SERVICE=my-web-app
export DD_VERSION=1.0.3
```

**Note**: If you’re already using Datadog APM, you are already calling `init` and don’t need to do so again. If you are not, ensure the tracer and the profiler are loaded together:

```node
node -r dd-trace/init app.js
```

{{% /tab %}}
{{% tab "In code" %}}

```js
const tracer = require('dd-trace').init({
  profiling: true,
  env: 'prod',
  service: 'my-web-app',
  version: '1.0.3'
})
```

**Note**: If you’re already using Datadog APM, you are already calling `init` and don’t need to do so again. If you are not, ensure the tracer and the profiler are loaded together:

```node
const tracer = require('dd-trace/init')
```

{{% /tab %}}
{{< /tabs >}}

4. A minute or two after starting your Node.js application, your profiles will show up on the [APM > Profiler page][3].

## Not sure what to do next?

The [Getting Started with Profiler][4] guide takes a sample service with a performance problem and shows you how to use Continuous Profiler to understand and fix the problem.

## Experiencing high overhead?

Node.js 16 or higher is recommended. On earlier versions, some applications see tail latency spikes every minute while starting the next profile.

## Further Reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: https://app.datadoghq.com/account/settings#agent/overview
[2]: https://app.datadoghq.com/account/settings?agent_version=6#agent
[3]: https://app.datadoghq.com/profiling
[4]: /getting_started/profiler/
