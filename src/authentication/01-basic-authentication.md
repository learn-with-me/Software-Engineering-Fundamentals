# 'Basic' HTTP Authentication Scheme

This is the most basic level of authentication. The key is `base64 encoded`, usually is derived from username and password. They key is sent in HTTP `Authorization` header of each API request, in the form `Basic xxxxxxxxx`.

What's the point?
I could've sent username and password as is.
True. Anyone can base64 decode the key and extract the credentials.
The reason for this authentication exists:
- Something is better than nothing
- Relies on the client for not sharing the key with anyone. Even though it doesn't guarantee that bad actors cannot somehow obtain the key

Where could this authentication be used?

## Key rotation
It is recommended to rotate your keys periodically.
Some service provide this ability built-in.
If the key is stolen by a bad actor

### Replacing Key


### Managing active/passive keys


## Deep Dive

HTTP Basic authentication is described in [RFC 2617](https://www.ietf.org/rfc/rfc2617.txt). It’s a simple username/password scheme. The user of an API is supposed to set up a username and password ahead of time—probably by registering an account on an affiliated website, or by sending an email requesting anAPI account. There’s no standard for how to request a username and password for a given site.

However it happens, once user has their username and password, they can make that original HTTP request again. This time they uses their username and password to generate a value for the request header Authorization.

Basic Auth is simple, but it has two big problems. The first is that it’s not secure. `YWxpY2U6cGFzc3dvcmQ=` looks like encrypted gibberish, but it’s actually the string `alice:password` run through a simple, reversible transform called Base64. This means that anyone spying on User’s Internet connection now knows their password. They can impersonate the user by sending HTTP requests that include `Authorization: Basic YWxpY2U6cGFzc3dvcmQ=`

This problem goes away if the API uses HTTPS instead of plain HTTP. Someone spying on user’s Internet connection will see them open a connection, but the request and response will be encrypted by the SSL layer.

RFC 2617 defines a second authentication method called Digest, which avoids this problem even when HTTPS is not in use. Digest and Basic share a second problem, which is not a big deal on the World Wide Web, but is very serious in the world of APIs: the people who use an API generally can’t trust their clients.

To make the problem obvious, imagine a very popular API such as the Twitter API. This API is so popular that user is using 10 different clients for this one API. There are a few on their mobile phone, a few on their desktop computer, and they’re given permission to several different websites to use this API on their behalf. \(This happens all the time.\) Ten different clients. What happens when one of the clients goes rogue and starts posting spam to user’s account? \(This also happens frequently.\) In the wake of the attack, User must change their password. They must do this so that the rogue client no longer has valid credentials. But they've given all 10 clients the same password. Nine of the clients are still trustworthy, but changing the password breaks all 10.

### RFC 7617

Defines the "Basic" Hypertext Transfer Protocol (HTTP) authentication scheme, which transmits credentials as user-id/password pairs, encoded using Base64.

## References

- [RFC 7617](https://httpwg.org/specs/rfc7617.html) - The 'Basic' HTTP Authentication Scheme
- [RFC 2617](https://www.ietf.org/rfc/rfc2617.txt) - HTTP Authentication: Basic and Digest Access Authentication
