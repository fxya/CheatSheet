## Key Jakarta EE Annotations

### 1. @ApplicationScoped
- The `@ApplicationScoped` annotation is used to specify that a bean should have a lifecycle that is scoped to the entire application.

```java
import javax.enterprise.context.ApplicationScoped;

@ApplicationScoped
public class MyService {
    // ...
}
```

### 2. @RequestScoped
- The `@RequestScoped` annotation is used to specify that a bean should have a lifecycle that is scoped to a single HTTP request.

```java
import javax.enterprise.context.RequestScoped;

@RequestScoped
public class MyBean {
    // ...
}
```

### 3. @SessionScoped
- The `@SessionScoped` annotation is used to specify that a bean should have a lifecycle that is scoped to a user session.

```java
import javax.enterprise.context.SessionScoped;

@SessionScoped
public class UserData {
    // ...
}
```

### 4. @Inject
- The `@Inject` annotation is used to indicate that a dependency should be injected into a class.

```java
import javax.inject.Inject;

public class MyService {
    @Inject
    private MyRepository repository;
    // ...
}
```

### 5. @EJB
- The `@EJB` annotation is used to inject an Enterprise JavaBean (EJB) into another class.

```java
import javax.ejb.EJB;

public class MyService {
    @EJB
    private MyBean bean;
    // ...
}
```

### 6. @Entity
- The `@Entity` annotation is used to mark a class as an entity in the Java Persistence API (JPA).

```java
import javax.persistence.Entity;

@Entity
public class Customer {
    // ...
}
```

### 7. @Resource
- The `@Resource` annotation is used to inject a resource (such as a data source or JMS queue) into a class.

```java
import javax.annotation.Resource;

public class MyService {
    @Resource
    private DataSource dataSource;
    // ...
}
```

### 8. @Path
- The `@Path` annotation is used to specify the URL path for a RESTful web service endpoint.

```java
import javax.ws.rs.GET;
import javax.ws.rs.Path;

@Path("/users")
public class UserResource {
    @GET
    public String getUsers() {
        // ...
    }
}
```

### 9. @Produces
- The `@Produces` annotation is used to specify the media types that a RESTful web service can produce.

```java
import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.Produces;
import javax.ws.rs.core.MediaType;

@Path("/users")
public class UserResource {
    @GET
    @Produces(MediaType.APPLICATION_JSON)
    public List<User> getUsers() {
        // ...
    }
}
```

### 10. @TransactionAttribute
- The `@TransactionAttribute` annotation is used to specify the transaction attribute for an EJB method.

```java
import javax.ejb.TransactionAttribute;
import javax.ejb.TransactionAttributeType;

@TransactionAttribute(TransactionAttributeType.REQUIRED)
public class MyService {
    // ...
}
```

