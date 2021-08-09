## Identity

### Introduction to Identity on ASP.NET Core

ASP.NET Core Identity is a membership system that adds login functionality to ASP.NET Core apps. Users can make an account with the login information stored in Identity, or by using an external login provider, such as Facebook, Google, Microsoft Account, and Twitter. Identity can be configured using an SQL Server database.

### Authentication and Authorization System Demystified

#### Identity

##### Claims

A Claim is a single fact about the user, and therefore contains only a single piece of information. Claims are an object in ASP.NET Core, the most common constructor accepts two strings, type and value.

##### ClaimsIdentity

An identity represents a form of identification. A ClaimsIdentity is ASP.NET Cores parallel to a driver's license. A single instance of a ClaimsIdentity can be authenticated or not. Setting the AuthenticationType property will set IsAuthenticated to true.

##### ClaimsPrincipal

A Principal represents the user. It contains at least one instance of ClaimsIdentity. A ClaimsPrincipal contains ClaimsIdentity which contain Claims.

##### Verbs

The auth system uses five verbs, these are all independent actions that allow the user to sing in and access pages otherwise unavailable to them when used together.

- Authenticate
  - Gets user info if any exists.
- Challenge
  - Requests authentication from the user
- SignIn
  - Persists user's information somewhere
- SignOut
  - Removes useres persisted data
- Forbid
  - Denies access to unauthorized users.

##### Authentication Handlers

Authentication handlers implement the aforementioned verbs. ASP.NET Core's default auth handler is the Cookies authentication handler. An auth handler is not required to implement all of the verbs. Authentication hanglers must be registered with the auth ststem in order to be used and are associated with schemes. A scheme is a string that identifies a unique auth handler in a dictionary of auth handlers. The default Cookies auth handler scheme is "Cookies", but the scheme can be changed to anything, like a virtual property. Multiple auth handlers can be used in conjunction.

##### Authentication Middleware

Authentication middleware is a module that can be inserted into the startup sequence and runs on every request. Any time the user makes a request this code checks if the user is authenticated or not. The auth middleware makes all its requests to the auth handler, which returns the info to the auth middleware, which THEN populates the HttpContext.User object with returned information.

##### Authentication and Authorization Flow

All the aforementioned components must be used together to successfully authenticate and authorize a user to access a resource.

1. The request arrives at the server.
2. The authentication middleware calls the default handler's Authenticate method and populates the HttpContext.User object with any available information.
3. The ewquest arrives at the controller action.
4. If the action is not decorated with the `[Authorize]` attribute, display the page and stop.
5. If the action does have the `[Authorize]` attribute, the auth filter checks if the user is authenticated.
6. If the user isn't, the auth filter calls Challenge, redirecting to a signing authority.
7. Once the signing authority directs the user to the app, the auth filter checks if the user is authroized to view the page.
8. If the user is authorized, the page displays, otherwise Forbid is called, with displays the 'not authorized' page.



[<==Back](README.md)