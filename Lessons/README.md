# Here's a 7-day Scala learning roadmap, with examples each day, designed for a quick start. This assumes you have some prior programming experience.

---

### 🚀 Day 1: Getting Started with Scala - Basics & REPL

**Focus:** Introduction to Scala syntax, variables, data types, basic operations, and the Scala REPL (Read-Eval-Print Loop).

**Concepts:**
* **`val` vs. `var`**: Immutable vs. mutable variables.
* Basic data types: `Int`, `Double`, `String`, `Boolean`.
* Arithmetic operations.
* Printing to console.
* Scala REPL usage.

**Example:**

```scala
// Day 1 Example: Basics and REPL

// Declare immutable variable (preferred)
val greeting: String = "Hello, Scala!"
println(greeting)

// Declare mutable variable (use sparingly)
var age: Int = 30
println(s"My age is: $age")
age = 31 // Can reassign var
println(s"My new age is: $age")

// Basic arithmetic
val num1: Int = 10
val num2: Int = 5
val sum: Int = num1 + num2
println(s"Sum: $sum")

// String interpolation
val name: String = "Alice"
val message: String = s"Welcome, $name!"
println(message)

// Try this in Scala REPL:
// scala> val x = 10
// scala> val y = 20
// scala> x + y
```

---

### 🚦 Day 2: Control Structures & Functions

**Focus:** Understanding how to control program flow and write reusable blocks of code.

**Concepts:**
* **`if/else`** statements.
* **`for` loops** (comprehensions).
* **`while` loops** (less common in idiomatic Scala).
* **Functions**: defining, parameters, return types, higher-order functions (brief intro).

**Example:**

```scala
// Day 2 Example: Control Structures & Functions

// If/Else
val score: Int = 85
if (score >= 90) {
  println("Excellent!")
} else if (score >= 70) {
  println("Good!")
} else {
  println("Needs improvement.")
}

// For loop (comprehension)
println("Numbers from 1 to 5:")
for (i <- 1 to 5) {
  println(i)
}

// For loop with filter and yield (powerful!)
val numbers = List(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
val evenNumbers = for {
  num <- numbers
  if num % 2 == 0
} yield num
println(s"Even numbers: $evenNumbers")

// Function definition
def add(a: Int, b: Int): Int = {
  a + b
}
println(s"2 + 3 = ${add(2, 3)}")

// Function with no parameters
def greet(): String = {
  "Hello!"
}
println(greet())

// Higher-order function (brief intro)
def applyOperation(x: Int, y: Int, op: (Int, Int) => Int): Int = {
  op(x, y)
}
val multiply = (a: Int, b: Int) => a * b
println(s"Applying multiply: ${applyOperation(4, 5, multiply)}")
```

---

### 📚 Day 3: Collections - Lists, Arrays, Maps, Sets

**Focus:** Working with Scala's rich and **immutable collection library**, which is a cornerstone of functional programming in Scala.

**Concepts:**
* **`List`**, `Array`, `Vector`.
* **`Map`**.
* **`Set`**.
* Common collection methods: `map`, `filter`, `reduce`, `foreach`, `find`.
* **Immutability of collections**.

**Example:**

```scala
// Day 3 Example: Collections

// Lists (immutable, linked list)
val colors = List("red", "green", "blue")
println(s"Colors: $colors")
println(s"First color: ${colors.head}")
println(s"Remaining colors: ${colors.tail}")

// Adding to a list (creates a new list)
val newColors = "yellow" :: colors // Prepending
println(s"New colors: $newColors")

// Arrays (mutable, fixed-size)
val numbersArray = Array(1, 2, 3, 4, 5)
println(s"Array element at index 2: ${numbersArray(2)}")
numbersArray(2) = 10 // Arrays are mutable
println(s"Modified array: ${numbersArray.mkString(", ")}")

// Maps (immutable key-value pairs)
val ages = Map("Alice" -> 30, "Bob" -> 25, "Charlie" -> 35)
println(s"Bob's age: ${ages("Bob")}")
println(s"All keys: ${ages.keys}")
println(s"All values: ${ages.values}")

// Sets (immutable, unique elements)
val uniqueNumbers = Set(1, 2, 2, 3, 4, 4, 5)
println(s"Unique numbers: $uniqueNumbers")
println(s"Does set contain 3? ${uniqueNumbers.contains(3)}")

// Common collection methods
val prices = List(10.5, 20.0, 15.75)
val doubledPrices = prices.map(price => price * 2)
println(s"Doubled prices: $doubledPrices")

val total = prices.reduce((acc, price) => acc + price)
println(s"Total price: $total")

prices.foreach(price => println(s"Price: $price"))

val foundPrice = prices.find(price => price > 15)
println(s"Found price > 15: $foundPrice") // Option[Double]
```

---

### 🧩 Day 4: Object-Oriented Programming (OOP) in Scala

