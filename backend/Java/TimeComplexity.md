# Time Complexity Cheat Sheet for key Java Collections classes

### Arrays

- Access: `O(1)`
  ```java
  int[] array = {1, 2, 3, 4, 5};
  int element = array[0];
  ```

- Search: `O(n)`
  ```java
  int[] array = {1, 2, 3, 4, 5};
  int index = -1;
  for (int i = 0; i < array.length; i++) {
      if (array[i] == 3) {
          index = i;
          break;
      }
  }
  ```

- Insertion (at the end): `O(1)`
  ```java
  List<Integer> list = new ArrayList<>();
  list.add(1);
  list.add(2);
  list.add(3);
  ```

- Insertion (at the beginning or middle): `O(n)`
  ```java
  List<Integer> list = new ArrayList<>();
  list.add(1);             // O(1)
  list.add(0, 2);          // O(n)
  list.add(1, 3);          // O(n)
  ```

- Deletion (at the end): `O(1)`
  ```java
  List<Integer> list = new ArrayList<>();
  list.add(1);
  list.add(2);
  list.add(3);
  list.remove(list.size() - 1);
  ```

- Deletion (at the beginning or middle): `O(n)`
  ```java
  List<Integer> list = new ArrayList<>();
  list.add(1);
  list.add(2);
  list.add(3);
  list.remove(0);
  ```

### ArrayList

- Search: `O(n)`
  ```java
  List<Integer> arrayList = new ArrayList<>();
  arrayList.add(1);
  arrayList.add(2);
  arrayList.add(3);
  int index = arrayList.indexOf(2);
  ```

- Insertion/Deletion (at the end): `O(1)`
  ```java
  List<Integer> arrayList = new ArrayList<>();
  arrayList.add(1);
  arrayList.add(2);
  arrayList.add(3);
  arrayList.add(4);
  arrayList.remove(arrayList.size() - 1);
  ```

- Insertion/Deletion (at the beginning or middle): `O(n)`
  ```java
  List<Integer> arrayList = new ArrayList<>();
  arrayList.add(1);
  arrayList.add(2);
  arrayList.add(3);
  arrayList.add(4);
  arrayList.remove(0);
  ```

### LinkedList

- Search: `O(n)`
  ```java
  List<Integer> linkedList = new LinkedList<>();
  linkedList.add(1);
  linkedList.add(2);
  linkedList.add(3);
  int index = linkedList.indexOf(2);
  ```

- Insertion/Deletion (at the beginning or middle): `O(1)`
  ```java
  List<Integer> linkedList = new LinkedList<>();
  linkedList.add(1);
  linkedList.add(2);
  linkedList.add(3);
  linkedList.add(0, 4);
  linkedList.remove(1);
  ```

### HashSet

- Insertion/Deletion/Search: `O(1)`, on average
  ```java
  Set<Integer> hashSet = new HashSet<>();
  hashSet.add(1);
  hashSet.add(2);
  hashSet.add(3);
  boolean contains = hashSet.contains(2);
  hash

Set.remove(3);
  ```

### TreeSet

- Insertion/Deletion/Search: `O(log n)`
  ```java
  Set<Integer> treeSet = new TreeSet<>();
  treeSet.add(1);
  treeSet.add(2);
  treeSet.add(3);
  boolean contains = treeSet.contains(2);
  treeSet.remove(3);
  ```

### HashMap

- Insertion/Deletion/Search: `O(1)`, on average
  ```java
  Map<String, Integer> hashMap = new HashMap<>();
  hashMap.put("Apple", 1);
  hashMap.put("Banana", 2);
  hashMap.put("Orange", 3);
  int value = hashMap.get("Banana");
  hashMap.remove("Orange");
  ```

### TreeMap

- Insertion/Deletion/Search: `O(log n)`
  ```java
  Map<String, Integer> treeMap = new TreeMap<>();
  treeMap.put("Apple", 1);
  treeMap.put("Banana", 2);
  treeMap.put("Orange", 3);
  int value = treeMap.get("Banana");
  treeMap.remove("Orange");
  ```

### PriorityQueue

- Insertion/Deletion: `O(log n)`
  ```java
  Queue<Integer> priorityQueue = new PriorityQueue<>();
  priorityQueue.offer(2);
  priorityQueue.offer(1);
  priorityQueue.offer(3);
  int element = priorityQueue.poll();
  ```

### Stack (ArrayDeque)

- Push/Pop: `O(1)`
  ```java
  Deque<Integer> stack = new ArrayDeque<>();
  stack.push(1);
  stack.push(2);
  stack.push(3);
  int element = stack.pop();
  ```

### Iteration

- For-each loop: `O(n)`
  ```java
  List<Integer> list = new ArrayList<>();
  // Add elements to the list...

  for (int element : list) {
      // Process each element
  }
  ```

- Iterator: `O(n)`
  ```java
  List<Integer> list = new ArrayList<>();
  // Add elements to the list...

  Iterator<Integer> iterator = list.iterator();
  while (iterator.hasNext()) {
      int element = iterator.next();
      // Process each element
  }
  ```
  