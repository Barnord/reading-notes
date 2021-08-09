## Claims-based authorization in ASP.NET Core

### Introduction to Authentication with ASP.NET Core

Authentication is who you are, authorization is what you're allowed to do.

#### Authentication is ASP.NET Core

ASP.NET 4.x has a property called User on HttpContext, which is a type of IPrincipal, which represents the current user in a request. In ASP.NET Core User is a property of ClaimsPrincipal, which implements IPrincipal. This switch highlights ASP.NET distancing from Role-based permissions, and their movement towards claims-based authentication.

#### Multiple Identities

Fancy guy Andrew Lock flies VIP apparently. This entire section just boils down to ClaimsPrincipal can have like a billion Identities, which can all have like a billion Claims each.

#### Creating a new Principal

Make claims, put them in ClaimsIdentity, put that in ClaimsPrincipal. All of those steps require a key.

### JWT to authenticate Servers API's

#### What is JWT?

JSON Web Token, ALL ABOARD THE CLAIM TRAIN.
Or if you want a real definition its a thing that encodes a JSON object to grant authorization from the server.

#### JWT Hammertime?

The three parts of a JWT are the Header, Payload, and Signature.

##### Header

alg: There are two main algorithms to sign our JWT signature, so we put what the algorithm is in the header to make sure both the client and the server (which I assume is what we're meaning when he says producer and consumer) are using the same one.
typ: Define the type of token, which for the purposes of JWT, will always be JWT.

##### Payload

Mostly contains claims. I regret making a header for this.

##### Signature

This is calculated by base64url encoding the header and payload and concatenating them with a period as a seperator, then encrypted with something and also the key.

#### Producer and Consumer concept of API's

Yep, server/client, except the client is also a server.

In server 2 server authentication both parties share the custom contract for API(s).

The producer side shares the secret, which is used to verify the token on one end, and create it on the other.

The consumer end encodes all the data in the payload of the JWT, which is decoded and verified by the producer.

The token should be sent in the header under the key jwt-token. Unless you name it something else.

We can identify the consumer by either setting `iss: CONSUMER_NAME_HERE` or by sending another header.

In summation JWT's are neat.



[<==Back](README.md)