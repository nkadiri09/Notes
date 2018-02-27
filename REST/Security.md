# How To Secure RESTful Services:

 Before a user can retrieve his data, he has to authorize himself. In the world of a REST service, sessions in the classical sense do not exist. Every call has to be authorized to access the resource.
 
 services are protected by Basic Auth. Basic Auth requires the client to send the username and password with each request (Base64 encoded as part of the header information). A sniffer could use that information to authorize his calls. Even if we would protect our service by SSL, we decided that Basic Auth was not the right approach for our service. Another method is to use a token, which will be changed with each request. A successful request would return the next token together with the response In this case, parallel requests or errors could easily lead to a logout. That’s why we decided to use OAuth 2.0. OAuth 2.0 uses the password only for the initial login. The OAuth login will return 2 tokens. Future requests have to be executed with the first token (Access Token). This token replaces the password for a given period of time. If someone would be able to intercept the traffic, he could use that token for that timeframe until the token expires. As soon as the token expires, the client can retrieve a new token by using the second token (refresh token).
 
 
