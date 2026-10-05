# Python String Methods — Data Analysis Notes

> **Source:** Python 3.12 Official Documentation — `str` methods  
> **Status:** Completed study set  
> **Focus:** Python skills useful for Data Analysis and Data Engineering

---

## 1. What is a String?

A string is a sequence of characters.

```python
text = "Python"
```

Characters can be accessed using indexing:

```python
text[0]    # "P"
text[-1]   # "n"
```

Strings are immutable, so string methods return a new string rather than changing the original string.

---

# 2. Data Analysis Priority

### ⭐⭐⭐ Very Important

These are especially useful for cleaning and transforming real-world data:

- `replace()`
- `split()`
- `strip()`
- `find()`
- `startswith()`
- `endswith()`
- `lower()`
- `upper()` — reference for future use
- `join()`
- `isdigit()`
- `isdecimal()`
- `isnumeric()`
- `isalpha()`
- `isalnum()`
- `isspace()`
- `format()`
- `partition()`
- `rsplit()`

### ⭐⭐ Useful

- `count()`
- `index()`
- `rfind()`
- `rindex()`
- `rpartition()`
- `lstrip()`
- `rstrip()`
- `removeprefix()`
- `removesuffix()`
- `title()`
- `translate()`
- `maketrans()`
- `splitlines()`
- `isprintable()`
- `isidentifier()`

### ⭐ Lower Priority

- `center()`
- `encode()`
- `expandtabs()`
- `format_map()`
- `isascii()`
- `islower()`
- `istitle()`
- `isupper()`
- `ljust()`
- `rjust()`
- `swapcase()`
- `zfill()` — useful in specific formatting situations

---

# 3. String Methods Studied

## `center()`

Centers a string inside a field of a specified width.

```python
text = "Python"

print(text.center(10))
# "  Python  "
```

Useful for formatting output.

---

## `count()`

Counts how many times a substring occurs.

```python
text = "banana"

print(text.count("a"))
# 3
```

Useful for simple text-frequency checks.

---

## `encode()`

Converts a string into bytes using a specified encoding.

```python
text = "Hello"

result = text.encode("UTF-8")
print(result)
```

The reverse operation is decoding:

```python
result.decode("UTF-8")
```

Useful when working with files, APIs, and encoded data.

---

## `endswith()`

Checks whether a string ends with a specified suffix.

```python
filename = "sales.csv"

print(filename.endswith(".csv"))
# True
```

Very useful for checking file extensions.

---

## `expandtabs()`

Replaces tab characters (`\t`) with spaces.

```python
text = "Name\tAge"
print(text.expandtabs(4))
```

Useful when cleaning text containing tab characters.

---

## `find()`

Returns the lowest index where a substring is found.

```python
text = "Python"

print(text.find("t"))
# 2
```

If the substring is not found:

```python
print(text.find("z"))
# -1
```

### `in` vs `find()`

```python
"Python" in text
# True
```

`in` returns a Boolean.

```python
text.find("Python")
# 0
```

`find()` returns the position.

---

## `format()`

Inserts values into a string.

```python
name = "Bhavana"
age = 24

print("Name: {} | Age: {}".format(name, age))
```

Keyword arguments:

```python
print("Name: {name}, Job: {job}".format(
    name="Bhavana",
    job="Data Analyst"
))
```

Number formatting:

```python
salary = 26500

print("Salary: {:,}".format(salary))
# Salary: 26,500
```

Decimal formatting:

```python
accuracy = 89.44

print("Accuracy: {:.2f}%".format(accuracy))
# Accuracy: 89.44%
```

---

## `format_map()`

Similar to `format()`, but uses a mapping such as a dictionary.

```python
data = {
    "name": "Bhavana",
    "role": "Data Analyst"
}

print("{name} - {role}".format_map(data))
```

Useful when values already exist in a dictionary.

---

## `index()`

Returns the lowest index where a substring occurs.

```python
text = "Python"

print(text.index("t"))
# 2
```

Unlike `find()`, it raises `ValueError` when the substring is missing.

```python
text.index("z")
# ValueError
```

### Remember

| Method | If missing |
|---|---|
| `find()` | `-1` |
| `index()` | `ValueError` |

---

# Character-Checking Methods

## `isalnum()`

Checks whether all characters are letters or numbers.

```python
"Python123".isalnum()
# True

"Python 123".isalnum()
# False
```

Spaces and punctuation make it `False`.

---

## `isalpha()`

Checks whether all characters are alphabetic.

