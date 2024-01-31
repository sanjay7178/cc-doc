---
title: Tags
description: >
  Active Tags Used In Frontend
categories: [cc-backend]
tags: [Frontend, User]
weight: 10
---

{{< figure src="../../figures/tags.png" alt="Tag List View" width="100%" class="ccfigure mw-sm">}}

This view lists all tags currently used within the ClusterCockpit instance:

* The `type` of the tag(s) is displayed as dark grey header, collecting all tags which share it.
* The `name`s of all tags sharing one `type` are rendered as yellow pills below the header.
* How often a tag was applied to a job is shown in the number following the tags `name`

Each tags' pill is clickable, and leads to a [job list]({{< ref "joblist" >}} "Job List") with a preset filter matching only jobs tagged with this specific label.

{{< alert >}}*Please note:* Creating tags and adding them to jobs is either done by using the respective REST API call, or manually from the [job view]({{< ref "job#tagging" >}} "Job View Tag Create").{{< /alert >}}