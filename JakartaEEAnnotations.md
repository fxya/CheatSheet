# Key Java EE Annotations

### 1. `@Entity`
- Used to define an entity class that represents a table in a database. Each instance of the class corresponds to a row in the table.

```java
@Entity
public class User {
  @Id
  private Long id;
  private String name;
  // ...
}
```

### 2. `@PersistenceContext`
- Used to inject a reference to the persistence context, which provides access to the EntityManager for managing entity objects.

```java
@Stateless
public class UserService {
  @PersistenceContext
  private EntityManager entityManager;
  // ...
}
```

### 3. `@Repository`
- Used to indicate that a class is a repository or a data access object (DAO) component.

```java
@Repository
public class UserRepository {
  @PersistenceContext
  private EntityManager entityManager;
  // ...
}
```

### 4. `@Service`
- Used to indicate that a class is a service component that provides business logic and acts as an intermediary between controllers and repositories.

```java
@Service
public class UserService {
  @Autowired
  private UserRepository userRepository;
  // ...
}
```

### 5. `@RestController`
- Used to indicate that a class is a RESTful controller that handles HTTP requests and returns responses as JSON or XML.

```java
@RestController
@RequestMapping("/users")
public class UserController {
  @Autowired
  private UserService userService;
  // ...
}
```

### 6. `@RequestMapping`
- Used to map HTTP requests to methods in a controller. It specifies the URL path and the HTTP method to handle.

```java
@RestController
@RequestMapping("/users")
public class UserController {
  @GetMapping("/{id}")
  public User getUserById(@PathVariable Long id) {
    // Code to retrieve user by ID
  }
}
```

### 7. `@RequestBody`
- Used to bind the request body to a method parameter in a controller. It is used when receiving data from the client in the form of JSON or XML.

```java
@RestController
@RequestMapping("/users")
public class UserController {
  @PostMapping
  public User createUser(@RequestBody User user) {
    // Code to create a new user
  }
}
```

### 8. `@PathParam`
- Used to extract path parameters from the URL in a RESTful controller.

```java
@RestController
@RequestMapping("/users")
public class UserController {
  @GetMapping("/{id}")
  public User getUserById(@PathVariable Long id) {
    // Code to retrieve user by ID
  }
}
```

### 9. `@QueryParam`
- Used to extract query parameters from the URL in a RESTful controller.

```java
@RestController
@RequestMapping("/users")
public class UserController {
  @GetMapping
  public List<User> getUsers(@QueryParam("page") int page, @QueryParam("limit") int limit) {
    // Code to retrieve users with pagination
  }
}
```
