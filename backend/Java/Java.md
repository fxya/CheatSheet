# Intermediate Java Cheat Sheet

### Generics
- Generics allow you to write reusable code that can work with different types.

```java
// Example of a generic class
class Box<T> {
  private T item;

  public void setItem(T item) {
    this.item = item;
  }

  public T getItem() {
    return item;
  }
}

// Usage of the generic class
Box<String> stringBox = new Box<>();
stringBox.setItem("Hello");
String item = stringBox.getItem(); // "Hello"
```

### Wildcards
- Wildcards allow for flexibility when working with generics by representing an unknown type.

```java
// Example of a method with a wildcard parameter
void printList(List<?> list) {
  for (Object item : list) {
    System.out.println(item);
  }
}

// Usage of the method with different types of lists
List<Integer> numbers = Arrays.asList(1, 2, 3);
printList(numbers);

List<String> names = Arrays.asList("John", "Alice", "Bob");
printList(names);
```

### Enumerations (Enums)
- Enums define a fixed set of constants. You can use enums within switch statements.

```java
// Example enum definition
enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY
}

// Using enum constants
Day today = Day.WEDNESDAY;
System.out.println(today); // Output: WEDNESDAY

// Enum with custom values and methods
enum TrafficSignal {
    RED("Stop"), GREEN("Go"), YELLOW("Caution");

    private final String action;

    TrafficSignal(String action) {
        this.action = action;
    }

    public String getAction() {
        return action;
    }
}

TrafficSignal signal = TrafficSignal.RED;
System.out.println(signal.getAction()); // Output: Stop

```

### Lambda Expressions
- Lambda expressions provide a concise way to write anonymous functions.

```java
// Example of a lambda expression
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.forEach(number -> System.out.println(number));

// Example of using lambda with functional interfaces
interface Operation {
  int perform(int a, int b);
}

Operation addition = (a, b) -> a + b;
int result = addition.perform(3, 5); // 8
```

### Method References
- Method references provide a shorthand syntax for lambda expressions that call a single method.

```java
// Example of method reference to a static method
Function<Integer, Double> converter = Integer::doubleValue;
Double result = converter.apply(5); // Output: 5.0

// Example of method reference to an instance method of an object
List<String> names = Arrays.asList("John", "Alice", "Bob");
names.forEach(System.out::println); // Output: John, Alice, Bob

// Example of method reference to an instance method of a specific object
StringJoiner joiner = new StringJoiner(", ");
names.forEach(joiner::add);
String result = joiner.toString(); // Output: John, Alice, Bob
```

### Streams
- Streams provide a concise and functional approach to perform operations on collections in Java.
```java
// Example of using streams
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

int sum = numbers.stream()
    .filter(n -> n % 2 == 0)
    .mapToInt(n -> n)
    .sum();

System.out.println(sum); // 6
```

### Optional
- Optional is a container object used to represent a possibly null value and avoid null pointer exceptions.


```java
// Example of creating an Optional
Optional<String> nameOptional = Optional.of("John");

//  Example of checking if a value is present
    if (nameOptional.isPresent()) {
        String name = nameOptional.get();
    }

//  Example of using default value with Optional
    String name = nameOptional.orElse("Unknown");

//  Example of mapping a value with Optional
    Optional<Integer> lengthOptional = nameOptional.map(String::length);

//  Example of chaining operations with Optional
    Optional<String> upperCaseOptional = nameOptional.map(String::toUpperCase);

```

### Exception Handling
- Exception handling allows you to handle and recover from errors or exceptional situations.

```java
// Example of exception handling with try-catch block
try {
  int result = divide(10, 0); // Potential exception
  System.out.println(result);
} catch (ArithmeticException e) {
  System.out.println("Error: Division by zero");
}

// Example of throwing a custom exception
class CustomException extends Exception {
  public CustomException(String message) {
    super(message);
  }
}

void process(int value) throws CustomException {
  if (value < 0) {
    throw new CustomException("Invalid value");
  }
  // Other processing logic
}

// Example of try-with-resources with a file
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    String line = reader.readLine();
    // Process the file
    } catch (CustomException e) {
    // Handle exception
}

// Example of try-with-resources with multiple resources
    try (InputStream input = new FileInputStream("file1.txt");
    OutputStream output = new FileOutputStream("file2.txt")) {
    // Read from input and write to output
    } catch (CustomException e) {
    // Handle exception
}

```

### Multithreading
- Multithreading enables concurrent execution of multiple threads for efficient utilization of resources.

```java
// Example of creating and running a thread
class MyThread extends Thread {
  public void run() {
    System.out.println("Thread running");
  }
}

MyThread thread = new MyThread();
thread.start(); // Start the thread

// Example of creating a thread using Runnable interface
class MyRunnable implements Runnable {
  public void run() {
    System.out.println("Runnable thread running");
  }
}

Thread thread = new Thread(new MyRunnable());
thread.start(); // Start the thread
```

