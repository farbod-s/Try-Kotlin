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

> **On the JVM**: the named argument syntax cannot be used when calling Java functions because Java bytecode does not always preserve names of function parameters.

### Unit-Returning Functions
If a function does not return any useful value, its return type is `Unit`. `Unit` is a type with only one value `Unit`. This value does not have to be returned explicitly:

```kotlin
fun printHello(name: String?): Unit { // the `Unit` return type declaration is also optional
    if (name != null)
        println("Hello ${name}")
    else
        println("Hi there!")
    // `return Unit` or `return` is optional
}
```

### Single-Expression Functions
When a function returns a single expression, the curly braces can be omitted and the body is specified after a `=` symbol:

```kotlin
fun double(x: Int): Int = x * 2
```

Explicitly declaring the return type is optional when this can be inferred by the compiler.

### Generic Functions
Functions can have generic parameters which are specified using angle brackets before the function name:
```kotlin
fun <T> singletonList(item: T): List<T> { /*...*/ }
```

### Tail Recursive Functions
Kotlin supports a style of functional programming known as tail recursion. This allows some algorithms that would normally be written using loops to instead be written using a recursive function, but without the risk of stack overflow. When a function is marked with the `tailrec` modifier and meets the required form, the compiler optimises out the recursion, leaving behind a fast and efficient loop based version instead:

```kotlin
val eps = 1E-10 // "good enough", could be 10^-15

tailrec fun findFixPoint(x: Double = 1.0): Double
        = if (Math.abs(x - Math.cos(x)) < eps) x else findFixPoint(Math.cos(x))
```

The resulting code is equivalent to this more traditional style:

```kotlin
private fun findFixPoint(): Double {
    var x = 1.0
    while (true) {
        val y = Math.cos(x)
        if (Math.abs(x - y) < eps) return x
        x = Math.cos(x)
    }
}
```

To be eligible for the `tailrec` modifier, a function must call itself as the last operation it performs. You cannot use tail recursion when there is more code after the recursive call, and you cannot use it within try/catch/finally blocks.
Currently, tail recursion is supported by Kotlin for JVM and Kotlin/Native.

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

### Top-Level Functions
Top-level functions are functions inside a Kotlin package that are defined outside of any class, object, or interface. This means that they are functions you call directly, without the need to create any object or call any class.

> Given that Java doesn't support top-level functions, the Kotlin compiler behind the scenes will create a Java class, and the individual top-level functions will be converted to static methods.

Note that we can change the Java class name that the Kotlin compiler generates by using the `@JvmName` annotation.

```kotlin
@file:JvmName("UserUtils")
package com.chikekotlin.projectx.utils
 
fun checkUserStatus(): String {
    return "online"
}
```

### Lambda Expressions
Here are the characteristics of a lambda expression in Kotlin:
+ It must be surrounded by curly braces `{}`.
+ It doesn't have the `fun` keyword. 
= There is no access modifier (`private`, `public` or `protected`) because it doesn't belong to any class, object, or interface.
+ It has no function name. In other words, it's anonymous. 
+ No return type is specified because it will be inferred by the compiler.
+ Parameters are not surrounded by parentheses `()`.

And, what's more, we can assign a lambda expression to a variable and then execute it.

```kotlin
val addNumbers = { number1: Int, number2: Int ->
    val result = number1 + number2
    println("The result is $result")
}
addNumbers(1, 3)
```

We can pass lambda expressions as parameters to functions: these are called **higher-order functions**, because they are functions of functions. These kinds of functions can accept a lambda or an anonymous function as parameter.

```kotlin
val stringList: List<String> = listOf("in", "the", "club")
stringList.f({ s: String -> s.length == 3})

// the Kotlin compiler allows us to remove the function parentheses if the last argument in the function is a lambda expression.
stringList.last { s: String -> s.length == 3 }

// we can make it more concise by removing the parameter type
// we don't need to specify the parameter type explicitly, because the parameter type is always the same as the collection element type.
stringList.last { s -> s.length == 3 }
```

We can even simplify the lambda expression further again by replacing the lambda expression argument with the auto-generated default argument name `it`.

```kotlin
stringList.last { it.length == 3 }
```

