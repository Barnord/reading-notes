## Testing, Swagger, & Deployments

### Using HTTP Cookies

An HTTP cookie is a piece of data that servers send to browsers, the browser can save it and send it back with requests to the server that provided it.

Cookies are primarily used for three things:
- Session Management
  - Logins
  - Shopping carts
  - Game Scores
- Personalization
  - User Preferences
  - Themes
  - Other settings
- Tracking
  - Recording and analyzing user behavior

In the past cookies have been used for client-side storage. This is now atpyical and it is recommended to use storage APIs. Cookies are sent with every request, so performance can take a nose dive real quick when they're used frivolously.

### Creating Cookies

Upon receiving an HTTP request, a server can send Set-Cookie headers in the response. Browsers typically store the cookie, to send back with requests made to the same server inside a Cookie HTTP header. The server can set an expiration date or duration, after which the cookie will not be sent. The lifetime of a cookie can be set for the session, for a certain amount of time, or until a certain time. However, some browsers use session restoring, so a cookie set to expire at the end of a session, may last indefinitely.

### Restricting Access to Cookies

We can ensure cookies are only used how we want them using the `Secure` or `HttpOnly` attributes, though I have a feeling those are a javascript thing I'm sure there are parallels.

A cookie that was been secured with the attribute can only be sent back to the server, over an encrypted request using the HTTPS protocol, the only exception being over localhost. Insecure sites can't set cookies with the Secure attribute.

A cookie with the HttpOnly attribute can only be used by the server.

### Guiding Cookies

The `Domain` and `Path` attributes define where the cookies should be sent.

#### Domain Attribute

The `Domain` attribute sets which domains are eligible for the cookie. If Domain is specified, subdomains are always included.

#### Path Attribute

The `Path` attribute sets a URL path that has to exist in the requested URL in order to send the Cookie header.

#### SameSite Attribute

The `SameSite` attribute lets servers specify wheather/when cookies are sent with cross-site requests, which provides protection against cross-site request forgery attacks. It takes one of three values, `Strict`, `Lax`, or `None`. With `Strict` the cookie will only be sent to the same site it was created on. `Lax` is similar, except cookies are sent when a user navigates to the origin site. Setting `None` requires the `Secure` attribute to be set. If no `SameSite` attribute is set, the cookie is treated as `Lax`.

### Cookie Prefixes

Cookies are designed so a server can't tell where or how a cookie was originally set. You can set two hidden prefixes though, being `_Host-` and `_Secure-`. 

If a cookie has the `_Host-` prefix, it will be accepted in a `Set-Cookie` header only if it is also marked with the `Secure` attribute, does not include a `Domain` attribute, and has the `Path` attribute set to `/`. These cookies are seen as domain locked.

If a cookie has the `_Secure-` prefix, it will only be accepted in a `Set-Cookie` header if it is marked with the `Secure` attribute.

Cookies marked with these prefixes that do not meet all the restrictions are rejected by the browser.

### Cookies Explained

I thought I would go my entire life without hearing the word Netscape again, but here we are. Lou Montulli, of Netscape Communications, invented HTTP cookies, and now has a patent for them. Most of this article was explained in the MDN Docs.

### Cookies Simplified

HTTP is a stateless protocol, meaning different sites, or even different pages on one server don't inherently share any data

#### Setting and Reading Cookies

Cookies in ASP.NET look something like this:
```HttpContext.Response.Cookies.Append("user_id", "1");```
The `Response` property on the `HttpContext` also has a `Cookies` property. Using Append we added a user_id property to the cookie, which we can read like this:
```var userId = HttpContext.Request.Cookies["user_id"];```
They used var but in this instance I think int would likely be better.

We can access various properties of the cookie if we include the following namespace:
```using Microsoft.AspNetCore.Http;```
Now we can set some options too the cookie, by instantiating a CookieOptions object, and including it as the third argument in an Append like before.

Examples of properties we can add:
- .Expires: `cookieOptions.Expires = new DateTimeOffset(DateTime.Now.AddDays(7));`
- .Domain: `cookieOptions.Domain = ".mywebsite.com";`
- .Path: `cookieOptions.Path = "/users/";`


[<==Back](README.md)