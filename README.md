# Go Complete Handbook

## Table of Contents

### Part 1 - Go Fundamentals

1. [What is Go](#1-what-is-go)
2. [Why Go](#2-why-go)
3. [Installation](#3-installation)
4. [Program Structure](#4-program-structure)
5. [Variables](#5-variables)
6. [Constants](#6-constants)
7. [Data Types](#7-data-types)
8. [Type Conversion](#8-type-conversion)
9. [Operators](#9-operators)
10. [Conditions](#10-conditions)
11. [Loops](#11-loops)
12. [Functions](#12-functions)
13. [Multiple Returns](#13-multiple-returns)
14. [Defer](#14-defer)
15. [Panic and Recover](#15-panic-and-recover)
16. [Go routines]

---

# 1. What is Go

Go (also called Golang) is an open-source programming language developed by Google in 2009.

The language was designed to solve common backend development problems such as:

* Slow compilation
* Complex concurrency
* High memory usage
* Difficult deployments

Go combines:

* Simplicity of Python
* Speed of C/C++
* Concurrency support built into the language

---

## Main Characteristics

### a. Statically Typed

The type of a variable is checked during compilation.

```go
var age int = 25
```

Invalid:

```go
age = "Prateek"
```

The compiler immediately throws an error.

Benefits:

* Fewer runtime bugs
* Better performance
* Safer code

---

### b. Compiled Language

Go code is converted directly into machine code.

```text
Go Code
   |
Compiler
   |
Machine Code
   |
Executable
```

Example:

```bash
go build main.go
```

Output:

```bash
main.exe
```

or

```bash
main
```

depending on OS.

---

### c. Garbage Collected

Memory cleanup is automatic.

Developers do not need to manually free memory.

---

### d. Concurrent

Go supports concurrency through Goroutines.

```go
go sendEmail()
```

---

# 2. Why Go

## Reasons to choose Go over Node.js, Java and Python

### 1. Fast Compilation

Go compiles very quickly.

```bash
go build main.go
```

No JVM startup.

No transpilation.

---

### 2. Fast Startup

Go applications start instantly because they are native binaries.

Unlike:

* Java (JVM required)
* Node.js (Runtime required)

---

### 3. Performance

Go is compiled.

Because of this:

* Faster execution
* Lower latency
* Lower memory consumption

---

### 4. Built-in Concurrency

Go has Goroutines.

Creating concurrent tasks is extremely simple.

```go
go sendEmail()
go processPayment()
go generateReport()
```

---

### 5. Simplicity

Go intentionally has a small syntax.

Less code.

Less complexity.

Easier maintenance.

---

### 6. Single Binary Deployment

After building:

```bash
go build main.go
```

You get:

```bash
main.exe
```

Deploy that file directly.

No runtime setup required.

---

# 3. Installation

Verify installation:

```bash
go version
```

Example output:

```bash
go version go1.24 windows/amd64
```

---

## Useful Commands

Run file:

```bash
go run main.go
```

Build executable:

```bash
go build main.go
```

Format code:

```bash
go fmt
```

Run tests:

```bash
go test
```

---

# 4. Program Structure

Example:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello World")
}
```

---

## package

Defines a package.

```go
package main
```

Every Go file belongs to a package.

---

## import

Imports external packages.

```go
import "fmt"
```

---

## main()

Entry point of application.

Execution starts here.

---

## fmt.Println()

Prints output.

```go
fmt.Println("Hello")
```

---

# 5. Variables

Variables store data.

---

## Explicit Declaration

```go
var name string = "Prateek"
```

---

## Type Inference

```go
var age = 25
```

Go automatically detects type.

---

## Short Declaration

Most common.

```go
name := "Prateek"
```

Only valid inside functions.

---

## Multiple Variables

```go
var (
    name = "Prateek"
    age = 25
)
```

---

# 6. Constants

Values that never change.

```go
const PI = 3.14
```

Invalid:

```go
PI = 10
```

Compiler error.

---

# 7. Data Types

## Integer

```go
var age int = 25
```

---

## Float

```go
var salary float64 = 50000.50
```

---

## String

```go
var name string = "Prateek"
```

---

## Boolean

```go
var active bool = true
```

---

## Common Integer Types

| Type  | Size             |
| ----- | ---------------- |
| int8  | 8 bits           |
| int16 | 16 bits          |
| int32 | 32 bits          |
| int64 | 64 bits          |
| int   | System dependent |

---

## Zero Values

| Type    | Default Value |
| ------- | ------------- |
| int     | 0             |
| float64 | 0.0           |
| bool    | false         |
| string  | ""            |
| pointer | nil           |

Example:

```go
var age int

fmt.Println(age)
```

Output:

```text
0
```

---

# 8. Type Conversion

Go does not perform implicit conversions.

Invalid:

```go
var a int = 10
var b float64 = a
```

Compiler error.

---

Correct:

```go
var a int = 10

var b float64 = float64(a)
```

---

String to Integer:

```go
num, err := strconv.Atoi("123")
```

---

Integer to String:

```go
str := strconv.Itoa(123)
```

---

# 9. Operators

## Arithmetic

```go
+
-
*
/
%
```

Example:

```go
a := 10
b := 5

fmt.Println(a + b)
```

---

## Comparison

```go
==
!=
>
<
>=
<=
```

---

## Logical

```go
&&
||
!
```

---

# 10. Conditions

## If

```go
age := 20

if age >= 18 {
    fmt.Println("Adult")
}
```

---

## If Else

```go
if age >= 18 {
    fmt.Println("Adult")
} else {
    fmt.Println("Minor")
}
```

---

## Switch

```go
day := 1

switch day {

case 1:
    fmt.Println("Monday")

case 2:
    fmt.Println("Tuesday")

default:
    fmt.Println("Unknown")
}
```

No break required.

---

# 11. Loops

Go has only one loop keyword:

```go
for
```

---

## Traditional Loop

```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

---

## While Style

```go
i := 0

for i < 5 {
    i++
}
```

---

## Infinite Loop

```go
for {
}
```

---

# 12. Functions

Functions help organize code.

---

## Basic Function

```go
func greet() {
    fmt.Println("Hello")
}
```

---

## Function With Parameters

```go
func greet(name string) {
    fmt.Println(name)
}
```

---

## Returning Values

```go
func add(a int, b int) int {
    return a + b
}
```

Usage:

```go
result := add(10, 20)
```

---

# 13. Multiple Returns

One of Go's most important features.

```go
func getUser() (string, int) {
    return "Prateek", 25
}
```

Usage:

```go
name, age := getUser()
```

---

## Real World Example

```go
user, err := getUser()
```

Common pattern:

```go
if err != nil {
    return
}
```

---

# 14. Defer

Defer delays execution until the surrounding function returns.

Example:

```go
func main() {

    defer fmt.Println("Second")

    fmt.Println("First")
}
```

Output:

```text
First
Second
```

---

## Why Use Defer?

Closing files:

```go
file, _ := os.Open("test.txt")

defer file.Close()
```

Database connections:

```go
defer db.Close()
```

Unlocking mutex:

```go
defer mu.Unlock()
```

---

# 15. Panic and Recover

## Panic

Stops normal execution.

Example:

```go
panic("Something went wrong")
```

Output:

```text
panic: Something went wrong
```

Program crashes.

---

## Recover

Recover catches panic.

Example:

```go
func safe() {

    defer func() {

        if r := recover(); r != nil {
            fmt.Println("Recovered:", r)
        }

    }()

    panic("Crash")
}
```

Output:

```text
Recovered: Crash
```

---

## When To Use Panic

Use panic only for unrecoverable situations:

* Corrupted application state
* Critical startup failures
* Invalid program assumptions

Do not use panic for normal error handling.

Use:

```go
return err
```

instead.

---

# Goroutines

## What is a Goroutine?

A Goroutine is a lightweight thread managed by the Go Runtime.

In simple words:

A Goroutine allows a function to run independently and concurrently with other functions.

Normal Function:

```go
sendEmail()
```

Goroutine:

```go
go sendEmail()
```

The keyword:

```go
go
```

creates a new Goroutine.

---

## Why Were Goroutines Created?

Before Go, concurrency was usually handled using Operating System Threads.

Problem with Threads:

- Heavyweight
- Expensive to create
- Consume more memory
- Difficult to manage at scale

Example:

```text
10000 Threads
```

would consume a huge amount of memory.

Go introduced:

```text
Goroutines
```

which are:

- Lightweight
- Fast to create
- Managed by Go Runtime
- Scalable

---

## Real World Example

Suppose a user places an order.

Tasks:

1. Save Order
2. Send Email
3. Send SMS
4. Update Inventory

Without Goroutines:

```text
Save Order
    ↓
Send Email
    ↓
Send SMS
    ↓
Update Inventory
```

Total Time:

```text
1 + 2 + 1 + 1 = 5 Seconds
```

---

With Goroutines:

```text
Save Order
      |
      +---- Send Email
      |
      +---- Send SMS
      |
      +---- Update Inventory
```

Total Time:

```text
≈ 2 Seconds
```

because tasks run concurrently.

---

## First Goroutine Example

```go
package main

import (
    "fmt"
    "time"
)

func hello() {
    fmt.Println("Hello from Goroutine")
}

func main() {

    go hello()

    time.Sleep(time.Second)
}
```

Output:

```text
Hello from Goroutine
```

---

## Why Is Sleep Used Here?

Without:

```go
time.Sleep()
```

main function may finish before the Goroutine executes.

Example:

```go
func main() {

    go hello()
}
```

Possible Output:

```text
Nothing
```

because:

```text
Main Function Finished
      ↓
Program Exits
      ↓
Goroutine Dies
```

---

## Go Scheduler

Question:

Who manages Goroutines?

Answer:

Go Runtime Scheduler.

Not the Operating System directly.

Architecture:

```text
Application
      |
Goroutines (G)
      |
Scheduler
      |
OS Threads (M)
      |
CPU
```

The scheduler decides:

- Which Goroutine runs
- When it runs
- On which OS thread it runs

---

## Goroutine vs Thread

| Feature | Goroutine | Thread |
|----------|----------|----------|
| Managed By | Go Runtime | Operating System |
| Memory | ~2 KB | ~1 MB |
| Creation Cost | Very Low | High |
| Switching Cost | Low | High |
| Count | Millions | Thousands |

---

## Multiple Goroutines

```go
package main

import (
    "fmt"
    "time"
)

func worker(id int) {
    fmt.Println("Worker", id)
}

func main() {

    for i := 1; i <= 5; i++ {
        go worker(i)
    }

    time.Sleep(time.Second)
}
```

Output:

```text
Worker 3
Worker 1
Worker 5
Worker 2
Worker 4
```

Notice:

Order changes every run.

Reason:

Concurrent execution.

---

## Anonymous Goroutine

You can create Goroutines without a separate function.

```go
go func() {
    fmt.Println("Running")
}()
```

Very common.

---

## Common Use Cases

### Sending Emails

```go
go sendEmail(user)
```

---

### Sending Notifications

```go
go sendNotification(user)
```

---

### Background Logging

```go
go saveLogs()
```

---

### Payment Processing

```go
go processPayment()
```

---

### Generating Reports

```go
go generateReport()
```

---

## Problem: Shared Data

Consider:

```go
counter++
```

from multiple Goroutines.

Two Goroutines may:

```text
Read 5
Read 5

Write 6
Write 6
```

Expected:

```text
7
```

Actual:

```text
6
```

This is called:

```text
Race Condition
```

---

## Solution: Mutex

```go
var mu sync.Mutex

mu.Lock()

counter++

mu.Unlock()
```

Only one Goroutine can access the shared variable at a time.

---

## Communication Between Goroutines

Go follows:

```text
Don't communicate by sharing memory.
Share memory by communicating.
```

Instead of sharing variables directly:

Use Channels.

---

## Channel Example

```go
package main

import "fmt"

func worker(ch chan string) {

    ch <- "Task Completed"
}

func main() {

    ch := make(chan string)

    go worker(ch)

    result := <-ch

    fmt.Println(result)
}
```

Output:

```text
Task Completed
```

---

## WaitGroup

Used to wait for all Goroutines.

```go
var wg sync.WaitGroup

wg.Add(1)

go func() {

    defer wg.Done()

    fmt.Println("Working")

}()

wg.Wait()
```

Without WaitGroup:

```text
Main function may exit early.
```

---

## Why Goroutines Are One of Go's Biggest Features

Because they make concurrent programming:

- Easier
- Safer
- Faster
- More scalable

This is one reason companies use Go for:

- Microservices
- APIs
- Payment Systems
- Distributed Systems
- Cloud Platforms
- High Traffic Applications

Examples:

- Kubernetes
- Docker
- Terraform
- Prometheus


These concepts form the foundation required before learning slices, maps, structs, interfaces, concurrency and backend development.
