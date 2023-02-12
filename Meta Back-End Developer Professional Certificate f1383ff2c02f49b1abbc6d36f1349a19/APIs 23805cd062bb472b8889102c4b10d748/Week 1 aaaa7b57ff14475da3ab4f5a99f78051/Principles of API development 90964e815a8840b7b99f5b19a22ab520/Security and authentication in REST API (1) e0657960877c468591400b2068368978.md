# Security and authentication in REST API (1)

# Securing API

APIs make data more accessible, but they also pose a risk to back-end services since they allow third-party apps to access the server and database. Here are the best practices for securing APIs:

## SSL (Secure Socket Layer)

- SSL encrypts data and protects it when it travels between the browser and the web server.
- To set up SSL certificates properly, APIs should be served over HTTPS instead of HTTP.
- Always check that the endpoint of your APIs starts with HTTPS instead of HTTP.

**Example:**

The Little Lemon project team uses SSL certificates from a reputable provider to secure all API endpoints.

## Signed URLs

- Signed URLs limit client application access to a specific resource for a brief period of time.
- The signature is included with the URL in every API call to verify the authenticity of the message.
- HMAC (Hash-based Message Authentication Code) is a popular signing mechanism used to create signatures.

**Example:**

- The Little Lemon team uses signed URLs to ensure that API calls only come from their mobile application and website.
- A secret message is encoded with a digest algorithm and secret key to create the HMAC signature.

# ****Authentication****

- Token-based authentication is preferred over HTTP-based authentication for better security.
- The user sends their username and password to a sign-in URL, and receives a unique token in return.
- Every API call includes the token as a HTTP header, and the server-side code verifies the token and matches it with an existing user.
- JSON Web Token (JWT) is a popular industry standard for token creation.

**Example:**

- The Little Lemon team uses token-based authentication for its APIs.
- The user sends their username and password to the sign-in URL and receives a unique token in return.
- The token is included in every API call as a HTTP header.

# **HTTP Codes**

- 401 means unauthorized (username and password don't match).
- 403 means forbidden (credentials are valid but the user doesn't have the authority to perform the action).

# **CORS Policy and Firewalls**

- APIs can either accept calls from everywhere, or only from specific domains by configuring the CORS headers.
- Firewalls can be used to ensure that only specific IP addresses can access the API.

Example:

- The Little Lemon project team uses a firewall application on their server to ensure that only specific IP addresses can access their API.

# Conclusion

Security is a crucial aspect of API design. By following these best practices for securing APIs, you can protect your infrastructure and user data.