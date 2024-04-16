# API Authentication

All the doors of a house is locked, including the main door. You want a guest to be able to access the house even when you're not around, so you hand them a special key. Without this key no one can enter the house. And any person who has that special key can open any door in the house. Think of authentication the same way.

API authentication is similar but in the world of software. You want clients to access your services through APIs, regardless of implementations like REST, gRPC, GraphQL, etc.

Authentication can be needed for various reasons: including blocking unauthorized access completely, or even gating certain operations to specific clients only, while everyone else can access everything. 

But there's another part to this story: `authorization`. Think of it as managing who gets access to different parts of the digital space. Authentication is like having a key, and authorization is deciding which rooms you can enter once you have that key. Together, they shape how we secure and control digital interactions.

It's important to note that authentication isn't necessary to protect against DDOS attacks. For that, techniques like `rate-limiting` requests can help.

## Index

* ['Basic' HTTP Authentication](./01-basic-authentication.md)
* [API Access Tokens](./02-access-tokens.md)
* [OAuth with OpenID](./03-oauth.md)
* SAML Federated Identity

## Authentication Methods

Adding authentication to APIs is crucial for securing access to resources and ensuring that only authorized users can interact with the API. There are several ways to implement authentication for APIs, depending on the requirements and the level of security needed. Here are different methods commonly used:

1. **API Keys:**
      - **How it works:** Developers generate an API key and include it in the API request headers.
      - **Pros:** Simple implementation, suitable for public APIs with lower security requirements.
      - **Cons:** API keys can be easily exposed if not handled securely.

2. **OAuth 2.0:**
      - **How it works:** OAuth 2.0 is an authorization framework that enables a third-party application to obtain limited access to an HTTP service. It involves roles such as clients, resource servers, and authorization servers.
      - **Pros:** Supports various grant types, including authorization code, implicit, client credentials, and more. Suitable for secure authentication in various scenarios.
      - **Cons:** Requires more complex setup and understanding, might be overkill for simpler applications.

3. **JWT (JSON Web Tokens):**
      - **How it works:** A compact, URL-safe means of representing claims to be transferred between two parties. It is often used for authentication and authorization.
      - **Pros:** Stateless, compact, and self-contained. Widely used for token-based authentication.
      - **Cons:** Tokens can be decoded to reveal information, so they should not contain sensitive data.

4. **Basic Authentication:**
      - **How it works:** Username and password are Base64-encoded and included in the Authorization header.
      - **Pros:** Simplicity and easy to implement.
      - **Cons:** Credentials are sent with each request, making it vulnerable to interception if not used with HTTPS.

5. **Bearer Token:**
      - **How it works:** Similar to API keys but often used with OAuth 2.0. The token is sent in the Authorization header.
      - **Pros:** Secure, can be easily revoked, and allows for fine-grained access control.
      - **Cons:** Tokens need to be stored securely, and the expiration time must be managed.

6. **OpenID Connect:**
      - **How it works:** Built on top of OAuth 2.0, provides identity layer by adding an identity token.
      - **Pros:** Standardized, widely adopted, and adds authentication capabilities to OAuth 2.0.
      - **Cons:** Complexity, might be overkill for simple applications.

7. **Certificate-based Authentication:**
      - **How it works:** Clients present a certificate to authenticate their identity.
      - **Pros:** Highly secure, suitable for situations where strong authentication is required.
      - **Cons:** Complex setup and management of client certificates.

When choosing an authentication method, consider factors such as the sensitivity of data, user experience, and the level of security required for your API. It's often a good practice to use HTTPS in conjunction with any authentication method to ensure secure communication.

## OAuth 2.0 + OpenID Connect

OAuth 2.0 and OpenID Connect (OIDC) are often used together to provide a comprehensive identity and access management solution. OAuth 2.0 primarily deals with authorization, allowing third-party applications to access resources on behalf of a user, whereas OpenID Connect extends OAuth 2.0 to provide an identity layer.

Here's a brief overview of how they work together:

1. **OAuth 2.0: Authorization Framework**
      - **Purpose:** Allows secure authorization from one system to another without exposing credentials.
      - **Usage:** Commonly used for delegated authorization scenarios, such as allowing a third-party application to access a user's resources (e.g., photos, contacts) on a resource server.

2. **OpenID Connect (OIDC): Identity Layer on Top of OAuth 2.0**
      - **Purpose:** Extends OAuth 2.0 to provide authentication and identity information.
      - **Usage:** Focuses on user authentication and provides identity information about the end-user.

By combining OAuth 2.0 and OpenID Connect, you can achieve both authorization and authentication in a single flow. When a user wants to access a resource (OAuth flow), they are also authenticated (OIDC flow), and the application receives an ID token along with the access token. The ID token contains information about the user, providing details like their identity and potentially other profile information.

This integration is particularly useful in scenarios where both access to resources and user identity information are required, such as in Single Sign-On (SSO) systems or when building applications that rely on user authentication and authorization. The use of OAuth 2.0 and OpenID Connect together is a common practice in modern authentication and authorization protocols.

## TODO

- API Authentication
- Ways to authentication
    - Issue with each method
    - Uses
- Authentication Protocols

##### Protocols

* SCRAM-SHA
* SASL-SSL

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
