# 📊 Vectors

> **Author:** RP &nbsp;|&nbsp; [@priyasaivasan](https://github.com/priyasaivasan)

---

# Part 1 — Understanding the Concept

## What is a Vector?

A **vector** is the most fundamental data structure in R. Almost everything in R is built on top of vectors — once you understand them well, the rest of R starts to make a lot of sense.

In simple terms: a vector is **an ordered collection of values, all of the same type**.

Think of it like a single column in a spreadsheet:

```
scores:  [ 85 | 90 | 78 | 92 | 88 ]
           1    2    3    4    5     ← position (called index)
```

Each value has a fixed position (called an **index**), starting from **1**. This is different from languages like Python, where counting starts at 0 — in R, the first element is always at position 1.

You create a vector using the `c()` function — `c` stands for **combine**:

```r
scores <- c(85, 90, 78, 92, 88)
```

---

## The "Same Type" Rule

A vector can only hold one type of data — all numbers, all text, or all TRUE/FALSE. You cannot mix types in a single vector.

What happens if you try? R doesn't give you an error — it quietly converts everything to the most flexible type available. This is called **type coercion**, and it follows the same hierarchy you saw in data types:

```
logical  →  integer  →  numeric  →  character
```

**Example:**
```r
c(1, 2, "three")
# [1] "1"     "2"     "three"
```

R converted `1` and `2` into `"1"` and `"2"` because character is the most flexible type. This is silent — R won't warn you. Always use `class()` to check what type your vector actually is.

---

## Creating Vectors

### Using `c()`

The most common way — just list your values separated by commas:

```r
# Numeric vector
scores <- c(85, 90, 78, 92, 88)

# Character vector
students <- c("Alice", "Bob", "Clara", "David", "Eva")

# Logical vector
passed <- c(TRUE, TRUE, FALSE, TRUE, TRUE)
```

### Using `:` for Integer Sequences

The colon `:` creates a sequence of consecutive integers in one step:

```r
1:10
# [1]  1  2  3  4  5  6  7  8  9 10

10:1        # counting down
# [1] 10  9  8  7  6  5  4  3  2  1
```

### Using `seq()` for Custom Sequences

`seq()` gives you much more control — you can specify the step size or the number of values you want:

```r
seq(1, 20, by = 5)           # step of 5
# [1]  1  6 11 16

seq(0, 1, length.out = 5)    # exactly 5 values between 0 and 1
# [1] 0.00 0.25 0.50 0.75 1.00
```

### Using `rep()` for Repetitions

`rep()` repeats values in different patterns:

```r
rep(0, times = 4)
# [1] 0 0 0 0

rep(c(1, 2, 3), times = 2)     # repeat the whole vector twice
# [1] 1 2 3 1 2 3

rep(c(1, 2, 3), each = 2)      # repeat each element twice
# [1] 1 1 2 2 3 3
```

---

## Accessing Elements — Indexing

To get a specific element out of a vector, you use **square brackets** `[ ]` with the position number:

```r
scores <- c(85, 90, 78, 92, 88)

scores[1]      # first element  → 85
scores[3]      # third element  → 78
scores[5]      # last element   → 88
```

You can also:

**Get a range of elements:**
```r
scores[2:4]       # elements 2 through 4 → 90 78 92
```

**Get specific elements by listing their positions:**
```r
scores[c(1, 5)]   # first and fifth → 85 88
```

**Exclude an element using negative indexing:**
```r
scores[-3]        # everything except the 3rd → 85 90 92 88
```

**Update an element:**
```r
scores[2] <- 95   # change the 2nd element to 95
scores
# [1] 85 95 78 92 88
```

---

## Filtering — Getting Elements That Match a Condition

One of R's most powerful features is the ability to extract elements from a vector based on a condition, in a single line of code.

When you write a condition on a vector, R evaluates it for **every element** and returns a logical vector of TRUE/FALSE:

```r
scores <- c(85, 90, 78, 92, 88)

scores > 85
# [1] FALSE  TRUE FALSE  TRUE  TRUE
```

You can then use that logical vector inside `[ ]` to keep only the TRUE positions:

```r
scores[scores > 85]
# [1] 90 92 88
```

You can combine conditions with `&` (AND) and `|` (OR):

```r
scores[scores >= 80 & scores <= 90]
# [1] 85 90 88

scores[scores < 80 | scores > 90]
# [1] 78 92
```

For character vectors, use `==` to match exact values:

```r
students <- c("Alice", "Bob", "Clara", "David", "Eva")
students[students == "Clara"]
# [1] "Clara"
```

---

## Vector Arithmetic — Vectorisation

In R, when you perform arithmetic on a vector, the operation is applied to **every element automatically**. This is called **vectorisation**, and it's one of the most important ideas in R.

```r
scores <- c(85, 90, 78, 92, 88)

scores + 5      # add 5 to every score
# [1]  90  95  83  97  93

scores / 100    # convert to proportions
# [1] 0.85 0.90 0.78 0.92 0.88
```

When you operate on two vectors of the **same length**, R matches them element by element:

```r
test1 <- c(80, 70, 90)
test2 <- c(60, 85, 75)

test1 + test2
# [1] 140 155 165

(test1 + test2) / 2     # average of two tests
# [1] 70.0 77.5 82.5
```

If the vectors are different lengths, R "recycles" the shorter one — this can lead to unexpected results, so be careful.

---

## Useful Vector Functions

R comes with a rich set of built-in functions for summarising and working with vectors:

| Function | What it does | Example result |
|----------|-------------|----------------|
| `length(x)` | Number of elements | `5` |
| `sum(x)` | Total of all elements | `433` |
| `mean(x)` | Average | `86.6` |
| `median(x)` | Middle value | `88` |
| `min(x)` | Smallest value | `78` |
| `max(x)` | Largest value | `92` |
| `range(x)` | Min and max together | `78 92` |
| `sd(x)` | Standard deviation | `5.18` |
| `sort(x)` | Sorted lowest to highest | `78 85 88 90 92` |
| `rev(x)` | Reversed order | `88 92 78 90 85` |
| `which.min(x)` | Index of the smallest | `3` (position of 78) |
| `which.max(x)` | Index of the largest | `4` (position of 92) |
| `unique(x)` | Remove duplicate values | removes repeats |
| `table(x)` | Count how many times each value appears | useful for categories |

---

# Part 2 — Hands-On

## Try These in RStudio

![Creating Vectors in RStudio Console](../screenshots/vec_01_create.png)

```r
# Creating vectors
scores   <- c(85, 90, 78, 92, 88)
students <- c("Alice", "Bob", "Clara", "David", "Eva")
passed   <- c(TRUE, TRUE, FALSE, TRUE, TRUE)

scores
# [1] 85 90 78 92 88

class(scores)
# [1] "numeric"

length(scores)
# [1] 5
```

![Sequences in RStudio Console](../screenshots/vec_02_sequences.png)

```r
# Sequences
1:10
# [1]  1  2  3  4  5  6  7  8  9 10

seq(0, 50, by = 10)
# [1]  0 10 20 30 40 50

rep(c("A", "B"), each = 3)
# [1] "A" "A" "A" "B" "B" "B"
```

![Vector Indexing in RStudio Console](../screenshots/vec_03_index.png)

```r
# Indexing
scores[1]        # [1] 85
scores[3]        # [1] 78
scores[2:4]      # [1] 90 78 92
scores[-2]       # [1] 85 78 92 88   — drops 2nd element
```

![Vector Filtering in RStudio Console](../screenshots/vec_04_filter.png)

```r
# Filtering
scores[scores > 85]
# [1] 90 92 88

scores[scores >= 80 & scores <= 90]
# [1] 85 90 88

students[students != "Bob"]
# [1] "Alice" "Clara" "David" "Eva"
```

![Vector Arithmetic in RStudio Console](../screenshots/vec_05_arithmetic.png)

```r
# Vectorised arithmetic
scores + 5
# [1]  90  95  83  97  93

test1 <- c(80, 70, 90)
test2 <- c(60, 85, 75)
(test1 + test2) / 2
# [1] 70.0 77.5 82.5
```

![Vector Functions in RStudio Console](../screenshots/vec_06_functions.png)

```r
# Summary functions
mean(scores)      # [1] 86.6
max(scores)       # [1] 92
min(scores)       # [1] 78
sort(scores)      # [1] 78 85 88 90 92
which.max(scores) # [1] 4   — 92 is at position 4
```

---

# Part 3 — Exercises

---

## ### Exercise 1 — Creating and Inspecting a Vector

> **Create a vector called `temps` with these 7 daily temperatures: `32, 35, 30, 28, 33, 36, 29`. Find its length, mean, max, and min.**

&nbsp;

&nbsp;

&nbsp;

```r
temps <- c(32, 35, 30, 28, 33, 36, 29)

length(temps)   # [1] 7
mean(temps)     # [1] 31.86
max(temps)      # [1] 36
min(temps)      # [1] 28
```

---

## ### Exercise 2 — Indexing

> **Using the `temps` vector from Exercise 1, extract:**
> - The temperature on day 3
> - Temperatures from day 2 to day 5
> - All days except day 4

&nbsp;

&nbsp;

&nbsp;

```r
temps[3]       # [1] 30

temps[2:5]     # [1] 35 30 28 33

temps[-4]      # [1] 32 35 30 33 36 29
```

---

## ### Exercise 3 — Filtering

> **From the `temps` vector, extract only the days where temperature was strictly above 32. How many such days were there?**

&nbsp;

&nbsp;

&nbsp;

```r
hot_days <- temps[temps > 32]
hot_days
# [1] 35 33 36

length(hot_days)
# [1] 3
```

---

## ### Exercise 4 — Vectorised Operations

> **A student scored the following marks out of 50 in 5 subjects: `38, 45, 29, 42, 36`. Convert these to percentages (out of 100) and add 5 bonus marks to each. What are the final scores?**

&nbsp;

&nbsp;

&nbsp;

```r
marks <- c(38, 45, 29, 42, 36)

percentage <- (marks / 50) * 100
# [1] 76 90 58 84 72

final <- percentage + 5
final
# [1] 81 95 63 89 77
```

---

## ⬅️ [Back: Variables](05_variables.md) &nbsp;|&nbsp; [➡️ Next: Matrices](06_matrices.md)
