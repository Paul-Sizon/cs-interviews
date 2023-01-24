# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Interviews](#interviews)
  - [What interviewer might ask you](#what-interviewer-might-ask-you)
    - [Data Structures](#data-structures)
    - [Algorithms](#algorithms)
    - [Coding Skills](#coding-skills)
    - [Low-Level Programming](#low-level-programming)
    - [Architecture/OOD](#architectureood)
    - [Database](#database)
    - [Testing](#testing)
    - [General](#general)
    - [Non-technical](#non-technical)
  - [What you can ask the interviewer](#what-you-can-ask-the-interviewer)
    - [Company](#company)
    - [Project](#project)

## Interviews

A list of fancy questions

## What interviewer might ask you

### Data Structures

- What is a priority queue?
  - A priority queue is a queue where each element has a priority. An element with high priority is dequeued before an element with low priority. If two elements have the same priority, they are served according to their order in the queue.
- What is a heap?
  - A heap is a specialized tree-based data structure that satisfies the heap property: if P is a parent node of C, then the key (the value) of P is either greater than or equal to (in a max heap) or less than or equal to (in a min heap) the key of C. A common implementation of a heap is the binary heap, in which the tree is a complete binary tree.
- What is B-tree?
  - A B-tree is a self-balancing tree data structure that maintains sorted data and allows searches, sequential access, insertions, and deletions in logarithmic time. The B-tree is a generalization of a binary search tree in that a node can have more than two children. Unlike self-balancing binary search trees, the B-tree is optimized for systems that read and write large blocks of data. It is commonly used in databases and file systems.
- What is 2-3-tree?
  - A 2-3 tree is a self-balancing binary search tree that is used in computer science. It is a generalization of the 2-3-4 tree, which is a generalization of the red–black tree. It is a type of B-tree, and is a type of search tree. It is a type of self-balancing binary search tree. It is a type of ordered tree. It is a type of binary tree. It is a type of tree.
- What is RB-tree? What is AVL-tree?
  -  A red–black tree is a kind of self-balancing binary search tree in computer science. Each node of the binary tree has an extra bit, and that bit is often interpreted as the color (red or black) of the node. These color bits are used to ensure the tree remains approximately balanced during insertions and deletions.
- What is Set?
  -  A set is an abstract data type that can store certain values, without any particular order, and no repeated values. It is a computer implementation of the mathematical concept of a finite set. Unlike most other collection types, rather than retrieving a specific element from a set, one typically tests a value for membership in a set.
- What are HashMap and HashSet? Difference between them
  -  A HashMap is an object that maps keys to values. A HashMap cannot contain duplicate keys; each key can map to at most one value. A HashSet is a collection that contains no duplicate elements. More formally, sets contain no pair of elements e1 and e2 such that e1.equals(e2), and at most one null element. As implied by its name, this interface models the mathematical set abstraction.
- Implement a linked list during an interview
  - A linked list is a linear collection of data elements, whose order is not given by their physical placement in memory. Instead, each element points to the next. It is a data structure consisting of a group of nodes which together represent a sequence. Under the simplest form, each node is composed of data and a reference (in other words, a link) to the next node in the sequence; more complex variants add additional links. This structure allows for efficient insertion or removal of elements from any position in the sequence during iteration. More complex variants add additional links, allowing more efficient insertion or removal of nodes at arbitrary positions. A drawback of linked lists is that access time is linear (and difficult to pipeline). Faster access, such as random access, is not feasible. Arrays have better cache locality as compared to linked lists.

```java
class Node {
    int data;
    Node next;
 
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}
 
class LinkedList {
    Node head;
 
    public void append(int data) {
        if (head == null) {
            head = new Node(data);
            return;
        }
        Node current = head;
        while (current.next != null) {
            current = current.next;
        }
        current.next = new Node(data);
    }
 
    public void prepend(int data) {
        Node newHead = new Node(data);
        newHead.next = head;
        head = newHead;
    }
 
    public void deleteWithValue(int data) {
        if (head == null) return;
        if (head.data == data) {
            head = head.next;
            return;
        }
        Node current = head;
        while (current.next != null) {
            if (current.next.data == data) {
                current.next = current.next.next;
                return;
            }
            current = current.next;
        }
    }
}

```

- Implement a graph during an interview
```java
class Edge {
    int source;
    int destination;
    int weight;
    Edge(int source, int destination, int weight) {
        this.source = source;
        this.destination = destination;
        this.weight = weight;
    }
}

class Graph {
    private int vertexCount;
    private List<List<Edge>> adjacencyList;

    Graph(int vertexCount) {
        this.vertexCount = vertexCount;
        adjacencyList = new ArrayList<>(vertexCount);
        for (int i = 0; i < vertexCount; i++) {
            adjacencyList.add(new ArrayList<>());
        }
    }

    public void addEdge(int source, int destination, int weight) {
        Edge edge = new Edge(source, destination, weight);
        adjacencyList.get(source).add(edge);
    }
}
```

### Algorithms

- Given a stream of Arabic numerals. Find the one that occurs maximum times.
  - A: Use a hash table to store the count of each number. Then, iterate through the hash table to find the maximum count.
- Reverse a linked list during an interview
  - A: Use 3 pointers: current, previous, and next. Iterate through the linked list and reverse the pointers.
- Convert a binary tree into a doubly linked list during an interview
  - A: Use a recursive function to traverse the tree. In the recursive function, first call the function for the left subtree. Then change left pointer of the root to point to the previous processed node in DLL. If the previous processed node is not NULL, then change right pointer of it to point to the root. Finally, change right pointer of root to point to the next node in DLL, and change left pointer of next node to point to root.
- Find a loop in a linked list during an interview
  - A: Use 2 pointers: slow and fast. Move slow pointer by 1 and fast pointer by 2. If they meet at some point then there is a loop. If pointers do not meet then linked list doesn’t have a loop.
- Sort an array of integers during an interview
  - A: Use a sorting algorithm like merge sort, quick sort, or heap sort.
- Search an element in a sorted and shifted array during the interview (5, 6, 1, 2, 3)
  - A: Use binary search. Find the pivot point, divide the array in two sub-arrays and call binary search.
- What is an in-place sorting algorithm?
  - A: An in-place algorithm is an algorithm which transforms input using no auxiliary data structure.
- Write an algorithm to rotate an image 90 degrees clockwise
  - A: Use a temporary array to store the rotated values. Then, copy the values back to the original array.
- What is an NP problem? How to identify it?
  - A: An NP problem is a problem that can be verified in polynomial time. To identify an NP problem, you need to be able to verify the solution in polynomial time. Polynomial time is O(n^k) where k is a constant.
- What is O(n) notation? Come up with some examples
  - A: O(n) notation is the notation used to describe the time complexity of an algorithm. Some examples are: searching an element in a linked list, searching an element in a hash table, and searching an element in a binary search tree.
- What is a hash collision? What are the ways to handle it?
  - A: A hash collision is when two different keys map to the same hash value. The ways to handle it are: separate chaining, linear probing, and quadratic probing. Separete chaining is the method of storing a linked list at each hash table index. Linear probing is the method of storing the element at the next available index in the hash table. Quadratic probing is the method of storing the element at the next available index in the hash table, but the index is calculated using a quadratic function.
- What is a good hash function?
  - A: A good hash function is a function that minimizes collisions. It should be easy to compute, and should uniformly distribute the keys.
- Describe a Travelling Salesman Problem
  - A: Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city exactly once and returns to the origin city? The answer is the shortest Hamiltonian cycle. Hamiltonian cycle is a cycle that visits each node exactly once. The way to solve this problem is to use dynamic programming. The time complexity is O(n^2 * 2^n).
- What is dynamic programming?
  - A: Dynamic programming is a method for solving a complex problem by breaking it down into a collection of simpler subproblems, solving each of those subproblems just once, and storing their solutions.
- What is memoization?
  - A: Memoization is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again.
- Find intersection between 3 sorted arrays: [2,6,7,8], [3,6,8,10], [4,5,6,8] => [6,8]
  - A: Use 3 pointers to iterate through the arrays. If the values are equal, then add it to the result. If the value is not equal, then move the pointer that points to the smallest value.
- Generate a [sequence of unique random numbers.](https://stackoverflow.com/questions/196017/unique-non-repeating-random-numbers-in-o1)
  - A: Use a hash table to store the generated numbers. Then, generate a random number and check if it exists in the hash table. If it does not exist, then add it to the hash table. If it exists, then generate another random number.

### Coding Skills

- What is OOP?
A: OOP is a programming paradigm that uses objects and their interactions to design applications and computer programs. OOP principles include encapsulation, abstraction, inheritance, and polymorphism. Encapsulation is the process of combining data and methods into a single unit. Abstraction is the process of hiding the implementation details from the user, only the functionality will be provided to the user. Inheritance is the process of using details from a new class without modifying existing class. Polymorphism is the process of using a common interface for multiple forms (data types).
- What are OOP weaknesses?
  - A: Object-oriented programming (OOP) has several weaknesses, including:

  - Complexity: OOP can make code more complex, particularly when dealing with large and complex class hierarchies. This can make the code harder to understand and maintain.

  - Overuse of Inheritance: Inheritance is one of the core concepts of OOP, but it can be overused and misused. This can lead to a complex class hierarchy and make it difficult to understand the relationships between classes.

  - Performance: OOP can have a performance overhead, particularly when using polymorphism and virtual method calls. This can be an issue in performance-critical applications.

  - Rigidity: OOP can be rigid, making it difficult to change the code as requirements change. This can lead to a lot of refactoring and make the code less adaptable.

  - Lack of support for non-object-oriented languages: OOP is only suitable for certain types of applications and languages, and it may not be the best choice for functional or procedural languages.

  - Dependency Management: OOP can make it difficult to manage dependencies between objects, particularly in large and complex systems. This can lead to tightly coupled code and make it difficult to test and maintain.

It's important to note that OOP weaknesses can be mitigated by using good practices and design patterns and by using other programming paradigms like functional programming or procedural programming along with OOP in the same project.
- what are procedural / functional / OO: can you describe them?
  - A: Procedural programming is a programming paradigm based on the concept of the procedure call. A procedure, also known as a subroutine or a function, is a set of programming instructions that performs a specific task. Functional programming is a programming paradigm based on the concept of mathematical functions. An object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data, in the form of fields, often known as attributes; and code, in the form of procedures, often known as methods. A feature of objects is that an object's procedures can access and often modify the data fields of the object with which they are associated (objects have a notion of "this" or "self"). In OOP, computer programs are designed by making them out of objects that interact with one another. There is significant diversity of OOP languages, but the most popular ones are class-based, meaning that objects are instances of classes, which also determine their types.
- Why OOP was favored by the industry for so many years?
  - A: Object-oriented programming (OOP) has been favored by the industry for many years for several reasons:

  - Abstraction: OOP allows developers to abstract away complex details and work with objects that represent real-world entities. This makes the code more readable and understandable, and it also makes it easier to change the implementation without affecting the rest of the code.

  - Reusability: OOP allows developers to create reusable code in the form of classes and objects. This allows developers to use existing code rather than writing new code from scratch, which can save time and effort.

  - Modularity: OOP allows developers to break down a complex system into smaller, more manageable pieces. This makes it easier to understand, test, and maintain the code.

  - Encapsulation: OOP allows developers to encapsulate data and behavior within objects, which makes it easier to protect the internal state of an object and control access to it.

  - Inheritance: OOP allows developers to create a class hierarchy, where a subclass inherits the properties and methods of its parent class. This allows developers to reuse code and create new classes with minimal effort.

  - Polymorphism: OOP allows developers to write code that works with different types of objects in a generic way, using polymorphism. This allows developers to write code that is more flexible and adaptable to changing requirements.

  - OOP provides better scalability: OOP is more suitable for large and complex systems, where the number of objects can be very large and the relationships between them can be complex.

  These features of OOP, along with the popularity of object-oriented languages like Java and C++, have made OOP the go-to programming paradigm for many developers and organizations for a long time. 
- What is the value object? Why should you use them?
  - A: A value object is an object that represents a value, rather than an entity. Value objects are immutable, which means that they cannot be changed once they are created. This makes them ideal for representing values that should not be changed, such as currency amounts, dates, and email addresses. Value objects are also easier to compare, which makes them ideal for use in collections and as keys in hash tables. Value objects are also easier to test, which makes them ideal for use in unit tests. Value objects are also easier to serialize, which makes them ideal for use in distributed systems.
- What is IoC?
  - A: Inversion of control (IoC) is a design principle in which custom-written portions of a computer program receive the flow of control from a generic framework. IoC is one of the principles of the SOLID object-oriented design principles. IoC is also known as dependency injection (DI). IoC is used to increase modularity of the program and make the program easier to test. IoC is also used to increase the flexibility of the program and make it easier to change the behavior of the program without changing the code. IoC is also used to increase the reusability of the program and make it easier to reuse the code in different projects.
- What is Dependency Inversion?
  - A: Dependency inversion is a design principle in which high-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions. Dependency inversion is one of the principles of the SOLID object-oriented design principles. Dependency inversion is also known as the dependency inversion principle (DIP). Dependency inversion is used to increase the flexibility of the program and make it easier to change the behavior of the program without changing the code. Dependency inversion is also used to increase the reusability of the program and make it easier to reuse the code in different projects.
- What is Dependency Injection?
  - A: Dependency injection is a design pattern in which an object receives other objects that it depends on. These other objects are called dependencies. Dependency injection is one of the principles of the SOLID object-oriented design principles. Dependency injection is also known as the dependency injection principle (DIP). Dependency injection is used to increase the flexibility of the program and make it easier to change the behavior of the program without changing the code. Dependency injection is also used to increase the reusability of the program and make it easier to reuse the code in different projects.
- Why are interfaces important?
  - A: Interfaces are important because they allow developers to create loosely coupled code, which makes the code easier to test and maintain. Interfaces are also important because they allow developers to create code that is more flexible and adaptable to changing requirements. Interfaces are also important because they allow developers to create code that is more reusable and easier to reuse in different projects.
- What is the difference between an exception and a validation error? When an exception should be thrown and when you should catch an exception?
  - A: The main difference between an exception and a validation error is that an exception is typically used to indicate an unexpected or exceptional situation, such as a runtime error, while a validation error is used to indicate that the input data is invalid or does not meet certain requirements.

    - An exception should be thrown when a program encounters an unexpected situation that it cannot handle, such as a null pointer exception, an index out of bounds exception, or a file not found exception. These are typically situations that are beyond the control of the program, and they indicate that something has gone wrong that the program cannot recover from.

    - On the other hand, validation errors are typically used when the program receives input data that is not in the expected format or does not meet certain requirements. For example, if a program expects to receive an integer but instead receives a string, it can throw a validation error.

    - An exception should be caught when the program can recover from the exception and continue executing normally. For example, if a program tries to open a file and the file is not found, the program can catch the exception and display an error message to the user, instead of crashing. It's also important to log the error and notify the responsible team or person. It's also important to note that exceptions should not be used to control the program flow, for example, using exceptions for validation. Exceptions are intended to be used for exceptional situations, such as unexpected runtime errors. Instead, it's better to use validation checks to ensure that the input data is valid before proceeding with the program's logic.
- Concurrency
- Why do we need concurrency?
  - A: Concurrency is important because it allows developers to write code that can perform multiple tasks at the same time, which can improve the performance of the program. Concurrency is also important because it allows developers to write code that is more responsive and can handle more requests at the same time. Concurrency is also important because it allows developers to write code that is more scalable and can handle more requests at the same time.
- What are Multithreading concepts?
  - A: Multithreading is a programming concept that allows developers to write code that can perform multiple tasks at the same time. Multithreading is also known as concurrency. Multithreading is important because it allows developers to write code that can perform multiple tasks at the same time, which can improve the performance of the program. Multithreading is also important because it allows developers to write code that is more responsive and can handle more requests at the same time. Multithreading is also important because it allows developers to write code that is more scalable and can handle more requests at the same time.
- How is Concurrency different from Multithreading?
  - A: Concurrency and multithreading are related concepts but are not the same thing.

    - Concurrency refers to the ability of a program or system to handle multiple tasks or operations simultaneously. This can be achieved by dividing a task into smaller subtasks and executing them in parallel, or by interleaving the execution of multiple tasks so that they appear to be executing simultaneously. Concurrency can be implemented at different levels, such as at the process or thread level.

    - Multithreading, on the other hand, is a specific technique for achieving concurrency at the process level. A multithreaded program is a program that has multiple threads of execution, which are lightweight units of computation that can run in parallel. Each thread has its own program counter, stack, and local variables, and they share the same code and data. Multithreading allows a program to perform multiple tasks simultaneously by creating and executing multiple threads.

    - In summary, concurrency is a general concept that refers to the ability to handle multiple tasks or operations simultaneously, while multithreading is a specific technique for achieving concurrency by using multiple threads.

    - Additionally, it's worth mentioning that Multiprocessing is another way of achieving concurrency, it consists of using multiple processors or cores to run different processes at the same time, unlike multithreading, where multiple threads run on the same core.
- What is `Thread`? What is `Task`? What is `Process`?
  - A: 
    - A thread is a lightweight unit of execution that can run in parallel with other threads. A thread has its own program counter, stack, and local variables, and it shares the same code and data with other threads. A thread is typically used to implement concurrency at the thread level.

    - A task is a lightweight unit of execution that can run in parallel with other tasks. A task is typically used to implement concurrency at the task level.

    - A process is a program in execution. A process is typically used to implement concurrency at the process level.
- What async/await does under the hood?
  - A: 
    - The async and await keywords in C# and other languages are used to write asynchronous code in a way that looks similar to synchronous code. They are built on top of an underlying mechanism called the Task-based Asynchronous Pattern (TAP).

    - When a method is marked with the async keyword, it tells the compiler that the method may contain one or more await expressions. When the await keyword is used inside an async method, it tells the compiler to generate code that will return control to the caller while the asynchronous operation is in progress.

    - Under the hood, when a method marked as async is called, the compiler generates a state machine that tracks the progress of the asynchronous operation. The state machine wraps the method body in a try-finally block, and it also wraps any code that is executed after an await expression in a continuation. The continuation is a function that will be called when the asynchronous operation completes, allowing the method to continue executing from where it left off.

    - The await keyword also works with Task and Task<T> objects, which are used to represent the asynchronous operation. When an await expression is encountered, the code execution is suspended until the task completes. Once the task is completed, the continuation is scheduled to run, and the method resumes executing from where it left off.

    - In summary, the async and await keywords provide a way to write asynchronous code that looks similar to synchronous code, and they are built on top of the Task-based Asynchronous Pattern (TAP) to make it more readable and maintainable. The async keyword tells the compiler to generate a state machine that tracks the progress of the asynchronous operation, and the await keyword tells the compiler to return control to the caller while the asynchronous operation is in progress, and schedule a continuation to execute when the operation completes.
- What is the Difference between optimistic and pessimistic concurrency models?
  - A: 
    - Optimistic concurrency is a concurrency control mechanism that assumes that there will be no conflicts between concurrent transactions, and that the transactions will succeed unless there is a conflict. The optimistic concurrency model is based on the assumption that the data will not be modified by other transactions while the current transaction is executing. If the data is modified by another transaction, the current transaction will fail and will have to be retried.

    - Pessimistic concurrency is a concurrency control mechanism that assumes that there will be conflicts between concurrent transactions, and that the transactions will fail unless there is a conflict. The pessimistic concurrency model is based on the assumption that the data will be modified by other transactions while the current transaction is executing. If the data is not modified by another transaction, the current transaction will succeed.

    - In summary, optimistic concurrency assumes that there will be no conflicts between concurrent transactions, and that the transactions will succeed unless there is a conflict. Pessimistic concurrency assumes that there will be conflicts between concurrent transactions, and that the transactions will fail unless there is a conflict.
- What is the Difference between being async and concurrent?
  - A: The terms "asynchronous" and "concurrent" are related, but they have slightly different meanings.

    - Asynchronous refers to the ability of a program or system to perform multiple tasks or operations without blocking the execution of other tasks or operations. In other words, an asynchronous operation does not wait for the previous operation to complete before starting a new one, instead it starts the new operation and continue with other operations.

    - Concurrent, on the other hand, refers to the ability of a program or system to handle multiple tasks or operations simultaneously. This can be achieved by dividing a task into smaller subtasks and executing them in parallel, or by interleaving the execution of multiple tasks so that they appear to be executing simultaneously.

    - So, both asynchronous and concurrent refer to the ability of a system to handle multiple tasks at the same time, but they have a slightly different focus:

    - Asynchronous is focused on non-blocking execution, allowing multiple tasks to progress without waiting for previous tasks to complete.
    - Concurrent is focused on executing multiple tasks simultaneously, whether they are blocking or non-blocking.
    It's also worth mentioning that Asynchronous programming helps to handle the concurrency by allowing the system to handle multiple tasks without blocking the execution, it's a way to achieve concurrency but it's not the only way.

In summary, both asynchronous and concurrent refer to the ability of a program or system to handle multiple tasks or operations simultaneously, but asynchronous is focused on non-blocking execution, while concurrent is focused on executing multiple tasks simultaneously.
- Sync primitives - semaphore, mutex, monitor?
- A: 
  - A semaphore is a synchronization primitive that can be used to control access to a shared resource. A semaphore is a counter that is used to keep track of the number of threads that can access a shared resource. When a thread wants to access the shared resource, it calls the WaitOne() method of the semaphore. If the semaphore's counter is greater than zero, the counter is decremented and the thread can access the shared resource. If the semaphore's counter is zero, the thread is blocked until another thread calls the Release() method of the semaphore, which increments the counter and unblocks a waiting thread.

  - A mutex is a synchronization primitive that can be used to control access to a shared resource. A mutex is a boolean variable that is used to keep track of whether a thread has exclusive access to a shared resource. When a thread wants to access the shared resource, it calls the WaitOne() method of the mutex. If the mutex is false, the mutex is set to true and the thread can access the shared resource. If the mutex is true, the thread is blocked until another thread calls the Release() method of the mutex, which sets the mutex to false and unblocks a waiting thread.

  - A monitor is a synchronization primitive that can be used to control access to a shared resource. A monitor is a lock that is used to keep track of whether a thread has exclusive access to a shared resource. When a thread wants to access the shared resource, it calls the Enter() method of the monitor. If the monitor is not locked, the monitor is locked and the thread can access the shared resource. If the monitor is locked, the thread is blocked until another thread calls the Exit() method of the monitor, which unlocks the monitor and unblocks a waiting thread.
- What is lock()? What is lock() underneath?
- A: 
  - The lock keyword is used to acquire a lock on a given object. When a thread acquires a lock on an object, it prevents other threads from acquiring a lock on the same object
- Describe a race condition with a real-world example
  - A: A race condition is a situation in which the outcome of a program depends on the relative timing or ordering of multiple threads or processes. This can occur when multiple threads or processes try to access or modify the same shared resource simultaneously, leading to unexpected or inconsistent results.

A real-world example of a race condition is an ATM (Automatic Teller Machine) that allows multiple customers to withdraw money simultaneously. Suppose two customers, Alice and Bob, both try to withdraw $100 from their account at the same time. The ATM has a balance of $1000, and it checks the account balance before allowing a withdrawal.

In the absence of proper synchronization, the following scenario may occur:

Alice checks the account balance, which is $1000
Bob checks the account balance, which is also $1000
Alice requests a withdrawal of $100, and the ATM deducts $100 from the balance
Bob requests a withdrawal of $100, and the ATM also deducts $100 from the balance
Now, the account balance is $800, but both Alice and Bob received $100 each
This scenario is a race condition, as the outcome of the program (the withdrawal) depends on the relative timing of the actions of Alice and Bob. To avoid this race condition, the ATM must use synchronization mechanisms, such as locks or semaphores, to ensure that only one customer can access the account balance at a time, and that the withdrawal is made atomically.

In this example, the shared resource is the account balance, and the problem is caused by multiple threads trying to access and modify it simultaneously without proper synchronization. The solution is to use synchronization mechanisms to ensure that only one thread can access the shared resource at a time. 
- What are non-blocking/non-waiting algorithms?
  - A: 
    - A non-blocking algorithm is an algorithm that can be executed by multiple threads simultaneously without requiring synchronization. This is achieved by ensuring that the algorithm does not depend on the relative timing or ordering of the threads, and that the algorithm's state can be updated atomically.

    - A non-waiting algorithm is an algorithm that does not block the execution of the current thread. This is achieved by ensuring that the algorithm does not depend on the relative timing or ordering of the threads, and that the algorithm's state can be updated atomically.
- Which types of threads do we have?
  - A: 
    - There are two types of threads: user threads and kernel threads.

    - User threads are threads that are managed by the application. They are created and scheduled by the application, and they are executed by the application's own thread scheduler. User threads are also known as application threads, or application-level threads.

    - Kernel threads are threads that are managed by the operating system. They are created and scheduled by the operating system, and they are executed by the operating system's thread scheduler. Kernel threads are also known as system threads, or system-level threads.
- Where the threads come from?
  - A: 
    - Threads are created by the operating system. When a process is created, the operating system creates a thread for that process, which is called the main thread. The main thread is the first thread that is executed by the process. When the main thread terminates, the process terminates. The main thread is also known as the primary thread.

    - Additional threads can be created by the main thread, or by other threads. These additional threads are called worker threads. Worker threads are created by calling the CreateThread() function, which takes a pointer to a function as a parameter. The function that is passed to CreateThread() is the entry point of the thread, and it is executed when the thread is created. The function that is passed to CreateThread() can be a function that is defined in the current process, or it can be a function that is defined in a DLL that is loaded by the current process.
- Explain the concepts of coupling and cohesion and how they relate to maintainability. As a follow-up, please explain afferent coupling and efferent coupling, and how those concepts fit above.
  - A: Coupling and cohesion are two important concepts that are related to the maintainability of software systems.

    - Coupling refers to the degree to which different components or modules of a system depend on each other. High coupling means that a change in one component or module will likely affect other components or modules, making the system less flexible and harder to maintain. Low coupling, on the other hand, means that changes in one component or module have minimal impact on other components or modules, making the system more flexible and easier to maintain.

    - Cohesion, on the other hand, refers to the degree to which the responsibilities of a single component or module are related to each other. High cohesion means that a component or module has a single, well-defined responsibility and that its internal parts are strongly related to each other. Low cohesion, on the other hand, means that a component or module has multiple, poorly-defined responsibilities and that its internal parts are loosely related to each other. High cohesion is desirable because it makes it easier to understand and maintain the component or module.

    - Afferent coupling refers to the degree to which a component or module depends on other components or modules. It's also known as "incoming coupling" and it's measured by the number of external components or modules that depend on it. High afferent coupling means that a component or module is dependent on many other components or modules, making it less flexible and harder to maintain.

    - Efferent coupling refers to the degree to which a component or module depends on other components or modules. It's also known as "outgoing coupling" and it's measured by the number of external components or modules that a component or module depends on. High efferent coupling means that a component or module depends on many other components or
    -  high efferent coupling means that a component or module depends on many other components or modules, making it less flexible and harder to maintain. This is because changes in the external components or modules will likely affect the component or module with high efferent coupling. Low efferent coupling, on the other hand, means that a component or module has minimal dependencies on other components or modules, making it more flexible and easier to maintain.

    - Efferent coupling is an important concept to consider when designing a system, because it directly affects the maintainability and scalability of the system. A system with low efferent coupling is more flexible and easier to maintain because changes in one component or module will have minimal impact on other components or modules. This makes it easier to add new features or make changes to the system without affecting the existing functionality.

    - On the other hand, a system with high efferent coupling is more rigid and harder to maintain because changes in one component or module will likely affect many other components or modules. This makes it harder to add new features or make changes to the system without affecting the existing functionality.

    - In summary, both coupling and cohesion are important concepts that are related to the maintainability of software systems. Low coupling and high cohesion are desirable because they make it easier to understand and maintain the system. While Afferent and Efferent coupling are two different ways of measuring the dependencies of a component or module, Afferent coupling is the degree to which a component or module is dependent on, and Efferent coupling is the degree to which a component or module depends on.
- What are LINQ, lazy execution, EF limitations.
  - A: 
    - LINQ is a set of extension methods that are defined in the System.Linq namespace. These extension methods allow you to query objects that implement the IEnumerable<T> interface, such as arrays, lists, and dictionaries. LINQ queries are executed lazily, which means that the query is not executed until the query results are actually accessed. This allows you to write queries that are more efficient and easier to understand.

    - Lazy execution is a feature of LINQ queries that allows you to write queries that are more efficient. A LINQ query is executed lazily, which means that the query is not executed until the query results are actually accessed. This allows you to write queries that are more efficient.

    - Entity Framework is an object-relational mapper (ORM) that is used to access and manipulate data in a database. It allows you to define classes that map to tables in a database, and it automatically generates the necessary SQL code to access and manipulate the data in the database. However, Entity Framework has some limitations, such as the inability to execute raw SQL queries, and the inability to use stored procedures.
- What is an ORM? Why is it useful and why not?
  - A: An ORM is an object-relational mapper that is used to access and manipulate data in a database. It allows you to define classes that map to tables in a database, and it automatically generates the necessary SQL code to access and manipulate the data in the database. However, ORMs have some limitations, such as the inability to execute raw SQL queries, and the inability to use stored procedures.
- What is refactoring?
  - A: Refactoring is the process of improving the design of existing code without changing its external behavior. It's a way to make the code easier to understand and maintain, and it can be applied to any programming language. Refactoring is an important part of the software development process because it allows you to improve the design of your code without changing its external behavior. This makes it easier to add new features or make changes to the code without affecting the existing functionality.
- Please refactor some given piece of code and comment your actions.
- What is covariance? What is contravariance?
  - A: Covariance and contravariance are two important concepts that are related to the design of generic types in C#. Covariance refers to the ability of a generic type to be used as a base type. Contravariance refers to the ability of a generic type to be used as a derived type. Both covariance and contravariance are important concepts to consider when designing generic types in C#, because they allow you to create generic types that are more flexible and easier to use. 
- Implement a singleton
  - A: A singleton is a design pattern that is used to ensure that only one instance of a class is created. It's useful when you want to ensure that only one instance of a class is created,
- What is unsafe code? When should you use it?
  - A: Unsafe code is code that is not type-safe. It allows you to access memory directly, which can be useful when you need to access memory that is not managed by the .NET runtime. However, unsafe code is not type-safe, which means that it can cause runtime errors if you access memory that is not managed by the .NET runtime. This makes it harder to debug and maintain the code, so you should only use unsafe code when you need to access memory that is not managed by the .NET runtime.

### Low-Level Programming

- What is Garbage Collector? What problem does it solve?
- How does Garbage Collector work? What are the steps?
- GC Generations
- What is non-deterministic finalization?
- Explain weak references
- Describe the process of memory allocation
- IDisposable and Finalizer
- How is using() construct useful? How can it result in resource leaks?
- Stack/heap. What is a stack overflow physically?
- Large object heap
- SIMD
- What are WebSockets? Where can you use them?
- What is the difference between polling and long polling in sockets?

### Architecture/OOD

- Design an Instagram
- SOLID
- What are GoF design patterns? Why should you care?
- What's can go wrong with Active Record pattern?
- What do you think about `null`? How to avoid it?
- What is [composition over inheritance](https://stackoverflow.com/questions/49002/prefer-composition-over-inheritance)?
- What should you return concrete implementation or abstraction? E.g. `List` or `IList`? When you would pick one approach over another? Think about performance as well.
- What is the difference between IoC and service locator?
- Name a few anti-patterns
- What is MVC? Explain it using ASP.NET example. Define responsibilities.
- What is MVVM? Define responsibilities for each component.
- Layered architecture
- Explain pub/sub to me
- [What is CQRS](https://www.youtube.com/watch?v=y819dMehw6M)?
- What is CQS and how it relates to CQRS?
- What is a command in CQRS terms?
- What is the difference between command and event?
- What command handler is and what it does?
- Which type of projects is the best to introduce CQRS?
- Difference between stateful and stateless service.
- What is the blue DDD book?
- What is DDD?
- What is the domain model?
- What is the anemic domain model? Is it useful?
- What is the bounded context? How to identify a bounded context? Describe the example of two bounded contexts in terms of the same domain.
- What is the difference between a bounded context and a subdomain?
- Aggregate, AggregateRoot, Entity, ValueObject - what are those? Describe the difference between them
- What is an ubiquitous language? Why is that important?
- Immutability - what is that? Should commands or events be immutable?
- What is saga? Come up with a real-world example to explain sagas.
- What is event sourcing?
- What is snapshotting in terms of event sourcing?
- What is a projection?
- Describe the role of aggregate in CQRS/ES/DDD environment. Go deep on two-phase commit on writing an event to the event store and publishing event to a bus. Are transactions good candidates for that kind of case? If not, how to avoid transactions in that case?
- Can you send a command to another bounded context in CQRS/ES/DDD environment? Can you publish an event to another bounded context in CQRS/ES/DDD environment?
- What is AOP? Which parts of the system would you move to aspects?
- [Messaging patterns](https://www.enterpriseintegrationpatterns.com/patterns/messaging/)
  - What is [CorrelationId](https://www.enterpriseintegrationpatterns.com/patterns/messaging/CorrelationIdentifier.html)?
  - When a retry policy is suitable in general? When should you retry your command/API call?
- How to design against vendor lock-in?


### Database

- What is CAP theorem?
- Why CAP theorem is obsolete? Is it?
- What is RAFT? How does it solve the problem?
- What is ACID? Is it still a thing?
- What is eventual consistency?
- Is the use of GUID as IDs a good practice?
- What is sharding?
- What is partitioning?
- How to design a good partitioning?
- What is an index? Clustered/Non-clustered?
- How much clustered indexes might be? What is clustered index physically? What kind of data structures could be used for indexes? Why index lookups are fast? Is clustered index faster than non-clustered? Why?
- Explain the difference between index seek and index scan
- What is column-store index? When would you use it?
- How can databases be replicated?
- What is cold data and hot data?
- How would you migrate an application from one database to another, for example from MySQL to PostgreSQL? If you had to manage that project, which issues would you expect to face?
- What is lazy loading? What are the drawbacks of this approach?
- How to find the most expensive queries in an application? How to monitor your database health and load?
- What are database normalization rules? Is it acceptable to have denormalized database? If so, in which cases?
- How to do blue-green deployments including database?
- How NoSQL databases scale? How SQL databases scale?
- When to use NoSQL and when to use SQL?

### Testing

- What is a unit test? Academic definition vs real world definition
- What is the difference between unit/integration/automated test? Discuss examples
- What is TDD?
- What is BDD?
- What is performance testing?
- What is load testing?
- What is smoke testing?
- What is regression testing? Is that correct that benchmarking is a part of the regression testing process?
- What is [chaos testing](https://boyter.org/2016/07/chaos-testing-engineering/)?
- Why in TDD are tests written before code?
- How to test a distributed system? Which types of test will you write? Which instruments would you use?
- What is a [test pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)?

### General

- How testing frameworks such as xUnit & NUnit know what methods to run?
- What is the most interesting thing you've made?
- What is Docker?
- How Dockerfile relates to Docker image layers?
- What is Kubernetes?
- What happens when [you run `kubectl run --image=nginx --replicas=3`](https://github.com/jamiehannaford/what-happens-when-k8s)?
- What is [blue-green deployment](https://martinfowler.com/bliki/BlueGreenDeployment.html)?
- What is [CanaryRelease](https://martinfowler.com/bliki/CanaryRelease.html)?
- What is the concept of [infrastructure as code](https://www.thoughtworks.com/de/insights/blog/infrastructure-code-reason-smile)?
- What is the difference between authorization and authentication?
- What is .NET standard?
- What is merge and rebase, the difference between them?
- [Git hooks](https://www.atlassian.com/git/tutorials/git-hooks)
- Git reset, revert, checkout
- What is the difference between Mongo and Redis?
- What is the difference between queue and topic in messaging systems?
- What is REST? RESTful?
- What is idempotency? in terms of HTTP and/or messaging
- What is RPC? What are the general pitfalls of RPC?
- What is gRPC? When it could be useful?
- What is the difference between RPC and gRPC?
- What is SOAP?
- What is HATEOAS?
- What is HAL?
- What is eventual consistency? BASE?
- What is reactive programming?
- What is tail recursion?
- What is cyclomatic complexity?
- Public API versioning, how to do that right.
- What is [feature toggling/flagging](https://martinfowler.com/articles/feature-toggles.html)? [[1]](https://www.youtube.com/watch?v=7qTOdbUAqno) [[2]](https://www.pluralsight.com/courses/dotnet-featuretoggle-implementing) [[3]](http://swreflections.blogspot.com/2014/08/feature-toggles-are-one-of-worst-kinds.html)
- [What happens when you type 'google.com' into the browser address bar and press Enter](https://dev.to/antonfrattaroli/what-happens-when-you-type-googlecom-into-a-browser-and-press-enter-39g8)?
- What is public IP, private IP? NAT? IPv4? IPv6? [[0]](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) [[1]](https://www.digitalocean.com/community/tutorials/an-introduction-to-networking-terminology-interfaces-and-protocols)
- Explain event hub over service bus, consumer groups and other concepts related.
- What is partitioned consumer pattern? [Competing Consumer](https://docs.microsoft.com/en-us/azure/architecture/patterns/competing-consumers)?
- What is tracing, spans, [opentracing](https://github.com/opentracing/specification/blob/master/specification.md)?
- What is [ELK stack](https://www.elastic.co/elk-stack)?
- What is [structured logging](https://nblumhardt.com/2016/06/structured-logging-concepts-in-net-series-1/)? Does it have any advantages over plaintext logging?
- [Why does array index start with '0' in most languages?](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html)
- What are dynamic- and static-typed languages? Which one to pick for developing enterprise software? Explain your thoughts.
- What is overengineering? How can it affect enterprise software in the short run and in the long run?
- What is the difference between pattern matching and just a switch clause?
- Pretend you have a time machine and pretend that you have the opportunity to go to a particular point in time during Java's (or C#, Python, Go or whatever) history, and talk with some of the JDK architects. What would you try to convince them of? Removing checked exceptions? Adding unsigned primitives? Adding multiple-inheritance?
- How to explain legacy code to non-technical person e.g. Project Manager or Product Owner? Why it's important to care about legacy code? How would you deal with legacy code?
- When to use cache? When it can be not useful or even dangerous?
- I want to refactor a legacy system. You want to rewrite it from scratch. Argument. Then, switch our roles.
- What is GOTO statement? [What's wrong with it](https://homepages.cwi.nl/~storm/teaching/reader/Dijkstra68.pdf)? Do we still have GOTO statements or something similar to them in modern programming languages?
- What is monorepo and what is multirepo? When it's better to chose one over another? [[0]](https://medium.com/@adamhjk/monorepo-please-do-3657e08a4b70) [[1]](https://medium.com/@mattklein123/monorepos-please-dont-e9a279be011b)
- Tell me about your favorite language/framework. Is it really that good? Does it have any weaknesses?

### Non-technical

- What motivates you?
- What do you think of technical conferences/meetups? Are they important and why?
- [Why are you looking for a job?](Answers/Non-technical/Why%20are%20you%20looking%20for%20a%20job.md)
- Tell about your last project
- What are you learning right now? Teach me this.
- Last book you read
- How much time do you need to start working full time for us?
- What do you do when you get stuck on some problem for too long?
- Tell me your 3 best/last failures
- Describe what Human Resources means to you.
- What is broken around you?
- When was the last time when you did not agree with some blog post/book/video? What was that and why you did not agree?
- When was the last time when you shared the knowledge with somebody else? Did you like it? Why did you do that?
- Explain to me your learning process, validation of the information and using it in practice.

## What you can ask the interviewer

Don't ask them if you just want to make an impression because you will. And this is not going to be a very positive impression - asking by template without any enthusiasm. Instead, you should at least seem interested.
What I also really like to do is to start doing 96 so after recruiter asked you "Where do you see yourself in 5 years" it's totally reasonable to ask where the company sees itself in 5 years.

### Company

- Why have you left your last company for this?
- How do you train/ramp up engineers who are new to the team?
- Do you have your [onboarding process documented](https://twitter.com/housecor/status/1142153344179429378)?
- Who is your ideal candidate and how can I make myself more like them?
- Describe what Human Resources means to you.
- How do you find the best talents? Are you focused on acquiring the best ones?
- Do you have a shower to use at your place? Does anyone use it?
- Do you have a library at your place? Name a few books there.
- Do you have any teambuildings and what they look like?
- Do you know anything about your employees' hobbies? What they are interested in?
- How much vacation does the average employee take?
- Do you enforce a minimum number of days of taken vacation per year? (Secret: a lot of “unlimited vacation day” policies actually lead to employees taking less time off because they feel guilty.)
- Do you have any internal tech talks to improve the technical expertise of your employees? If so, who is in charge of that?
- Do you use any time logging system?
- Describe the paid vacations policy.
- Describe the process of salary review/performance review. What are the factors included in forming my salary?
- Do you have any competence matrix?
- Will I be able to work remotely? If so, then how much time/month?
- How flexible the schedule is?
- What do you think of remote-async workflow?
- How often will I have to over-time and how it's paid?
- Which devices will I be provided to work with - laptops/PCs, monitors, smartphones for testings, etc?
- Do you provide any insurance? If so, describe it briefly.
- Do you offer parking space for your employees? For car/bike.
- Do you have any probationary period for new employees?
- Do you have something like 13th salary / any other bonuses?
- What are the weaknesses of the organization?
- What do you consider as the strongest advantage of your company over others?
- What are the educational opportunities?
- How often are 1:1s conducted?
- What opportunities are available to switch roles? How does this work?
- If you could change one thing about the company, whether it's a process, technology used, or anything else, what would it be?
- What is the toughest problem company've faced so far, aside from not enough people, and how did you or plan to solve it?

### Project

- What project I will start with? Describe the problem it solves. Describe the technical stack chosen, why it is like that and which tasks I will be asked to solve there.
- Do you have any code review process?
- What is the structure of the environment I will be working in? Will I have managers attached to me and, if so, then how much? Who will provide me with the work to do?
- Will I have the ability to communicate with the client side? How much time will I communicate in English everyday?
- Which instruments does your company use for development? Are there any limitations?
- What level of responsibilities will I have?
- Does the project offer any business trips/on sites?
