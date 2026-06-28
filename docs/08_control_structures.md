# 🔀 Control Structures

> **Author:** RP &nbsp;|&nbsp; [@priyasaivasan](https://github.com/priyasaivasan)

---

# Part 1 — Understanding the Concept

## What Are Control Structures?

By default, R reads your code from top to bottom, one line at a time, and executes each line in order. But most real problems aren't that simple — you need to make decisions, repeat tasks, or skip steps depending on the situation.

**Control structures** are the tools that let you change this default flow. They answer questions like:

- *"Should I do this or that?"* → **if / else**
- *"Do this for each item in a list"* → **for loop**
- *"Keep doing this until something changes"* → **while loop**
- *"Stop the loop early"* → **break**
- *"Skip this one and continue"* → **next**

Mastering control structures is what takes you from writing isolated one-line calculations to writing programs that can actually make decisions and automate repetitive tasks.

---

## if / else — Making Decisions

The `if / else` statement lets R choose between two (or more) paths based on whether a condition is `TRUE` or `FALSE`.

### Structure

```r
if (condition) {
  # this block runs when condition is TRUE
} else if (another_condition) {
  # this block runs when the first is FALSE but this is TRUE
} else {
  # this block runs when everything above is FALSE
}
```

**The curly braces `{ }` define a block of code.** Everything inside the braces belongs to that branch. The `else if` and `else` parts are optional — you can have just an `if` on its own.

### How R Evaluates Conditions

The condition inside `if ( )` must evaluate to either `TRUE` or `FALSE`. Common comparisons:

| Operator | Meaning | Example |
|----------|---------|---------|
| `==` | Equal to | `grade == 90` |
| `!=` | Not equal to | `status != "fail"` |
| `>` | Greater than | `score > 75` |
| `<` | Less than | `age < 18` |
| `>=` | Greater than or equal | `marks >= 50` |
| `<=` | Less than or equal | `temp <= 0` |
| `&` | AND — both must be true | `x > 0 & x < 100` |
| `\|` | OR — at least one must be true | `grade == "A" \| grade == "B"` |

### The Vectorised `ifelse()`

The regular `if / else` works on a **single value**. When you need to apply a condition to an entire vector (all elements at once), use `ifelse()`:

```r
ifelse(condition_vector, value_if_true, value_if_false)
```

This is extremely useful when working with data — applying a label or category to many values in one go.

---

## for Loop — Repeating a Fixed Number of Times

A `for` loop repeats a block of code **once for each item in a sequence**. You know in advance how many times it will run — it goes through every item in the sequence and stops when it reaches the end.

### Structure

```r
for (variable in sequence) {
  # code to run for each item
}
```

The `variable` (often called `i` by convention, but it can be anything) takes on the value of each item in `sequence` one by one. After the last item, the loop ends and R moves on to the next line after the closing `}`.

### What Can You Loop Over?

- A numeric range: `for (i in 1:10)` — runs 10 times, i = 1, 2, ..., 10
- A vector: `for (name in students)` — runs once per student
- Any sequence created with `seq()` or `c()`

### Accumulating Results Inside a Loop

A very common pattern is to start with an empty result and build it up inside a loop:

```r
total <- 0
for (i in 1:5) {
  total <- total + i
}
total
# [1] 15
```

---

## while Loop — Repeating Until a Condition Changes

A `while` loop keeps running **as long as a condition remains TRUE**. Unlike a `for` loop, you don't always know in advance how many times it will run — it runs until something inside the loop causes the condition to become `FALSE`.

### Structure

```r
while (condition) {
  # code to run
  # something here must eventually make the condition FALSE
}
```

**Important:** If the condition never becomes `FALSE`, the loop runs forever — this is called an **infinite loop** and it will freeze R. Always make sure something inside the loop eventually breaks the condition.

`while` loops are typically used when:
- You're waiting for user input
- You're searching for something and don't know where it is
- You're repeating until a threshold is reached

---

## break and next — Fine-Tuning Loop Behaviour

These two keywords give you control over what happens mid-loop:

### `break` — Exit the Loop Early

When R hits a `break`, it immediately stops the entire loop and moves to the next line of code after it. Useful when you've found what you're looking for and don't need to continue.

### `next` — Skip This Iteration

When R hits `next`, it skips the rest of the current loop iteration and jumps to the next one. Useful for ignoring certain values without stopping the whole loop.

---

## Quick Reference

| Structure | Use when |
|-----------|----------|
| `if / else` | Making a decision based on a condition |
| `ifelse()` | Applying a condition to an entire vector |
| `for` | You know how many times to repeat |
| `while` | You repeat until something changes |
| `break` | Exit a loop early |
| `next` | Skip one iteration and continue |

> 💡 **R Tip:** Loops are great for learning logic, but R is designed for **vectorised operations** — once you're comfortable, you'll find that many loops can be replaced with a single line using functions like `sapply()`, `lapply()`, or `ifelse()`. These are faster and considered more R-idiomatic.

---

# Part 2 — Hands-On

## Try These in RStudio

### if / else

![If/Else in RStudio Console](../screenshots/09_ifelse.png)

```r
# Grade classification
grade <- 72

if (grade >= 90) {
  print("A — Excellent")
} else if (grade >= 75) {
  print("B — Good")
} else if (grade >= 60) {
  print("C — Satisfactory")
} else {
  print("F — Needs Improvement")
}
# [1] "C — Satisfactory"
```

```r
# Checking if a number is even or odd
x <- 17
if (x %% 2 == 0) {
  print("Even")
} else {
  print("Odd")
}
# [1] "Odd"
```

```r
# ifelse() on a whole vector
scores <- c(85, 60, 92, 45, 78)
ifelse(scores >= 75, "Pass", "Fail")
# [1] "Pass" "Fail" "Pass" "Fail" "Pass"
```

### for Loop

![For Loop in RStudio Console](../screenshots/10_forloop.png)

```r
# Squares of 1 to 5
for (i in 1:5) {
  cat("Square of", i, "is", i^2, "\n")
}
# Square of 1 is 1
# Square of 2 is 4
# Square of 3 is 9
# Square of 4 is 16
# Square of 5 is 25
```

```r
# Looping over a character vector
fruits <- c("apple", "banana", "cherry")
for (fruit in fruits) {
  cat("I enjoy", fruit, "\n")
}
# I enjoy apple
# I enjoy banana
# I enjoy cherry
```

```r
# Accumulating a sum
total <- 0
for (n in 1:10) {
  total <- total + n
}
total
# [1] 55   — sum of 1 through 10
```

### while Loop

```r
# Count down from 5
count <- 5
while (count > 0) {
  cat(count, "")
  count <- count - 1
}
# 5 4 3 2 1
```

```r
# Double a number until it exceeds 100
value <- 1
while (value <= 100) {
  value <- value * 2
}
value
# [1] 128
```

### break and next

```r
# break — stop when we hit 5
for (i in 1:10) {
  if (i == 5) break
  cat(i, "")
}
# 1 2 3 4

# next — skip even numbers
for (i in 1:8) {
  if (i %% 2 == 0) next
  cat(i, "")
}
# 1 3 5 7
```

---

# Part 3 — Exercises

---

## ### Exercise 1 — Grade Classifier

> **Write an `if / else` block that takes a score stored in a variable `marks` and prints:**
> - `"Distinction"` if marks >= 85
> - `"First Class"` if marks >= 60
> - `"Pass"` if marks >= 40
> - `"Fail"` otherwise
>
> **Test it with `marks <- 67`.**

&nbsp;

&nbsp;

&nbsp;

```r
marks <- 67

if (marks >= 85) {
  print("Distinction")
} else if (marks >= 60) {
  print("First Class")
} else if (marks >= 40) {
  print("Pass")
} else {
  print("Fail")
}
# [1] "First Class"
```

---

## ### Exercise 2 — Vectorised Labels

> **You have a vector of temperatures: `c(22, 38, 15, 41, 29)`. Use `ifelse()` to label each as `"Hot"` if above 30, and `"Cool"` otherwise.**

&nbsp;

&nbsp;

&nbsp;

```r
temps <- c(22, 38, 15, 41, 29)
ifelse(temps > 30, "Hot", "Cool")
# [1] "Cool" "Hot"  "Cool" "Hot"  "Cool"
```

---

## ### Exercise 3 — for Loop with Accumulation

> **Use a `for` loop to calculate the sum of all even numbers from 1 to 20. Print the result.**

&nbsp;

&nbsp;

&nbsp;

```r
total <- 0
for (i in 1:20) {
  if (i %% 2 == 0) {
    total <- total + i
  }
}
total
# [1] 110
# (2 + 4 + 6 + ... + 20 = 110)
```

---

## ### Exercise 4 — while Loop

> **Start with `n <- 1`. Keep multiplying `n` by 3 using a `while` loop until `n` exceeds 500. What is the final value of `n`?**

&nbsp;

&nbsp;

&nbsp;

```r
n <- 1
while (n <= 500) {
  n <- n * 3
}
n
# [1] 729
# (1 → 3 → 9 → 27 → 81 → 243 → 729)
```

---

## ### Exercise 5 — break in Action

> **Loop through numbers 1 to 100. Print each number, but stop the loop as soon as you hit a number divisible by both 7 and 11. What is that number?**

&nbsp;

&nbsp;

&nbsp;

```r
for (i in 1:100) {
  if (i %% 7 == 0 & i %% 11 == 0) {
    cat("Found:", i, "\n")
    break
  }
  cat(i, "")
}
# 1 2 3 4 ... 76 Found: 77
```

---

## ⬅️ [Back: Functions](07_functions.md) &nbsp;|&nbsp; [🏠 Back to Home](../README.md)
