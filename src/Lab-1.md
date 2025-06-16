# 💻 Lab: Programming Practices and Graph Algorithms (Week 1)

*Based on [this resource](https://github.com/SVF-tools/Software-Security-Analysis/blob/slides/1.lab-cpp.pdf)*

---

## 🧪 What to Expect from Each Lab

Each lab is designed to:

* **Demonstrate** how to use development tools (e.g., IDEs like VS Code or CLion).
* Show **coding examples** based on the lecture topics.
* Help you **practice and reinforce** your programming knowledge.
* Prepare you to complete **lab exercises and assignments** confidently.

---

## 🚀 A Quick Overview of C++

### What is C++?

* **C++** is a **general-purpose programming language**, originally created as an extension of C.
* It adds powerful features like **object-oriented programming (OOP)**, making it suitable for complex software systems.

### Why Learn C++?

* Widely used to build:

  * **System software** (OS, compilers)
  * **Web browsers**, **game engines**
  * **Cloud and distributed systems**
* Offers:

  * High **performance**
  * Low-level **memory access** with pointers
  * Both **procedural** and **object-oriented** programming styles
* One of the **most popular and fast-growing** languages in the world

**Note:** This lab gives you just the basics you need to start writing C++ programs and building algorithms — not everything about the language.

---

## 👨‍💻 Write Your First C++ Program

```cpp
#include <iostream>  // Include library for input and output
using namespace std; // Use standard namespace (std)

int main() {         // Entry point of every C++ program
    cout << "Hello, World\n";  // Output to the screen
    return 0;        // End the program
}
```

### Key Concepts:

* `#include <iostream>` includes the standard input/output library.
* `using namespace std;` lets you avoid writing `std::cout`, `std::endl`, etc.
* `cout` is used to print messages to the screen.

---

## 🔢 C++ Primitive Data Types and Variables

### Syntax:

```cpp
type variable = value;
```

### Common Primitive Types:

| Type     | Description                   | Example                    |
| -------- | ----------------------------- | -------------------------- |
| `int`    | Integer (whole numbers)       | `int myNum = 5;`           |
| `float`  | Floating-point (decimal)      | `float myFloat = 5.99;`    |
| `double` | Double-precision float        | `double myDouble = 9.98;`  |
| `char`   | Single character              | `char myChar = 'D';`       |
| `bool`   | Boolean (true or false)       | `bool isTrue = true;`      |
| `string` | Text (from `<string>` header) | `string myText = "Hello";` |

> 💡 **Difference between `float` and `double`:**

* Both are used for decimal numbers.
* `double` is **more precise** (can store more digits after the decimal point).
* Use `double` when precision is important.

---

## 🧱 C++ Classes and Objects

In C++, a **class** is a blueprint for creating **objects**. It lets you group data and behavior together.

### Object-Oriented Features:

* **Abstraction:** Hide complex details, show only what’s necessary.
* **Encapsulation:** Keep data safe from outside interference by using `private` members and public methods.

### Example: A Simple `Graph` Class

```cpp
#include<iostream>
using namespace std;

class Graph {
private:
    int numOfNodes;
    int numOfEdges;

public:
    int getNumberOfNodes() {
        return numOfNodes;
    }

    void setNumOfNodes(int n) {
        numOfNodes = n;
    }
};

int main() {
    Graph graphObj;           // Create an object of Graph
    graphObj.setNumOfNodes(10); // Set the number of nodes
    cout << graphObj.getNumberOfNodes() << "\n"; // Output: 10
}
```

---

## 🏗️ Constructor

A **constructor** is a special method that is **automatically called when an object is created**. It’s often used to initialize values.

### Constructor Example:

```cpp
#include<iostream>
using namespace std;

class Graph {
private:
    int numOfNodes;
    int numOfEdges;

public:
    // Constructor
    Graph(int n, int e) {
        numOfNodes = n;
        numOfEdges = e;
    }

    int getNumberOfNodes() {
        return numOfNodes;
    }

    void setNumOfNodes(int n) {
        numOfNodes = n;
    }
};

int main() {
    Graph myGraph(5, 7); // Calls the constructor with 5 nodes, 7 edges
    cout << myGraph.getNumberOfNodes() << "\n"; // Output: 5
}
```

---

## 📦 Containers / Collections in C++

### What is a Container?

A **container** is a structure that **stores multiple values** (like an array or list).

---

### 1. Plain C Array

```cpp
int myNum[3] = {10, 20, 30};
```

* Fixed size
* Stores data **sequentially**
* Basic, fast, but limited flexibility

---

### 2. C++ Standard Template Library (STL) Containers

The STL offers **ready-to-use data structures**.

#### ✅ Sequence Containers:

* Store data in a **linear order**
* Common types:

  * `vector`: dynamic array (resizable)
  * `deque`: double-ended queue
  * `list`: doubly linked list
  * `stack`: LIFO (last-in, first-out)

#### ✅ Associative Containers:

* Store data in a **sorted manner** and allow fast lookup
* Common types:

  * `set`: collection of **unique** sorted keys
  * `map`: collection of **key-value** pairs

---

### 🧪 Example: Using a `vector`

```cpp
#include<vector>
#include<iostream>
using namespace std;

int main() {
    vector<int> nodeIDs;  // Create a dynamic array (vector) of integers

    // Add elements to the vector
    nodeIDs.push_back(1);
    nodeIDs.push_back(2);
    nodeIDs.push_back(3);

    // Iterate and print elements
    for (auto i : nodeIDs) {
        cout << i << endl;  // Output: 1 2 3
    }
}
```

### 🧪 Example: Using a `set`

```cpp
#include<set>
#include<iostream>
using namespace std;

int main() {
    set<int> nodeIDs;  // Create a dynamic array (vector) of integers

    // Add elements to the vector
    nodeIDs.insert(1);
    nodeIDs.insert(2);
    nodeIDs.insert(3);

    // Iterate and print elements
    for (auto i : nodeIDs) {
        cout << i << endl;  // Output: 1 2 3
    }
}
```
## 🔄 Containers/Collections Used in a Class

### What is a Container?

A **container** is a data structure that holds multiple values. Think of it like a box that stores items of the same type. C++ provides many built-in containers like `vector`, `set`, `map`, etc.

### Example: Using `set` in a Class

```cpp
#include <set>      // For using the set container
#include <iostream> // For input-output operations
using namespace std;

class Graph {
private:
    int numOfNodes;
    int numOfEdges;
    set<int> nodeIDs; // A set to store unique node IDs

public:
    Graph(int n, int e) {
        numOfNodes = n;
        numOfEdges = e;
    }

    void addNode(int id) {
        nodeIDs.insert(id); // Insert node ID into the set
    }
};

int main() {
    Graph graphObj(5, 10);
    graphObj.addNode(1);
    graphObj.addNode(2);
    return 0;
}
```

---

## 🧠 Pointers for Primitive Types

### What is a Pointer?

A **pointer** is a variable that stores the memory address of another variable.

```cpp
int nodeID = 5;
int *ptr = &nodeID; // `ptr` now stores the address of nodeID

cout << nodeID << endl;   // Prints: 5
cout << &nodeID << endl;  // Prints: memory address (e.g., 0x6dfed4)
cout << ptr << endl;      // Same as above
cout << *ptr << endl;     // Dereference the pointer → prints: 5
```

---

## 🔁 References for Primitive Types

### What is a Reference?

A **reference** is another name (alias) for an existing variable. It is declared using `&`.

```cpp
int nodeID = 5;
int &ref = nodeID;

ref = 20; // nodeID becomes 20
cout << "nodeID = " << nodeID << endl;

nodeID = 30; // ref becomes 30
cout << "ref = " << ref << endl;
```

---

## 🔐 `const` Type Qualifier in C++

### Why use `const`?

* Prevent accidental changes to a variable.
* Allow compiler optimizations.

```cpp
const int nodeID = 5; // You can't modify nodeID

const int *ptr = &nodeID; // Pointer to a const int

int anotherNodeID = 6;
int *const cptr = &anotherNodeID; // Constant pointer to int
```

---

## 🔁 Parameter Passing in Functions

### 1. Pass by Value

```cpp
void swap(int n1, int n2) {
    int tmp = n1;
    n1 = n2;
    n2 = tmp;
}

int main() {
    int a = 2, b = 3;
    swap(a, b);
    cout << a << " " << b << endl; // Output: 2 3 (no change!)
}
```

> Pass-by-value **copies** the variables — changes inside the function don’t affect the original.

---

### 2. Pass by Reference

```cpp
void swap(int &n1, int &n2) {
    int temp = n1;
    n1 = n2;
    n2 = temp;
}

int main() {
    int a = 2, b = 3;
    swap(a, b);
    cout << a << " " << b << endl; // Output: 3 2
}
```

> Pass-by-reference shares the **original** variable. Changes affect the original.

---

### 3. Pass by Pointer

```cpp
void swap(int *n1, int *n2) {
    int temp = *n1;
    *n1 = *n2;
    *n2 = temp;
}

int main() {
    int a = 2, b = 3;
    swap(&a, &b);
    cout << a << " " << b << endl; // Output: 3 2
}
```

> Pass-by-pointer uses the variable’s **address** to change it.

---

## 🔁 Pass by Reference vs Pass by Pointer: Key Differences

| Feature            | Reference (`&`)        | Pointer (`*`)              |
| ------------------ | ---------------------- | -------------------------- |
| Syntax             | Cleaner, easier to use | Slightly more complex      |
| Can be reassigned? | No                     | Yes                        |
| Can be null?       | No                     | Yes (dangerous if misused) |
| Usage              | Safer                  | More flexible              |

---

## 🧠 Efficient Function Arguments

If you pass a large object (like a class), copying it is slow. Instead, use **reference or pointer** to avoid copying.

```cpp
class Graph {
public:
    int numOfNodes;
    int numOfEdges;
};

// Pointer version
void print(const Graph *g) {
    cout << g->numOfNodes << " " << g->numOfEdges;
}

// Reference version
void print(const Graph &g) {
    cout << g.numOfNodes << " " << g.numOfEdges;
}
```

---

## 📦 Using Pointers in Classes

Here's how you define and use pointers in classes to represent relationships between objects.

```cpp
#include <iostream>
#include <set>
using namespace std;

class Edge; // Forward declaration

class Node {
private:
    int nodeID;
    set<Edge*> outEdges; // Set of outgoing edges (pointers)

public:
    Node(int i) { nodeID = i; }

    int getNodeID() { return nodeID; }

    set<Edge*>& getOutEdges() {
        return outEdges;
    }
};

class Edge {
private:
    Node *src;
    Node *dst;

public:
    Edge(Node *s, Node *d) {
        src = s;
        dst = d;
    }

    Node* getSrc() { return src; }
    Node* getDst() { return dst; }
};

class Graph {
private:
    set<Node*> nodes;

public:
    Graph() {}

    set<Node*>& getNodes() {
        return nodes;
    }
};

int main() {
    Node* srcNode = new Node(1);
    Node* dstNode = new Node(2);

    cout << srcNode->getNodeID() << endl;
    cout << dstNode->getNodeID() << endl;

    Edge* edge = new Edge(srcNode, dstNode);
    cout << edge->getSrc()->getNodeID() << endl;
    cout << edge->getDst()->getNodeID() << endl;

    srcNode->getOutEdges().insert(edge);

    Graph* graph = new Graph();
    graph->getNodes().insert(srcNode);
    graph->getNodes().insert(dstNode);
}
```

---

### 🧼 Notes:

* `->` is used to access members of a pointer to an object (e.g., `ptr->x` is equivalent to `(*ptr).x`).
* Use `new` to create dynamic memory (allocated on the heap).
* `set<Type*>` is a collection of unique pointers.



Here's a **clear and beginner-friendly explanation** of **C++ Inheritance, Function Overriding, and Virtual Functions** using your example, with step-by-step breakdowns and comments.

---

# 🧱 C++ Inheritance, Function Overriding, and Polymorphism

## 🔹 What is **Inheritance**?

**Inheritance** allows one class (child/derived class) to **reuse** the attributes and methods of another class (parent/base class).

---

## 🚧 Example: C++ Inheritance

```c++
#include<iostream>
using namespace std;

class GraphBuilder {
public:
    GraphBuilder() {} // Constructor

    // Method to build a graph
    void build() {
        cout << "Parent's way to build\n";
        // Example code to build a graph:
        // 1. Create two nodes
        // 2. Create an edge between them
        // 3. Add them to a graph
        // (Imagine Node, Edge, and Graph are already defined)
    }
};

// SubGraphBuilder inherits from GraphBuilder
class SubGraphBuilder : public GraphBuilder {
public:
    SubGraphBuilder() {} // Constructor
};

int main() {
    // Create an object of SubGraphBuilder
    SubGraphBuilder* builder = new SubGraphBuilder();

    // It can use the build() method from GraphBuilder
    builder->build();  // Output: "Parent's way to build"

    delete builder; // Always delete heap-allocated memory
    return 0;
}
```

### ✅ What’s happening?

* `SubGraphBuilder` **inherits** from `GraphBuilder`.
* It can use the method `build()` even though it's not defined inside `SubGraphBuilder`.
* This is **code reuse**, the core benefit of inheritance.

---

## 🔄 Function Overriding in C++

### 🔹 What is Function Overriding?

**Function overriding** means that a **child class** can provide its **own version** of a function that already exists in the **parent class**.

> Both methods must have the **same name and signature**.

---

### 📘 Example: Function Overriding **without** `virtual`

```c++
#include<iostream>
using namespace std;

class GraphBuilder {
public:
    void build() {
        cout << "Parent's way to build\n";
    }
};

class SubGraphBuilder : public GraphBuilder {
public:
    void build() {
        cout << "Child's way to build\n";
    }
};

int main() {
    SubGraphBuilder* builder = new SubGraphBuilder();
    builder->build();  // Output: Child's way to build

    GraphBuilder* builder2 = new SubGraphBuilder();
    builder2->build(); // Output: Parent's way to build ❌ (unexpected!)

    delete builder;
    delete builder2;
    return 0;
}
```

### ⚠️ Why does `builder2->build()` call the **parent’s method**, not the child’s?

Because **`build()` is not marked as `virtual`** in the parent class.
Without `virtual`, **C++ resolves the function call based on the pointer type**, not the object type.

---

## 🧠 Virtual Functions & Polymorphism

### 🔹 What is a **Virtual Function**?

A **virtual function** allows **runtime polymorphism** in C++.

When a method in the base class is declared `virtual`, and it's overridden in the derived class, the **child's version is called**, even if you're using a base class pointer.

---

### 📘 Example: Virtual Function

```c++
#include<iostream>
using namespace std;

class GraphBuilder {
public:
    GraphBuilder() {}

    // Make build() virtual so derived classes can override it
    virtual void build() {
        cout << "Parent's way to build\n";
    }
};

class SubGraphBuilder : public GraphBuilder {
public:
    SubGraphBuilder() {}

    // Override the build() method
    void build() override {
        cout << "Child's way to build\n";
    }
};

int main() {
    SubGraphBuilder* builder = new SubGraphBuilder();
    builder->build();  // Output: Child's way to build ✅

    GraphBuilder* builder2 = new SubGraphBuilder();
    builder2->build(); // Output: Child's way to build ✅ (polymorphism)

    GraphBuilder* builder3 = new GraphBuilder();
    builder3->build(); // Output: Parent's way to build ✅

    delete builder;
    delete builder2;
    delete builder3;

    return 0;
}
```

---

## 🤔 Key Differences Summary

| Concept             | What It Means                                  | Output Behavior                                                             |
| ------------------- | ---------------------------------------------- | --------------------------------------------------------------------------- |
| Inheritance         | Child class can use parent’s methods/variables | Code reuse                                                                  |
| Function Overriding | Child redefines a method from parent           | Without `virtual`, **base class version** is called when using base pointer |
| Virtual Function    | Enables **runtime polymorphism**               | Child class version is called even via base pointer                         |

---

## 🧠 Real World Analogy

* **Inheritance**: Like a **child** inheriting traits from a **parent**.
* **Overriding**: The child can behave **differently** even if the method has the same name.
* **Virtual function**: C++ asks the actual **object type** (not pointer type) at **runtime** to decide which method to call.