**Focus:** Understanding Scala's take on OOP, which integrates well with functional paradigms.

**Concepts:**
* **Classes and Objects**.
* Constructors.
* Methods.
* Inheritance and Traits.
* **Case Classes** (very common and powerful).

**Example:**

```scala
// Day 4 Example: Object-Oriented Programming

// Class definition
class Person(val name: String, var age: Int) {
  def sayHello(): Unit = {
    println(s"Hello, my name is $name and I am $age years old.")
  }
}

val person1 = new Person("David", 28)
person1.sayHello()
person1.age = 29 // 'age' is a var
person1.sayHello()

// Case Classes (ideal for data modeling)
// Automatically generates equals, hashCode, toString, and companion object
case class Book(title: String, author: String, year: Int)

val book1 = Book("The Hitchhiker's Guide to the Galaxy", "Douglas Adams", 1979)
val book2 = Book("The Hitchhiker's Guide to the Galaxy", "Douglas Adams", 1979)

println(s"Book 1: $book1")
println(s"Are book1 and book2 equal? ${book1 == book2}") // True due to case class equality

// Inheritance
class Animal(val species: String) {
  def makeSound(): Unit = {
    println("Generic animal sound.")
  }
}

class Dog(name: String) extends Animal("Canine") {
  override def makeSound(): Unit = {
    println(s"Woof! My name is $name.")
  }
}

val myDog = new Dog("Buddy")
myDog.makeSound()
println(s"Dog species: ${myDog.species}")

// Traits (like interfaces in Java but with implemented methods)
trait Greeter {
  def greet(name: String): Unit = {
    println(s"Greetings, $name!")
  }
}

class User(val username: String) extends Greeter

val user1 = new User("ScalaLearner")
user1.greet(user1.username)
```

---

### ✨ Day 5: Functional Programming Concepts

**Focus:** Diving deeper into Scala's functional programming capabilities, which are crucial for writing concise, robust, and concurrent code.

**Concepts:**
* **Immutability**.
* First-class functions (functions as values).
* **Higher-order functions** (revisited: `map`, `filter`, `fold/reduce`).
* Lambda expressions (anonymous functions).
* Currying.
* **`Option` type** (handling nulls gracefully).

**Example:**

```scala
// Day 5 Example: Functional Programming Concepts

// Immutability (revisited)
// Emphasize that most Scala collections are immutable
val immutableList = List(1, 2, 3)
// immutableList(0) = 10 // This would be a compilation error

// Functions as first-class citizens
val multiplyByTwo = (x: Int) => x * 2
println(s"Multiply by two (5): ${multiplyByTwo(5)}")

// Higher-order function with lambda
val numbersForFP = List(1, 2, 3, 4, 5)
val squaredNumbers = numbersForFP.map(x => x * x)
println(s"Squared numbers: $squaredNumbers")

val sumOfNumbers = numbersForFP.foldLeft(0)((acc, num) => acc + num)
println(s"Sum of numbers: $sumOfNumbers")

// Currying (functions that return functions)
def addCurried(a: Int)(b: Int): Int = a + b
val addFive = addCurried(5)_ // Partially applied function
println(s"Add five to 10: ${addFive(10)}")

// Option Type: Handling potential absence of a value (safer than null)
val someValue: Option[String] = Some("Hello")
val noValue: Option[String] = None

println(s"Value from someValue: ${someValue.getOrElse("Default")}")
println(s"Value from noValue: ${noValue.getOrElse("Default")}")

someValue.foreach(value => println(s"Found: $value")) // Only executes if Some
noValue.foreach(value => println(s"Found: $value"))   // Does not execute

val lengthOfValue = someValue.map(_.length)
println(s"Length of someValue: $lengthOfValue") // Some(5)
val lengthOfNoValue = noValue.map(_.length)
println(s"Length of noValue: $lengthOfNoValue") // None
```

---

### 🔍 Day 6: Pattern Matching & Error Handling

**Focus:** Powerful features for deconstructing data and handling different scenarios, including errors.

**Concepts:**
* **`match` expressions**.
* Matching on data types, values, and case classes.
* `Try`, `Success`, `Failure` for error handling.
* `Either` for representing success or failure.

**Example:**

