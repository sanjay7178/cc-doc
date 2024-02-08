---
title: JSON Web Token
description: >
 JSON Web Token (JWT) support in ClusterCockpit
categories: [cc-backend, cc-metric-store]
tags: [Developer, Admin]
---

## Introduction

ClusterCockpit uses JSON Web Tokens (JWT) for authorization of its APIs.
JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.
This information can be verified and trusted because it is digitally signed.
In ClusterCockpit JWTs are signed using a public/private key pair using ECDSA.
Because tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.
Expiration of the generated tokens as well as the maximum length of a browser session can be configured in the `config.json` file described [here]({{< ref "configuration" >}} "Job Metadata Schema Reference").

The [Ed25519](https://ed25519.cr.yp.to/) algorithm for signatures was used because it is compatible with other tools that require authentication, such as NATS.io, and because these elliptic-curve methods provide simillar security with smaller keys compared to something like RSA. They are sligthly more expensive to validate, but that effect is negligible.

## JWT Payload

You may view the payload of a JWT token at [https://jwt.io/#debugger-io](https://jwt.io/#debugger-io).
Currently ClusterCockpit sets the following claims:

* `iat`: Issued at claim. The “iat” claim is used to identify the the time at which the JWT was issued. This claim can be used to determine the age of the JWT.
* `sub`: Subject claim. Identifies the subject of the JWT, in our case this is the username.
* `roles`: An array of strings specifying the roles set for the subject.
* `exp`: Expiration date of the token (only if explicitly configured)

It is important to know that JWTs are not encrypted, only signed. This means that outsiders cannot create new JWTs or modify existing ones, but they are able to read out the username.

## Workflow

1. Create a new ECDSA Public/private keypair:

```bash
> go build ./cmd/gen-keypair/
> ./gen-keypair
```

2. Add keypair in your `.env` file. A template can be found in `./configs`.

When a user logs in via the `/login` page using a browser, a session cookie (secured using the random bytes in the `SESSION_KEY` env. variable you shoud change as well) is used for all requests after the successfull login. The JWTs make it easier to use the APIs of ClusterCockpit using scripts or other external programs. The token is specified n the `Authorization` HTTP header using the [Bearer schema](https://datatracker.ietf.org/doc/html/rfc6750) (there is an example below). Tokens can be issued to users from the configuration view in the Web-UI or the command line. In order to use the token for API endpoints such as `/api/jobs/start_job/`, the user that executes it needs to have the `api` role. Regular users can only perform read-only queries and only look at data connected to jobs they started themselves.

There are two usage scenarios:

* The APIs are used during a browser session. API accesses are authorized with
  the active session.
* The REST API is used outside a browser session, e.g. by scripts. In this case
  you have to issue a token manually. This possible from within the
  configuration view or on the command line. It is recommended to issue a JWT
  token in this case for a special user that only has the `api` role. By using
  different users for different purposes a fine grained access control and
  access revocation management is possible.

The token is commonly specified in the Authorization HTTP header using the Bearer schema.

## cc-metric-store

The [cc-metric-store](https://github.com/ClusterCockpit/cc-metric-store) also uses JWTs for authentication. As it does not issue new tokens, it does not need to kown the private key. The public key of the keypair that is used to generate the JWTs that grant access to the `cc-metric-store` can be specified in its `config.json`. When configuring the `metricDataRepository` object in the `cluster.json` file, you can put a token issued by ClusterCockpit itself.

## Setup user and JWT token for REST API authorization

1. Create user:

```bash
> ./cc-backend --add-user <username>:api:<password> --no-server
```

2. Issue token for user:

```bash
> ./cc-backend --jwt <username> --no-server
```

3. Use issued token token on client side:

```bash
> curl -X GET "<API ENDPOINT>" -H "accept: application/json" -H "Content-Type: application/json" -H "Authorization: Bearer <JWT TOKEN>"
```

## Accept externally generated JWTs provided via cookie

If there is an external service like an AuthAPI that can generate JWTs and hand
them over to ClusterCockpit via cookies, CC can be configured to accept them:

1. `.env`: CC needs a public ed25519 key to verify foreign JWT signatures.
   Public keys in PEM format can be converted with the instructions in
   [/tools/convert-pem-pubkey-for-cc](https://github.com/ClusterCockpit/cc-backend/blob/master/tools/convert-pem-pubkey/Readme.md)
   .

```bash
CROSS_LOGIN_JWT_PUBLIC_KEY="+51iXX8BdLFocrppRxIw52xCOf8xFSH/eNilN5IHVGc="
```

2. `config.json`: Insert a name for the cookie (set by the external service)
   containing the JWT so that CC knows where to look at. Define a trusted issuer
   (JWT claim 'iss'), otherwise it will be rejected. If you want usernames and
   user roles from JWTs ('sub' and 'roles' claim) to be validated against CC's
   internal database, you need to enable it here. Unknown users will then be
   rejected and roles set via JWT will be ignored.

```json
"jwts": {
    "cookieName": "access_cc",
    "forceJWTValidationViaDatabase": true,
    "trustedExternalIssuer": "auth.example.com"
}
```

3. Make sure your external service includes the same issuer (`iss`) in its JWTs.
   Example JWT payload:

```json
{
  "iat": 1668161471,
  "nbf": 1668161471,
  "exp": 1668161531,
  "sub": "alice",
  "roles": [
    "user"
  ],
  "jti": "a1b2c3d4-1234-5678-abcd-a1b2c3d4e5f6",
  "iss": "auth.example.com"
}
```