The `it` argument name was auto-generated because `last` can accept a lambda expression or an anonymous function (we'll get to that shortly) with only one argument, and its type can be inferred by the compiler.

> The last expression in a lambda is considered the return value.

We can explicitly return a value from the lambda using the qualified return syntax. Otherwise, the value of the last expression is implicitly returned.

```kotlin
ints.filter {
    val shouldFilter = it > 0 
    shouldFilter
}

ints.filter {
    val shouldFilter = it > 0 
    return@filter shouldFilter
}
```

If the lambda parameter is unused, you can place an underscore instead of its name:

```kotlin
map.forEach { _, value -> println("$value!") }
```

#### Local Return in Lambda Expressions
```kotlin
fun surroundingFunction() {
    val intList = listOf(1, 2, 3, 4, 5)
    intList.forEach {
        if (it % 2 == 0) {
            return@forEach
        }
    }
    println("End of surroundingFunction()") // Now, it will execute
}
 
surroundingFunction() // print "End of surroundingFunction()"
```

The return statement won't return from the lambda but instead from the containing function `surroundingFunction()`.

To fix this problem, we need to tell it explicitly which function to return from by using a label or name tag.

In the updated code above, we specified the default tag `@forEach` immediately after the `return` keyword inside the lambda. We have now instructed the compiler to return from the lambda instead of the containing function `surroundingFunction()`. Now the last statement of `surroundingFunction()` will execute.

Note that we can also define our own label or name tag:
```kotlin
// ...
intList.forEach myLabel@ {
    if (it % 2 == 0) {
        return@myLabel
// ...
```

In the code above, we defined our custom label called `myLabel@` and then specified it for the `return` keyword. The `@forEach` label generated by the compiler for the `forEach` function is no longer available because we have defined our own.

#### Closures
A lambda expression or anonymous function (as well as a local function and an object expression) can access its closure, i.e. the variables declared in the outer scope. The variables captured in the closure can be modified in the lambda:

```kotlin
var sum = 0
ints.filter { it > 0 }.forEach {
    sum += it
}
print(sum)
```

### Higher-Order Functions
A higher-order function is a function that takes functions as parameters, or returns a function.

```kotlin
fun <T, R> Collection<T>.fold(
    initial: R, 
    combine: (acc: R, nextElement: T) -> R
): R {
    var accumulator: R = initial
    for (element: T in this) {
        accumulator = combine(accumulator, element)
    }
    return accumulator
}
```

In the code above, the parameter combine has a function type `(R, T) -> R`, so it accepts a function that takes two arguments of types `R` and `T` and returns a value of type `R`.

### Function Types
- All function types have a parenthesized parameter types list and a return type: `(A, B) -> C` denotes a type that represents functions taking two arguments of types `A` and `B` and returning a value of type `C`. The parameter types list may be empty, as in `() -> A`. The `Unit` return type cannot be omitted.
- Function types can optionally have an additional receiver type, which is specified before a dot in the notation: the type `A.(B) -> C` represents functions that can be called on a receiver object of `A` with a parameter of `B` and return a value of `C`. Function literals with receiver are often used along with these types.
- Suspending functions belong to function types of a special kind, which have a `suspend` modifier in the notation, such as `suspend () -> Unit` or `suspend A.(B) -> C`.

The function type notation can optionally include names for the function parameters: `(x: Int, y: Int) -> Point`. These names can be used for documenting the meaning of the parameters.

To specify that a function type is nullable, use parentheses: `((Int, Int) -> Int)?`.

Function types can be combined using parentheses: `(Int) -> ((Int) -> Unit)`

The arrow notation is right-associative, `(Int) -> (Int) -> Unit` is equivalent to the previous example, but not to `((Int) -> (Int)) -> Unit`.

You can also give a function type an alternative name by using a type alias:
```kotlin
typealias ClickHandler = (Button, ClickEvent) -> Unit
```

#### Instantiating a Function Type
- Using a code block within a function literal, in one of the forms:
    - a lambda expression: `{ a, b -> a + b }`
    - an anonymous function: `fun(s: String): Int { return s.toIntOrNull() ?: 0 }`
- Using a callable reference to an existing declaration:
    - a top-level, local, member, or extension function: `::isOdd, String::toInt`
    - a top-level, member, or extension property: `List<Int>::size`
    - a constructor: `::Regex`
- Using instances of a custom class that implements a function type as an interface:

```kotlin
class IntTransformer: (Int) -> Int {
    override operator fun invoke(x: Int): Int = TODO()
}

val intFunction: (Int) -> Int = IntTransformer()
```

#### Invoking a Function Type Instance
A value of a function type can be invoked by using its **invoke(...)** operator: `f.invoke(x)` or just `f(x)`.

```kotlin
val stringPlus: (String, String) -> String = String::plus
val intPlus: Int.(Int) -> Int = Int::plus

println(stringPlus("Hello, ", "world!"))  // Hello, world!

println(intPlus.invoke(1, 1)) // 2
println(intPlus(1, 2)) // 3

// extension-like call
println(2.intPlus(3)) // 5
```

### Inline Functions
Using higher-order functions imposes certain runtime penalties: each function is an object, and it captures a closure, i.e. those variables that are accessed in the body of the function. Memory allocations (both for function objects and classes) and virtual calls introduce runtime overhead.

But it appears that in many cases this kind of overhead can be eliminated by inlining the lambda expressions.

```kotlin
inline fun <T> lock(lock: Lock, body: () -> T): T { ... }
```

Inlining may cause the generated code to grow; however, if we do it in a reasonable way (i.e. avoiding inlining large functions), it will pay off in performance, especially at "megamorphic" call-sites inside loops.

#### Noinline
In case you want only some of the lambdas passed to an inline function to be inlined, you can mark some of your function parameters with the `noinline` modifier:

```kotlin
inline fun foo(inlined: () -> Unit, noinline notInlined: () -> Unit) { ... }
```

### Member Functions
This kind of function is defined inside a class, object, or interface. Using member functions helps us to modularize our programs further.

### Anonymous Functions
An anonymous function is another way to define a block of code that can be passed to a function. It is not bound to any identifier. Here are the characteristics of an anonymous function in Kotlin:
+ has no name
+ is created with the fun keyword
+ contains a function body

```kotlin
val strLenThree = stringList.last( fun(string): Boolean {
    return string.length == 3
})
print(strLenThree) // will print "the"
```

In the above code, we have replaced the lambda expression with an anonymous function because we want to be explicit about the return type. 

The return expression returns from the anonymous function and not from the surrounding one:
```kotlin
fun surroundingFunction() {
    val intList = listOf(1, 2, 3, 4, 5)
    intList.forEach ( fun(number) {
        if (number % 2 == 0) {
            return
        }
    })
    println("End of surroundingFunction()") // statement executed
}
 
surroundingFunction() // will print "End of surroundingFunction()"
```

> Lambda expressions and anonymous functions are **function literals**, i.e. functions that are not declared, but passed immediately as an expression. Consider the following example:
```kotlin
max(strings, { a, b -> a.length < b.length })
```
Function `max` is a higher-order function, it takes a function value as the second argument. This second argument is an expression that is itself a function, i.e. a function literal, which is equivalent to the following named function:
```kotlin
fun compare(a: String, b: String): Boolean = a.length < b.length
```

### Local or Nested Functions
A local function is a function that is declared inside another function.

The nested functions can be called only from within the enclosing function and not outside.

We can make our local functions more concise by not explicitly passing parameters to them. This is possible because local functions have access to all parameters and variables of the enclosing function.

```kotlin
fun printCircumferenceAndArea(radius: Double): Unit {
    fun calCircumference(): Double = (2 * Math.PI) * radius
    val circumference = "%.2f".format(calCircumference())
 
    fun calArea(): Double = (Math.PI) * Math.pow(radius, 2.0)
    val area = "%.2f".format(calArea())
    // ...
}
```

### [Infix Functions](https://code.tutsplus.com/tutorials/kotlin-from-scratch-more-functions--cms-29479)
The `infix` notation allows us to easily call a one-argument member function or extension function. In addition to a function being one-argument, you must also define the function using the `infix` modifier. To create an infix function, two parameters are involved. The first parameter is the target object, while the second parameter is just a single parameter passed to the function.

> Infix function calls have lower precedence than the arithmetic operators, type casts, and the rangeTo operator.
> 
> - 1 shl 2 + 3 is equivalent to 1 shl (2 + 3)
> - 0 until n * 2 is equivalent to 0 until (n * 2)
> - xs union ys as Set<*> is equivalent to xs union (ys as Set<*>)

> On the other hand, infix function call's precedence is higher than that of the boolean operators && and ||, is- and in-checks, and some other operators.
>
> - a && b xor c is equivalent to a && (b xor c)
> - a xor b in c is equivalent to (a xor b) in c

#### Creating an Infix Member Function
```kotlin
class Student {
    var kotlinScore = 0.0
     
    infix fun addKotlinScore(score: Double): Unit {
        this.kotlinScore = kotlinScore + score
    }
}
```

#### Calling an Infix Function
+ we don't need to use the dot notation
+ we don't need to wrap the parameter with parentheses
```kotlin
val student = Student()
student addKotlinScore 95.00
print(student.kotlinScore) // will print "95.0"
```

#### The `to` Infix Function
In Kotlin, we can make the creation of a `Pair` instance more succinct by using the `to` infix function instead of the `Pair` constructor. (Behind the scenes, `to` also creates a `Pair` instance.)

Note that the `to` function is also an extension function:
```kotlin
public infix fun <A, B> A.to(that: B): Pair<A, B> = Pair(this, that)
```

compare the creation of a map by using both the `to` infix function and the `Pair` constructor to create the individual pairs:

```kotlin
val nigeriaCallingCodePair = 234 to "Nigeria"
val nigeriaCallingCodePair2 = Pair(234, "Nigeria") // same as above
val nigeriaCallingCodePair3 = 234.to("Nigeria") // same as using 234 to "Nigeria"

val callingCodesMap: Map<Int, String> = mapOf(234 to "Nigeria", 1 to "USA", 233 to "Ghana")
val callingCodesPairMap: Map<Int, String> = mapOf(Pair(234, "Nigeria"), Pair(1, "USA"), Pair(233, "Ghana"))
```

### Extension Function
Kotlin provides the ability to extend a class with new functionality without having to inherit from the class or use design patterns such as Decorator. For example, you can write new functions for a class from a third-party library that you can't modify.

To declare an extension function, we need to prefix its name with a receiver type, i.e. the type being extended.

```kotlin
fun MutableList<Int>.swap(index1: Int, index2: Int) {
    // the this keyword inside an extension function corresponds to the receiver object (the one that is passed before the dot).
    val tmp = this[index1] // 'this' corresponds to the list
    this[index1] = this[index2]
    this[index2] = tmp
}
```

Extension cannot be overloaded. So, it’s impossible to use the override keyword to modify the behavior of an extension that’s already been created.

If a class has a member function, and an extension function is defined which has the same receiver type, the same name, and is applicable to given arguments, the member always wins.

> **Extensions are resolved statically**
>
> Extensions do not actually modify classes they extend. By defining an extension, you do not insert new members into a class, but merely make new functions callable with the dot-notation on variables of this type.
>
> Extension functions are dispatched statically, i.e. they are not virtual by receiver type. This means that the extension function being called is determined by the type of the expression on which the function is invoked, not by the type of the result of evaluating that expression at runtime.

### Extension Properties
```kotlin
val <T> List<T>.lastIndex: Int
    get() = size - 1
```

Note that, since extensions do not actually insert members into classes, there's no efficient way for an extension property to have a backing field. This is why **initializers are not allowed for extension properties**. Their behavior can only be defined by explicitly providing getters/setters.

```kotlin
val House.number = 1 // error: initializers are not allowed for extension properties
```

### Declaring Extensions as Members
Inside a class, you can declare extensions for another class. Inside such an extension, there are multiple implicit receivers - objects members of which can be accessed without a qualifier. The instance of the class in which the extension is declared is called **dispatch receiver**, and the instance of the receiver type of the extension method is called **extension receiver**.

```kotlin
class Host(val hostname: String) {
    fun printHostname() { print(hostname) }
}

class Connection(val host: Host, val port: Int) {
    fun printPort() { print(port) }

    fun Host.printConnectionString() {
        printHostname() // calls Host.printHostname()
        print(":")
        printPort() // calls Connection.printPort()
    }

    fun connect() {
        /*...*/
        host.printConnectionString() // calls the extension function
    }
}

fun main() {
    Connection(Host("kotl.in"), 443).connect()
    //Host("kotl.in").printConnectionString(443)  // error, the extension function is unavailable outside Connection
}
```

In case of a name conflict between the members of the dispatch receiver and the extension receiver, the extension receiver takes precedence. To refer to the member of the dispatch receiver you can use the qualified `this` syntax.

```kotlin
class Connection {
    fun Host.getConnectionString() {
        toString() // calls Host.toString()
        this@Connection.toString() // calls Connection.toString()
    }
}
```

Extensions declared as members can be declared as `open` and overridden in subclasses. This means that the dispatch of such functions is virtual with regard to the dispatch receiver type, but static with regard to the extension receiver type.

```kotlin
open class Base { }

class Derived : Base() { }

open class BaseCaller {
    open fun Base.printFunctionInfo() {
        println("Base extension function in BaseCaller")
    }

    open fun Derived.printFunctionInfo() {
        println("Derived extension function in BaseCaller")
    }

    fun call(b: Base) {
        b.printFunctionInfo() // call the extension function
    }
}

class DerivedCaller: BaseCaller() {
    override fun Base.printFunctionInfo() {
        println("Base extension function in DerivedCaller")
    }

    override fun Derived.printFunctionInfo() {
        println("Derived extension function in DerivedCaller")
    }
}

fun main() {
    BaseCaller().call(Base()) // "Base extension function in BaseCaller"
    DerivedCaller().call(Base()) // "Base extension function in DerivedCaller" - dispatch receiver is resolved virtually
    DerivedCaller().call(Derived()) // "Base extension function in DerivedCaller" - extension receiver is resolved statically
}
```

### Extension Visibility
- An extension declared on top level of a file has access to the other private top-level declarations in the same file.
- If an extension is declared outside its receiver type, such an extension cannot access the receiver's private members.

Conditions
---
```kotlin
val state = readline()
val capital: String?

when (state) {
    "CA" -> capital = "Sacramento"
    "OR" -> capital = "Salem"
    "NH", "VT", "MA" -> capital = "New England"
    else -> capital = "Unknown"
}

println("The capital is $capital")
```
or
```kotlin
val state = readline()
val capital = when (state) {
    "CA" -> "Sacramento"
    "OR" -> "Salem"
    "NH", "VT", "MA" -> "New England"
    else -> "Unknown"
}

println("The capital is $capital")
```

```kotlin
val answer = 42
when (answer) {
    in 1..49 -> println("Not yet")
    in 50..75 -> println("Close enough")
    else -> {
        println("Definitely not!")
        println("No really")
    }
}
```
or
```kotlin
when {
    number < 1 -> print("Number is less than 1")
    number > 1 -> print("Number is greater than 1")
}
```

### Null Values
```kotlin
var nullvalue: String? = null
println("nullValue is $nullValue") // null

val length: Int? = nullValue?.length
println("length is $length") // length is null

val message = if (length != null) "length is $length" else "length is null"
println(message)

val length2: Int = length ?: -1
println("length2 is $length2") // length2 is -1

val length3: Int = length!!
try {
    print("length3 is $length3") // will raise KotlinNullPointerException because length is null
} catch(e: KotlinNullPointerException) {
    println("length3 is null")
}
```

### Loops
```kotlin
val colors = arrayOf("Red", "Green", "Blue")
val values = intArrayOf(1, 3, 5, 7, 9)

// for each loop
for (color in colors) {
    println(color)
}

// for loop with indices
for (i in values.indices step 2) {
    println(values[i])
}

for (i in 0 until colors.size) { // 0..colors.size - 1
    println(colors[i])
}

// while loop
var counter = 0
while (counter < colors.size) {
    println("color = ${colors[counter]}")
    ++counter
}

// do/while loop
counter = 0
do {
    println("color = ${colors.get(counter)}")
    ++counter
} while (counter < colors.size)
```

Classes
---
### Object
Kotlin has language support for creating singletons with the `object` keyword.

### Companion Object
The same as with normal objects, companion objects cannot have constructors, but can extend other classes and implement interfaces.
```kotlin
class MathLib {
    companion object {
        fun addValues(num1: Int, num2: Int) = num1 + num2
    }
}
```

### Enum Class
```kotlin
enum class Operation(val operator: String) {
    ADD("+"), SUBTRACT("-"), MULTIPLY("*"), DIVIDE("/")
}
```

### Data Class
To ensure consistency and meaningful behavior of the generated code, data classes have to fulfill the following requirements:

- The primary constructor needs to have at least one parameter;
- All primary constructor parameters need to be marked as `val` or `var`;
- Data classes cannot be abstract, open, sealed or inner;
- (before 1.1) Data classes may only implement interfaces.

```kotlin
// primary constructor
data class ClothingItem(val type: String,
                        val size: String,
                        val price: Double)

fun main() {
    val item = ClothingItem("Short", "L", 19.99)
    println(item) // ClothingItem(type=short, size=L, price=19.99)
}
```

### Class Constructors
```kotlin
// primary constructor
data class ClothingItem constructor (var type: String?,
                        val size: String,
                        val price: Double) {
    // executed when primary constructor called
    init {
        type = type?.toUpperCase() ?: "UNKNOWN"
    }

    // secondary constructor: has to daisy chain to primary constructor
    constructor(size: String, price: Double): this(null, size, price) {
        // type = "Unknown"
    }
}

fun main() {
    val item = ClothingItem("M", 14.99)
    println(item) // ClothingItem(type=UNKNOWN, size=M, price=14.99)
}
```

### Class Properties
```kotlin
data class ClothingItem(private var _type: String?,
                        val size: String,
                        private var _price: Double) {
    var type: String? = _type
        get() = field ?: "Unknown"

    var price = _price
        set(value) {
            field = value * .9
        }
}

fun main() {
    val item = ClothingItem("M", 14.99)
    println("item type = ${item.type}") // item type = Unknown

    item.price = 10.0
    println("item price = ${item.price}") // item price = 9.0
}
```

### Inheritance
```kotlin
open class SuperClass(anInt: Int) {
    protected val _anInt = anInt

    override fun toString(): String {
        return "${this::class.simpleName} [anInt: $_anInt]"
    }

    open fun multiply(factor: Int): Int {
        return _anInt * factor
    }
}

class SubClass(anInt: Int): SuperClass(anInt) {
    override fun multiple(factor: Int): Int {
        return super.multiply(factor) * factor
    }
}
```
 
### Interface
```kotlin
interface Dog {
    var fur: String
    fun speak() {
        println("Woof!")
    }
}

interface Cat {
    var fur: String
    fun speak() {
        println("Meow!")
    }
}

class Retriever: Dog, Cat  {
    override var fur: String
        get() = "golder"
        set(value) {}

    override fun speak() {
        super<Dog>.speak()
    }
}

fun makeItTalk(dog: Dog) {
    dog.speak()
}

fun reportBreed(name: String, dog: Dog) {
    println("$name is a ${dog::class.simpleName}")
}

fun main() {
    val buster = Retriever()
    makeItTalk(buster)
    reportBreed("Buster", buster)
}
```

### Callbacks
```kotlin
class ClickEvent(x: Int, y: Int)

interface ClickListener {
    fun onClick(event: ClickEvents)
}

class StatefulWidget(listener: ClickListener) {
    private var _listener: ClickListener? = listener

    fun click(x: Int, y: Iny) {
        listener?.onClick(ClickEvent(x, y))
    }
}

fun main() {
    // using anonymous object
    val widget = StatefulWidget(object: ClickListener {
        override fun onClick(event: ClickEvent) {
            println("clicked at (${event.x}, ${event.y})s")
        }
    })

    widget.click(5, 18)
}
```

### Sealed Class
```kotlin
// abstract class
sealed class ClothingItem(val type: String) {
    abstract val size: String
    abstract val price: Double
}

// subclasses must be in the same code file
data class Shirt(override var size: String,
                 override var price: Double): ClothingItem("Shirt")

data class Pants(override var size: String,
                 override var price: Double): ClothingItem("Pants")

fun main() {
    val item1 = Shirt("XL", 19.99)
    val item2 = Pants("32", 24.99)

    val mostExpensive =
            if (item1.price > item2.price) item1 else item2

    val instructions = when(mostExpensive) {
        is Shirt -> "Button it!"
        is Pants -> "Buckle it!"
    }

    println(instructions)
}
```

More Kotlin
---

### Enums
Enums are **exhaustive** in `when` expressions (`switch` in Java). In Kotlin, we can return on expressions or assign a value to one, forcing each branch of the expression to supply a valid value to fulfill the expression return type.

> In **Java**, `enum` are static singleton objects that cannot have multiple instances.

### Sealed Class
**Sealed Classes** are a special kind of class such that the Kotlin compiler can verify all subtypes during compilation, adding some unique benefits.

To allow our `enum` to hold state, but have the compiler verify we covered all cases of an instance, we change the declaration to a `sealed class`.

```kotlin
sealed class Result <out T: Any> {
    data class Success <out T: Any> (val data: T): Result<T>()
    data class Error(val exception: Exception): Result<Nothing>()
    object InProgress: Result<Nothing>()
}

fun handleResult(result: Result<Int>) {
    val action = when(result) {
        is Result.Success -> {}
        is Result.Error -> {}
        Result.InProgress -> {}
    }.exhaustive
}

val <T>.exhaustive: T
    get() = this
```

### Unit
`Unit` in Kotlin corresponds to the `void` in Java. Like void, Unit is the return type of any function that does not return any meaningful value, and it is optional to mention the Unit as the return type. But unlike void, Unit is a real class (Singleton) with only one instance.

### Nothing
`Nothing` is a type in Kotlin that represents "a value that never exists", that means just "no value at all".

### `lateinit` vs `lazy`
`lateinit`:
- Use it with mutable variable `var`
```kotlin
lateinit var name: String       //Allowed
lateinit val name: String       //Not Allowed
```

- Allowed with only **non-nullable** data types
```kotlin
lateinit var name: String       //Allowed
lateinit var name: String?      //Not Allowed
```

- It is a promise to compiler that the value will be initialized in future.

> If you try to access `lateinit` variable without initializing it then it throws `UnInitializedPropertyAccessException`.

`lazy`:
- Lazy initialization was designed to prevent unnecessary initialization of objects.
- Your variable will not be initialized unless you use it.
- It is initialized only once. Next time when you use it, you get the value from cache memory.
- It is thread safe (It is initializes in the thread where it is used for the first time. Other threads use the same value stored in the cache).
- The variable can only be `val`.
- The variable can only be **non-nullable**.

```kotlin
val aVar by lazy {
    println("I am computing this value") // prints only once
    "Hola" // the return value of lambda expression
}

fun main(args: Array<String>) {
    println(aVar)
    println(aVar)
}

// Result:
// "I am computing this value"
// "Hola"
// "Hola"
```

### Type Checks and Casts
#### `is` and `!is` Operators
We can check whether an object conforms to a given type at runtime by using the `is` operator or its negated form `!is`:
```kotlin
if (obj is String) {
    print(obj.length)
}

if (obj !is String) { // same as !(obj is String)
    print("Not a String")
}
```

#### Smart Casts
In many cases, one does not need to use explicit cast operators in Kotlin, because the compiler tracks the `is`-checks and explicit casts for immutable values and inserts (safe) casts automatically when needed.

The compiler is smart enough to know a cast to be safe if a negative check leads to a return.

or in the right-hand side of `&&` and `||`.

```kotlin
fun demo(x: Any) {
    if (x is String) {
        print(x.length) // x is automatically cast to String
    }
}

if (x !is String) return
print(x.length) // x is automatically cast to String

// x is automatically cast to string on the right-hand side of `||`
if (x !is String || x.length == 0) return

// x is automatically cast to string on the right-hand side of `&&`
if (x is String && x.length > 0) {
    print(x.length) // x is automatically cast to String
}

when (x) {
    is Int -> print(x + 1)
    is String -> print(x.length + 1)
    is IntArray -> print(x.sum())
}
```

#### "Unsafe" cast operator
Usually, the cast operator throws an exception if the cast is not possible. Thus, we call it unsafe. The unsafe cast in Kotlin is done by the infix operator `as`:
```kotlin
val x: String = y as String
```

Note that null cannot be cast to `String` as this type is not nullable, i.e. if `y` is null, the code above throws an exception. To make such code correct for null values, use the nullable type on the right hand side of the cast:
```kotlin
val x: String? = y as String?
```

#### "Safe" (nullable) cast operator
To avoid an exception being thrown, one can use a safe cast operator `as?` that returns `null` on failure:
```kotlin
val x: String? = y as? String
```
Note that despite the fact that the right-hand side of `as?` is a non-null type `String` the result of the cast is nullable.

### Coroutines
Kotlin Coroutines are like lightweight threads. They are lightweight because creating coroutines doesn’t allocate new threads. Instead, they use predefined thread pools, and smart scheduling. Scheduling is the process of determining which piece of work you will execute next.

Additionally, coroutines can be **suspended** and **resumed** mid-execution. This means you can have a long-running task, which you can execute little-by-little. You can pause it any number of times, and resume it when you’re ready again.

#### CoroutineScope
- Keep track of coroutines
- Ability to cancel ongoing work
- Notified when a failure happens 

```kotlin
val scope = CoroutineScope(Job())
val job = scope.launch {
    // Coroutine
}
```

> Cancelling the scope **cancels its children**.
>
> a **cancelled** child doesn't affect other siblings.

#### Job
- Provides lifecycle
- Couroutine hierarchy

#### Job Lifecycle
**States**:
- New, Active
- Completing, Completed
- Cancelling, Cancelled

**Properties**:
- isActive
- isCancelled
- isCompleted

<image src="./resource/7.png" width="500">

#### CoroutineContext
Defines the behavior of coroutine and consist set of elements with default values:
- CoroutineDispatcher -> Threading (Dispatchers.Default)
- Job -> Lifecycle (No parent Job)
- CoroutineExceptionHandler (None)
- CoroutineName ("coroutine")

> a **new coroutine** inherits the parent context.
>
> Parent context = Defaults + inherited context + arguments
> 
> Coroutine context = parent context + Job()

#### Cooperative Cancellation
`val isActive`:
- Do an action before finishing the coroutine.

`fun ensureActive()`:
- Instantaneously stop work.

`suspend fun yield()`:
- CPU heavy computation that may exhaust thread-pool.
- Checks if the coroutine Job was completed. If yes, throws `CancellationException`.

> **PRO TIP**: All the suspending functions in `Kotlin.coroutines` are **cancellable**.
>
> If you create your own suspend functions, make them cancellable.

### Singleton
```kotlin
object SomeSingleton
```
The above Kotlin object will be compiled to the following equivalent Java code:
```kotlin
public final class SomeSingleton {
   public static final SomeSingleton INSTANCE;

   private SomeSingleton() {
      INSTANCE = (SomeSingleton)this;
      System.out.println("init complete");
   }

   static {
      new SomeSingleton();
   }
}
```

This is the preferred way to implement singletons on a JVM because it enables thread-safe lazy initialization without having to rely on a locking algorithm like the complex double-checked locking.

### `suspending` vs. `blocking`
- A **blocking** call to a function means that a call to any other function, from the same thread, will halt the parent’s execution. Following up, this means that if you make a blocking call on the main thread’s execution, you effectively freeze the UI. Until that blocking calls finishes, the user will see a static screen, which is not a good thing.

- **Suspending** doesn’t necessarily block your parent function’s execution. If you call a suspending function in some thread, you can easily push that function to a different thread. In case it is a heavy operation, it won’t block the main thread. If the suspending function has to suspend, it will simply pause its execution. This way you free up its thread for other work. Once it’s done suspending, it will get the next free thread from the pool, to finish its work.

> Suspending functions can invoke any other regular functions, but to actually suspend the execution, it has to be another suspending function. A suspending function cannot be invoked from a regular function, therefore several so-called coroutine builders are provided, which allow calling a suspending function from a regular non-suspending scope like `launch`, `async`, `runBlocking`.

### Flow
Using the `List<Int>` result type, means we can only return all the values at once. To represent the stream of values that are being asynchronously computed, we can use a `Flow<Int>` type just like we would the `Sequence<Int>` type for synchronously computed values:

```kotlin
suspend fun foo(): List<Int> {
    delay(1000) // pretend we are doing something asynchronous here
    return listOf(1, 2, 3)
}

fun main() = runBlocking<Unit> {
    foo().forEach { value -> println(value) } 
}
```

```kotlin
fun foo(): Flow<Int> = flow { // flow builder
    for (i in 1..3) {
        delay(100) // pretend we are doing something useful here
        emit(i) // emit next value
    }
}

fun main() = runBlocking<Unit> {
    // Launch a concurrent coroutine to check if the main thread is blocked
    launch {
        for (k in 1..3) {
            println("I'm not blocked $k")
            delay(100)
        }
    }
    // Collect the flow
    foo().collect { value -> println(value) } 
}

// Result:
// I'm not blocked 1
// 1
// I'm not blocked 2
// 2
// I'm not blocked 3
// 3
```

- A builder function for `Flow` type is called `flow`.
- Code inside the `flow { ... }` builder block can suspend.
- The function `foo()` is no longer marked with `suspend` modifier.
- Values are emitted from the flow using `emit` function.
- Values are collected from the flow using `collect` function.

> We can replace `delay` with `Thread.sleep` in the body of foo's `flow { ... }` and see that the main thread is blocked in this case.

Flows are cold streams similar to sequences — the code inside a flow builder does not run until the flow is collected.

> **Hot Observables**: are ones that are pushing event when you are not subscribed to the observable. Like mouse moves, or Timer ticks or anything like that.
>
> **Cold Observables**: are ones that start pushing only when you subscribe, and they start over if you subscribe again.

### Scope Functions
functions whose sole purpose is to execute a block of code within the context of an object without its name.
There are five of them: `let`, `run`, `with`, `apply`, and `also`.

There are two main differences between each scope function:
- The way to refer to the context object
- The return value.

Each scope function uses one of two ways to access the context object: as a lambda receiver (`this`) or as a lambda argument (`it`).

`run`, `with`, and `apply` refer to the context object as a lambda receiver - by keyword `this`.

```kotlin
val adam = Person("Adam").apply { 
    age = 20 // same as this.age = 20 or adam.age = 20
    city = "London"
}
println(adam)
```

`let` and `also` have the context object as a lambda argument. If the argument name is not specified, the object is accessed by the implicit default name `it`.

```kotlin
fun getRandomInt(): Int {
    return Random.nextInt(100).also {
        writeToLog("getRandomInt() generated value $it")
    }
}

val i = getRandomInt()
```

The scope functions differ by the result they return:
- `apply` and `also` return the context object.
- `let`, `run`, and `with` return the lambda result.

```kotlin
val numberList = mutableListOf<Double>()
numberList.also { println("Populating the list") }
    .apply {
        add(2.71)
        add(3.14)
        add(1.0)
    }
    .also { println("Sorting the list") }
    .sort()
```

```kotlin
val numbers = mutableListOf("one", "two", "three")
val countEndsWithE = numbers.run { 
    add("four")
    add("five")
    count { it.endsWith("e") }
}
println("There are $countEndsWithE elements that end with e.")
```

| Function | Object reference | Return value | Is extension function |
| --- | --- | --- | --- |
| let | it | Lambda result | Yes |
| run | this | Lambda result | Yes |
| run | - | Lambda result | No: called without the context object |
| with | this | Lambda result | No: takes the context object as an argument. |
| apply | this | Context object | Yes |
| also | it | Context object | Yes |

Here is a short guide for choosing scope functions depending on the intended purpose:

- Executing a lambda on non-null objects: `let`
- Introducing an expression as a variable in local scope: `let`
- Object configuration: `apply`
- Object configuration and computing the result: `run`
- Running statements where an expression is required: non-extension `run`
- Additional effects: `also`
- Grouping function calls on an object: `with`

