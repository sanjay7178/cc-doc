---
title: Release cc-backend v1.2.0
date: 2023-09-06
description: Minor release
---
## Changelog
### New Features
* 742c2e3 feat: Add uplot histogram, implemented in userview
* f6c4c96 feat: Add users rest endpoint swagger docs
* da8cefe feat: Change histogram to piechart in status view
* c4a9fcc feat: Implemented rooflineplot with uPlot
* e80ce7a feat: Rework analysis view top to contain piechart
* b42a11d feat: Use chart.js for polarplot n jobview
* 36abed2 feat: add auto-reloading to system and node views
* 423e800 feat: add hover-legend to histograms & metricplots
* 3014f59 feat: add new distribution plots to status view
* 59c749a feat: add select to analysis view pie chart
* f933cad feat: add select to status view pie charts
* ed056b0 feat: add sorting in sub-node scopes in statsTable
* 2655bda feat: enable uplot XY-Zoom for metrics
* b623092 feat: persist analysis and status pie selections
### Bug fixes
* 80be786 fix: Responsive Navbar
* 6a1e351 fix: analysis metric histogram normalized by scope
* 4eceab4 fix: change analysis top users to core hours
* 8a473de fix: core/accelerator scope in statstable on load
* 4244a37 fix: correct timestamp logic in node-view
* f286872 fix: hover legend display now depends on datasize
* 69ee19b fix: include running jobs case in statsQueries
* 129e6a6 fix: metric y-range render limit for data outliers
* c84a0fb fix: push bootstrap to v5.3.1 and icons to v1.10.5

Supports job archive version 1 and database version 6.

[Download the release on GitHub!](https://github.com/ClusterCockpit/cc-backend/releases/tag/v1.2.0) 
