---
title: Application Security
kind: documentation
disable_sidebar: true
further_reading:
- link: "/security_platform/guide/how-appsec-works/"
  tag: "Guide"
  text: "How Datadog Application Security Monitoring Works"
- link: "/security_platform/application_security/setup_and_configure/#compatibility"
  tag: "Documentation"
  text: "Programming Language and Framework Compatibility"
---

Datadog Application Security provides protection against application-level threats by identifying and blocking attacks that target code-level vulnerabilities, such as SQL injections and cross-site scripting (XSS) exploits.

Powered by [Datadog APM][1], Application Security leverages Datadog [tracing libraries][2], the [Datadog Agent][3], and in-app detection rules to detect threats in your application environment and trigger signals whenever a vulnerability or attack occurs.

Once Application Security is enabled, you can begin detecting attacks on your services and gain deep observability data that is provided by Application Security and APM distributed tracing.

 investigate and remediate threats immediately by leveraging deep observability data that is provided by Application Security and APM distributed tracing.

* Walk through user journey of detecting first threats with security signals
* How to investigate/respond to them thanks to the deep observability data provided by both Application Security and APM distributed tracing


## Further Reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: /tracing/
[2]: /security_platform/application_security/getting_started/
[3]: /agent/
