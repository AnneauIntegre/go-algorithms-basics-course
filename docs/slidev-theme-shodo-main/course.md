---
theme: ./
titleTemplate: "%s - Shodo"
author: Manon Carbonnel
layout: cover
---

<div class="subtitle">Shodo</div>

# Foundations of algorithms with Go

---

```yaml
layout: intro
```

**I'm Alex(andre)**

- Backend developer
- Worked one year for OVH
- Loves to write articles about IT

---

```yaml
layout: center
```

<strong>How about you?</strong>

---

```yaml
layout: three-cols-header
```

### What's the plan?

::left::

#### Learn Go basics 

`int`, `for`, `slice`, `func`…

::center::

#### Revisit theoretical concepts in Go

Control flows and algorithms.

::right::

#### Pratice a lot

1/3 theory, 2/3 exercises.

---

```yaml
layout: section
index: 1
```

## What is Go?

---

```yaml
layout: three-cols-header
```

### A little bit of history

::left::
<v-click>
2007

Project began at Google.
</v-click>


::center::
<v-click>
2009

Publicly announced.
</v-click>

::right::
<v-click>
2012

Version 1.0 released.
</v-click>


---

```yaml
layout: full
```

# 📝 Exercise : verify Go Installation

- Open a terminal and run `go version` command. If Go is properly installed, the result should look like this.

```console
$ go version
go version go1.23.1 linux/amd64
$
```

🚨 Go is not installed? Download Go from the official website and follow installation instructions : https://go.dev/doc/install


---

```yaml
layout: full
```

# Go commands

- `go run` will be our primary command for running Go programs.
- When in doubt, use `go help`

```console {all|1|13|all}
$ go help
Go is a tool for managing Go source code.

Usage:

        go <command> [arguments]

The commands are:

        build       compile packages and dependencies
        doc         show documentation for package or symbol
        fmt         gofmt (reformat) package sources
        run         compile and run Go program
        test        test packages
        version     print Go version

Use "go help <command>" for more information about a command.
```


---

```yaml
layout: full
```

# 📝 Exercise : run your first program

- Navigate to the `ex-01` folder and run the `hello-world.go` program with the following using `go run`.

```console
$ cd exercises
$ cd ex-01
$ go run hello-world.go
hello, world
$
```

---

```yaml
layout: section
index: 2
```

## First steps

---

```yaml
layout: full
```

# Basic types

|             |                                  |
| ----------- | -------------------------------  |
| `bool`      | `true` / `false`                 |
| `int`       | …, `-1`, `-2`, `0`, `1`, `2`, …  |
| `float64`   | `19.99`, `7.0`                   |
| `string`    | `"hello, world"`                 |

---

```yaml
layout: full
```

# Basic operations

### Boolean operations

AND (`&&`), OR (`||`), NOT (`!`)

### Arithmetic operations

Addition (`+`), Subtraction (`-`), Multiplication (`*`), Division (`/`), Modulus (`%`)

###  Comparison operations

Equal (`==`), Less than (`<`), Greater than (`>`), …

### String operations

Concatenation (`+`)

---

```yaml
layout: full
```

# 📝 Exercise : play with basic types

- Navigate to the `ex-02` folder to edit the `basics.go` file.
- Add the missing code in place of the TODO.

```console
$ cd exercises
$ cd ex-02
$ go run basics.go
11 plus 4 IS 15
22.0 divided 7.0 IS 3.142857142857143
true AND false IS false
NOT false IS true
"go" plus "lang" IS golang
-------------------------------------------
256 times 128 IS TODO
28.0 divided by 7.0 IS TODO
28 divided by 17 IS TODO
28 mod 17 IS TODO
"basics" plus "." plus "go" IS TODO
...
```

---

```yaml
layout: full
```

# Variables

- Multiple ways to declare a variable.

```go {all|6|7|8|all}
package main

import "fmt"

func main() {
	var a int = -6
	var b int
	c := 13
	fmt.Println(a, b, c) // -6 0 13
}
```

---

```yaml
layout: full
```

# Variables

- Variables without an initial value are automatically set to their zero value.
- Variables in Go can be reassigned with new values after their initial declaration

```go {all|6-9|11-14|all}
package main

import "fmt"

func main() {
	var d int       // 0
	var e float64   // 0.0
	var f string    // ""
	var g bool      // false

	i := 2          // i == 2
	i = 3           // i == 3
	i = i + 1       // i == 4
	i = i * 2       // i == 8
}

```

---

```yaml
layout: three-cols-header
```

### `:=`, `=` and `==` are different 

::left::

#### `:=`

Declare a new variable
```go
x := 42
```

::center::

#### `=`

Assign a new value to a variable.
```go
x = x * 2
```

::right::

#### `==`

Compare two values for equality.
```go
11+4 == 15
```

---

```yaml
layout: full
```

# 📝 Exercise : create and use variables

- Navigate to the `ex-03` folder and edit the `variables.go` file.
- Assign values to `quotient` and `remainder` using appropriate basic operations.
- Replace `TODO` with logic to check if `a` and `b` are even.

```console
$ cd exercises
$ cd ex-03
$ go run variables.go
a = 28 b = 3
Quotient: 0
Remainder: 0
Is 28 even ? TODO
Is 3 even ? TODO
$
```
---

```yaml
layout: section
index: 3
```

## Control structures

---

```yaml
layout: full
```

# `if` statements

- If the condition is `true`, the code inside the `if` block is executed.
- `else if` is used to test multiple conditions in sequence.
- `else` keyword provides an alternative block of code if the conditions are false.

