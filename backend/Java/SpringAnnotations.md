# Key Spring Annotations

### 1. @Component
- Used to indicate that a class is a Spring component. It is a generic stereotype annotation for any Spring-managed component.

```java
@Component
public class MyComponent {
    // Class implementation
}
```

### 2. @Autowired
- Used to automatically wire dependencies by type. It allows Spring to resolve and inject the appropriate beans into a dependent class.

```java
@Component
public class MyComponent {
    @Autowired
    private MyDependency myDependency;
    
    // Class implementation
}
```

### 3. @Controller
- Used to mark a class as a Spring MVC controller. It is typically used in combination with `@RequestMapping` to handle incoming web requests.

```java
@Controller
public class MyController {
    @RequestMapping("/hello")
    public String hello() {
        return "hello";
    }
    
    // Other handler methods
}
```

### 4. @Service
- Used to indicate that a class is a Spring service. It serves as a specialization of the `@Component` annotation and is used to define business logic.

```java
@Service
public class MyService {
    // Service methods
}
```

### 5. @Repository
- Used to indicate that a class is a Spring repository. It is typically used for database access and encapsulates storage, retrieval, and querying of data.

```java
@Repository
public class MyRepository {
    // Repository methods
}
```

### 6. @RequestMapping
- Used to map a URL pattern to a controller method. It handles incoming requests and directs them to the appropriate handler method.

```java
@Controller
@RequestMapping("/books")
public class BookController {
    @GetMapping("/{id}")
    public String getBook(@PathVariable String id) {
        // Retrieve book by ID
    }
    
    // Other handler methods
}
```

### 7. @PathVariable
- Used to bind a method parameter to a path variable in a URL. It allows you to extract dynamic values from the URL and use them in your controller methods.

```java
@Controller
@RequestMapping("/users")
public class UserController {
    @GetMapping("/{id}")
    public String getUser(@PathVariable String id) {
        // Retrieve user by ID
    }
    
    // Other handler methods
}
```

### 8. @RequestBody
- Used to bind the request body to a method parameter. It converts the request body (in JSON, XML, or other formats) into an object.

```java
@Controller
@RequestMapping("/users")
public class UserController {
    @PostMapping("/")
    public String createUser(@RequestBody User user) {
        // Create a new user
    }
    
    // Other handler methods
}
```

### 9. @Configuration
- Used to indicate that a class provides bean definitions. It is typically used in conjunction with `@Bean` to configure beans in a Spring application.

```java
@Configuration
public class AppConfig {
    @Bean
    public MyBean myBean() {
        return new MyBean();
    }
    
    // Other bean definitions
}
```

### 10. @Transactional
- Used to define the scope of a database transaction. It ensures that a method is executed within a transactional context, enabling ACID properties.

```java
@Service
@Transactional
public class MyService {
    // Transactional methods
}
```

### 11. @Scope
- Used to define the scope of a bean. It is typically used in combination with `@Component`, `@Service`, or `@Controller` annotations.

```java
@Component
@Scope("prototype") // Create a new instance for each request
public class MyComponent {
    // Class implementation
}
```

### 12. @Bean
- Used to declare a bean in Spring. It is typically used in methods annotated with `@Configuration` to define beans that will be managed by Spring.

```java
@Configuration
public class AppConfig {
    @Bean
    public MyBean myBean() {
        return new MyBean();
    }
    
    // Other bean definitions
}
```

### 13. @Value
- Used to inject values into fields in Spring-managed beans. It can be used in conjunction with `@PropertySource` to read values from a properties file.

```java
@Component
public class MyComponent {
    @Value("${my.property}")
    private String myProperty;
    
    // Class implementation
}
```

### 14. @Qualifier
- Used to resolve ambiguous dependencies. It is typically used in combination with `@Autowired` when a class has multiple beans of the same type.

```java
@Component
public class MyComponent {
    @Autowired
    @Qualifier("myBean")
    private MyBean myBean;
    
    // Class implementation
}
```

### 15. @PostConstruct
- Used to perform initialization logic after a bean has been constructed. It is typically used on methods that are called after dependency injection is complete.

```java
@Component
public class MyComponent {
    @PostConstruct
    public void init() {
        // Initialization logic
    }
    
    // Class implementation
}
```
