# Booleans and Conditional Statements

---

Erin R. Hoffman, February 2022

## Prerequisites

Before this lesson, students should already be able to:

* Create ***variables*** in Java, particularly integers and doubles
* Use ***expressions*** to manipulate and combine variables
* Follow the appropriate ***order of operations*** in Java expressions, including math operations

## Learning Objectives

By the end of this lesson, students will be able to:
* Define the term ***control flow*** and explain why it is a useful tool in programming
* Describe the two values of the ***boolean*** data type in Java
* Apply ***operators*** to variables in order to form ***boolean expressions***
* Utilize boolean expressions in ***conditional statements*** that determine whether or not a given ***code block*** will be executed
* Practice translating English-language word problems into conditional statements and code blocks


## The Motivation: Control Flow

When do we need control flow?

<img src="images/workflow.png" alt="three shapes with arrows going from the first to the second to the third" style="width: 20%">

<a href="https://www.flaticon.com/free-icons/workflow" title="workflow icons"><small>Workflow icons created by Uniconlabs - Flaticon</small></a>

A better question might be...when do we **not** need control flow?

## The Boolean Data Type

### Recall: What Is a Data Type?

Some data types you have seen already include:

#### Integers


```Java
// Declaring and assigning variable
int month = 12;
```


```Java
// Printing variable value
System.out.println(month);
```


```Java
// Performing math operation on variable
System.out.println(month - 2);
```


```Java
// Performing multiple math operations, with parentheses for order of operations
System.out.println((month - 2) % 2);
```

#### Doubles


```Java
// Declaring and assigning variable
double length = 1.5;
```


```Java
// Printing variable value
System.out.println(length);
```


```Java
// Performing math operation on variable
System.out.println(length * 7);
```


```Java
// Performing multiple math operations, with parentheses for order of operations
System.out.println(10 / (length + 0.5));
```

#### Boolean is another data type


```Java
boolean isSunny = true;
```


```Java
isSunny
```


```Java
boolean isRaining = false;
```


```Java
isRaining
```

<details>
    <summary style="cursor: pointer;">Clarification (click to expand)</summary>
    <p>Confusingly, there is also a wrapper object called <code>Boolean</code> (note the capital "B"). We won't be using it, but you can read the documentation <a href="https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Boolean.html">here</a> if you're curious</p>
</details>


### Boolean Data Type Recap

* A ***data type*** is something like `int` or `double`, which defines the "kind of thing" being stored in a variable
* You have just been introduced to a data type called `boolean`
* It can only have two values: `true` or `false`

Ok but...why?

## Boolean Operators and Expressions

Let's set up some example variables:


```Java
int lower = 0;
int upper = 100;
```

### Equality

*Is 5 the minimum?*


```Java
5 == lower
```

*Is the maximum 100?*


```Java
upper == 100
```

*Are the minimum and maximum the same?*


```Java
lower == upper
```

### Not

*Is 5* **not** *the minimum?*


```Java
!(5 == lower)
```


```Java
5 != lower
```

### Greater Than, Less Than

*The user has input a value of 50. Is that more than the minimum?*


```Java
50 > lower
```

*Is it less than the maximum?*


```Java
50 < upper
```

*Now the user has input 100. Is that less than the maximum?*


```Java
100 < upper
```

### Greater Than Or Equal To, Less Than Or Equal To

*What if we want to define the valid range as 0 to 100* **inclusive**_? Is 100 a valid input?_


```Java
100 >= lower
```


```Java
100 <= upper
```

### And and Or

#### And

*Can we check whether an input is valid in a single line?*


```Java
(lower <= 100) && (100 <= upper)
```


```Java
(lower <= 500) && (500 <= upper)
```


```Java
(lower <= -5) && (-5 <= lower)
```

#### Or

*What if, instead of an inclusive range, inputs are valid if they're* **either** *below the lower bound* **or** *above the upper bound?*


```Java
(100 <= lower) || (upper <= 100)
```


```Java
(500 <= lower) || (upper <= 500)
```


```Java
(-5 <= lower) || (upper <= -5)
```

### Boolean Operators and Expressions Recap

* ***Boolean expressions*** are expressions that result in a boolean, although they can (and typically do) compare non-boolean values
* ***Boolean operators*** are used to make comparisons in boolean expressions. The Java boolean operators are:
  * `==` (is equal to)
  * `!=` (is not equal to)
  * `>` (is greater than)
  * `<` (is less than)
  * `>=` (is greater than or equal to)
  * `<=` (is less than or equal to)
  * `&&` (and)
  * `||` (or)
  * `!` (not)

## Conditional Statements

Now we can finally start to implement control flow!

<img src="images/flowchart.png" alt="flowchart" style="width: 20%">

<a href="https://www.flaticon.com/free-icons/process" title="process icons"><small>Process icons created by Uniconlabs - Flaticon</small></a>

### `if`

*User input is invalid if it's smaller than the minimum.*


```Java
int userInput = -5;
```


```Java
if (userInput < lower) System.out.println("Input too small");
```

### `else if`

*User input is also invalid if it's larger than the maximum.*


```Java
if (userInput < lower) System.out.println("Input too small");
else if (userInput > upper) System.out.println("Input too big");
```


```Java
userInput = 500;
```


```Java
if (userInput < lower) System.out.println("Input too small");
else if (userInput > upper) System.out.println("Input too big");
```

### `else`

*Otherwise, user input is valid.*


```Java
if (userInput < lower) System.out.println("Input too small");
else if (userInput > upper) System.out.println("Input too big");
else System.out.println("Valid input!");
```


```Java
userInput = 75;
```


```Java
if (userInput < lower) System.out.println("Input too small");
else if (userInput > upper) System.out.println("Input too big");
else System.out.println("Valid input!");
```

### Code Blocks: The Dreaded Curly Braces


```Java
if (userInput < lower) {
    System.out.println("Input too small");
} else if (userInput > upper) {
    System.out.println("Input too big");
} else {
    System.out.println("Valid input!");
}
```

### Conditional Statements Recap

* A ***conditional statement*** = a boolean expression + `if`, `else if`, or `else` keyword
* Conditional statements determine whether a given piece of code will be executed
* Typically this code is contained in a ***code block*** surrounded by curly braces

## Practice

A tricky but exemplary conditional statement word problem is FizzBuzz, which comes from a [children's game](https://en.wikipedia.org/wiki/Fizz_buzz).

It goes like this:

* Given a number, print it out
* Except if the number is divisible by 3, print out "Fizz" instead
* And if the number is divisible by 5, print out "Buzz" instead
* Finally, if the number is divisible by both 3 and 5, print out "FizzBuzz" instead


```Java
// Given a number, print it out
// Except if the number is divisible by 3, print out "Fizz" instead
// And if the number is divisible by 5, print out "Buzz" instead
// Finally, if the number is divisible by both 3 and 5, print out "FizzBuzz" instead
```


```Java

```

## Recap

### Reviewing Learning Objectives

Now you should be able to:

* Define the term ***control flow*** and explain why it is a useful tool in programming

* Describe the two values of the ***boolean*** data type in Java

* Apply ***operators*** to variables in order to form ***boolean expressions***

* Utilize boolean expressions in ***conditional statements*** that determine whether or not a given ***code block*** will be executed

* Practice translating English-language word problems into conditional statements and code blocks

That's all, folks! Up next, another type of control flow: loops.
