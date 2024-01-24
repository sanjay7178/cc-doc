---
title: Searchbar
description: >
  Searchbar Functionality
categories: [cc-backend]
tags: [Frontend, User]
weight: 3
---

The top searchbar will handle page wide searches either by entering a searchterm directly as `<query>`, or by using a "search tag" implemented in the form of `<tag>:<query>`. Entering a searchterm directly will start a hierarchical search which will return the first match in the hierarchy (see table below). It is recommended to supply the search with a tag to specify the searched entity. For example, `jobName:myJobName` will specifically search for all jobs which have the queried string (or a part thereof) in their `job.meta_data` column in the database. For all tags with examples, see the table below.

Both tags and queries are trimmed of all spaces before performing the search, returning the same results independently of location and number of spaces, e.g. ` name : Paul` and `name:  paul  ` are both handled identically.

Unprocessable queries will return a message detailing the cause of the error.

### Available Tags

|Tag|Example Query|Destination|Note|
|---|-------------|-----------|----|
|No Tag Used | `abcd100`           | [Joblist]({{< ref "views/joblist" >}} "Joblist") or [User Joblist]({{< ref "views/userjobs" >}} "User Joblist") | Performs hierarchical search `jobId -> username -> name -> projectId -> jobName` |
|JobId       | `jobId:123456`      | [Joblist]({{< ref "views/joblist" >}} "Joblist")         | Allows multiple identical matches, e.g. JobIds from different clusters |
|JobName     | `jobName:myJobName` | [Joblist]({{< ref "views/joblist" >}} "Joblist")         | Works with partial queries. Allows multiple identical matches, e.g. JobNames from different clusters |
|ProjectId   | `projectId:abcd100` | [Joblist]({{< ref "views/joblist" >}} "Joblist")         | All Jobs of the given project |
|Username    | `username:abcd100a` | [Users Table]({{< ref "views/users" >}} "Users Table")   | Only active users are returned; Users without jobs are not shown. Also, a `Last 30 Days` is active by default and might filter out expected users. **Admin Only**|
|Name        | `name:Paul`         | [Users Table]({{< ref "views/users" >}} "Users Table")   | Works with partial queries. Only active users are returned; Users without jobs are not shown. Also, a `Last 30 Days` is active by default and might filter out expected users. **Admin Only**|
|ArrayJobId  | `arrayJobId:891011` | [Joblist]({{< ref "views/joblist" >}} "Joblist")         | All Jobs of the given arrayJobId|
