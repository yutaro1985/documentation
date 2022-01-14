
The APM UI provides many tools to troubleshoot application performance and correlate it throughout the product, which helps you find and resolve issues in distributed systems.

## Glossary


### Added this heading

| Concept                         | Description                                                                                                                                                                                                          |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Service](#services)            | Services are the building blocks of modern microservice architectures - broadly a service groups together endpoints, queries, or jobs for the purposes of building your application.                                  |
| [Resource](#resources)          | Resources represent a particular domain of a customer application - they are typically an instrumented web endpoint, database query, or background job.                                                              |
| [Monitors][101]                   | APM metric monitors work like regular metric monitors, but with controls tailored specifically to APM. Use these monitors to receive alerts at the service level on hits, errors, and a variety of latency measures. |
| [Trace](#trace)                 | A trace is used to track the time spent by an application processing a request and the status of this request. Each trace consists of one or more spans.                                                             |
| [Span](#spans)                  | A span represents a logical unit of work in a distributed system for a given time period. Multiple spans construct a trace.                                                                                          |
| [Service entry span](#service-entry-span) | A span is a service entry span when it is the entrypoint method for a request to a service. You can visualize this within Datadog APM when the color of the immediate parent on a flame graph is a different color.                                                                                            |
| [Trace metrics](#trace-metrics) | Trace metrics are automatically collected and kept with a 15-month retention policy similar to other [Datadog metrics][102]. They can be used to identify and alert on hits, errors, or latency. Statistics and metrics are always calculated based on _all_ traces, and are not impacted by ingestion controls.                       |
| [Indexed Span](#indexed-span) | Indexed Spans represent all spans indexed by retention filters or legacy App Analytics analyzed spans and can be used to search, query, and monitor in *Analytics*.                                                                                                |
| [Span tags](#span-tags)         | Tag spans in the form of key-value pairs to correlate a request in the *Trace View* or filter in *Analytics*.                                                                                                    |
| [Retention Filters](#retention-filters) | Retention filters are tag-based controls set within the Datadog UI that determine what spans to index in Datadog for 15 days.                                                                                              |
| [Ingestion Controls](#ingestion-controls) | Ingestion Controls are used to send up to 100% of traces to Datadog for live search and analytics for 15 minutes.
| [Sublayer Metric](#sublayer-metric) | A sublayer metric is the execution duration of a given type / service within a trace.
| [Execution Time](#execution-time) | Total time that a span is considered 'active' (not waiting for a child span to complete).

[101]: /monitors/create/types/apm/
[102]: /developers/guide/data-collection-resolution-retention/