```go {all|1-2|3-4|5-7|9-11|all}
if (28 % 2) == 0 {
	fmt.Println("28 is an even number")
} else if (28 > 3) && (28-3 >= 0) {
	fmt.Println("28 is really greater than 3")
} else {
	fmt.Println("Well, I guess none of the above is true")
}

if result := someFunction("INFO", 1726667324, "192.168.1.1"); result > 5 {
	fmt.Println("The computed result was superior to 5: ", result)
}
```

---

```yaml
layout: full
```

# `switch` statements

- `switch` is used to select one of many blocks of code to be executed.
- Multiple expressions can be evaluated in the same `case` by separating them with commas.

```go {all|1-3|4-9|10-11|all}
food := "apple"

switch food {
case "apple":
	fmt.Println(food, "is a fruit")
case "carrot", "spinach":
	fmt.Println(food, "is a vegetable")
case "chicken", "beef", "pork":
	fmt.Println(food, "is a meat")
default:
	fmt.Println("Unknown food type")
}
```

---

```yaml
layout: full
```

# `for` statements

- Unlike other languages, Go has only one looping construct, the `for` loop.

```go {all|1-3|5-9|all}
for i := 0; i < 10; i++ {
	fmt.Println(i)
}

j := 1
for j < 1000000 {
	fmt.Println(j)
	j *= 2
}
```

---

```yaml
layout: full
```

# `for` statements

- `break` terminates the loop immediately.
- `continue` skips the remaining code in the loop and moves to the next iteration.

```go {all|5-7|9-11|all}
i := 0
for {
	i++

	if i > 9 {
		break
	}

	if i%2 == 0 {
		continue
	}

	fmt.Println(i)
}
// 1
// 3
// 5
// 7
// 9
```

---

```yaml
layout: full
```

# 📝 Exercise : work with control structures

- Navigate to the `ex-04` folder and edit the `statements.go` file.
- Replace `TODO` with logic that sets `isPrime` based on whether the number is prime.

```console
$ cd exercises
$ cd ex-04
$ go run statements.go
1948764641 is not a prime number
$
```

---

```yaml
layout: section
index: 4
```

## Slices

---

```yaml
layout: full
```

# Arrays or slices?
- You may see "arrays" and "slices" in Go documentation.
- Arrays and slices are both sequences of elements of a single type.
- Arrays have a fixed length, not flexible.
- Slices can grow or shrink, easier to work with.
- In this course, when we refer to arrays or lists, we’ll mostly mean slices.

---

```yaml
layout: full
```

# Creating slices

```go {all|1-2|4-5|7-8|all}
// Declare an empty slice of integers
var sli []int

// Declare a slice of integers with initial values
sli := []int{1, 2, 3} 

// Create a slice of integers with 5 elements
sli := make([]int, 5)
```
---

```yaml
layout: full
```

# Accessing and modifying slices

```go {all|3-4|6-8|10-11|all}
sli := []string{"perl", "go", "java", "python", "c"}

// Access an element
lang := sli[0]

// Edit an element
sli[1] = "golang"
sli[4] += "++" 

// Swap elements
sli[2], sli[3] = sli[3], sli[2]
```
---

```yaml
layout: full
```
# Common slices operations

```go {all|3-4|6-8|9-12|all}
sli := []float64{ 3.14159, 2.71828, 1.61803 }

// len() returns the number of elements in the slice
fmt.Println(len(sli))

// append() add elements to a slice
sli = append(sli, 1.41421)

// for statement to iterate over a slice
for i := 0; i < len(sli); i++ {
	fmt.Println("This is the element", i, "in my slice:", sli[i])
}
```

---

```yaml
layout: full
```

# 📝 Exercise : compare two slices

- Navigate to the `ex-05` folder and edit the `slices.go` file.
- Replace `TODO` with logic that sets `areSlicesEqual` based on whether the slices are equal.

```console
$ cd exercises
$ cd ex-05
$ go run slices.go
false
false
false
$
```

---

```yaml
layout: section
index: 5
```

## Functions
---

```yaml
layout: full
```
# Functions
- A function can take zero or more arguments.
- A function can return zero or more values. 

```go {all|1-3|5-7|9-11|13-15|all}
func zeroArgumentsZeroValues() {
	fmt.Println("Hello from empty function")
}

func oneArgumentZeroValues(message string) {
	fmt.Println("This is what the function got:", message)
}

func oneArgumentOneValue(name string) string {
	return "Hello " + name
}

func manyArgumentsManyValues(message string, timestamp int, ip string) (string, int) {
	return ip + " said " + message, timestamp / 1000
}
```

---

```yaml
layout: full
```
#  Declaring and calling a function

```go
// Declare a function with parameters and a return type.
func add(a int, b int) int {
	return a + b
}

// Call the function by passing arguments.
result := add(1, 5)
fmt.Println("Result:", result)
```

---

```yaml
layout: full
```
#  Return zero or more values

```go
// Functions can perform tasks without returning anything.
func sayHi() {
	fmt.Println("Hello, World!")
}
sayHi()

// Functions can return a single value.
func square(n int) int {
	return n * n
}
result := square(5)
fmt.Println("Square of 5:", result)

// Go allows functions to return multiple values.
func divide(a, b int) (int, int) {
	return a / b, a % b
}
quotient, remainder := divide(9, 4)
fmt.Println("Quotient:", quotient, "Remainder:", remainder)
```

---

```yaml
layout: full
```

# 📝 Exercise : declare and call functions

- Navigate to the `ex-06` folder and edit the `functions.go` file.
- Replace `TODO` with the proper function implementation.

```console
$ cd exercises
$ cd ex-05
$ go run functions.go

$
```