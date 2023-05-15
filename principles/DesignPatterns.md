## Software Engineering Design Patterns

### 1. Singleton Pattern
- Ensures that a class has only one instance and provides a global point of access to it.

```java
// Example of Singleton Pattern
public class Database {
    private static Database instance;

    private Database() {
        // Private constructor to prevent instantiation
    }

    public static Database getInstance() {
        if (instance == null) {
            instance = new Database();
        }
        return instance;
    }
}
```

### 2. Factory Pattern
- Provides an interface for creating objects but allows subclasses to decide which class to instantiate.

```java
// Example of Factory Pattern
public interface Animal {
    void makeSound();
}

public class Dog implements Animal {
    public void makeSound() {
        System.out.println("Bark!");
    }
}

public class Cat implements Animal {
    public void makeSound() {
        System.out.println("Meow!");
    }
}

public class AnimalFactory {
    public Animal createAnimal(String type) {
        if (type.equalsIgnoreCase("Dog")) {
            return new Dog();
        } else if (type.equalsIgnoreCase("Cat")) {
            return new Cat();
        }
        return null;
    }
}
```

### 3. Observer Pattern
- Defines a one-to-many dependency between objects, where a change in one object triggers updates to its dependents.

```java
// Example of Observer Pattern
import java.util.ArrayList;
import java.util.List;

public interface Observer {
    void update();
}

public class Subject {
    private List<Observer> observers = new ArrayList<>();

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update();
        }
    }
}

public class ConcreteObserver implements Observer {
    public void update() {
        System.out.println("Received update notification.");
    }
}
```

### 4. Strategy Pattern
- Enables selecting an algorithm at runtime and encapsulating it within its own class.

```java
// Example of Strategy Pattern
public interface SortingStrategy {
    void sort(int[] array);
}

public class BubbleSortStrategy implements SortingStrategy {
    public void sort(int[] array) {
        // Implementation of bubble sort algorithm
    }
}

public class QuickSortStrategy implements SortingStrategy {
    public void sort(int[] array) {
        // Implementation of quick sort algorithm
    }
}

public class Sorter {
    private SortingStrategy strategy;

    public void setStrategy(SortingStrategy strategy) {
        this.strategy = strategy;
    }

    public void sortArray(int[] array) {
        strategy.sort(array);
    }
}
```

### 5. Decorator Pattern
- Adds behavior or responsibilities to individual objects dynamically without affecting the behavior of other objects.

```java
// Example of Decorator Pattern
public interface Shape {
    void draw();
}

public class Circle implements Shape {
    public void draw() {
        System.out.println("Drawing a circle.");
    }
}

public abstract class ShapeDecorator implements Shape {
    protected Shape decoratedShape;

    public ShapeDecorator(Shape decoratedShape) {
        this.decoratedShape = decoratedShape;
    }

    public void draw() {
        decoratedShape.draw();
    }
}

public class RedShapeDecorator extends ShapeDecorator {
    public RedShapeDecorator(Shape decoratedShape) {
        super(decoratedShape);
    }

    public void draw() {
        decoratedShape.draw();
        setRedBorder();
    }

    private void setRedBorder() {
        System.out.println("Adding red border to the shape.");
    }
}
```

### 6. Visitor Pattern
- The Visitor pattern separates the logic for performing operations on a data structure from the structure itself by defining separate visitor classes. This allows new operations to be added without modifying the existing structure.

```java
// Example demonstrating Visitor Pattern
interface Visitor {
  void visit(ElementA elementA);
  void visit(ElementB elementB);
}

interface Element {
  void accept(Visitor visitor);
}

class ElementA implements Element {
  public void accept(Visitor visitor) {
    visitor.visit(this);
  }
}

class ElementB implements Element {
  public void accept(Visitor visitor) {
    visitor.visit(this);
  }
}

class ConcreteVisitor implements Visitor {
  public void visit(ElementA elementA) {
    // Code to perform operation on ElementA
  }

  public void visit(ElementB elementB) {
    // Code to perform operation on ElementB
  }
}
```

### 7. Builder Pattern
- The Builder pattern is used to construct complex objects step by step. It provides a way to construct objects of a class without exposing its internal representation.

