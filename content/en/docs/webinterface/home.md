---
title: Home
description: >
  Webinterface Home Page
categories: [cc-backend]
tags: [Frontend, User]
weight: 1
---

The entrypoint for each login via the login mask is a table containing each configured cluster as a row with the following columns:

* **Name**: The configured clusters' name
* **Running Jobs**: Number of Jobs currently running longer than 5 minutes (or configured `shortRunning` amount of time)
  * Clicking the Link will forward to the [job list]({{< ref "views/joblist" >}} "Job List") with preset filters for cluster and running jobs
* **Total Jobs**: Number of Jobs in the respective job-archive
  * Clicking the Link will forward to the [job list]({{< ref "views/joblist" >}} "Job List") with preset filter for cluster
* **Status View**: Link to the [status view]({{< ref "views/status" >}} "Status View") of the respective cluster
* **Systems View**: Link to the [systems view]({{< ref "views/systems" >}} "Systems View") view of the respective cluster

{{< alert >}}TODO: Add Picture of home table{{< /alert >}}
