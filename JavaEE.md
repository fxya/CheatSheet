# Java EE Cheat Sheet

### Servlets
- Servlets are Java classes that handle HTTP requests and generate HTTP responses.

```java
// Example Servlet
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
  protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    response.setContentType("text/plain");
    PrintWriter out = response.getWriter();
    out.println("Hello, World!");
    out.close();
  }
}
```

### JSP (JavaServer Pages)
- JSP allows you to embed Java code in HTML to dynamically generate web content.

```jsp
<!-- Example JSP -->
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
  <body>
    <h1>Welcome, <%= request.getParameter("name") %>!</h1>
  </body>
</html>
```

### JPA (Java Persistence API)
- JPA provides a standardized way to interact with databases using object-relational mapping (ORM).

```java
// Example JPA Entity
@Entity
@Table(name = "employees")
public class Employee {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;
  
  @Column(name = "name")
  private String name;
  
  // Getters and setters...
}
```

### EJB (Enterprise JavaBeans)
- EJBs are server-side components for building scalable and transactional business logic.

```java
// Example EJB Session Bean
@Stateless
public class ProductService {
  @PersistenceContext
  private EntityManager entityManager;
  
  public List<Product> getAllProducts() {
    TypedQuery<Product> query = entityManager.createQuery("SELECT p FROM Product p", Product.class);
    return query.getResultList();
  }
  
  // Other business methods...
}
```

### JAX-RS (Java API for RESTful Web Services)
- JAX-RS provides a simplified way to build RESTful web services.

```java
// Example JAX-RS Resource
@Path("/products")
public class ProductResource {
  @Inject
  private ProductService productService;
  
  @GET
  @Produces(MediaType.APPLICATION_JSON)
  public List<Product> getAllProducts() {
    return productService.getAllProducts();
  }
  
  // Other resource methods...
}
```

### JSF (JavaServer Faces)
- JSF is a component-based framework for building user interfaces.

```java
// Example JSF Managed Bean
@ManagedBean
@ViewScoped
public class UserBean {
  private String name;
  
  public void saveUser() {
    // Code to save user data
  }
  
  // Getters and setters...
}
```