```python
"Python".isalpha()
# True

"Python123".isalpha()
# False
```

---

## `isascii()`

Checks whether all characters are ASCII characters.

```python
"Python".isascii()
# True

"Python😊".isascii()
# False
```

An empty string returns `True`.

---

## `isdecimal()`

Checks whether all characters are decimal characters.

```python
"123".isdecimal()
# True

"Python".isdecimal()
# False

"12.5".isdecimal()
# False
```

An empty string returns `False`.

---

## `isdigit()`

Checks whether all characters are digits.

```python
"123".isdigit()
# True
```

It is broader than `isdecimal()`.

Example:

```python
"²".isdigit()
# True

"²".isdecimal()
# False
```

---

## `isidentifier()`

Checks whether a string is a valid Python identifier.

```python
"name".isidentifier()
# True

"user_name".isidentifier()
# True

"123name".isidentifier()
# False

"user-name".isidentifier()
# False
```

Important: being a valid identifier does not mean it is available as a variable name.

```python
"def".isidentifier()
# True
```

But `def` is a Python keyword.

---

## `islower()`

Checks whether all cased characters are lowercase.

```python
"hello".islower()
# True

"Hello".islower()
# False
```

---

## `isnumeric()`

Checks whether all characters are numeric.

It is broader than `isdecimal()` and `isdigit()`.

```python
"123".isnumeric()
# True
```

---

## `isprintable()`

Checks whether all characters are printable.

```python
"Hello".isprintable()
# True

"Hello\n".isprintable()
# False
```

---

## `isspace()`

Checks whether all characters are whitespace.

```python
"   ".isspace()
# True

"\t".isspace()
# True

"Hello".isspace()
# False
```

Useful when cleaning blank or whitespace-only values.

---

## `istitle()`

Checks whether the string is titlecased.

```python
"Hello World".istitle()
# True

"hello world".istitle()
# False
```

---

## `isupper()`

Checks whether all cased characters are uppercase.

```python
"HELLO".isupper()
# True

"Hello".isupper()
# False
```

---

# 4. Formatting and Cleaning

## `join()`

Joins elements of an iterable using the string as a separator.

```python
items = ["Python", "SQL", "Excel"]

result = ", ".join(items)

print(result)
# Python, SQL, Excel
```

Very useful when converting a list of values into one string.

---

## `ljust()`

Left-justifies a string and pads the right side.

```python
text = "Python"

print(text.ljust(10, "-"))
# Python----
```

Mainly useful for text formatting.

---

## `lower()`

Converts uppercase characters to lowercase.

```python
text = "PYTHON SQL"

print(text.lower())
# python sql
```

### Data Analysis importance: ⭐⭐⭐

Useful for standardizing categorical/text data.

```python
value = "  BANGALORE  "

cleaned = value.strip().lower()

print(cleaned)
# bangalore
```

---

## `lstrip()`

Removes leading whitespace or specified characters from the left side.

```python
text = "   Python"

print(text.lstrip())
# Python
```

---

## `maketrans()`

Creates a translation table used by `translate()`.

```python
table = str.maketrans("ae", "12")
```

Then:

```python
"hello".translate(table)
# h2llo
```

Usually learned together with `translate()`.

---

## `partition()`

Splits a string into three parts at the first occurrence of a separator.

```python
text = "Python-SQL-Excel"

print(text.partition("-"))
```

Result:

```python
("Python", "-", "SQL-Excel")
```

Useful when you specifically need:

1. text before separator
2. separator
3. text after separator

---

## `removeprefix()`

Removes a specified prefix if the string starts with it.

```python
text = "Mr. Bhavana"

print(text.removeprefix("Mr. "))
# Bhavana
```

Unlike `lstrip()`, it removes the exact prefix.

---

## `removesuffix()`

Removes a specified suffix if the string ends with it.

```python
filename = "sales.csv"

print(filename.removesuffix(".csv"))
# sales
```

Useful when processing filenames.

---

## `replace()`

Replaces occurrences of one substring with another.

```python
text = "Python is easy"

print(text.replace("easy", "powerful"))
# Python is powerful
```

Can also remove text:

```python
text.replace("Python ", "")
# "is easy"
```

### `count` argument

```python
text = "apple apple apple"

print(text.replace("apple", "orange", 1))
# orange apple apple
```

### ⭐⭐⭐ Very important for Data Analysis

Example:

```python
salary = "₹26,500"

clean_salary = int(
    salary.replace("₹", "").replace(",", "")
)

print(clean_salary)
# 26500
```

