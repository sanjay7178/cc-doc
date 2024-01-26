---
title: Node
description: >
  All Metrics Of One Selected Node
categories: [cc-backend]
tags: [Frontend, User]
weight: 13
---

{{< alert >}}TODO: Add Picture{{< /alert >}}

The node view is always called in respect to one specified cluster and one specified node (host). It displays the current state of *all* metrics for that node, rendered in form of [metric plots]({{< ref "plots#metric-plots" >}} "Metric Plots"), and *independent* of job meta data, i.e. without consideration for job start and end timestamps.

*Please note:* The X-Axis of all plots rendered in this view are relative to the latest data point received from the collector daemon, and thus, the time displayed reaches *backward* as indicated by negative X-axis labels.

### Selection Bar

Information and selections regarding the data of the plots rendered in the node table can be performed here:

* *Name:* The hostname of the inspected node
* *Concurrent Jobs:* Number of jobs currently allocated to this node. Exclusively used nodes will always display `1` if a job is running at the moment, or `0` if not.
  * A link is provided which leads to the [joblist]({{< ref "joblist" >}} "Job List") with preset filter fetching only currently allocated jobs. 
* *(Periodic) Reload:* Force reload of fresh data from the backend or set a periodic reload in specified intervals
  * `30 Seconds, 60 Seconds, 120 Seconds, 5 Minutes`
* *Displayed Time:* Select the timeframe to be rendered in the node table
  * `Custom`: Select timestamp `from` and `to` in which the data shuld be fetched. It is possible to select date and time. 
  * `15 Minutes, 30 Minutes, 1 Hour, 2 Hours, 4 Hours, 12 Hours, 24 Hours`

### Node Table

Metrics are ordered alphanumerically in this table, rendering each metric in the selected timeframe.
