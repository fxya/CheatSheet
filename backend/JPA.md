# JPA Annotations Cheat Sheet

### 1. @Entity
- The `@Entity` annotation is used to mark a class as an entity, representing a table in the database. Each instance of the entity represents a row in the table.

```java
@Entity
public class User {
  // Class properties and methods...
}
```

### 2. @Table
- The `@Table` annotation is used to specify the table name for an entity. It can be applied at the entity level or on a specific property to override the default table name.

```java
@Entity
@Table(name = "users")
public class User {
  // Class properties and methods...
}
```

### 3. @Id
- The `@Id` annotation is used to mark a property as the primary key of the entity.

```java
@Entity
public class User {
  @Id
  private Long id;

  // Other properties and methods...
}
```

### 4. @GeneratedValue
- The `@GeneratedValue` annotation is used to specify the generation strategy for the primary key values.

```java
@Entity
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  // Other properties and methods...
}
```

### 5. @Column
- The `@Column` annotation is used to specify the mapping between an entity property and a database column.

```java
@Entity
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  @Column(name = "full_name")
  private String fullName;

  // Other properties and methods...
}
```

### 6. @OneToMany
- The `@OneToMany` annotation is used to define a one-to-many relationship between two entities.

```java
@Entity
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  @OneToMany(mappedBy = "user")
  private List<Order> orders;

  // Other properties and methods...
}

@Entity
public class Order {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  @ManyToOne
  @JoinColumn(name = "user_id")
  private User user;

  // Other properties and methods...
}
```

### 7. @ManyToOne
- The `@ManyToOne` annotation is used to define a many-to-one relationship between two entities.

```java
@Entity
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  // Other properties and methods...
}

@Entity
public class Order {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  @ManyToOne
  @JoinColumn(name = "user_id")
  private User user;

  // Other properties and methods...
}
```

### 8. @NamedQuery
- The `@NamedQuery` annotation is used to define a named query for an entity.

```java
@Entity
@NamedQuery(name = "User.findByUsername", query = "SELECT u FROM User u WHERE u.username = :username")
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  private String username;

  // Other properties and methods...
}
```

The `@NamedQuery` annotation allows you to define a named query that can be referenced in your code using the specified name.

### 9. @Transactional
- The `@Transactional` annotation is used to mark a method or class as transactional, ensuring that the operations within the annotated scope are executed within a transaction.

```java
@Service
@Transactional