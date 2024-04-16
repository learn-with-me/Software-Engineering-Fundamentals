# Proof Key for Code Exchange (PKCE)

Proof Key for Code Exchange (PKCE) is a security enhancement for the OAuth 2.0 authorization framework. It is specifically designed to address security concerns in scenarios where the traditional authorization code flow might be susceptible to interception attacks, particularly in mobile and native applications.

Here's a breakdown of PKCE:

1. **Background:**
   OAuth 2.0 authorization code flow involves exchanging an authorization code for an access token. However, in certain situations, malicious actors could intercept the authorization code during the callback to the client.

2. **Challenge-Response Mechanism:**
   PKCE introduces a challenge-response mechanism to secure the authorization code flow. Instead of sending the client secret with the authorization request (as in traditional OAuth flows), PKCE dynamically generates a secret for each authorization request.

3. **Code Verifier and Code Challenge:**
   Before initiating the authorization process, the client generates a random value called the "code verifier." It then transforms this verifier into a "code challenge" using a one-way cryptographic function, commonly SHA-256.

4. **Authorization Request:**
   The client includes the code challenge in the authorization request sent to the authorization server.

5. **Authorization Code Response:**
   If the authorization server approves the request, it returns an authorization code to the client.

6. **Token Exchange:**
   When exchanging the authorization code for an access token, the client includes the original code verifier. The authorization server verifies that the code verifier matches the one used to create the code challenge.

By employing PKCE, even if an attacker intercepts the authorization code, they won't be able to exchange it for an access token without the corresponding code verifier. PKCE adds an extra layer of security, especially in situations where client secrets cannot be reliably protected (e.g., in mobile or native applications).

In summary, PKCE is a security measure that helps prevent certain types of attacks in OAuth 2.0 authorization flows, making them more resilient in scenarios where code interception is a potential risk.

## References

* PKCE [RFC 7636](https://datatracker.ietf.org/doc/html/rfc7636)
