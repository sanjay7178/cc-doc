---
title: Users
description: >
  Table Of All Users Running Jobs On The Clusters
categories: [cc-backend]
tags: [Frontend, User]
weight: 6
---

{{< figure src="../../figures/usertable.png" alt="User Table" width="100%" class="ccfigure mw-md"
    caption="User Table, sorted by 'Total Jobs' in descending order. In addition, active filters reduce the underlying data to jobs with more than one hour runtime, started on the GPU accelerated cluster."
>}}

This view lists all users which are, and were, active on the configured clusters. Information about the total number of jobs, walltimes and calculation usages are shown.

It is possible to filter the list by username using the equally named prompt, which also accepts partial queries.

The [filter component]({{< ref "filters" >}} "Filter") allows limitation of the returned users based on job parameters like start timestamp or memory usage.

The table can be sorted by clicking the respective icon next to the column headers.

{{< alert >}}*Please Note:* By default, a "Last 30 Days" filter is activated by default when opening this view.{{< /alert >}}

### Details

|Column|Description|Note|
|-----|-----------|----|
|User Name|The user jobs are associated with|Links to the users' [job list]({{< ref "userjobs" >}} "User Job List") with preset filter returning only jobs of this user and additional histograms|
|Total Jobs|Users' total of all started jobs||
|Total Walltime|Users' total requested walltime||
|Total Core Hours|Users' total of all used core hours||
|Total Accelerator Hours|Users' total of all used accelerator hours|Please Note: This column is always shown, and will return `0` for clusters without installed accelerators|
