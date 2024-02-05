---
title: Command Line
description: >
  ClusterCockpit Command Line Options
categories: [cc-backend]
tags: [Backend]
weight: 1
---

This page describes the command line options for the `cc-backend` executable.

---

```
-add-user <username>:[admin,support,manager,api,user]:<password>
```

*Function:* Adds a new user to the database. Only one role can be assigned.

*Argument:* `<username>:[admin,support,manager,api,user]:<password>`

*Example:* `-add-user abcduser:manager:somepass`

---

```txt
  -config config.json
      Specify alternative path to config.json (default "./config.json")

  -del-user username
      Remove user by username

  -dev
      Enable development components: GraphQL Playground and Swagger UI

  -gops
      Listen via github.com/google/gops/agent (for debugging)

  -import-job <path-to-meta.json>:<path-to-data.json>,...
      Import a job. Argument format: <path-to-meta.json>:<path-to-data.json>,...

  -init
      Setup var directory, initialize swlite database file, config.json and .env

  -init-db
      Go through job-archive and re-initialize the 'job', 'tag', and 'jobtag' tables (all running jobs will be lost!)

  -jwt username
      Generate and print a JWT for the user specified by its username

  -logdate
      Set this flag to add date and time to log messages

  -loglevel [debug,info,warn (default),err,fatal,crit]
      Sets the logging level: [debug,info,warn,err,crit] (default: "info")

  -migrate-db
      Migrate database to supported version and exit

  -server
      Start a server, continues listening on port after initialization and argument handling

  -sync-ldap
      Sync the 'user' table with ldap

  -version
      Show version information and exit
```
