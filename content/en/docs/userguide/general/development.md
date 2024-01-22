---
title: Developement
description: >
  Tips for ClusterCockpit Development
---

## Frontend

The frontend assets including the Svelte js files are per default embedded in
the bgo binary. To enable a quick turnaround cycle for web development of the
frontend disable embedding of static assets in `config.json`:

```json
"embed-static-files": false,
"static-files": "./web/frontend/public/",

```

Start the node build process (in directory `./web/frontend`) in development mode:

```sh
$ npm run dev
```

This will start the build process in listen mode. Whenever you change a source
files the depending javascript targets will be automatically rebuild.
In case the javascript files are minified you may need to set the production
flag by hand to false in `./web/frontend/rollup.config.mjs`:

```mjs
const production = false
```

Usually this should work automatically.

Because the files are still served by ./cc-backend you have to reload the view
explicitly in your browser.

A common setup is to have three terminals open:
* One running cc-backend (working directory repository root): `./cc-backend -server -dev`
* Another running npm in developer mode (working directory `./web/frontend`): `npm run dev`
* And the last one editing the frontend source files

## Preparing Releases

### Steps

1. On `hotfix` branch:
   * Update ReleaseNotes.md
   * Update version in Makefile
   * Commit, push, and pull request
   * Merge in master

2. On Linux host:
   * Pull master
   * Ensure that GitHub Token environment variable `GITHUB_TOKEN` is set
   * Create release tag: `git tag v1.1.0 -m release`
   * Execute `goreleaser release`

### Release versions

Versions are marked according to [semantic versioning] (https://semver.org).
Each version embeds the following static assets in the binary:
* Web frontend with javascript files and all static assets.
* Golang template files for server-side rendering.
* JSON schema files for validation.
* Database migration files.

The remaining external assets are:
* The SQL database used.
* The job archive
* The configuration files `config.json` and `.env`.

The external assets are versioned with integer IDs.
This means that each release binary is bound to specific versions of the SQL
database and the job archive.
The configuration file is checked against the current schema at startup.
The `-migrate-db` command line switch can be used to upgrade the SQL database
to migrate from a previous version to the latest one.
We offer a separate tool `archive-migration` to migrate an existing job archive
archive from the previous to the latest version.

### Versioning of APIs

cc-backend provides two API backends:
* A REST API for querying jobs.
* A GraphQL API for data exchange between web frontend and cc-backend.

The REST API will also be versioned. We still have to decide whether we will also
support older REST API versions by versioning the endpoint URLs.
The GraphQL API is for internal use and will not be versioned.

### How to build

In general it is recommended to use the provided release binary.
In case you want to build build `cc-backend` please always use the provided makefile. This will ensure
that the frontend is also built correctly and that the version in the binary is encoded in the binary.

## Testing

We use the standard golang testing environment.

The following conventions are used:

* *White box unit tests*: Tests for internal functionality are placed in files
* *Black box unit tests*: Tests for public interfaces are placed in files
with `<package name>_test.go` and belong to the package `<package_name>_test`.
There only exists one package test file per package.
* *Integration tests*: Tests that use multiple componenents are placed in a
package test file. These are named `<package name>_test.go` and belong to the
package `<package_name>_test`.
* *Test assets*: Any required files are placed in a directory `./testdata`
within each package directory.

## Executing tests

Visual Studio Code has a very good golang test integration.
For debugging a test this is the recommended solution.

The Makefile provided by us has a `test` target that executes:
```sh
$ go clean -testcache
$ go build ./...
$ go vet ./...
$ go test ./...
```

Of course the commands can also be used on the command line.
For details about golang testing refer to the standard documentation:

* [Testing package](https://pkg.go.dev/testing)
* [go test command](https://pkg.go.dev/cmd/go#hdr-Test_packages)
