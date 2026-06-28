# 📦 Variables

> **Author:** RP &nbsp;|&nbsp; [@priyasaivasan](https://github.com/priyasaivasan)

---

# Part 1 — Understanding the Concept

## What is a Variable?

A **variable** is a named container that holds a value. Think of it like a labelled jar — you put something inside, give it a name, and whenever you need that thing again, you just use the name instead of remembering the actual value.

In real data work, you'll work with dozens, sometimes hundreds of values at once. Variables let you give meaningful names to those values so your code is readable, reusable, and easy to change.

In R, you create a variable using the **assignment operator** `<-`, which you read as "gets":

```r
age <- 21
```

This says: *"create a container called `age`, and put the value `21` inside it."*

From this point on, whenever you type `age`, R knows you mean `21`.

---

## Rules for Naming Variables

Not every name is a valid variable name in R. Here are the rules:

| Rule | Example |
|------|---------|
| Must start with a letter | `score`, `name1` ✅ — `1score` ❌ |
| Can contain letters, numbers, dots, underscores | `my_score`, `first.name` ✅ |
| No spaces | `my score` ❌ — use `my_score` instead |
| No hyphens | `my-score` ❌ — the `-` looks like subtraction to R |
| Case-sensitive | `Score` and `score` are different variables |
| Avoid built-in R names | Don't name a variable `mean`, `sum`, `c`, `TRUE`, `FALSE` |

**Naming conventions:** There are two popular styles. Pick one and be consistent:
- `snake_case` — words separated by underscores: `student_name`, `exam_score`
- `camelCase` — words capitalised after the first: `studentName`, `examScore`

---

## Assigning and Updating Variables

You assign a value with `<-`. You can reassign (overwrite) a variable at any time just by using `<-` again:

```r
x <- 10     # x is 10
x <- 20     # x is now 20 — the old value is gone
```

You can also assign the result of a calculation:

```r
radius <- 5
area <- pi * radius ^ 2     # pi is a built-in constant in R
```

And you can use one variable to define another:

```r
base_salary <- 50000
bonus <- 0.10 * base_salary     # 10% of base salary
total <- base_salary + bonus
```

---

## Checking What's Inside a Variable

Simply typing the variable name and pressing Enter prints its value:

```r
area
# [1] 78.53982
```

You can also check its type with `class()`:

```r
class(area)     # "numeric"
```

And see all variables currently in your environment with:

```r
ls()     # lists all variable names you've created
```

---

## `<-` vs `=` — Which Should You Use?

Both `<-` and `=` work for assignment in R. However, `<-` is the **community standard** — nearly all R code you'll ever read uses `<-`, and R style guides recommend it. The `=` sign also has a different meaning inside function calls (passing arguments), so using `<-` for assignment keeps things unambiguous. Develop the habit of using `<-` from the start.

---

# Part 2 — Hands-On

## Try These in RStudio

![Variables in RStudio Console](../screenshots/03_variables.png)

```r
# Creating variables
name    <- "Priya"
age     <- 21
gpa     <- 3.8
passed  <- TRUE

# Printing
name        # [1] "Priya"
age         # [1] 21

# Using variables in expressions
age + 4
# [1] 25

paste(name, "has a GPA of", gpa)
# [1] "Priya has a GPA of 3.8"

# Checking types
class(name)     # [1] "character"
class(age)      # [1] "numeric"
class(passed)   # [1] "logical"
```

```r
# Reassigning
score <- 80
score           # [1] 80
score <- score + 10
score           # [1] 90

# Using built-in constant pi
radius <- 7
circumference <- 2 * pi * radius
circumference   # [1] 43.98229
```

```r
# Listing all variables in environment
ls()
# [1] "age" "circumference" "gpa" "name" "passed" "radius" "score"
```

---

# Part 3 — Exercises

---

## ### Exercise 1 — Creating Variables

> **Create three variables: your name, your age, and your favourite subject. Then use `paste()` to print a sentence that combines all three, like: `"Priya is 21 years old and loves Statistics."`**

&nbsp;

&nbsp;

&nbsp;

```r
my_name    <- "Priya"
my_age     <- 21
my_subject <- "Statistics"

paste(my_name, "is", my_age, "years old and loves", paste0(my_subject, "."))
# [1] "Priya is 21 years old and loves Statistics."
```

---

## ### Exercise 2 — Arithmetic with Variables

> **A shopkeeper sells a product for ₹250. He gives a 15% discount. Create variables for the original price and the discount percentage, calculate the final price, and print it.**

&nbsp;

&nbsp;

&nbsp;

```r
original_price <- 250
discount_pct   <- 0.15
discount_amount <- original_price * discount_pct
final_price    <- original_price - discount_amount

final_price
# [1] 212.5
```

---

## ### Exercise 3 — Temperature Conversion

> **Create a variable `temp_c` set to `38` (a fever in Celsius). Convert it to Fahrenheit using the formula `(C × 9/5) + 32`. Store the result in `temp_f` and print it.**

&nbsp;

&nbsp;

&nbsp;

```r
temp_c <- 38
temp_f <- (temp_c * 9/5) + 32
temp_f
# [1] 100.4
```

---

## ### Exercise 4 — Spot the Error

> **The following code has a mistake. What is wrong, and how would you fix it?**
> ```r
> My Score <- 95
> class(my_score)
> ```

&nbsp;

&nbsp;

&nbsp;

```r
# Two problems:
# 1. "My Score" has a space — variable names cannot have spaces.
# 2. R is case-sensitive: "My Score" and "my_score" are different things.

# Fix:
my_score <- 95
class(my_score)
# [1] "numeric"
```

---

## ⬅️ [Back: Data Types](04_syntax_datatypes.md) &nbsp;|&nbsp; [➡️ Next: Vectors](05b_vectors.md)
