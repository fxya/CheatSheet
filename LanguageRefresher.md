# JavaScript Syntax

### Variables and Constants
- Declaration with `var`, `let`, and `const`:
  ```javascript
  var age = 25;
  let name = 'John';
  const PI = 3.14159;
  ```

### Data Types
- Primitive types: `number`, `string`, `boolean`, `null`, `undefined`
- Complex types: `object`, `array`, `function`, `date`
  ```javascript
  let age = 25; // number
  let name = 'John'; // string
  let isStudent = true; // boolean
  let person = { name: 'John', age: 25 }; // object
  let numbers = [1, 2, 3, 4, 5]; // array
  function greet() { /* ... */ } // function
  let now = new Date(); // date
  ```

### Control Flow
- `if` statement:
  ```javascript
  if (age >= 18) {
    console.log('You are an adult');
  } else {
    console.log('You are a minor');
  }
  ```

- `for` loop:
  ```javascript
  for (let i = 0; i < 5; i++) {
    console.log(i);
  }
  ```

- `while` loop:
  ```javascript
  let i = 0;
  while (i < 5) {
    console.log(i);
    i++;
  }
  ```

### Functions
- Function declaration:
  ```javascript
  function greet(name) {
    console.log('Hello, ' + name);
  }
  greet('John');
  ```

- Arrow function:
  ```javascript
  const greet = (name) => {
    console.log('Hello, ' + name);
  };
  greet('John');
  ```
  ```javascript
  // Regular Function Expression
  const multiply = function (a, b) {
  return a * b;
  };
  
  console.log(multiply(2, 3)); // Output: 6
  
  // Arrow Function
  const multiplyArrow = (a, b) => a * b;
  
  console.log(multiplyArrow(2, 3)); // Output: 6
  ```

### Objects
- Object creation and property access:
  ```javascript
  let person = {
    name: 'John',
    age: 25,
    greet() {
      console.log('Hello, ' + this.name);
    }
  };
  console.log(person.name);
  person.greet();
  ```
  
### Classes
  ```javascript

class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

    greet() {
      console.log(`Hello, my name is ${this.name}.`);
    }
  }

  // Creating an Instance
  const john = new Person('John', 25);
  john.greet(); // Output: Hello, my name is John.
```


### Array Destructuring
- Destructuring assignment allows you to extract values from arrays or objects and assign them to variables in a concise way.

```javascript
// Array Destructuring
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;

console.log(first); // Output: 1
console.log(second); // Output: 2
console.log(rest); // Output: [3, 4, 5]
```
### JavaScript Object Destructuring

- Object destructuring allows you to extract properties from an object and assign them to variables in a convenient way.

```javascript
// JavaScript Object Destructuring
const person = {
  name: 'John',
  age: 25,
  city: 'New York',
};

const { name, age } = person;

console.log(name); // Output: John
console.log(age); // Output: 25
```

### Spread Syntax
- The spread syntax allows you to expand elements of an array or object in places where multiple elements or key-value pairs are expected.

```javascript
// Spread Syntax with Arrays
const numbers = [1, 2, 3];
const newArray = [...numbers, 4, 5];

console.log(newArray); // Output: [1, 2, 3, 4, 5]

// Spread Syntax with Objects
const person = { name: 'John', age: 25 };
const newPerson = { ...person, city: 'New York' };

console.log(newPerson);
// Output: { name: 'John', age: 25, city: 'New York' }
```

### Promises
- Promises are used to handle asynchronous operations and provide a cleaner way to handle success and failure.

```javascript
// Creating a Promise
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Some data';
      if (data) {
        resolve(data);
      } else {
        reject('Error: Data not found');
      }
    }, 2000);
  });
};

// Consuming a Promise
fetchData()
  .then((data) => {
    console.log('Success:', data);
  })
  .catch((error) => {
    console.log('Error:', error);
  });
```

### Async/Await
- `async/await` is syntactic sugar on top of promises, providing a more sequential and synchronous-looking way to write asynchronous code.

```javascript
// Asynchronous Function using Async/Await
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.log('Error:', error);
  }
}

// Consuming the Asynchronous Function
async function getData() {
  const result = await fetchData();
  console.log('Data:', result);
}

getData();
```

In the example above:
- The `fetchData` function is marked as `async`, indicating that it will return a promise.
- Within `fetchData`, the `await` keyword is used to pause the execution until the promise is resolved or rejected.
- The code inside the `try` block is executed once the promise is resolved, and the response data is returned.
- If an error occurs during the promise execution, it will be caught in the `catch` block.

### Template Literals
- Template literals allow embedding expressions and variables in strings using backticks (`) and placeholders (${expression}).

```javascript
const name = 'John';
const age = 25;

const greeting = `Hello, my name is ${name} and I'm ${age} years old.`;

console.log(greeting);
// Output: Hello, my name is John and I'm 25 years old.
```


# TypeScript Syntax
Typescript supersets JavaScript by adding types to the language. It is a strongly typed language that compiles to plain 
JavaScript. 

### Type Annotations and Declarations
- Variable type annotation:
  ```typescript
  let age: number = 25;
  let name: string = 'John';
  ```

- Function parameter and return type annotation:
  ```typescript
  function greet(name: string): void {
    console.log('Hello, ' + name);
  }
  ```

### Interfaces and Type Definitions
- Interface declaration and usage:
  ```typescript
  interface Person {
    name: string;
    age: number;
  }
  function greet(person: Person): void {
    console.log('Hello, ' + person.name);
  }
  ```

### Enumerations (Enums)
- Enum declaration and usage:
  ```typescript
  enum Color {
    Red,
    Green,
    Blue,
  }
  let favoriteColor: Color = Color.Blue;
  ```

### Access Modifiers
- Class with public and private members:
  ```typescript
  class Person {
    private name: string;
    public constructor(name: string) {
      this.name = name;
    }
    public greet(): void {
      console.log('Hello, ' + this.name);
    }
  }
  let person = new Person('John');
  person.name; // Error: Property 'name' is private
  person.greet(); // Output: Hello, John
  ```
  
### Type inference
```typescript
let age = 25; // Inferred type: number
let message = 'Hello'; // Inferred type: string
```

### Generics
- Generic type annotation and usage:
```typescript
function identity<T>(arg: T): T {
  return arg;
}
let value = identity<number>(42); // Explicitly specifying the type
let result = identity('Hello'); // Type inference infers the type
```

### Union Types
- Variable or parameter that can accept multiple types:
```typescript
let value: number | string;
value = 42;
value = 'Hello';
```

### Type Assertions
- Explicitly specifying a type for a value:
```typescript
let length = (<string>someValue).length;
let length = (someValue as string).length;
```

### Modules
- Exporting and importing modules:
```typescript
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

// main.ts
import { add } from './math';
let result = add(3, 4);
```
  
### Inheritance
- TypeScript, as a superset of JavaScript, supports all the object-oriented features of JavaScript.
```typescript
// TypeScript Class Inheritance
class Student extends Person {
  studentId: string;

  constructor(name: string, age: number, studentId: string) {
    super(name, age);
    this.studentId = studentId;
  }

  study() {
    console.log(`${this.name} is studying.`);
  }
}

// Creating an Instance
const student = new Student('Alice', 20, 'S123');
student.greet(); // Output: Hello, my name is Alice.
student.study(); // Output: Alice is studying.
```
