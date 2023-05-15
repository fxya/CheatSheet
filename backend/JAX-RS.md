# JAX-RS Principles

### 1. Resource-Oriented Architecture
- JAX-RS follows a resource-oriented architecture where resources are exposed as endpoints and can be accessed using standard HTTP methods.

```java
// Example JAX-RS resource class
@Path("/users")
public class UserResource {

  @GET
  @Produces(MediaType.APPLICATION_JSON)
  public Response getUsers() {
    // Code to retrieve and return a list of users
  }

  @POST
  @Consumes(MediaType.APPLICATION_JSON)
  public Response createUser(User user) {
    // Code to create a new user
  }

  @GET
  @Path("/{id}")
  @Produces(MediaType.APPLICATION_JSON)
  public Response getUserById(@PathParam("id") String id) {
    // Code to retrieve and return a specific user by ID
  }

  @PUT
  @Path("/{id}")
  @Consumes(MediaType.APPLICATION_JSON)
  public Response updateUser(@PathParam("id") String id, User user) {
    // Code to update a specific user
  }

  @DELETE
  @Path("/{id}")
  public Response deleteUser(@PathParam("id") String id) {
    // Code to delete a specific user
  }
}
```

### 2. Annotations for Mapping HTTP Methods
- JAX-RS provides annotations to map Java methods to specific HTTP methods (GET, POST, PUT, DELETE) and define their behavior.

```java
@GET
@Path("/users")
@Produces(MediaType.APPLICATION_JSON)
public Response getUsers() {
  // Code to retrieve and return a list of users
}
```

### 3. Path Parameters and Query Parameters
- JAX-RS allows the use of path parameters and query parameters to pass data to resource methods.

```java
@GET
@Path("/users/{id}")
@Produces(MediaType.APPLICATION_JSON)
public Response getUserById(@PathParam("id") String id) {
  // Code to retrieve and return a specific user by ID
}

@GET
@Path("/users")
@Produces(MediaType.APPLICATION_JSON)
public Response getUsersByRole(@QueryParam("role") String role) {
  // Code to retrieve and return users by role
}
```

### 4. Content Negotiation
- JAX-RS supports content negotiation, allowing clients to specify the desired representation format (XML, JSON, etc.) using the `Accept` header.

```java
@GET
@Path("/users")
@Produces({ MediaType.APPLICATION_XML, MediaType.APPLICATION_JSON })
public Response getUsers() {
  // Code to retrieve and return a list of users
}
```

### 5. Response Building
- JAX-RS provides a `Response` object that allows you to build and customize the HTTP response sent back to the client.

```java
@POST
@Path("/users")
@Consumes(MediaType.APPLICATION_JSON)
public Response createUser(User user) {
  // Code to create a new user
  return Response.status(Response.Status.CREATED).build();
}
```

### 6. Exception Handling
- JAX-RS provides a `WebApplicationException` class that allows you to build and customize the HTTP response sent back to the client in case of an error.

```java
@GET
@Path("/users/{id}")
@Produces(MediaType.APPLICATION_JSON)
public Response getUserById(@PathParam("id") String id) {
  User user = // Code to retrieve a specific user by ID
  if (user == null) {
    throw new WebApplicationException(Response.Status.NOT_FOUND);
  }
  return Response.ok(user).build();
}
```

### 7. Client API
- JAX-RS provides a client API that allows you to invoke RESTful web services from Java code.

```java
Client client = ClientBuilder.newClient();
WebTarget target = client.target("http://localhost:8080/api/users");
Response response = target.request().get();
List<User> users = response.readEntity(new GenericType<List<User>>() {});
```

### 8. Asynchronous Processing
- JAX-RS supports asynchronous processing, allowing you to return a `Future` object from a resource method.

```java
@GET
@Path("/users")
@Produces(MediaType.APPLICATION_JSON)
public Future<Response> getUsers() {
  return executorService.submit(() -> {
    // Code to retrieve and return a list of users
  });
}
```

### 9. Filters and Interceptors
- JAX-RS provides filters and interceptors that allow you to intercept and modify HTTP requests and responses.

```java
@Provider
public class LoggingFilter implements ContainerRequestFilter, ContainerResponseFilter {

  @Override
  public void filter(ContainerRequestContext requestContext) throws IOException {
    // Code to log the request
  }

  @Override
  public void filter(ContainerRequestContext requestContext, ContainerResponseContext responseContext) throws IOException {
    // Code to log the response
  }
}
```

### 10. Dependency Injection
- JAX-RS supports dependency injection, allowing you to inject resources into resource classes and resource methods.

```java
@Path("/users")
public class UserResource {

  @Inject
  private UserService userService;

  @GET
  @Produces(MediaType.APPLICATION_JSON)
  public Response getUsers() {
    List<User> users = userService.getUsers();
    return Response.ok(users).build();
  }
}
```

### 11. Content Marshalling
- JAX-RS supports content marshalling, allowing you to convert Java objects to and from JSON, XML, and other formats.

```java
@GET
@Path("/users")
@Produces(MediaType.APPLICATION_JSON)
public Response getUsers() {
  List<User> users = // Code to retrieve a list of users
  return Response.ok(users).build();
}
```

### 12. Security
- JAX-RS supports security, allowing you to secure your RESTful web services using standard Java EE security mechanisms.

```java
@GET
@Path("/users")
@Produces(MediaType.APPLICATION_JSON)
@RolesAllowed("ADMIN")
public Response getUsers() {
  List<User> users = // Code to retrieve a list of users
  return Response.ok(users).build();
}
```

### 13. Caching
- JAX-RS supports caching, allowing you to cache responses using standard HTTP caching mechanisms.

```java
@GET
@Path("/users")
@Produces(MediaType.APPLICATION_JSON)
@Cacheable
public Response getUsers() {
  List<User> users = // Code to retrieve a list of users
  return Response.ok(users).build();
}
```
