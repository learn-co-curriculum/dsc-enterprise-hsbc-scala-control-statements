
# Control Statements

## `if`, `else if`, `else` imperative

Scala programmers often do not use var although that is not quite exactly a hard rule.

This is imperative style code and thus not common or preferred. `if` statements can be made imperatively, but will often require a mutable variable `var`. *_NOTE: This is not Scala convention_*


```scala
val a = 10
var result = "" // var is usually a code smell
if (a < 10) {
  result = "Less than 10"
} else if (a > 10) {
  result = "Greater than 10"
} else {
  result = "It is 10!"
}
```

## `if`, `else if`, `else` functional

What is different about `if` statements in Scala as well as other functions is that they are assignable

In this case we are assigning to result, a `val`

Arguably, cleaner and concise code.


```scala
val a = 10
val result = if (a < 10) "Less than 10"
             else if (a > 10) "Greater than 10"
             else "It is 10!"
```

NOTE: There is no "ternary" operator in Scala. This is as close as you'll get.

## `while` loops

* Nearly the same as in Java
* Imperative Style
* Runs the code within the block until there the boolean condition becomes `false`
* Not used as much by Scala programmers, unless
  * You are writing APIs
  * Using a mutable collection
  * A few other rare occasions


```scala
var a = 10
var result = "" // var is usually a code smell
while (a > 0) {
   result = result + a
   if (a > 1) result = result + ","
   a = a - 1
}
result
```

For a taste of idiomatic Scala, see if you can piece together what is happening here.


```scala
(100 to 1 by -1).mkString(",") //Deliciousness!
```

## `do`-`while` loops

* Nearly the same as in Java
* Imperative Style
* Runs the code within the block until there the boolean condition becomes false
* At least runs once
* Not used as much by Scala programmers


```scala
var a = 10 // var is usually a code smell
var result = ""
do {
   result = result + a
   if (a > 1) result = result + ","
   a = a - 1
} while (a > 0)
```

## `for` loops

* You can still perform the classic idea of a for-loop
* Often underused in the Scala community
* Replaced in favor of _for comprehensions_


```scala
var result = "" // var is usually a code smell
for (a <- 1 to 10) { // a for loop
   if (a != 1) result = result + ","
   result = result + a
}
```

The above was useless since it can be written concisely with the following.


```scala
(1 to 10).mkString(",")
```

## `for` comprehensions
For the flavor of `for` comprehensions here is an example using a collection type called a `List`.


```scala
for (i <- List(1,2,3,4)) yield (i * 2)
```

This has very little relation to its cousin `for` loop. The above says "for every element in this collection, multiply by 2" and put it into a new collection of the same type. The same type being in this case is a `List`

## Control Statements Conclusion

* `if` statements exist like other languages except they are assignable to a `val` or `var` (preferably a `val`)
* `while`, `do`-`while` exists but are rarely used in Scala, because they cause the programmer to resort to variables (`var`)
* `for`-loops are also available, those too are underused, we use `for`-comprehensions in favor of `for`-loops
