---
title: Application Types - Confidential vs. Public
description: Understand the difference between confidential and public application types.
toc: true
topics:
  - applications
  - application-types
contentType: reference
useCase:
  - build-an-app
---
# Application Types: Confidential vs. Public

According to the [OAuth 2.0 spec](https://tools.ietf.org/html/rfc6749#section-2.1), applications can be classified as either confidential or public. The main difference relates to whether or not the application is able to hold credentials (such as a client ID and secret) securely.

## Confidential applications

Confidential applications are able to hold credentials in a secure way without exposing them to unauthorized parties. They require a trusted backend server to store the secret(s).

### Grant types

Because they use a trusted backend server, confidential applications can use grant types that require them to authenticate by specifying their client ID and secret when calling the token endpoint.

The following are considered to be confidential applications:

* A web application with a secure backend that uses the [Authorization Code grant](/api-auth/grant/authorization-code), [Password grant](/api-auth/grant/password), or [Password grant with Realm support](/api-auth/tutorials/password-grant#realm-support)
* A machine-to-machine (M2M) application that uses the [Client Credentials grant](/api-auth/grant/client-credentials)

### ID Tokens

Since confidential applications are capable of holding secrets, you can have ID Tokens issued to them that have been signed in one of two ways:

* Symmetrically, using their client secret (`HS256`)
* Asymmetrically, using a private key (`RS256`)

For more info, see [Signing Algorithms](//signing-algorithms)

## Public applications

Public applications **cannot** hold credentials securely. The following application types use public applications:

* Native desktop or mobile applications using the [Authorization Code grant with PKCE](/api-auth/grant/authorization-code-pkce)
* JavaScript-based client-side web applications (such as single-page apps) using the [Implicit](/api-auth/grant/implicit) grant

Since public applications are unable to hold secrets, [ID Tokens](/tokens/id-token) issued to them must be:

* Signed asymmetrically using a private key (`RS256`)
* Verified using the public key corresponding to the private key used to sign the token

## Keep reading
* Learn about other application categories, such as [first-party vs. third-party](/applications/concepts/app-types-first-third-party) and [Auth0 application types](/applications/concepts/app-types-auth0).