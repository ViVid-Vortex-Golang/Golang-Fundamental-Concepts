# Go Named vs Unnamed Types (Compared to Java)

Go's **named vs unnamed types** can be understood very cleanly by comparing them to Java.

The big idea is that Go has **named types** and **unnamed (type-expression) types**, while Java mainly uses **classes/interfaces** and **type expressions** like generics or arrays.

In Go, named types are created using `type`, such as:

```go
type Age int
type Numbers []int
type Person struct {
    name string
}
```

These are **named types**, meaning they create a **new type identity** and allow methods to be attached.

In Java, the closest equivalent would be classes like:

```java
class Age {
    int value;
}

class Numbers {
    List<Integer> values;
}

class Person {
    String name;
}
```

The key idea is that **named types in Go have identity and behavior**, similar to Java classes.

Go also has built-in named types like:

- `int`
- `string`
- `bool`
- `float64`

These roughly correspond to Java's:

- `int`
- `String`
- `boolean`
- `double`

although Java primitives behave slightly differently internally.

On the other hand, Go **unnamed types** are type expressions such as:

```go
[]int
map[string]int
chan int
func(int) string
```

These are **not named entities**; they are defined purely by their structure.

The closest Java concepts are:

| Go | Java Equivalent |
|-----|-----------------|
| `[]int` | `int[]` |
| `map[string]int` | `Map<String, Integer>` |
| `func(int) string` | `Function<Integer, String>` |
| `chan int` | `BlockingQueue<Integer>` (conceptually) |

A key difference is that Java wraps these structures inside classes if you want behavior, while Go allows direct use of structural types.

For example, in Go you can write:

```go
type Numbers []int

func (n Numbers) Sum() int {
    // implementation
}
```

In Java, you cannot write:

```java
int[].sum()
```

Instead, you would wrap it in a class:

```java
class Numbers {
    int[] values;

    int sum() {
        // implementation
    }
}
```

The mental mapping is:

### Go Named Types

- `Person`
- `Age`
- `Numbers`

≈ Java classes like:

- `Person`
- `Integer`
- `String`

### Go Unnamed Types

- `[]int`
- `map[string]int`

≈ Java type expressions like:

- `int[]`
- `List<Integer>`
- `Map<String, Integer>`

## Core Concept

Java assumes **everything should live inside a class or wrapper**, whereas Go allows you to use **raw structural types directly**, while also giving you the option to create named types when additional identity or behavior is needed.

### Simple Analogy

- **Java:** "Everything must be inside a class."
- **Go:** "You can use raw shapes directly, or give them names when useful."

### Final Mapping

**Named Go Types**

```go
type Person struct{}
type Numbers []int
type Age int
```

≈ Java

```java
class Person {}
class Numbers {}
class Age {}
```

**Unnamed Go Types**

```go
[]int
map[string]int
func(int) string
```

≈ Java

```java
int[]
Map<String, Integer>
Function<Integer, String>
```
