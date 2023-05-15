# SOLID Principles

### 1. Single Responsibility Principle (SRP)
- A class should have only one reason to change.

```java
// Example demonstrating Single Responsibility Principle
class UserService {
  public void createUser(User user) {
    // Code to create a new user
  }
}

class EmailService {
  public void sendEmail(String recipient, String message) {
    // Code to send an email
  }
}
```

### 2. Open-Closed Principle (OCP)
- Software entities should be open for extension but closed for modification.

```java
// Example demonstrating Open-Closed Principle
interface Shape {
  double calculateArea();
}

class Rectangle implements Shape {
  private double width;
  private double height;

  // Constructor and other methods...

  public double calculateArea() {
    return width * height;
  }
}

class Circle implements Shape {
  private double radius;

  // Constructor and other methods...

  public double calculateArea() {
    return Math.PI * radius * radius;
  }
}
```

### 3. Liskov Substitution Principle (LSP)
- Subtypes must be substitutable for their base types.

```java
// Example demonstrating Liskov Substitution Principle
class Shape {
  public double calculateArea() {
    // Code to calculate area
  }
}

class Rectangle extends Shape {
  private double width;
  private double height;

  // Constructor and other methods...
}

class Square extends Shape {
  private double side;

  // Constructor and other methods...
}
```

### 4. Interface Segregation Principle (ISP)
- Clients should not be forced to depend on interfaces they do not use.

```java
// Example demonstrating Interface Segregation Principle
interface Flyable {
  void fly();
}

interface Swimmable {
  void swim();
}

class Bird implements Flyable {
  public void fly() {
    // Code for flying
  }
}

class Fish implements Swimmable {
  public void swim() {
    // Code for swimming
  }
}
```

### 5. Dependency Inversion Principle (DIP)
- High-level modules should not depend on low-level modules. Both should depend on abstractions.

```java
// Example demonstrating Dependency Inversion Principle
interface NotificationService {
  void sendNotification();
}

class EmailService implements NotificationService {
  public void sendNotification() {
    // Code to send an email notification
  }
}

class SMSService implements NotificationService {
  public void sendNotification() {
    // Code to send an SMS notification
  }
}

class NotificationClient {
  private final NotificationService notificationService;

  public NotificationClient(NotificationService notificationService) {
    this.notificationService = notificationService;
  }

  public void sendNotification() {
    notificationService.sendNotification();
  }
}
```
