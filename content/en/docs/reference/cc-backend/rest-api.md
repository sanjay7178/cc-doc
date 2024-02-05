---
title: REST API
type: "swagger"
description: >
  ClusterCockpit RESTful API Endpoint Reference
categories: [cc-backend]
tags: [Backend]
weight: 4
---
## Usage of Swagger UI

To use the [Swagger UI](https://swagger.io/tools/swagger-ui/) for testing you have to run an instance of cc-backend on localhost
(and use the default port 8080):

```bash
./cc-backend -server
```

You may want to start the demo as described [here](/docs/getting-started/) .
This Swagger UI is also available as part of `cc-backend` if you start it with
the `dev` option:

```bash
./cc-backend -server -dev
```

You may access it at [this URL](http://localhost:8080/swagger/).

## Swagger API Reference

{{< alert title="Non-Interactive Documentation" >}}
This reference is rendered using the `swaggerui` plugin based on the original definition file found in the ClusterCockpit [repository](https://github.com/ClusterCockpit/cc-backend/blob/master/api/swagger.json "ClusterCockpit GitHub"), *but without a serving backend*.</br></br>
This means that all interactivity ("Try It Out") will not return actual data. However, a `Curl` call and a compiled `Request URL` will still be displayed, if an API endpoint is executed.
{{< /alert >}}

{{< swaggerui src="https://raw.githubusercontent.com/ClusterCockpit/cc-backend/master/api/swagger.json" >}}
