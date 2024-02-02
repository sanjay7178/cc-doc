---
title: Environment
description: >
  ClusterCockpit Environment Variables
categories: [cc-backend]
tags: [Backend]
weight: 3
---

## Environment Variables

An example env file is found in this directory. Copy it to `.env` in the project root and adapt it for your needs.

* `JWT_PUBLIC_KEY` and `JWT_PRIVATE_KEY`: Base64 encoded Ed25519 keys used for JSON Web Token (JWT) authentication. You can generate your own keypair using `go run ./cmd/gen-keypair/gen-keypair.go`. More information in [README_TOKENS.md](./README_TOKENS.md).
* `SESSION_KEY`: Some random bytes used as secret for cookie-based sessions.
* `LDAP_ADMIN_PASSWORD`: The LDAP admin user password (optional).
* `CROSS_LOGIN_JWT_HS512_KEY`: Used for token based logins via another authentication service.
* `LOGLEVEL`: Can be `err`, `warn`, `info` or `debug` (optional, `warn` by default). Can be used to reduce logging.
