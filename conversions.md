# 🧠 DSA Conversion Cheat Sheet

## ☕ Java

```java
// String → int
int n = Integer.parseInt("123");

// int → String
String s = String.valueOf(123);

// String → char[]
char[] arr = "hello".toCharArray();

// char[] → String
String s = new String(arr);

// String → StringBuilder
StringBuilder sb = new StringBuilder(s);

// StringBuilder → String
String s = sb.toString();

// List → Set
Set<Integer> set = new HashSet<>(list);

// Set → List
List<Integer> list = new ArrayList<>(set);

// String → parts
String[] arr = "a,b,c".split(",");

// List → String
String s = String.join(",", list);

// int[] → List<Integer>
List<Integer> list = Arrays.stream(arr)
        .boxed()
        .collect(Collectors.toList());

// Sort ascending
Arrays.sort(arr);

// Reverse String
String reverse = new StringBuilder(s)
        .reverse()
        .toString();

// Print array
System.out.println(Arrays.toString(arr));
```

### ⭐ Java Core

```text
Integer.parseInt()
String.valueOf()
.toCharArray()
new String()
new StringBuilder()
.toString()
new HashSet<>()
new ArrayList<>()
.split()
String.join()
Arrays.sort()
Arrays.toString()
```

---

# 🐍 Python

```python
# String → int
n = int("123")

# int → String
s = str(123)

# String → list
arr = list("hello")

# List → String
s = "".join(arr)

# List → Set
s = set(arr)

# Set → List
arr = list(s)

# String → list of words
words = "a b c".split()

# String → parts
arr = "a,b,c".split(",")

# List → sorted list
arr = sorted(arr)

# Reverse list
arr.reverse()

# Reverse String
reverse = s[::-1]
```

### ⭐ Python Core

```text
int()
str()
list()
set()
.split()
.join()
sorted()
.reverse()
[::-1]
```

---

# 🟦 TypeScript

```typescript
// String → number
const n = Number("123");

// number → String
const s = String(123);

// String → array
const arr = "hello".split("");

// Array → Set
const set = new Set(arr);

// Set → Array
const arr2 = [...set];

// String → words
const words = "a b c".split(" ");

// String → parts
const parts = "a,b,c".split(",");

// Array → String
const s = arr.join("");

// Array → String with separator
const s = arr.join(",");

// Sort ascending numbers
arr.sort((a, b) => a - b);

// Sort descending numbers
arr.sort((a, b) => b - a);

// Reverse array
arr.reverse();

// Reverse String
const reverse = s.split("").reverse().join("");
```

### ⭐ TypeScript Core

```text
Number()
String()
.split()
new Set()
[...set]
.join()
.sort()
.reverse()
```

---

# 🔥 Same Pattern in All 3

## List/Array → Set

```text
Java:
new HashSet<>(list)

Python:
set(list)

TypeScript:
new Set(array)
```

## Set → List/Array

```text
Java:
new ArrayList<>(set)

Python:
list(set)

TypeScript:
[...set]
```

## String → Characters

```text
Java:
"hello".toCharArray()

Python:
list("hello")

TypeScript:
"hello".split("")
```

## String → Integer/Number

```text
Java:
Integer.parseInt("123")

Python:
int("123")

TypeScript:
Number("123")
```

## Number → String

```text
Java:
String.valueOf(123)

Python:
str(123)

TypeScript:
String(123)
```

## Reverse String

```text
Java:
new StringBuilder(s).reverse().toString()

Python:
s[::-1]

TypeScript:
s.split("").reverse().join("")
```

---

# 🎯 What to Actually Memorize

Don't try to memorize every line.

Memorize these patterns:

```text
             JAVA              PYTHON            TYPESCRIPT

String → Num parseInt()        int()             Number()

Num → String  valueOf()        str()             String()

String → Chars
              toCharArray()    list()            split("")

→ Set         HashSet          set()             new Set()

Set → Array   ArrayList        list()             [...set]

Split         split()          split()            split()

Join          String.join()    "".join()          join()

Sort          Arrays.sort()    sorted()           sort()

Reverse       StringBuilder    [::-1]             split/reverse/join
```

For DSA, you don't need to memorize hundreds of conversions.

**Learn the pattern → use it → forget it → look it up → use it again → eventually remember it.**
