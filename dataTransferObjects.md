## Data Transfer Objects (DTOs)

A Data Transfer Object, is an object we create based on the object the client references in our database. We use DTO's to hide properties that the client doesn't need, or that we don't want them to have. We do this by setting another model to use to send data to the client, using only things we want them to have. We set our get requests to create a new object using the DTO that we then send to the client. DTO's typically only contain data.

[<==Back](README.md)