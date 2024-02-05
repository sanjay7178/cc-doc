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

```txt
-add-user <username>:[admin,support,manager,api,user]:<password>
```

*Function:* Adds a new user to the database. Only one role can be assigned.

*Example:* `-add-user abcduser:manager:somepass`

---

```txt
  -config <path>
```

*Function:* Specifies alternative path to application configuration file.

*Default:* `./config.json`

*Example:* `-config ./configfiles/configuration.json`

---

```txt
  -del-user <username>
```

*Function:* Removes a user from the database by username.

*Example:* `-del-user abcduser`

---

```txt
  -dev
```

*Function:* Enables development components: GraphQL Playground and Swagger UI.

---

```txt
  -gops
```

*Function:* Go server listens via github.com/google/gops/agent (for debugging).

---

```txt
  -import-job <path-to-meta.json>:<path-to-data.json>, ...
```

*Function:* Import one or more jobs by comma seperated list of paths to `meta.json` and `data.json`.

*Example:* `-import-job ./to-import/job1-meta.json:./to-import/job1-data.json,./to-import/job2-meta.json:./to-import/job2-data.json`

---

```txt
  -init
```

*Function:* Setups `var` directory. Initializes sqlite database file, `config.json` and `.env` environment variable file.

---

```txt
  -init-db
```

*Function:* Iterates the job-archive and re-initializes the 'job', 'tag', and 'jobtag' tables based on archived jobs.

{{< alert color="warning">}}**Caution:** All running jobs will be lost!{{< /alert >}}

---

```txt
  -jwt <username>
```

*Function:* Generates and prints a JWT for the user specified by its username.

*Example:* `-jwt abcduser`

---

```txt
  -logdate
```

*Function:* Set this flag to add date and time to log messages.

---

```txt
  -loglevel <level>
```

*Function:* Sets the loglevel of the running ClusterCockpit instance. "Debug" will print all levels, "Crit" will only log critical log messages.

*Arguments:* `debug | info | warn | err | crit`

*Default:* `info`

*Example:* `-loglevel debug`

---

```txt
  -migrate-db
```

*Function:* Migrate database to latest supported version and exit.

---

```txt
  -server
```

*Function:* Start a server, continues listening on configured port (Default: `:8080`) after initialization and argument handling.

---

```txt
  -sync-ldap
```

*Function:* Synchronizes the 'user' table with LDAP.

---

```txt
  -version
```

*Function:* Shows version information and exits.
