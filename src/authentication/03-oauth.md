# OAuth

OAuth (Open Authorization) is an open standard and protocol that facilitates secure authorization and access control for applications, enabling them to interact with each other on behalf of users without exposing their credentials. It is commonly used in scenarios where a third-party application needs access to a user's resources or data hosted on another service.

The primary use case for OAuth is to allow users to grant limited access to their resources on one website or application to another, without sharing their credentials (e.g., username and password). OAuth works by providing a secure and standardized way for users to authorize third-party applications to access specific resources on their behalf.

Here's a simplified breakdown of how OAuth works:

1. **User Initiates Authorization:**
   - A user wants to grant a third-party application access to their resources on a service (e.g., social media data, photos, contacts).

2. **Requesting Authorization (OAuth Client):**
   - The third-party application, known as the OAuth client, requests authorization from the user to access specific resources.

3. **Authorization Server Comes into Play:**
   - The OAuth client redirects the user to the authorization server (which is often the service where the user's resources are hosted). The user is asked to log in and grant or deny access to the requested resources.

4. **User Grants Access:**
   - If the user approves, the authorization server issues an authorization grant to the OAuth client.

5. **OAuth Client Requests Access Token:**
   - The OAuth client uses the authorization grant to request an access token from the authorization server. This access token is a key that allows the client to access the user's resources.

6. **Access Token Granted:**
   - If the authorization server verifies the request and the user's approval, it issues an access token to the OAuth client.

7. **Accessing Resources:**
   - The OAuth client uses the access token to authenticate itself and access the user's resources on the resource server (the server hosting the user's data).

By using OAuth, users can grant specific permissions to third-party applications without exposing their login credentials. It enhances security, privacy, and user control over their data while enabling seamless interactions between different applications and services. OAuth 2.0 is the most widely adopted version, providing improvements and enhancements over the original OAuth 1.0.

## OAuth 2.0

OAuth 2.0 (Open Authorization 2.0) is a widely adopted and standardized protocol that facilitates secure authorization and delegation of access in the context of web and mobile applications. It is designed to allow third-party applications to access resources on behalf of a user without exposing their credentials. OAuth 2.0 is widely used for enabling secure API authorization and access control.

Here's a high-level overview of how OAuth 2.0 works:

1. **Roles in OAuth 2.0:**
   - **Resource Owner:** The user who owns the resources (e.g., data, photos).
   - **Client:** The third-party application requesting access to the user's resources.
   - **Authorization Server:** The server that authenticates the user and issues access tokens.
   - **Resource Server:** The server hosting the user's resources.

2. **Authorization Grant Types:**
   - OAuth 2.0 defines several grant types that determine how the client obtains authorization. Common types include Authorization Code, Implicit, Resource Owner Password Credentials, and Client Credentials.

3. **Authorization Flow (Common Web Server Flow):**
   - The client redirects the user to the authorization server for authentication.
   - The user logs in and grants the client permission to access their resources.
   - The authorization server returns an authorization code to the client.

4. **Token Request:**
   - The client uses the authorization code to request an access token from the authorization server.

5. **Access Token Issued:**
   - If the authorization server verifies the request, it issues an access token to the client.

6. **Accessing Resources:**
   - The client uses the access token to authenticate itself when making requests to the resource server on behalf of the user.

7. **Refresh Token (Optional):**
   - To obtain a new access token without involving the user, the client can use a refresh token if provided during the initial authorization.

OAuth 2.0 provides a flexible and extensible framework, allowing implementations to tailor the protocol to specific use cases. It is widely used for securing API access in scenarios such as social media logins, allowing third-party applications to interact with user data without exposing sensitive information.

It's important to note that while OAuth 2.0 focuses on authorization, it does not explicitly address authentication. OpenID Connect (OIDC) is an extension of OAuth 2.0 that adds an authentication layer, providing a comprehensive solution for both authorization and user authentication.

## OAuth 1.0 vs 2.0

OAuth 1.0 and OAuth 2.0 are two versions of the OAuth protocol, each designed to address specific needs and challenges in securing authorization for web and mobile applications. Here are some key differences between OAuth 1.0 and OAuth 2.0:

1. **Security Mechanism:**
   - **OAuth 1.0:** Relies on a complex signature mechanism to ensure the integrity and authenticity of requests. It requires the use of cryptographic algorithms to sign each request, adding a layer of security.
   - **OAuth 2.0:** Simplifies the security model by relying on secure transport (e.g., HTTPS) for communication. It removes the complex signature mechanism used in OAuth 1.0, making it more straightforward to implement.

2. **Token Handling:**
   - **OAuth 1.0:** Involves the use of both access tokens and request tokens. Request tokens are exchanged for access tokens, adding an extra step to the process.
   - **OAuth 2.0:** Streamlines the token handling process by using only access tokens. It eliminates the need for request tokens, making the flow more straightforward.

3. **Authorization Grant Types:**
   - **OAuth 1.0:** Primarily relies on the "three-legged" authentication model, involving the resource owner, client, and server. It doesn't explicitly define different grant types.
   - **OAuth 2.0:** Introduces a variety of grant types, including Authorization Code, Implicit, Resource Owner Password Credentials, and Client Credentials. This provides flexibility for different use cases, such as web server flows, mobile app flows, and more.

4. **Scope of Standardization:**
   - **OAuth 1.0:** Offers a comprehensive specification for secure authorization but lacks a standardized framework for token refresh and other aspects.
   - **OAuth 2.0:** Provides a more modular and extensible framework. It standardizes not only the authorization process but also includes specifications for token refresh, scope, and additional features, allowing for easier integration and adaptation to various scenarios.

5. **Complexity:**
   - **OAuth 1.0:** Implementation can be more complex due to the signature mechanism, multiple token types, and a more intricate process.
   - **OAuth 2.0:** Simplifies the protocol, reducing complexity and making it more accessible for developers. However, the simplicity comes with a trade-off, as certain security responsibilities are shifted to the transport layer.

6. **Adoption and Compatibility:**
   - **OAuth 1.0:** Used in various applications but has seen a decline in adoption in favor of OAuth 2.0 due to its complexity.
   - **OAuth 2.0:** Widely adopted and considered the modern standard for secure authorization. It is the go-to choice for new applications and APIs.

In summary, OAuth 2.0 is a more streamlined, flexible, and widely adopted version of the OAuth protocol, addressing the shortcomings and complexities of OAuth 1.0. It has become the standard choice for securing authorization in modern web and mobile applications.

## OAuth 1.0

Under OAuth, user gives each client an individual set of credentials. If they decides they don’t like one of the clients, they can revokes its credentials, and the other nine clients are unaffected. If a client goes rogue and starts posting spam under the names of its users, the service provider can step in and revoke the credentials for every instance of that client’s and everyone else’s.

There are two versions of OAuth. OAuth 1.0 (defined in RFC 5849) works well for allowing the developers of consumer-facing websites to integrate with your API. It starts falling apart when you want to allow the integration of desktop, mobile, or in-browser applications with your API. OAuth 2.0 is very similar to 1.0, but it defines ways to handle these scenarios.

## References

* RFC 5849 | OAuth 1.0
* https://developer.box.com/reference/post-oauth2-token/
* https://developers.google.com/identity/protocols/oauth2
* https://www.oauth.com/oauth2-servers/access-tokens/
* https://learning.postman.com/docs/sending-requests/authorization/
* https://developer.twitter.com/en/docs/authentication/oauth-2-0/user-access-token
