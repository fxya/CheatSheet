# Java Collections Cheatsheet

### List

- ArrayList:
  ```java
  List<String> arrayList = new ArrayList<>();
  arrayList.add("Apple");
  arrayList.add("Banana");
  arrayList.add("Orange");
  ```

- LinkedList:
  ```java
  List<String> linkedList = new LinkedList<>();
  linkedList.add("Apple");
  linkedList.add("Banana");
  linkedList.add("Orange");
  ```

### Set

- HashSet:
  ```java
  Set<String> hashSet = new HashSet<>();
  hashSet.add("Apple");
  hashSet.add("Banana");
  hashSet.add("Orange");
  ```

- TreeSet:
  ```java
  Set<String> treeSet = new TreeSet<>();
  treeSet.add("Apple");
  treeSet.add("Banana");
  treeSet.add("Orange");
  ```

### Map

- HashMap:
  ```java
  Map<String, Integer> hashMap = new HashMap<>();
  hashMap.put("Apple", 1);
  hashMap.put("Banana", 2);
  hashMap.put("Orange", 3);
  ```

- TreeMap:
  ```java
  Map<String, Integer> treeMap = new TreeMap<>();
  treeMap.put("Apple", 1);
  treeMap.put("Banana", 2);
  treeMap.put("Orange", 3);
  ```

### Queue

- LinkedList:
  ```java
  Queue<String> queue = new LinkedList<>();
  queue.offer("Apple");
  queue.offer("Banana");
  queue.offer("Orange");
  ```

- PriorityQueue:
  ```java
  Queue<String> priorityQueue = new PriorityQueue<>();
  priorityQueue.offer("Apple");
  priorityQueue.offer("Banana");
  priorityQueue.offer("Orange");
  ```

### Stack

- ArrayDeque:
  ```java
  Deque<String> stack = new ArrayDeque<>();
  stack.push("Apple");
  stack.push("Banana");
  stack.push("Orange");
  ```

### Iteration

- For-each loop:
  ```java
  List<String> list = new ArrayList<>();
  // Add elements to the list...

  for (String element : list) {
      // Process each element
  }
  ```

- Iterator:
  ```java
  List<String> list = new ArrayList<>();
  // Add elements to the list...

  Iterator<String> iterator = list.iterator();
  while (iterator.hasNext()) {
      String element = iterator.next();
      // Process each element
  }
  ```

### Sorting

- Sorting a list in ascending order:
  ```java
  List<Integer> numbers = new ArrayList<>();
  // Add numbers to the list...

  Collections.sort(numbers);
  ```

- Sorting a list with a custom comparator:
  ```java
  List<String> fruits = new ArrayList<>();
  // Add fruits to the list...

  Collections.sort(fruits, (a, b) -> a.compareTo(b));
  ```

### Searching

- Searching for an element in a list:
  ```java
  List<String> list = new ArrayList<>();
  // Add elements to the list...

  int index = list.indexOf("Apple");
  ```

- Searching for an element in a sorted list:
  ```java
  List<String> list = new ArrayList<>();
  // Add elements to the sorted list...

  int index = Collections.binarySearch(list, "Apple");
  ```
