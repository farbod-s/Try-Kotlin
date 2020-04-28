<image src="./resource/logo.png" width="500">

Kotlin
===
+ kotlin is an open source language
+ **Edu Tools** plugin from [kotlinlang.org](try.kotlinlang.org)

The Philosophy of Kotlin
---
A statically typed language for multiple application platforms.

+ Kotlin/JVM compiles to Java bytecode
+ Kotlin/JS transpiles to JavaScript code
+ Kotlin/Native compiles to native binaries

> **Statically typed languages**: A language is statically typed if the type of a variable is known at compile time. some languages offer some form of type inference, the capability of the type system to deduce the type of a variable.

> **Dynamically typed languages**: A language is dynamically typed if the type is associated with run-time values, and not named variables/fields/etc.Most scripting languages have this feature as there is no compiler to do static type-checking anyway.

Kotlin Goals
---
### Concise
+ Reduces use of unnecessary declarations and keywords
+ Generates code that has to be explicit in Java
+ Semi-colons not required!

### Safe
+ Avoids entire classes of errors such as null pointer exceptions
+ Auto-casting of variables when checking types

### Interoperable
+ Kotlin/JVM code can be mixed with Java or any other JVM language
+ Kotlin code works both in JVM and in a web browser

### Tool Friendly
+ IntelliJ IDEA includes the kotlin plugin
+ Android Studio inherits Kotlin support

How Java Compiles to Bytecode
---
Each Java class in its own file compiles to a `.class` bytecode file.

<image src="./resource/1.png" width="500">

How Kotlin Compiles to Bytecode
---
Each Kotlin class also compiles to a `.class` bytecode file.

<image src="./resource/2.png" width="500">

Multiple Kotlin classes
---
Each class in a single code file is compiled to its own bytecode file.

<image src="./resource/3.png" width="500">

Coding Conventions
---
### Naming Packages
+ Package names should be in lower case with no underscores.
+ Use camel-case if necessary for readability.
+ Unlike Java, package and directory names don't have to match. But IntelliJ IDEA likes it when they do match!

```kotlin
package utilities
```

### Packages in Mixed Projects
+ Use reverse domain notation.

```kotlin
package com.example.kotlin
```

<image src="./resource/4.png" width="250">

### Packages in Pure Kotlin Projects
+ Place main code file in source code root directory
+ No package decleration needed in main code file
+ Sub-packages have shallow names

### Naming Classes and Interfaces
+ Class and interface identifiers starts with upper-case character
+ Use cammel-case for readablility

```kotlin
data class Person
interface MyInterface {}
```

### Naming Variables
+ Variable and function identifiers starts with lower-case character
+ Use cammel-case for readablility

```kotlin
val number = 1
fun add(a: Int, b: Int): Int {}

val aNumber = 1
fun addValues(a: Int, b: Int): Int {}
```

### Naming Constants
+ Constants are declared as member of companion objects
+ Identifiers are upper-case
+ Use underscores fore readability

```kotlin
class Constants {
    companion object {
        const val A_FIXED_VALUE = "a fixed value"
    }
}
```

Kotlin Keywords
---
### Hard Keywords
+ Have specific meanings everywhere
+ Cannot be used as identifiers

```kotlin
// declare variables
val, var

// define various kinds of entities
class, interfcace, object

// organize codes
package, fun, return

// create code blocks
for, while, when, try

// operators
as, is, in, out

// boolean values
true, false
```

### Soft Keywords
+ Reserved in particular contexts
+ Can otherwise be used as identifiers

```kotlin
catch, finally
import, init
set, setparam
constructor, dynamic
```

### Modifier Keywords
+ Modify effect of hard keywords
+ Can otherwise be used as identifiers

```kotlin
// apply to classes
enum, data, sealed, open

// apply to objects
companion

// apply to functions
constructor, infix
```

Built-In Types
---
+ Unlike Java, Kotlin doesn't support primitive types
+ Everything is a class
+ Limited number of built-in types
+ Numeric, characters, booleans, arrays

### Numbers
| Kotlin (Java)   | Bit width |
| --------------- |:---------:|
| Double (double) | 64        |
| Float (float)   | 32        |
| Long (long)     | 64        |
| Int (int)       | 32        |
| Short (short)   | 16        |
| Byte (byte)     | 8         |

### Other Built-In Types
| Kotlin (Java)     | Notes                        |
| ----------------- |:----------------------------:|
| Char (char)       | Not treated as a number      |
| Boolean (boolean) | `true` or `false`            |
| String (String)   | always immutable             |
| Array (n/a)       | A Kotlin class named `Array` |

### Declaring a Variable
+ Either the type or the initial value are always required
+ Type can sometimes be inferred from initial value

```kotlin
val myVariable: Int = 1
```

> **Variables**
>
> `val` means that the variable is immutable and cannot be changed once set. `var` means it is mutable.

```kotlin
const val myConstant: Int = 1
```

> **Compile-Time Constants**
>
> Properties the value of which is known at compile time can be marked as compile time constants using the const modifier. Such properties need to fulfill the following requirements:
> * Top-level or member of an object declaration or a companion object.
> * Initialized with a value of type String or a primitive type
> * No custom getter
>
> Such properties can be used in annotations.

<image src="./resource/5.png" width="250">

### Declaring a Nullable Value
+ Initialization with `null` keyword not always required

```kotlin
val myVariable: Int? = null
```

<image src="./resource/6.png" width="250">

### Instantiating a Class
+ Type is inferred from constructor method call

```kotlin
val myObject = MyClass("parameter")
```

String Templates
---
```kotlin
println("this is my message ${message}")
println("this is my message $message")
```

Numeric Values
---
### Type Casting
```kotlin
val myInt = 1
val myLong: Long = myInt.toLong()

println("the type of myLong is ${myLong::class.simpleName}")
// output: "the type of myLong is kotlin.Long"

val myLong2 = 1.5
val myInt2 = myLong2.toInt()

println("the value of myInt2 is $myInt2")
// output: "the value of myInt2 is 1"
```

### Comparision
```kotlin
val num1 = 1
val num2 = 2

// using operator (efficient way)
println("match is ${num1 == num2}")
// => System.out.println("match is " + false);

// using built-in methods
println("match is ${num1.equals(num2)}")
// => System.out.println("match is " + Integer.valueOf(num1).equals(Integer.valueOf(num2)));

// using comparison method
println("comparison result is ${num1.compareTo(num2)}")
// output: "comparison result is -1"
// -1: less than
//  0: is equal
// +1: greater than
```

