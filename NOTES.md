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
- [Comments](#contents)
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

TBD.

....

