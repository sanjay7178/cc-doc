---
title: Plots
description: >
  PLot Functionality
categories: [cc-backend]
tags: [Frontend, User]
weight: 3
---

{{< alert >}}TODO: Add Picture{{< /alert >}}

{{< alert >}}TODO: Add Functional Instructions{{< /alert >}}

Most plots visible in the ClusterCockpit webinterface are implemented via `uplot` or `chart.js`, which both offer various functionality to the user.

### Metric Plots

The main plot component of ClusterCockpit renders the metric values retrieved from the systems in a time dependent manner.

background are colored depending on where the average value of the viewed metrix sits in respect to the configured threshold values.

#### Metric Legend

By hovering over a data point, a legend will appear, except then there is too much data to visualize.

#### Variations

* *Simple*: One line for each dataset.
* *Statistical*: Only three datasets are rednered:
  * Maximum: The maximum values of the base data set of each point in time, over time.
  * Average: The average values of the base data set of each point in time, over time.
  * Minimum: The minimal values of the base data set of each point in time, over time.

### Histograms

Histrograms display (binned) data allowing distributions of the repective data source to be visualized.

#### Histogram Legend

### Roofline Plot

A roofline plot, or rooflinemodel, represents the utilization of available resources as the relation between computation and memory usage over time.

#### Roofline Legend

A roofline plot has no legend.

### Polar Plots

A polar, or radar, plot represents the utilization of three key metrics: `flops_any`, `mem_used`, and `mem_bw`. Both the maximum and the average are rendered. In principle, this is a graphic representation of data also shown in the footprint component.

#### Polar Legend

A polar plot has no legend.

### Scatter / Bubble Plot

Each circle represents one job. The size of a circle is proportional to its node hours. Darker circles mean multiple jobs have the same averages for the respective metrics. Note that some metrics could be disabled for specific subclusters as per metricConfig and thus could affect shown average values.

#### Scatter Legend

A scatter plot has no legend.