```scala
// Day 6 Example: Pattern Matching & Error Handling

// Pattern Matching
def describe(x: Any): String = x match {
  case 1 => "One"
  case "hello" => "A string saying hello"
  case i: Int if i > 10 => s"An integer greater than 10: $i"
  case s: String => s"A string: $s"
  case list: List[_] => s"A list of length ${list.length}"
  case _ => "Something else" // Default case
}

println(describe(1))
println(describe("hello"))
println(describe(15))
println(describe("Scala"))
println(describe(List(1, 2, 3)))
println(describe(true))

// Pattern matching with Case Classes
case class PersonData(name: String, age: Int)

val personData1 = PersonData("Bob", 40)
val personData2 = PersonData("Alice", 25)

def greetPerson(p: PersonData): String = p match {
  case PersonData(name, age) if age < 30 => s"Hi, young $name!"
  case PersonData(name, _) => s"Hello, $name."
}

println(greetPerson(personData1))
println(greetPerson(personData2))

// Error Handling with Try
import scala.util.{Try, Success, Failure}

def divide(a: Int, b: Int): Try[Int] = Try {
  a / b
}

println(divide(10, 2)) // Success(5)
println(divide(10, 0)) // Failure(java.lang.ArithmeticException: / by zero)

divide(10, 2) match {
  case Success(result) => println(s"Division successful: $result")
  case Failure(ex) => println(s"Division failed: ${ex.getMessage}")
}

// Error Handling with Either (Left for error, Right for success)
def divideEither(a: Int, b: Int): Either[String, Int] = {
  if (b == 0) Left("Cannot divide by zero")
  else Right(a / b)
}

println(divideEither(10, 2)) // Right(5)
println(divideEither(10, 0)) // Left(Cannot divide by zero)

divideEither(10, 0) match {
  case Right(result) => println(s"Result: $result")
  case Left(error) => println(s"Error: $error")
}
```

---

### ☁️ Day 7: Concurrency & Build Tools (SBT)

**Focus:** A brief introduction to Scala's approach to concurrency and how to build Scala projects using SBT.

**Concepts:**
* **Futures** (asynchronous computation).
* Basic concepts of concurrency (non-blocking operations).
* **SBT (Scala Build Tool)**: project structure, running, compiling.

**Example:**

```scala
// Day 7 Example: Concurrency & SBT Basics

// Futures for asynchronous computation
import scala.concurrent.{Future, Await}
import scala.concurrent.duration._
import scala.concurrent.ExecutionContext.Implicits.global // Import default thread pool

println("Starting long-running operation...")

val futureResult: Future[Int] = Future {
  // Simulate a long computation
  Thread.sleep(2000)
  val result = 42
  println("Computation finished.")
  result
}

// Attach a callback to be executed when the Future completes
futureResult.onComplete {
  case Success(res) => println(s"Future completed with result: $res")
  case Failure(ex) => println(s"Future failed with exception: ${ex.getMessage}")
}

// Block until the future completes (for demonstration, avoid in real async code)
// Await.result(futureResult, 3.seconds) // Blocks for max 3 seconds

println("Main thread continues while future is running...")
// In a real application, you'd typically compose Futures or use Akka.

// --- SBT (Scala Build Tool) Basics ---
// This part is about setting up your project, not runnable code.

// 1. Create a new directory for your project:
//    mkdir my-scala-project
//    cd my-scala-project

// 2. Create a 'build.sbt' file in the root of your project:
//    echo 'name := "MyScalaProject"
//    version := "0.1"
//    scalaVersion := "2.13.12"' > build.sbt

// 3. Create a 'src/main/scala' directory:
//    mkdir -p src/main/scala

// 4. Create your Scala source file (e.g., 'src/main/scala/Main.scala'):
//    ```scala
//    // src/main/scala/Main.scala
//    object Main {
//      def main(args: Array[String]): Unit = {
//        println("Hello from SBT-managed Scala project!")
//      }
//    }
//    ```

// 5. Navigate to your project directory in the terminal and run SBT commands:
//    sbt compile     // Compiles your project
//    sbt run         // Runs your main object
//    sbt console     // Opens the Scala REPL with your project's dependencies
//    sbt clean       // Cleans compiled files

println("\nSBT instructions provided in comments above. This code doesn't execute SBT commands.")
println("To truly experience Day 7, you need to set up a project with SBT.")

Thread.sleep(3000) // Keep the main thread alive to see Future output
```

---

**Important Notes for this 7-Day Journey:**

* **Practice is Key**: The examples are starting points. Modify them, break them, and try to solve small problems using the concepts learned each day.
* **Immutability First**: Embrace immutability. It makes code safer and easier to reason about, especially in concurrent environments.
* **Functional Thinking**: Start thinking about transformations of data rather than mutable state changes.
* **Error Handling**: Use `Option`, `Try`, and `Either` consistently to avoid `NullPointerExceptions` and handle failures explicitly.
* **Community**: The Scala community is vast. Don't hesitate to look up documentation or ask questions online.
* **Beyond 7 Days**: This is just the beginning. Scala has much deeper topics like Akka (actor concurrency), Spark (big data), Cats/Scalaz (pure functional programming), Macros, etc.
* **IDE**: An IDE like **IntelliJ IDEA with the Scala plugin** greatly enhances the development experience (autocomplete, error highlighting, refactoring).

Good luck with your Scala journey! What specific aspect of Scala interests you most for a deeper dive?