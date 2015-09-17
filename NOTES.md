Scala notes
-----------

Notes from short video course about Scala covering basics of Scala programming language

References:
- https://www.youtube.com/watch?v=DzFt0YkZo8M
- http://www.newthinktank.com/2015/08/learn-scala-one-video/

Contents
--------
- [Compiling and executing programs](#compiling-and-executing-programs)
- [Values and variables](#values-and-variables)
- [Comments](#comments)
- [Data types](#data-types)
- [Math](#math)
- [Conditional statements](#conditional-statements)
- [Loops](#loops)
- [User's input/output](#users-inputoutput)
- [Strings](#strings)
- [Functions](#functions)
- [Recursion](#recursion)
- [Arrays](#arrays)
- [Maps](#maps)
- [Tuples](#tuples)
- [Classes](#classes)
- [Traits](#traits)
- [Higher order functions](#higher-order-functions)
- [Map](#map)
- [Filter](#filter)
- [Closures](#closures)
- [File I/O](#file-io)
- [Exception handling](#exception-handling)

Compiling and executing programs
--------------------------------

Compiling

```
scalac hello.scala
```

Running without compilation:

```
scala hello.scala
```

Values and variables
--------------------

```scala
var a = 1 // variable "a", which CAN be changed
val b = 2 // value "b", which CAN NOT be changed
```

### Incrementation and decrementation

`++` and `--` operators don't work

```scala
someVar += 1
someVar -= 1
```

Comments
--------

Same as Java

```scala
// one line comment

/* comment
   in many lines */
```

Data types
----------

```
String, Byte, Boolean, Char, Short, Int, Long, Float, Double
```

Math
----

In order to use math function, we need the following import

```scala
import scala.math._
```

sample math functions:

```scala
round(...), floor(...), ceil(...), hypot(...),
exp(...)  , pow(...)  , sqrt(...), abs(...),
min(...)  , max(...)  , log(...) , log10(...),
toRadians(...), toDegrees(...)

// generating random numbers

(random * (11 - 1) + 1).toInt
```

Conditional statements
----------------------

Same as Java

Conditional operators: `== != > < >= <=`
Logical operators: `&& || !`

Sample statement:

```scala
val canVote = if(age >= 18) "yes" else "no"
```

```scala
if(...) {
  ...
} else {
  ...
}
```

Loops
-----

while:

```scala
while(...) {
  ...
}
```

do while:

```scala
do {
  ...
} while(...)
```

for:

numbers:

```scala
for( i <- 1 to 10)
  println(i)
```

letters:

```scala
val randLetters = "ABCDEFGHIJ"

for( i <- 0 until randLetters.length)
  println(randLetters(i))
```

list:

```scala
val aList = List(1,2,3,4,5)
for(i <- aList) {
 println("item: " + i)
}
```

filtering list:

```scala
var i = 0

var evenList = for { i <- 1 to 20
  if (i % 2) == 0
  } yeild i

for(i <- evenList)
  println(i)
```

iterate through multiple variables:

```scala
var i = 0

for(i <- 1 to 5; j <- 6 to 10) {
  println("i: " + i)
  println("j: " + j)
}
```

There's no `break` and `continue` in Scala, but we can implement them:

```scala
for(i <- primeList) {
  if(i == 11) {
    return // implementation of break
  }

  if( i != 1) {
    println(i) // implementation of continue
  }

}
```

User's input/output
-----------------

```scala
import scala.io.StdIn.{readLine, readInt}
import scala.math._

var guessNumber = 0

do {
  print("Guess a number ")
  numberGuess = readLine.toInt
} while(numberGuess != 15)

printf("You guessed the secret number %d\n", 15)
```

```scala
val name = "Piotr"
val age = 26
val weight = 174.2

println(s"Hello $name")
println(f"I am ${age + 1} and weight $weight%.2f")
```

`%c` for characters, `%d` for integers, `%f` for floats and `%s` for Strings.

```scala
printf("'%5d'\n", 5)  	// five spaces on the left
printf("'%-5d'\n", 5) 	// five spaces on the right
printf("'%-5s'\n" "hi") // five spaces on the right (from String)
printf("'%05d'\n", 5) 	// zero fill on the left
printf("$.5f'\n", 3.14) // five decimal places: 3.14000
```

special characters: `\n` for new line, `\b` for backspace, `\\` for backslash

Strings
-------

```scala
var str = "I saw a dragon fly by"
println("character: " + str(3))
println("length: " + str.length)
println(str.concat(" and explode"))
println("are strings equal " + "I saw a dragon".equals(str))
println("dragon starts at: " + str.indexOf("dragon"))
```

converting string to array:

```scala
val strArr = str.toArray

for(v <- strArr)
  println(v)
```

Functions
---------

definition of function:

```scala
def funcName(param1:dataType, param2:dataType) : returnType = {
  // function body
  // return valueToReturn (optional)
}
```

function with parameters

```scala
def getSum(num1: Int = 1, num2: Int = 1): Int = {
  return num1 + num2
}

println("5 + 4 = " + getSum(5,4))
println("5 + 4 = " + getSum(num2=5,num1=4))
```

function without parameters

```scala
def sayHi() : Unit = {
  println("Hi, how are you?")
}

sayHi

```

function where number of parameters is varying

```scala
def getSum(args: Int*) : Int = {
  var sum : Int = 0
  for(num <- args) {
    sum += num
  }
  sum
}

println("Get sum " + getSum(1,2,3,4,5))
```

Recursion
---------

```scala
def factorial(num: BigInt) : BigInt = {
  if(num <= 1)
    1
  else
    num * factorial(num - 1)
}

println("factorial of 4 = " + factorial(4))
```

Arrays
------

```scala
val favNums = new Array[Int](20)
val friends = Array("Bob", "Tom")
friends(0) = "Sue"
println(friends(0))

// array buffers

val friends2 = ArrayBuffer[String]()
friends2.insert(0, "Phil")
friends2 += "Mark"
friends ++= Array("Susy", "Paul")
friends2.insert(1, "Mike", "Sally", "Sam")
friends2.remove(1, 2) // two elements starting at the second index

var friend : String = " "

for(friend <- friends2)
  println(friend)


for( j <- 0 to (favNums.length - 1)) {
  favNums(j) = j
  println(favNums(j))
}

val favNumsTimes2 = for(num <- favNums) yield 2 * num
favNumsTimes2.foreach(println)

var favNumsDiv4 = for(num <- favNums if num % 4 == 0) yield num
favNumsDiv4.foreach(println)

var multTable = Array.ofDim[Int](10,10) // multi-dimensional array

for(i <- 0 to 9) {
  for(j <- 0 to 9) {
    multTable(i)(j) = i * j
  }
}

for(i <- 0 to 9) {
  for(j <- 0 to 9) {
    printf("%d : %d = %d\n", i, j, multTable(i)(j))
  }
}

println("Sum: " + favNums.sum)
println("Min: " + favNums.min)
println("Max: " + favNums.max)

val sortedNums = favNums.sortWith(_>_) // descending sorting order

println(sortedNums.deep.mkString(", "))
```

Maps
----

```scala
// immutable map
val employees = Map("Manager" -> "Bob Smith", "Secretary" -> "Sue Brown")

if(employees.contains("Manager"))
  printf("Manager: %s\n", employees("Manager"))

// mutable map

val customers = collection.mutable.Map(100 -> "Paul Smith", 101 -> "Sally Smith")

printf("Cust 1: %s\n", customers(100))

customers(100) = "Tom Marks"
customers(102) = "Megan Swift"

for((k,v) <- customers)
  printf("%d: %s\n", k, v)
```

Tuples
------

Tuples holds values of different types and are normally immutable

```scala
// creating tuple
var tupleMarge = (103, "Marge Simpson", 10.25)

// printing values of tuple
printf("%s owes us $%.2f\n", tupleMarge._2, tupleMarge._3)

// iterating through tuple
tupleMarge.productIterator.foreach{ i => println(i)}

// converting tuple to a String
println(tupleMarge.toString())
```

Classes
-------

```scala
class Animal(var name: String, var sound: String) {
  this.setName(name)

  val id = Animal.nweIdNum

  // protected var name = "No Name"

  def getName() : String = name
  def getSound() : String = sound

  def setName(name: String) {
    if(!(name.matches(".*\\d+.*")))  // does not contain any decimals and numbers
      this.name = name
    else
      this.name = "No Name"
  }

  def setSound(sound: String) {
    this.sound = sound
  }

  // constructor
  def this(name: String) {
    this("No Name", "No Sound")
    this.setName(name)
  }

  // constructor
  def this() {
    thi("No Name", "No Sound")
  }

  // overriding methods
  override def toString() : String = {
    return "%s with the id %d says %s".format(this.name, this.id, this.sound)
  }
}

// static fields and static functions
object Animal {
  private var idNumber = 0
  private def newIdNum = { idNumber += 1; idNumber}  
}

// creating objects (instances of classes)

val rover = new Animal
rover.setName("Rover")
rover.setSound("Woof")
printf("%s says %s\n", rover.getName, rover.getSound)

val whiskers = new Animal("Whiskers", "Meow")
println(s"${whiskers.getName} with id ${whiskers.id} says  ${whiskers.sound}")

println(whiskers.toString)

// inheritance

class Dog(name: String, sound: String, growl: String) extends Animal(name, sound) {
  def this(name: String, sound: String) {
    this("No Name", sound, "No Growl")
    this.setName(name)
  }

  def this(name: String) {
    this("No Name", "No Sound", "No Growl")
    this.setName(name)
  }

  def this() {
    this("No Name", "No Sound", "No Growl")
  }

  override def toString() : String = {
    return "%s with the id %d says %s or %s".format(this.name, this.id, this.sound, this.growl)
  }
}

val spike = new Dog("Spike", "Woof", "Grrrr")
spike.setName("Spike")
println(spike.toString)

// abstract classes

abstract class Mammal(val name: String) {
  var moveSpeed: Double
  def move: String
}

class Wolf(name: String) extends Mammal(name) {
  var moveSpeed = 35.0
  def move = "The wolf %s runs %.2f mph".format(this.name, this.moveSpeed)
}

val fang = new Wolf("Fang")
fang.moveSpeed = 36.0
println(fang.move)
```

Traits
------

It's like a Java interface, but can provide concrete methods and fields.

```scala
trait Flyable {
  def fly: String
}

trait BulletProof {
  def hitByBullet: String

  def ricochet(startSpeed: Double) : String = {
    "The bullet ricochets at a speed of %.1f ft/sec".format(startSpeed * .75)  
  }
}

class Superhero(val name: String) extends Flyable with BulletProof {
  def fly = %s flies through the air".format(this.name)
  def hitByBullet = "The bullet bounces off %s".format(this.name)
}

val superman = new Superhero("superman")
println(superman.fly)
println(superman.hitByBullet)
println(superman.ricochet(2500))
```

Higher order functions
----------------------

```scala
val log10Func = log10 _

println(log10Func(1000))

List(1000.0, 10000).map(log10Func).foreach(println)
```

Map
---

```scala
List(1,2,3,4,5).map((x : Int) => x * 50).foreach(println)
```

Filter
------

```scala
List(1,2,3,4,5).filter(_ % 2 == 0).foreach(println)

def times3(num: Int) = num * 3
def times4(num: Int) = num * 4

def multIt(func: (Int) => Double, num: Int) = {
  func(num)
}

printf("3 * 100 = %.1f\n", multIt(times4, 100))
```

Closures
--------

```scala
val disorVal = 5
val divisor5 = (num: Duble) => num / divisorVal
println("5/5= " + divisorVal(5.0))
```

File I/O
--------

Necessary imports:

```scala
import java.io.PrintWriter // to write to a file
import scala.io.Source     // to read from file
```

```scala
// writing

val writer = PrintWriter("test.txt")
writer.write("Just some random text\nSome more random text")
writer.close()

// reading

val textFromFile = Source.fromFile("test.txt", "UTF-8")
val lineIterator = textFromFile.getLines

for(line <- lineIterator)
  println(line)

textFromFile.close()
```

Exception handling
------------------

```scala
def divideNums(num1: Int, num2: Int) = try
{
  (num1/num2)
} catch {
  case ex: java.lang.ArithmeticException => "Cant't divide by zero"
} finally {
  // clean up
}

println("3 / 0 = " + divideNums(3,0))
```
