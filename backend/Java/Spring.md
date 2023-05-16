# Spring Cheat Sheet

### Dependency Injection
- Spring provides powerful dependency injection capabilities, allowing you to manage object dependencies and promote loose coupling.

```java
// Example of dependency injection in Spring
@Service
public class UserService {
  private final UserRepository userRepository;

  @Autowired
  public UserService(UserRepository userRepository) {
    this.userRepository = userRepository;
  }

  // Other methods...
}
```

### Aspect-Oriented Programming (AOP)
- Spring AOP allows you to separate cross-cutting concerns and apply them to multiple components.

```java
// Example of AOP in Spring
@Aspect
@Component
public class LoggingAspect {

  @Before("execution(* com.example.service.UserService.*(..))")
  public void logBefore(JoinPoint joinPoint) {
    // Code to log before method execution
  }

  // Other advice types: @After, @Around, @AfterReturning, @AfterThrowing
}
```

### Spring MVC (Model-View-Controller)
- Spring MVC is a web framework that provides a flexible model for building web applications.

```java
// Example of a Spring MVC Controller
@Controller
@RequestMapping("/users")
public class UserController {

  @Autowired
  private UserService userService;

  @GetMapping("/{id}")
  public ResponseEntity<User> getUserById(@PathVariable("id") Long id) {
    User user = userService.getUserById(id);
    return ResponseEntity.ok(user);
  }

  // Other controller methods...
}
```

### Spring Data JPA
- Spring Data JPA provides an abstraction layer on top of JPA (Java Persistence API) for working with databases.

```java
// Example of a Spring Data JPA repository
@Repository
public interface UserRepository extends JpaRepository<User, Long> {

  List<User> findByAgeGreaterThan(int age);

  // Other query methods...
}
```

## Spring Boot Cheat Sheet

### Auto-Configuration
- Spring Boot provides automatic configuration based on dependencies, reducing boilerplate code.

```java
// Example of Spring Boot application class
@SpringBootApplication
public class MyApp {

  public static void main(String[] args) {
    SpringApplication.run(MyApp.class, args);
  }
}
```

### Embedded Web Server
- Spring Boot includes an embedded web server, making it easy to create standalone web applications.

```java
// Example of a Spring Boot REST Controller
@RestController
@RequestMapping("/api")
public class MyController {

  @GetMapping("/hello")
  public String hello() {
    return "Hello, World!";
  }

  // Other controller methods...
}
```

### Configuration Properties
- Spring Boot allows you to define configuration properties that can be easily accessed and configured.

```java
// Example of a Spring Boot configuration properties class
@ConfigurationProperties("myapp")
public class MyAppProperties {

  private String apiUrl;
  private int maxConnections;

  // Getters and setters...
}
```

### Spring Boot Actuator
- Spring Boot Actuator provides production-ready features for monitoring and managing your application.

```java
// Example of enabling Spring Boot Actuator
@SpringBootApplication
@EnableActuator
public class MyApp {

  // Main method and other configurations...
}
```
