---
title: Job
description: >
  Detailed Single Job Information View
categories: [cc-backend]
tags: [Frontend, User]
weight: 4
---

{{< alert >}}TODO: Add Picture{{< /alert >}}

The job view displays all data related to one specific job in full detail, and allows detailed inspection of all metrics at several scopes, as well as manual tagging of the job.

## Top Bar

The top bar of each job view replicates the "Job Info" and "Footprint" seen in the job list, and additionally renders general metric information in specialized plots.

### Job Info

Identical to the job list equivalent, this component displays meta data containing general information about the job. From here, users can navigate to the detailed view of one specific job as well as the user or project specific job lists.

|Field|Example|Description|Destination|
|-----|-------|-----------|----|
|Job Id|`123456`|The JobId of the job assigned by the scheduling daemon|[Job View]({{< ref "job" >}} "Job View")|
|Job Name|`myJobName`|The name of the job as supplied by the user|-|
|Username|`abcd10`|The username of the submitting user|[User Jobs]({{< ref "userjobs" >}} "User Jobs")|
|Project|`abcd`|The name of the usergroup the submitting user belongs to|[Joblist with preset Filter]({{< ref "#filters" >}} "Job List")|
|Resources|`n100`|Indicator for the allocated resources. Single resources will be displayed by name, i.e. exclusive single.node jobs or shared resources. Multiples of resources will be indicatet by icons for nodes, CPU Threads, and accelerators.|-|
|Partition|`main`|The cluster partition this job was startet at|-|
|Start Timestamp|`10.1.2024, 10:00:00`|The epoch timestamp the job was started at, formatted for human readability|-|
|Duration|`0:21:10`|The runtime of the job, will be updated for running jobs on reload. Additionally indicates the [state]({{< ref "filters#job-states" >}} "Job State") of the job as colored pill|-|
|Walltime|`24:00:00`|The allocated walltime for the job as per job submission script|-|

### Footprint

Identical to the job list equivalent, this component will show base metrics for job performance at a glance, and will hint to performance (and performance problems) in regard to configurable metric thresholds. In contrast to the job list, it is always active and shown in the detailed job view.

|Field|Description|Note|
|-----|-----------|----|
|cpu_load|Average CPU utilization|-|
|flops_any|Floprate calculated  as `f_any = (f_double x 2) + f_single`|-|
|mem_bw|Average memory bandwidth used|-|
|mem_used|Maximum memory used|Non-GPU Cluster only|
|acc_utilization|Average accelerator utilization|GPU Cluster Only|

Colors and icons differentiate between the different warning states based on the configured threshold of the metrics. Reported metric values below the warning threshold simply report bad performance in one or more metrics, and should therefore be inspected by the user for future performance improvement.

Metric values colored in blue, however, usually report performance above the expected levels - Which is exactly why these metrics should be inspected as well. The "maximum" thresholds are often the theoretically achievable performance by the respective hardware component, but rarely are they *actually* reached. Inspecting jobs reporting back such levels can lead to averaging errors, unrealistic spikes in the metric data or even bugs in the code of ClusterCockpit.

|Color|Level|Description|Note|
|-----|-----|-----------|----|
|Blue|Info|Metric value below or slightly above maximum configured threshold|Job performance above expected parameters - Inspection recommended|
|Green|OK|Metric value below normal configured threshold|Job performance within expected parameters|
|Yellow|Caution|Metric value below configured caution threshold|Job performance might be impacted|
|Red|Warning|Metric value below configured warning threshold|Job performance impacted with high probability - Inspection recommended|
|Dark Grey|Error|Metric value extremely above maximum configured threshold|Inspection required - Metric spikes in affected metrics can lead to errorneous average values|

### Concurrent Jobs

In the case of a shared job, this component will display all jobs, which were run on the same hardware at the same time. "At the same time" is defined as "has a starting or ending time, which lies between the starting and ending time of this job" for this purpose.

A cautious period of five minutes is applied to both limits, in order to restrict display of jobs which have too little overlap, and would just clutter the resulting list of jobs.

Each overlapping job is listed with its jobId as a link leading to this jobs detailed job view.

### Polar Representation

A [polar plot]({{< ref "plots#polar-plots" >}} "Polar Plot") representing the utilization of three key metrics: `flops_any`, `mem_used`, and `mem_bw`. Both the maximum and the average are rendered. In principle, this is a graphic representation of data also shown in the footprint component.

### Roofline Representation

A [roofline plot]({{< ref "plots#roofline-plot" >}} "Roofline Plot") representing the utilization of available resources as the relation between computation and memory usage over time (color scale blue -> red).

## Metric Plot Table

### Tagging

## Statistics Table

### Statistics

### Job Script

### Slurm Info
