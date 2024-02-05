---
title: Command Line
description: >
  ClusterCockpit Metric Store Command Line Options
categories: [cc-metric-store]
tags: [Backend]
weight: 1
---

This page describes the command line options for the `cc-metric-store` executable.

```txt
  -config <path>
```

*Function:* Specifies alternative path to application configuration file.

*Default:* `./config.json`

*Example:* `-config ./configfiles/configuration.json`

---

```txt
  -gops
```

*Function:* Go server listens via github.com/google/gops/agent (for debugging).
