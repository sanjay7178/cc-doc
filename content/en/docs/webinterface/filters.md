---
title: Filters
description: >
  Webinterface Filter Options
categories: [cc-backend]
tags: [Frontend, User]
weight: 4
---

{{< alert >}}TODO: Add Picture of each filter dropdown{{< /alert >}}

The filter component of ClusterCockpit is the same in most views and consists of several options to specify the jobs to be displayed, or to be used as data-source for calculated statistics.

### Cluster/Partition

Select a configured cluster, or a specified partition of a given cluster, and display only jobs started on that cluster.

*Options:* All cluster names, and nested partition names, configured in `config.json`

*Default:* Disabled

### Job States

Select one or more job states, and display only jobs matching the selected criteria.

*Options:* `running, completed, failed, cancelled, stopped, timeout, preempted, out_of_memory`

*Default:* All states

### Start Time

Select the timeframe in which jobs were started, and display only jobs matching the selected criteria.

*Options:* Free selection of date `dd.mm.YYY` and time `hh:mm` for `from` and `to` limits

*Default:* Jobs started one month ago until `$now`

### Duration

Select the duration of jobs, and display only jobs matching the selected criteria. Only one of the three options can be used at a time.

*Options:* Duration less than `hh:mm`, duration more than `hh:mm`, duration between two duration selections.

*Default:* No selection

### Tags

Select one or more job tags, and display only jobs matching the selected tags.

*Options:* All available tags. It is possible to search within the list of tags.

*Default:* No selection

### Resources

Select a named node or specify an amount of used resources, and display only jobs matching the selected criteria.

*Options:* Named node free text field; range selectors for nodes, HWThreads, and Accelerators (if available) ranging from the minimal configured resource count to the maximum configured resource count of all clusters. If the [cluster filter]({{< ref "#clusterpartition" >}} "Cluster Filter") is set, the ranges are limited to the respective resources' configuration.

*Default:* No named node, full resource ranges of all configured clusters

### Statistics

Specify ranges of metric statistics, and display only jobs matching the selected criteria.

*Options:* FLOPs (Avg.) From-To, Memory Bandwith (Avg.) From-To, Load (Avg.) From-To, Memory Used (Max.) From-To

*Default:* Full metric statistics ranges as configured

### Start Time Quick Selections

**Note** Not available in all views!

Quickly select a preconfigured range of job start times. Will display as named [start time filter]({{< ref "#starttime" >}} "Starttime Filter").

*Options:* `Last 6 hours, Last 24 hours, Last 7 Days, Last 30 Days`

*Default:* No selection
