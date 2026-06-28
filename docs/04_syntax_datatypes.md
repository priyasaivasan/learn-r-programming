# 🔢 04 — R Syntax & Data Types

> **Author:** RP &nbsp;|&nbsp; [@priyasaivasan](https://github.com/priyasaivasan)

---

## 📌 R Syntax Basics

> **What's happening:** R reads your instructions line by line. Each line is either a calculation, an assignment, or a function call. The `#` symbol starts a comment — R ignores anything after it.

![R Syntax in RStudio Console](../screenshots/01_syntax.png)

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `+` | Add | `5 + 3` | `8` |
| `-` | Subtract | `10 - 4` | `6` |
| `*` | Multiply | `3 * 4` | `12` |
| `/` | Divide | `10 / 2` | `5` |
| `^` | Power | `2 ^ 4` | `16` |
| `%%` | Modulo (remainder) | `10 %% 3` | `1` |
| `%/%` | Integer divide | `10 %/% 3` | `3` |

---

## 🏷️ Data Types

> **What's happening:** Every value in R has a *type*. R needs to know whether it's working with numbers, text, or true/false values. These are the 5 core types.

![Data Types in RStudio Console](../screenshots/02_datatypes.png)

### The 5 Core Types

| Type | Example | `class()` returns | Used for |
|------|---------|------------------|----------|
| **Integer** | `42L` | `"integer"` | Whole numbers (the `L` tells R it's integer) |
| **Numeric** | `3.14` | `"numeric"` | Decimal numbers |
| **Character** | `"hello"` | `"character"` | Text (always in quotes) |
| **Logical** | `TRUE` / `FALSE` | `"logical"` | Yes/no, true/false values |
| **Complex** | `2+3i` | `"complex"` | Complex numbers (rare in practice) |

### Type Hierarchy (Coercion Order)
```
logical  →  integer  →  double  →  character
  ↑ simplest                    ↑ most complex
```
When R mixes types, it converts everything to the *most complex* type in the mix.

---

## 🔍 Checking & Converting Types

> **What's happening:** R gives you simple functions to ask "what type is this?" and to convert between types. You'll use these constantly when debugging.

![Type Functions in RStudio Console](../screenshots/02b_typefunctions.png)

### Finding the Type

```r
x <- 42L
class(x)        # "integer"   — the category of the object
typeof(x)       # "integer"   — the internal storage type

y <- 3.14
class(y)        # "numeric"

z <- "hello"
class(z)        # "character"

b <- TRUE
class(b)        # "logical"
```

### Checking if Something IS a Type

```r
is.numeric(3.14)      # TRUE
is.character("hi")    # TRUE
is.logical(FALSE)     # TRUE
is.integer(42L)       # TRUE
is.integer(42)        # FALSE  — plain 42 is numeric, not integer!
```

### Converting Between Types

```r
as.character(100)     # "100"   — number becomes text
as.numeric("3.14")   # 3.14    — text becomes number
as.logical(0)         # FALSE   — 0 is always FALSE
as.logical(1)         # TRUE    — any non-zero is TRUE
as.integer(3.99)      # 3       — decimal is cut off, not rounded
```

> 💡 **Rule of thumb:** Use `class()` when you're not sure what something is. It's your best debugging friend.

---

## 📅 Working with Dates & Time

> **What's happening:** R has built-in functions to work with today's date, current time, and day information. These are handy for adding timestamps to reports or filtering data by date.

![Date Functions in RStudio Console](../screenshots/02c_dates.png)

```r
# Today's date
Sys.Date()
# [1] "2026-06-28"

# Current date AND time
Sys.time()
# [1] "2026-06-28 10:35:22 IST"

# What day of the week is it?
weekdays(Sys.Date())
# [1] "Sunday"

# What month?
months(Sys.Date())
# [1] "June"

# Format a date your own way
format(Sys.Date(), "%d %B %Y")
# [1] "28 June 2026"

# class of a date object
class(Sys.Date())
# [1] "Date"
```

### Format codes you'll use often

| Code | Meaning | Example |
|------|---------|---------|
| `%d` | Day (number) | `28` |
| `%m` | Month (number) | `06` |
| `%B` | Month (full name) | `June` |
| `%Y` | Year (4 digit) | `2026` |
| `%A` | Weekday name | `Sunday` |

---

## 💡 Tips & Gotchas

> ⚠️ `TRUE` and `FALSE` must be **ALL CAPS** in R. `True` or `true` will throw an error.

> ⚠️ Text (character) values must always be wrapped in `"quotes"` — without them R thinks it's a variable name.

> ⚠️ `42` is numeric but `42L` is integer. The `L` suffix is easy to forget.

> 💡 Use `class()` whenever you're unsure what type something is.

---

## ✏️ Try It Yourself

**Exercise — Data Types & Dates**

Try these in your RStudio console and note what you get:

1. What does `class(TRUE)` return?
2. What does `as.integer(7.9)` give you — is it `7` or `8`? Why?
3. Run `weekdays(Sys.Date())` — what day is it today?
4. What happens when you run `as.numeric("hello")`? What does the warning mean?
5. What is `class(Sys.Date())`?

<details>
<summary>💡 Click to reveal answers</summary>

1. `"logical"` — TRUE and FALSE are logical type
2. `7` — `as.integer()` truncates (chops off) the decimal, it does NOT round
3. Whatever today's day is — this is a live function!
4. You get `NA` with a warning — R cannot convert the word "hello" into a number, so it returns a missing value
5. `"Date"` — R stores dates in its own special Date class

</details>

---

## ⬅️ [Back: Environment](03_environment.md) &nbsp;|&nbsp; [➡️ Next: Variables](05_variables.md)
