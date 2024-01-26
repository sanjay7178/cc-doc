---
title: Analysis
description: >
  Metric Data Analysis View
categories: [cc-backend]
tags: [Frontend, User]
weight: 14
---

{{< alert >}}TODO: Add Picture{{< /alert >}}

The analysis view is always called in respect to one specified cluster. It collects and renders data based on the jobs returned by the active filter, which can be specified to a high detail, allowing analysis of specific aspects.

*Please note:* By default, the requested data is limited by a preset start time filter to jobs started within *the last 6 hours*. In addition, some results are not calculated when the returned amount of jobs exceeds 500 entries, in order to save on rendering time.

## General Information

### Totals

Total counts of collected data based on the returned jobs matching the requested filters:

* Total Jobs
* Total Short Jobs (By default defined as jobs shorter than 5 minutes)
* Total Walltime
* Total Node Hours
* Total Core Hours
* Total Accelerator Hours

### Top Users and Projects

The ten most active users or projects are rendered in a combination of pie chart and tabular legend. By default, the top ten users with the most jobs conforming to the selected filters will be showm.

The selection can be changed directly in the headers of the pie chart and the table, and can be changed to

|Element|Options|
|-------|-------|
|Pie Chart|`Users, Projcets`|
|Table|`Wall Time, Node Hours, Core Hours, Accelerator Hours`|

The selection is saved for each user and cluster, and will select the last chosen types of list as default the next time this view is rendered.

"User Names" and "Project Codes" are rendered as links, leading to [user job lists]({{< ref "userjobs" >}} "User Job List") or [project job lists]({{< ref "joblist" >}} "Project Jobs") with preset filters for cluster and entity ID.

### Heatmap Roofline

A [roofline plot]({{< ref "plots#roofline-plot" >}} "Roofline Plot") representing the utilization of available resources as the relation between computation and memory for all jobs matching the filters. In order to represent the data in a meaningful way, the time information of the raw data is abstracted and represented as a heat map, with redder sections of the roofline plot being the most populated regions of utilization.

### Histograms

Histograms depictinig the duration and number of allocated cores distributions for the returned jobs matching the filters.

## Average Distribution Histograms

These histograms show the distribution of the averages of all jobs matching the filters.

Each job/average is weighted by its node hours by default (Accelerator hours for native accelerator scope metrics, coreHours for native core scope metrics). Note that some metrics could be disabled for specific subclusters as per metricConfig and thus could affect shown average values.

## User Defined Scatterplots

Each circle represents one job. The size of a circle is proportional to its node hours. Darker circles mean multiple jobs have the same averages for the respective metrics. Note that some metrics could be disabled for specific subclusters as per metricConfig and thus could affect shown average values.
