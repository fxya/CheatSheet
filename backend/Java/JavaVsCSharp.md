# Java vs C# principles and language features.

### Principles and Language Features

| **Principle / Feature**          | **Java**                        | **C#**                          |
|----------------------------------|---------------------------------|---------------------------------|
| Object-Oriented                  | Yes                             | Yes                             |
| Garbage Collection               | Yes                             | Yes                             |
| Platform Independence            | Write Once, Run Anywhere (WORA) | Write Once, Run Anywhere (WORA) |
| Exception Handling               | try-catch-finally               | try-catch-finally               |
| Generics                         | Yes                             | Yes                             |
| Reflection                       | Yes                             | Yes                             |
| Multithreading                   | Yes                             | Yes                             |
| Lambda Expressions               | Yes                             | Yes                             |
| LINQ (Language Integrated Query) | No                              | Yes                             |

### Examples

#### Object-Oriented Programming

```java
// Java
public class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

```csharp
// C#
public class Person {
    private string name;
  
    public Person(string name) {
        this.name = name;
    }
  
    public string Name {
        get { return name; }
        set { name = value; }
    }
}
```

#### Exception Handling

```java
// Java
try{
        // Code that may throw an exception
        }catch(Exception e){
        // Handle the exception
        }finally{
        // Code that will always execute
        }
```

```csharp
// C#
try {
    // Code that may throw an exception
} catch (Exception e) {
    // Handle the exception
} finally {
    // Code that will always execute
}
```

#### Generics

```java
// Java
class Box<T> {
    private T value;

    public Box(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }

    public void setValue(T value) {
        this.value = value;
    }
}
```

```csharp
// C#
class Box<T> {
    private T value;
  
    public Box(T value) {
        this.value = value;
    }
  
    public T Value {
        get { return value; }
        set { this.value = value; }
    }
}
```

#### Reflection

```java
// Java
Class<Person> personClass=Person.class;
Method[]methods=personClass.getMethods();
```

```csharp
// C#
Type personType = typeof(Person);
MethodInfo[] methods = personType.GetMethods();
```

#### Multithreading

```java
// Java
Thread thread=new Thread(()->{
        // Code to be executed in a separate thread
        });
        thread.start();
```

```csharp
// C#
Thread thread = new Thread(() => {
    // Code to be executed in a separate thread
});
thread.Start();
```

#### Lambda Expressions

```java
// Java
List<Integer> numbers=Arrays.asList(1,2,3,4,5);
        numbers.forEach(number->System.out.println(number));
```

```csharp
// C#
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
numbers.ForEach(number => Console.WriteLine(number));
```

#### LINQ (Language Integrated Query)

```csharp
// C#
List<int>

numbers = new List<int> { 1, 2, 3, 4, 5 };
var evenNumbers = from number in numbers
                  where number % 2 == 0
                  select number;
```