This is a common data-cleaning pattern.

---

# 5. Reverse Search Methods

## `rfind()`

Like `find()`, but searches from the right and returns the highest index.

```python
text = "Python Python"

print(text.rfind("Python"))
# 7
```

If not found:

```python
text.rfind("Java")
# -1
```

---

## `rindex()`

Like `index()`, but returns the highest index.

```python
text = "Python Python"

print(text.rindex("Python"))
# 7
```

If not found, it raises `ValueError`.

### Search-method comparison

| Method | Search | Missing |
|---|---|---|
| `find()` | first | `-1` |
| `rfind()` | last | `-1` |
| `index()` | first | `ValueError` |
| `rindex()` | last | `ValueError` |

---

## `rjust()`

Right-justifies a string and pads the left side.

```python
text = "Python"

print(text.rjust(10, "-"))
# ----Python
```

Useful mainly for formatting.

---

## `rpartition()`

Like `partition()`, but uses the last occurrence of the separator.

```python
path = "data/2026/sales.csv"

print(path.rpartition("/"))
```

Result:

```python
("data/2026", "/", "sales.csv")
```

Useful for extracting the final part of a path.

---

## `rsplit()`

Splits from the right.

```python
text = "Python-SQL-Excel"

print(text.rsplit("-", 1))
# ["Python-SQL", "Excel"]
```

This is particularly useful with `maxsplit=1`.

### Data Analysis example

```python
path = "data/2026/october/sales.csv"

print(path.rsplit("/", 1))
# ["data/2026/october", "sales.csv"]
```

---

## `rstrip()`

Removes trailing whitespace or specified characters from the right.

```python
text = "Python   "

print(text.rstrip())
# Python
```

### Difference

```text
lstrip()      → left
rstrip()      → right
strip()       → both
```

---

# 6. Splitting Methods

## `split()`

Splits a string into a list.

### Whitespace

```python
text = "Python SQL Excel"

print(text.split())
# ["Python", "SQL", "Excel"]
```

### Delimiter

```python
text = "Python,SQL,Excel"

print(text.split(","))
# ["Python", "SQL", "Excel"]
```

### `maxsplit`

```python
text = "Python-SQL-Excel"

print(text.split("-", 1))
# ["Python", "SQL-Excel"]
```

### ⭐⭐⭐ Very important for Data Analysis

Example:

```python
location = "Bhimavaram,Andhra Pradesh,India"

parts = location.split(",")

print(parts)
# ["Bhimavaram", "Andhra Pradesh", "India"]
```

---

## `rsplit()`

```python
text = "Python-SQL-Excel"

text.rsplit("-", 1)
# ["Python-SQL", "Excel"]
```

### Difference

```text
split()   → starts splitting from left
rsplit()  → starts splitting from right
```

---

## `splitlines()`

Splits a string at line boundaries.

```python
text = "Python\nSQL\nExcel"

print(text.splitlines())
# ["Python", "SQL", "Excel"]
```

Useful when processing multiline text or file content.

---

## `startswith()`

Checks whether a string starts with a specified prefix.

```python
filename = "sales_2026.csv"

print(filename.startswith("sales"))
# True
```

### ⭐⭐⭐ Data Analysis relevance

Useful for:

- filtering IDs
- filenames
- URLs
- categories
- structured text

---

## `strip()`

Removes leading and trailing whitespace.

```python
text = "   Python   "

print(text.strip())
# Python
```

It can also remove specified characters:

```python
text = "###Python###"

print(text.strip("#"))
# Python
```

### ⭐⭐⭐ Very important for Data Analysis

A common cleaning pattern:

```python
value = "  BANGALORE  "

cleaned = value.strip().lower()

print(cleaned)
# bangalore
```

### Remember

```text
lstrip() → left
rstrip() → right
strip()  → both
```

### `strip()` vs `removeprefix()`

`strip()` removes characters from the ends.

`removeprefix()` removes one exact prefix.

---

# 7. Case Conversion

## `swapcase()`

Converts uppercase characters to lowercase and lowercase characters to uppercase.

```python
text = "Hello Python"

print(text.swapcase())
# hELLO pYTHON
```

Numbers and symbols are unchanged.

Low Data Analysis priority.

---

## `title()`

Converts text to title case.

```python
text = "hello world"

print(text.title())
# Hello World
```

Useful for formatting names and labels.

```python
name = "bhavana polnidi"

print(name.title())
# Bhavana Polnidi
```

### Difference from `capitalize()`

