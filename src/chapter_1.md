# 📘 Week 1: Introduction to Software Security Analysis

> Based on Prof. Yulei Sui’s [Lecture Slides](https://github.com/SVF-tools/Software-Security-Analysis/blob/slides/1.intro.pdf)

---

## 🌍 Why Is Software Security Important?

In today's world, **software runs everything** — from your smartwatch to airplanes, from financial systems to pacemakers. As we increasingly depend on software, its **correctness**, **security**, and **reliability** become essential to avoid catastrophic consequences.

### 📉 What Happens When Software Fails?

* A software bug in a **radiation therapy machine** led to lethal overdoses (Therac-25 incidents).
* A buffer overflow bug in **WannaCry ransomware** exploited Windows machines globally, causing billions in damage.
* The **Dark Web** actively trades in zero-day vulnerabilities (unknown, unpatched bugs) to hack into devices remotely.

### 📈 The Scale of the Problem

Modern software is **massive**:

* **Linux kernel** has over **30 million lines of code (LoC)**.
* A single change might affect hundreds of interconnected components.
* With such size, **manual review is impossible** and software becomes a fertile ground for **bugs and exploits**.

### 🧠 Real-World Statistics

> “About 70% of security bugs in Microsoft’s software are memory safety issues.”
> — [Microsoft Security Blog, 2019](https://www.microsoft.com/en-us/security/blog/2019/07/16/why-do-we-need-safe-systems-programming-languages/)

Common issues include:

* **Buffer overflows**
* **Use-after-free errors**
* **Null pointer dereferences**
* **Data races** (in multi-threaded code)
* **Memory leaks**

These bugs are dangerous because they often allow attackers to:

* Crash the system
* Steal sensitive data
* Gain control of the machine

---

## 🔍 What is Software Analysis and Verification?

### Definitions:

| Concept                   | What It Does                                             |
| ------------------------- | -------------------------------------------------------- |
| **Software Analysis**     | Identifies whether *bugs exist* in *some* execution path |
| **Software Verification** | Proves that *no bugs exist* in *any* execution path      |

### Analogy:

* **Analysis**: Like checking if a thief can sneak into a house through *any one* door or window.
* **Verification**: Like proving that **no** door or window can be broken into, *under all circumstances*.

Together, these techniques aim to ensure:

* Programs behave **as expected**
* No unexpected or insecure behavior occurs
* The implementation **meets** the design and user needs

---

## 🛑 Why Manual Code Review Is Not Enough

### The Scale of Modern Codebases

Consider a small benchmark program `twolf`:

* \~20,500 LoC
* 194 functions
* 20,773 pointer operations

Or the GNU Compiler Collection (GCC):

* \~230,000 LoC
* 2,256 functions
* 134,380 pointer references

### Challenges in Manual Review:

* **Too many execution paths** to check exhaustively
* **Dynamic memory and recursion** create unpredictable behaviors
* **Concurrency (multi-threading)** introduces race conditions

These make it practically **impossible** for humans to reason about all paths manually — especially under time constraints.

---

## 🤖 Automated Code Analysis: A Necessity

### Two Broad Approaches:

| Approach             | Description                                         | Example Techniques                          |
| -------------------- | --------------------------------------------------- | ------------------------------------------- |
| **Dynamic Analysis** | Runs the code and observes behavior at runtime      | Unit testing, fuzz testing, model testing   |
| **Static Analysis**  | Inspects the code without running it (compile-time) | Symbolic execution, abstract interpretation |

---

### 🔁 Dynamic Analysis (During Execution)

* **Fuzzing**: Feeding random or malformed inputs to the program.
* **Unit Testing**: Testing individual components with known inputs and expected outputs.
* **Stress Testing**: Pushing the system to its limits (e.g., memory exhaustion).
* **Model-Based Testing**: Tests derived from system models or specifications.

🧪 Example:

```c
int buffer[10];
buffer[10] = 5; // out-of-bounds write – may not crash in testing
```

A test case may or may not catch this depending on input — this is a **limitation of dynamic analysis**.

---

### 🧮 Static Analysis (Without Execution)

#### Key Ideas:

* Analyzes *all* possible code paths
* Works on **Control Flow Graphs (CFGs)** and **Data Flow Graphs**
* Helps catch bugs even if no test input triggers them

#### Techniques:

* **Control-Flow Analysis**: Who can call whom, and in what order?
* **Data-Flow Analysis**: How values move and are transformed.
* **Symbolic Execution**: Uses symbolic variables instead of actual values to explore program paths.
* **Abstract Interpretation**: Uses mathematical approximations to model all behaviors soundly.

📌 Real-World Tools:

* **CodeQL**: Used at GitHub to detect security issues across massive open-source projects.
* **Infer** by Meta: Focuses on null pointers and memory leaks in mobile codebases.
* **Coverity**: Widely used in industry for static bug detection.

---

## 🏗️ Design vs Code Verification

| Verification Type | Focus                          | Examples                                         |
| ----------------- | ------------------------------ | ------------------------------------------------ |
| **Design Level**  | Validates system architecture  | Z (business logic), Promela (process comm.), VDM |
| **Code Level**    | Validates implementation logic | Hoare logic, assertions, memory safety checks    |

### Example: Hoare Triple

```c
// {x > 0}
y = x + 1;
// {y > 1}
```

This means: *If x > 0 before execution, then y > 1 will be true after.*

---

## ✅ Benefits of Software Analysis and Verification

| Benefit                       | Why It Matters                                              |
| ----------------------------- | ----------------------------------------------------------- |
| **Higher reliability**        | Fewer bugs and crashes                                      |
| **Increased security**        | Less chance of being exploited                              |
| **Lower costs**               | Catching bugs early avoids expensive fixes later            |
| **Better compliance**         | Meets standards like EU Cyber Resilience Act                |
| **Developer productivity**    | Less time spent on debugging and patching                   |
| **Understanding legacy code** | Easier to analyze unfamiliar or poorly documented codebases |

---

## 🧪 Course Project: Building a Verification Tool

### Project Goal:

Create your own **static analysis engine** in C++ to:

* Analyze C programs at compile-time
* Detect bugs **without executing** the code

### Pipeline Overview:

```
Source Code 
   │
   ├──> Static Analysis Engine
   │     ├── Symbolic Execution
   │     ├── Information Flow Analysis
   │     └── Abstract Interpretation
   │
   └──> Generates Report: Tainted Inputs, Assertion Violations, Buffer Overflows
```

---

## 🧠 Recap of Key Concepts

| Concept               | Purpose                                                  |
| --------------------- | -------------------------------------------------------- |
| Software Security     | Prevent unauthorized access, crashes, or data theft      |
| Software Analysis     | Identify if bugs *can* occur                             |
| Software Verification | Prove that bugs *cannot* occur                           |
| Dynamic Analysis      | Test-based detection                                     |
| Static Analysis       | Code inspection with path exploration and approximations |
| Course Objective      | Build a static tool to find security bugs in C programs  |

---

## 🔗 References

1. Yulei Sui, *Software Security Analysis*, [Lecture 1](https://github.com/SVF-tools/Software-Security-Analysis/blob/slides/1.intro.pdf)
2. Microsoft Security Blog (2019), ["Why do we need safe systems programming languages?"](https://www.microsoft.com/en-us/security/blog/2019/07/16/why-do-we-need-safe-systems-programming-languages/)
3. EU Cyber Resilience Act (2023), [Link](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)
4. GitHub CodeQL: [https://codeql.github.com/](https://codeql.github.com/)
5. Patrick Cousot and Radhia Cousot. Abstract Interpretation: A Unified Lattice Model for Static Analysis of Programs. *POPL 1977*.

---
