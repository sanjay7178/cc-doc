---
title: Users
description: >
  Table Of All Users Running Jobs On The Clusters
categories: [cc-backend]
tags: [Frontend, User]
weight: 6
---

{{< alert >}}TODO: Add Picture{{< /alert >}}

This view lists all users which are, and were, active on the configured clusters. Information about the total number of jobs, walltimes and calculation usages are shown.

It is possible to filter the list by username using the equally named prompt, which also accepts partial queries.

The [filter component]({{< ref "filters" >}} "Filter") allows limitation of the returned users based on job parameters like start timestamp or memory usage.

*Please Note:* By default, a "Last 30 Days" filter is activated by default when opening this view.

### Details

|Column|Description|Note|
|-----|-----------|----|
|User Name|The user jobs are associated with|Links to the users' [job list]({{< ref "userjobs" >}} "User Job List") with preset filter returning only jobs of this user and additional histograms|
|Total Jobs|Total of all jobs started from this user||
|Total Walltime|Total requested walltime||
|Total Core Hours|Total of all core hours used by this user||
|Total Accelerator Hours|Total of all accelerator hours used by this user|Please Note: This column is always shown, and will return `0` for clusters without installed accelerators|
