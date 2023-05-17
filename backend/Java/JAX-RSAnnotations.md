# JAX-RS/Jersey annotations with code examples

### Resource Annotation
Use `@Path` to define the base URI path for the resource class or method.

```java
@Path("/users")
public class UserResource {
    // Class-level path: /users

    @GET
    @Path("/{id}")
    public Response getUserById(@PathParam("id") int id) {
        // Method-level path: /users/{id}
        // Code...
    }
}
```

### HTTP Methods
Use `@GET`, `@POST`, `@PUT`, `@DELETE`, `@HEAD`, or `@OPTIONS` to define HTTP methods.

```java
@Path("/users")
public class UserResource {

    @GET
    public Response getUsers() {
        // Code...
    }

    @POST
    public Response createUser(User user) {
        // Code...
    }

    @PUT
    @Path("/{id}")
    public Response updateUser(@PathParam("id") int id, User user) {
        // Code...
    }

    @DELETE
    @Path("/{id}")
    public Response deleteUser(@PathParam("id") int id) {
        // Code...
    }
}
```

### Path Parameters
Use `@PathParam` to extract path parameters.

```java
@Path("/users")
public class UserResource {

    @GET
    @Path("/{id}")
    public Response getUserById(@PathParam("id") int id) {
        // Code...
    }
}
```

### Query Parameters
Use `@QueryParam` to extract query parameters.

```java
@Path("/users")
public class UserResource {

    @GET
    public Response getUsers(@QueryParam("page") int page, @QueryParam("limit") int limit) {
        // Code...
    }
}
```

### Request Headers
Use `@HeaderParam` to extract request headers.

```java
@Path("/users")
public class UserResource {

    @GET
    public Response getUsers(@HeaderParam("Authorization") String token) {
        // Code...
    }
}
```

### Request Body
Use `@Consumes` to specify the MIME media types consumed by the resource.

```java
@Path("/users")
public class UserResource {

    @POST
    @Consumes(MediaType.APPLICATION_JSON)
    public Response createUser(User user) {
        // Code...
    }
}
```

### Response
Use `@Produces` to specify the MIME media types produced by the resource.

```java
@Path("/users")
public class UserResource {

    @GET
    @Produces(MediaType.APPLICATION_JSON)
    public Response getUsers() {
        // Code...
    }
}
```

### Exception Handling
Use `@Provider` to define an exception mapper.

```java
@Provider
public class CustomExceptionMapper implements ExceptionMapper<CustomException> {

    @Override
    public Response toResponse(CustomException ex) {
        // Code...
    }
}
```