```java
// Example demonstrating Builder Pattern
class Product {
  private String name;
  private String description;
  private double price;

  // Constructor and getters...

  static class Builder {
    private String name;
    private String description;
    private double price;

    public Builder setName(String name) {
      this.name = name;
      return this;
    }

    public Builder setDescription(String description) {
      this.description = description;
      return this;
    }

    public Builder setPrice(double price) {
      this.price = price;
      return this;
    }

    public Product build() {
      return new Product(name, description, price);
    }
  }
}

// Usage:
Product product = new Product.Builder()
  .setName("Example Product")
  .setDescription("Product description")
  .setPrice(9.99)
  .build();
```

### 8. Adapter Pattern
- The Adapter pattern allows objects with incompatible interfaces to work together. It converts the interface of one class into another interface that clients expect.

```java
// Example demonstrating Adapter Pattern
interface MediaPlayer {
  void play(String audioType, String fileName);
}

interface AdvancedMediaPlayer {
  void playVlc(String fileName);
  void playMp4(String fileName);
}

class VlcPlayer implements AdvancedMediaPlayer {
  public void playVlc(String fileName) {
    // Code to play Vlc file
  }

  public void playMp4(String fileName) {
    // Not supported
  }
}

class Mp4Player implements AdvancedMediaPlayer {
  public void playVlc(String fileName) {
    // Not supported
  }

  public void playMp4(String fileName) {
    // Code to play Mp4 file
  }
}

class MediaAdapter implements MediaPlayer {
  private AdvancedMediaPlayer advancedMediaPlayer;

  public MediaAdapter(String audioType) {
    if (audioType.equalsIgnoreCase("vlc")) {
      advancedMediaPlayer = new VlcPlayer();
    } else if (audioType.equalsIgnoreCase("mp4")) {
      advancedMediaPlayer = new Mp4Player();
    }
  }

  public void play(String audioType, String fileName) {
    if (audioType.equalsIgnoreCase("vlc")) {
      advancedMediaPlayer.playVlc(fileName);
    } else if (audioType.equalsIgnoreCase("mp4")) {
      advancedMediaPlayer.playMp4(fileName);
    }
  }
}

class AudioPlayer implements MediaPlayer {
  private MediaAdapter mediaAdapter;

  public void play(String audioType, String fileName) {
    if (audioType.equalsIgnoreCase("mp3"))
```

### 10. Delegation Pattern
- The Delegation pattern allows an object to delegate some of its responsibilities to another object. It promotes code reuse and separates concerns by encapsulating the delegated behavior in a separate object.

```java
// Example demonstrating Delegation Pattern
interface Printer {
  void print(String message);
}

class ConsolePrinter implements Printer {
  public void print(String message) {
    System.out.println("Printing: " + message);
  }
}

class PrinterClient {
  private Printer printer;

  public PrinterClient(Printer printer) {
    this.printer = printer;
  }

  public void print(String message) {
    printer.print(message);
  }
}

// Usage:
Printer printer = new ConsolePrinter();
PrinterClient client = new PrinterClient(printer);
client.print("Hello, World!");
```

In the above example, the `PrinterClient` delegates the responsibility of printing to the `Printer` interface. By providing different implementations of the `Printer` interface, such as `ConsolePrinter` or `FilePrinter`, the client can switch or extend the behavior of printing without modifying the client code.

### 11. Facade Pattern
- The Facade pattern provides a simplified interface to a complex subsystem. It defines a higher-level interface that makes the subsystem easier to use.

```java
// Example demonstrating Facade Pattern
class CPU {
  public void freeze() { ... }
  public void jump(long position) { ... }
  public void execute() { ... }
}

class HardDrive {
  public byte[] read(long lba, int size) { ... }
}

class Memory {
  public void load(long position, byte[] data) { ... }
}

/* Facade */
class Computer {
  private CPU cpu;
  private Memory memory;
  private HardDrive hardDrive;

  public Computer() {
    this.cpu = new CPU();
    this.memory = new Memory();
    this.hardDrive = new HardDrive();
  }

  public void startComputer() {
    cpu.freeze();
    memory.load(BOOT_ADDRESS, hardDrive.read(BOOT_SECTOR, SECTOR_SIZE));
    cpu.jump(BOOT_ADDRESS);
    cpu.execute();
  }
}
```
