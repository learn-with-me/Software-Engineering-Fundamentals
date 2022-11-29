# Authentication

##### Protocols

* LDAP
* Kerberos
* OAuth 2
* SAML
* RADUIS
* OpenID Connect

### API

##### Communication Protocols

* [https://en.wikipedia.org/wiki/WebDAV](https://en.wikipedia.org/wiki/WebDAV)
* [https://coap.technology](#)
  * [https://en.wikipedia.org/wiki/Constrained\_Application\_Protocol](https://en.wikipedia.org/wiki/Constrained_Application_Protocol)
* HTTP/2

##### Basic Authentication

HTTP Basic authentication is described in RFC 2617. It’s a simple username/password scheme. The user of an API is supposed to set up a username and password ahead of time—probably by registering an account on an affiliated website, or by sending an email requesting anAPI account. There’s no standard for how to request a username and password for a given site.

However it happens, once user has their username and password, they can make that original HTTP request again. This time they uses their username and password to generate a value for the request header Authorization.

Basic Auth is simple, but it has two big problems. The first is that it’s not secure. YWxpY2U6cGFzc3dvcmQ= looks like encrypted gibberish, but it’s actually the string user:password run through a simple, reversible transform called Base64. This means that anyone spying on User’s Internet connection now knows their password. They can impersonate the user by sending HTTP requests that include Authorization: Basic YWxpY2U6cGFzc3dvcmQ=.

This problem goes away if the API uses HTTPS instead of plain HTTP. Someone spying on user’s Internet connection will see them open a connection, but the request and response will be encrypted by the SSL layer.

RFC 2617 defines a second authentication method called Digest, which avoids this problem even when HTTPS is not in use. Digest and Basic share a second problem, which is not a big deal on the World Wide Web, but is very serious in the world of APIs: the people who use an API generally can’t trust their clients.

To make the problem obvious, imagine a very popular API such as the Twitter API. This API is so popular that user is using 10 different clients for this one API. There are a few on their mobile phone, a few on their desktop computer, and they’re given permission to several different websites to use this API on their behalf. \(This happens all the time.\) Ten different clients. What happens when one of the clients goes rogue and starts posting spam to user’s account? \(This also happens frequently.\) In the wake of the attack, User must change their password. They must do this so that the rogue client no longer has valid credentials. But they've given all 10 clients the same password. Nine of the clients are still trustworthy, but changing the password breaks all 10.

##### OAUTH 1.0

Under OAuth, user gives each client an individual set of credentials. If they decides they don’t like one of the clients, they can revokes its credentials, and the other nine clients are unaffected. If a client goes rogue and starts posting spam under the names of its users, the service provider can step in and revoke the credentials for every instance of that client’s and everyone else’s.

There are two versions of OAuth. OAuth 1.0 \(defined in RFC 5849\) works well for allowing the developers of consumer-facing websites to integrate with your API. It starts falling apart when you want to allow the integration of desktop, mobile, or in-browser applications with your API. OAuth 2.0 is very similar to 1.0, but it defines ways to handle these scenarios.

### Reference Articles

```
https://community.getkisi.com/which-authentication-protocol-to-choose-ldap-kerberos-oauth2-saml-radius/
https://learning.oreilly.com/library/view/restful-web-apis/9781449359713/ch11.html

Communication Protocols
https://www.westuc.com/en-us/blog/hosted-voice-networks/ip-communication-protocols-101
https://www.concise-courses.com/11-protocols/
https://www.lifewire.com/definition-of-protocol-network-817949
http://csfieldguide.org.nz/en/chapters/network-communication-protocols.html
https://www.postscapes.com/internet-of-things-protocols/
https://www.eclipse.org/community/eclipse_newsletter/2014/february/article2.php
https://www.micrium.com/iot/internet-protocols/
```



