---
title: Datadog Taxonomy
kind: documentation
description: 'Reference of tags, attributes, and label used in Datadog products.'
further_reading:
    - link: '/getting_started/tagging/assigning_tags/'
      tag: 'Documentation'
      text: 'Learn how to assign tags'
    - link: '/getting_started/tagging/unified_service_tagging/'
      tag: 'Documentation'
      text: 'Configure unified service tagging'
    - link: '/getting_started/tagging/using_tags/'
      tag: 'Documentation'
      text: 'Explore how to use tags in the Datadog app'
    - link: '/logs/log_configuration/attributes_naming_convention/#reserved-attributes'
      tag: 'Documentation'
      text: 'Explore Reserved and Standard attributes in logs'
---

## Table

Here is a list of all the tags that have specific functionality in datadog

| Key       |  Example Values | Definition   | Example Usage | 
| --------- | -- | --------------- | --- |
| `aws_account` | `172597598159` | Your AWS Account identification number is an important value used to track your account information with AWS. Your AWS ID is the twelve digit number located underneath the Account Settings section. | infra list groups by it, used in lambda facets |
| `account_id` | `172597598159` | alias of `aws_account` used by lambda serverless product |  |
| `kube_cluster_name` | `something` | name of a kubernetes cluster | default facet in cluster resource view of live orchestrator kubernetes data |
| `container_id` | `something` | name of a container | atomic unit for containers product |
| `cluster-name` | `something` | name of a cluster | default facet in live containers list, default facet for profiling metrics |
| `cluster_name` | `something` | name of a cluster | default facet in live containers list, default facet for profiling metrics |
| `language` | `java`, `python` | programming language | default facet for profiling |
| `functionname` | `coupon-counter` | aws lambda function name | atomic unit of serverless product for AWS |
| `cloud_provider` | `aws`, `azure`, `gcp`, `alibaba` | a company that delivers cloud computing based services and solutions to businesses and/or individuals | infra list groups by it |
| `device`  | `tmpfs`, `c:`, `/dev/root` | a disk or mounted filesystem or disk drive partition | template variable in disk dashboard |
| `env`     | `dev`, `staging`, `production` | the environment where applications are deployed. | primary tag in APM, links monitors and APM, facet in watchdog |
| `host`    | `i-00e2fe71c338a9f87`, `oracle-213-dd`, `vsphere-prod.c.fetch-171516.internal` |  what a computer is called on a network | applied by the agent to all data that leave it, atomic unit of host map/ infra list, correlates most products that focus on backend |
| `pod_name` | `something` | name of a kubernetes pod | resource type for cluster resource view of live orchestrator kubernetes data |
| `service` | `spring-storefront`, `mysql-orders` | the name of a web application, database, cache, or any other technology within your stack | used to group together replicas of the some codebase, atomic unit of service map, correlates most products |
| `source`  | `java`, `mongodb`, `cloudtrail` | a log format.   | pipelines automatically parses raw logs into structured json based on their source |
| `trace_id`  | `5432093789420` | a correlation id for a single request as it goes through various levels of technology   | correlates a single requests logs, traces, and RUM events |
| `version` | `v1.4.2`, `35.5553829`, `1.2.0-rc.3` | a released software state | allows for deployment tracking in APM, used for error tracking in RUM and APM |


