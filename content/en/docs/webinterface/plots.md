---
title: Plots
description: >
  Description and Functionality
categories: [cc-backend]
tags: [Frontend, User]
weight: 3
---

Most plots visible in the ClusterCockpit webinterface are implemented via `uplot` or `chart.js`, which both offer various functionality to the user.

## Metric Plots

The main plot component of ClusterCockpit renders the metric values retrieved from the systems in a time dependent manner.

A selector crosshair is shown when hovering over the rendered data, data points corresponding to the legend are highlighted. It is possible to zoom in by dragging a selection square with your mouse. Double-Clicking into the plot will reset the zoom.

### Conditional Legends

Hovering over the rendered data will display a legend as hovering box colored in yellow. Depending on the amount of data shown, this legend will render differently:

* *Single Dataset*: Runtime and Dataset Identifier Only
* *2 to 6 Datasets*: Runtime, Color and Dataset Identifier
* *7 to 12 Datasets*: Runtime and Dataset Identifier Only
* *More than 12 Datasets*: No Legend
* *Statistics Datasets*: Runtime and Dataset Identifier Only (See below)

The "no legend" case is required to not clutter the display in case of high data volume, e.g. core granularity data for more than 128 cores, which would result in 128 legend entries.

#### Example

{{< figure src="../figures/metricplot_multiline.png" alt="Metricplot Example" width="100%" class="ccfigure mw-xxs"
    caption="Eight datasets result in an average value within expected parameters, the job uses the resources well. The datasets correspond to eight allocated nodes for this job, thus, the legend displays their hostnames as identifier."
>}}

### Colored Backgrounds

The plots' background is colored depending the average value of the viewed metric in respect to its configured threshold values. The three cases are

* *White*: Metric average within expected parameters. No performance impact.
* *Yellow*: Metric average below expected parameters, but not yet critical. Possible performace impact.
* *Red*: Metric average unexpectedly low. Indicator for suboptimal usage of resources. Performance impact to be expected.

#### Example

{{< figure src="../figures/metricplot_colorleg_redback.png" alt="Metricplot Colored Background Example" width="100%" class="ccfigure mw-xxs"
    caption="Two datasets result in an average value of less than the configured 'alert' threshold: The legend displays both identifiers with their respective color, while the background is colored in red to indicate suboptimal metric performance."
>}}

### Statistics Variant

In the job list views, high amounts of data are by default rendered as a statistical representation of the numerous, single datasets:

* *Maximum*: The maximum values of the base datasets of each point in time, over time. Colored in green.
* *Average*: The average values of the base datasets of each point in time, over time. Colored in black.
* *Minimum*: The minimal values of the base datasets of each point in time, over time. Colored in red.

#### Example

{{< figure src="../figures/metricplot_stats.png" alt="Statistics Metricplot Example" width="100%" class="ccfigure mw-xxs"
    caption="A job with a high count of allocated nodes, running well within expected metric parameters. Since, by definition, the colors for this statistical render are always identical, only the runtime and the statistic datasets' identifiers are shown."
>}}

## Histograms

Histrograms display (binned) data allowing distributions of the repective data source to be visualized. Data highlighting, zooming, and resetting zoom work identical to the metric plots.

#### Example

{{< figure src="../figures/histogram.png" alt="Histogram Example" width="100%" class="ccfigure mw-xxs"
    caption="Duration distribution of selected jobs. The legends will display the X-Axis value label first, then the Y-Axis value label. The currently inspected bar is highlighted by a white dot and also the selection crosshair."
>}}

## Roofline Plot

A roofline plot, or roofline model, represents the utilization of available resources as the relation between computation and memory usage.

### Dotted Roofline

Roofline models rendered as dotted plots display the utilization of hardware resources over time.

{{< alert >}}*Please Note:* The roofline models rendered in the status view are *not* job-derived, but display the utilization of single nodes at the moment of data-collection. Therefore, no time information is required, and alle dots are colored blue.{{< /alert >}}

#### Example

{{< figure src="../figures/roofline_timed.png" alt="Dotted Roofline Example" width="100%" class="ccfigure mw-xs"
    caption="Roofline model as shown for a single job. Time information is encoded in the color range, starting from blue dots and ending in red dots."
>}}

### Heatmap Roofline

The roofline model shown in the analysis view, as the single exception, is rendered as a heatmap. This is due to the data being displayed is derived from a number of jobs greater than one, since the analysis view returns all jobs matching the selected fitlers. The roofline therefore colors regions of increased activity in increasing shades of red, depicting the regions below the roofs in which the returned jobs primarily perform.

*Please note:* The plot *is* rendered in double-logarithmic, yet the lines in the background seem linear: The heatmap roofline is rendered manually (and directly) using only HTML canvas, while the dotted roofline model is rendered with the help of the `uplot` package.

#### Example

{{< figure src="../figures/roofline_heatmap.png" alt="Heatmap Roofline Example" width="100%" class="ccfigure mw-xxs"
    caption="In this example, the selected jobs perform in near optimal, as depicted by increased job activity right below the first 'knee' of the roofline model."
>}}

## Polar Plots

A polar, or radar, plot represents the utilization of three key metrics: `flops_any`, `mem_used`, and `mem_bw`. Both the maximum and the average are rendered. In principle, this is a graphic representation of data also shown in the footprint component.

By clicking on one of the two legends, the respective dataset will be hidden. This can be useful if high overlap reduces visibility.

#### Example

{{< figure src="../figures/polarplot.png" alt="Polar Plot Example" width="100%" class="ccfigure mw-xxs"
    caption="In this example, the selected job performs quite well, as depicted in the acceptable and equally distributed usage of core metrics. On average, all three metrics are utilized at about 20% (0.2) of the configured hardware maximum. At a point in time, the maximum even reached close to 100% (1.0) of the memory bandwidth (mem_bw)."
>}}
## Scatter / Bubble Plot

Each circle represents one job. The size of a circle is proportional to its node hours. Darker circles mean multiple jobs have the same averages for the respective metrics. Note that some metrics could be disabled for specific subclusters as per metricConfig and thus could affect shown average values.

#### Example

{{< figure src="../figures/scatterplot.png" alt="Scatter Plot Example" width="100%" class="ccfigure mw-xxs"
    caption="In this example, the selected metrics are accelerator clock on the X-axis and accelerator temperature on the Y-axis. Expectedly, long running, high-clock jobs accumulate in the top-right corner, while jobs with less demanding (less clocking) jobs remain cooler."
>}}