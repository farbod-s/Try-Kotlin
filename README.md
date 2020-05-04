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

String Values
---
```kotlin
val myString = "hello, world"

val empty = String()
println("'$empty'")

val charArray = myString.toCharArray()
println(charArray.toList())

val len = myString.length
for (i in 0 until len) {
    println("${myString.get(i)}")
}

val i = myString.indexOf("w")
val subString = myString.substring(i)
println(subString)

val myString2 = myString.toUpperCase()
val match = myString.equals(myString2, true /*ignore case*/)
println("match=$match")

// string concatination (efficient way)
// in Kotlin String is immutable just like Java
// Kotlin StringBuilder is a type alias of Java StringBuilder class
val builder = StringBuilder("To be or not to be\n")
        .append("that is the question")

val result = builder.toString()
println(result)
```

Constant Values
---
+ Compile-time constants speed up and reduce memory usage

```kotlin
const val myConstant = "RED"
println("my constant is $myConstant")
// => System.out.println("my constant is RED");
```

> **Compile-Time Constants**
>
> Properties the value of which is known at compile time can be marked as compile time constants using the const modifier. Such properties need to fulfill the following requirements:
> * Top-level or member of an object declaration or a companion object.
> * Initialized with a value of type String or a primitive type
> * No custom getter
>
> Such properties can be used in annotations.

### Declaring Constants
```kotlin
class Consts {
    companion object {
        // using compile-time constants (efficient way)
        const val myConstant = "RED"

        // using Java annotations
        @JvmField val myConstant2 = "GREEN"
        // => Consts.myConstant2
    }
}
```

Functions
---
+ Function parameters don't need `val` or `var` keywords, because they are always immutable.
+ When passing paramters to function by name, we can change the order of parameters.
```kotlin
fun addValues(param1: Int, param2: Int): Int {
    return param1 + param2
}

val result = adValues(1, 2)

// passing paramters by names
val result = addValues(param2 = 2, param1 = 1)
```

### Optional Parameters
```kotlin
fun calcValues(param1: Int, param2: Int, op: String = "+"): Int {
    if (op.equals("+")) {
        return param1 + param2
    } else if (op.equals("-")) {
        return param1 - param2
    } else {
        return -1
    }
}

val result = calcValues(1, 2)
val result2 = calcValues(1, 2, "-")
```

### Variable Arguments
```kotlin
fun addValues(vararg numbers: Int): Int {
    var result = 0
    for (num in numbers) {
        result += num
    }
    return result
}

val result = addValues(1, 2, 3, 4, 5)
```

### [Is Java **pass-by-reference** or **pass-by-value**?](http://www.javadude.com/articles/passbyvalue.htm)
The Java Spec says that everything in Java is **pass-by-value**. There is no such thing as **~~pass-by-reference~~** in Java.

> Objects are not passed by reference. A correct statement would be **Object References** are passed by value.

```java
public void foo(Dog d) {
    d = new Dog("Fifi"); // creating the "Fifi" dog
}

Dog aDog = new Dog("Max"); // creating the "Max" dog
// at this point, `aDog` points to the "Max" dog

foo(aDog); 
// `aDog` still points to the "Max" dog
```

the variable passed in, `aDog`, is not modified! After calling `foo()`, `aDog` still points to the `Dog` with name `"Max"`!

Many people mistakenly think/state that something like:
```java
public void foo(Dog d) { 
    d.setName("Fifi");
}
```

> When you declare and instantiate an object. The actual object goes on the heap. What goes on the stack? The address of the object on the heap. C++ programmers would call this a pointer, but some Java developers are against the word "pointer". Whatever. Just know that the address of the object goes on the stack.

### [Is Kotlin **pass-by-value** or **pass-by-reference**?](https://stackoverflow.com/a/54689951/2034849)
It uses the same principles like Java. It is always pass-by-value, you can imagine that a copy is passed. For primitive types, e.g. `Int` this is obvious, the value of such an argument will be passed into a function and the outer variable will not be modified. Please note that parameters in Kotlin cannot be reassigned since they act like `val`s.

```kotlin
fun takeInt(a: Int) {
    // this code will not compile because `a` cannot be reassigned.
    a = 5
}
```

For objects it's a bit more difficult but it's also call-by-value. If you call a function with an object, a copy of its reference is passed into that function:

```kotlin
data class SomeObj(var x: Int = 0)

fun takeObject(o: SomeObj) {
    o.x = 1
}

fun main(args: Array<String>) {
    val obj = SomeObj()
    takeObject(obj)
    println("obj after call: $obj") // SomeObj(x=1)
}
```

You can use a reference passed into a function to change the actual object. This will influence the argument you passed in. But the reference itself, i.e. the value of the variable, will never be changed via a function call.

