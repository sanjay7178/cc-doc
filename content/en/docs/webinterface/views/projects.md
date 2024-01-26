---
title: Projects
description: >
  Table Of All Projects Running Jobs On The Clusters
categories: [cc-backend]
tags: [Frontend, User]
weight: 8
---

{{< alert >}}TODO: Add Picture{{< /alert >}}

This view lists all projects which are, and were, active on the configured clusters. Information about the total number of jobs, walltimes and calculation usages are shown.

It is possible to filter the list by project name using the equally named prompt, which also accepts partial queries.

The [filter component]({{< ref "filters" >}} "Filter") allows limitation of the returned projects based on job parameters like start timestamp or memory usage.

*Please Note:* By default, a "Last 30 Days" filter is activated by default when opening this view.

### Details

|Column|Description|Note|
|-----|-----------|----|
|Project Name|The project (usergoup) jobs are associated with|Links to a [job list]({{< ref "joblist" >}} "Project Job List") with preset filter returning only jobs of this project|
|Total Jobs|Total of all jobs started from this project||
|Total Walltime|Total requested walltime||
|Total Core Hours|Total of all core hours used by this project||
|Total Accelerator Hours|Total of all accelerator hours used by this project|Please Note: This column is always shown, and will return `0` for clusters without installed accelerators|