```text
title()      → Python Programming
capitalize() → Python programming
```

---

## `translate()`

Applies a translation table to characters.

```python
table = str.maketrans("ae", "12")

text = "hello"

print(text.translate(table))
# h2llo
```

Can also remove characters:

```python
text = "Hello, World!"

table = str.maketrans("", "", ",!")

print(text.translate(table))
# Hello World
```

Useful when replacing/removing multiple individual characters at once.

---

# 8. Important Method Comparisons

## `find()` vs `index()`

```text
find()  → returns -1 if missing
index() → raises ValueError if missing
```

## `find()` vs `rfind()`

```text
find()  → first occurrence
rfind() → last occurrence
```

## `index()` vs `rindex()`

```text
index()  → first occurrence
rindex() → last occurrence
```

## `split()` vs `rsplit()`

```text
split()  → split from left
rsplit() → split from right
```

## `partition()` vs `split()`

```text
partition() → returns exactly 3 parts
split()     → returns a list with variable number of parts
```

Example:

```python
"Python-SQL-Excel".partition("-")
# ("Python", "-", "SQL-Excel")

"Python-SQL-Excel".split("-")
# ["Python", "SQL", "Excel"]
```

## `strip()` vs `replace()`

```text
strip()   → removes from the beginning/end
replace() → replaces matching text anywhere
```

## `strip()` vs `removeprefix()`

```text
strip()         → character-based edge removal
removeprefix()  → exact prefix removal
```

---

# 9. Real Data-Cleaning Pattern

A very common workflow combines several string methods:

```python
value = "  BANGALORE, INDIA  "

cleaned = value.strip().lower()

parts = cleaned.split(",")

print(parts)
```

Result:

```python
["bangalore", " india"]
```

The second value can then be cleaned further:

```python
parts = [item.strip() for item in value.strip().lower().split(",")]
```

Result:

```python
["bangalore", "india"]
```

This demonstrates why these methods matter in Data Analysis.

---

# 10. Practical Data Analysis Toolkit

If you don't want to memorize every method equally, prioritize these:

```text
strip()
split()
replace()
lower()
upper()
find()
startswith()
endswith()
join()
count()
isdigit()
isdecimal()
isnumeric()
isalpha()
isalnum()
isspace()
partition()
rsplit()
format()
```

These will appear frequently when working with:

- CSV data
- Excel exports
- customer information
- names
- addresses
- IDs
- filenames
- categories
- API responses
- logs
- text columns

---

# 11. Progress Checklist

### Completed

- [x] center()
- [x] count()
- [x] encode()
- [x] endswith()
- [x] expandtabs()
- [x] find()
- [x] format()
- [x] format_map()
- [x] index()
- [x] isalnum()
- [x] isalpha()
- [x] isascii()
- [x] isdecimal()
- [x] isdigit()
- [x] isidentifier()
- [x] islower()
- [x] isnumeric()
- [x] isprintable()
- [x] isspace()
- [x] istitle()
- [x] isupper()
- [x] join()
- [x] ljust()
- [x] lower()
- [x] lstrip()
- [x] maketrans()
- [x] partition()
- [x] removeprefix()
- [x] removesuffix()
- [x] replace()
- [x] rfind()
- [x] rindex()
- [x] rjust()
- [x] rpartition()
- [x] rsplit()
- [x] rstrip()
- [x] split()
- [x] splitlines()
- [x] startswith()
- [x] strip()
- [x] swapcase()
- [x] title()
- [x] translate()

---

# 12. Methods to Keep as Reference

These methods are useful to know but do not need the same memorization priority for Data Analysis:

```text
center()
encode()
expandtabs()
format_map()
isascii()
isidentifier()
isprintable()
ljust()
rjust()
swapcase()
```

Also keep `upper()` and `zfill()` in the reference list when revising the complete Python `str` API.

---

# 13. Next Learning Step

After completing these string methods, the goal is not to memorize every method.

The important next step is to **practice combining them on realistic datasets**.

Example:

```python
raw = "  BHAVANA, DATA ANALYST, 26500  "

parts = [item.strip() for item in raw.split(",")]

name = parts[0].title()
role = parts[1].lower()
salary = int(parts[2])

print(name)
print(role)
print(salary)
```

This is the kind of Python string manipulation that will directly support later work with:

- Pandas
- CSV files
- Excel data
- SQL results
- APIs
- Data Engineering pipelines

---

## Source

Python 3.12 Official Documentation — `str` methods.

The notes above are based on the Python documentation excerpt used during this study session.
