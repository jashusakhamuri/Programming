Yes — I understand what you want now. You want a **proper DSA cheat sheet in Markdown**, not just a small comparison: **Python ↔ Java ↔ TypeScript/JavaScript**, with syntax, methods, collection equivalents, and **small practice problems for each topic**.

 Below is a version you can copy directly into a `.md` file.

 # Python vs Java vs TypeScript/JavaScript — DSA Cheat Sheet

 > A practical cheat sheet for DSA / LeetCode-style problems.

---

 # 1\. Variables & Basic Types

 | Concept | Python | Java | TypeScript |
| --- | --- | --- | --- |
| Integer | `x = 10` | `int x = 10;` | `let x: number = 10;` |
| Float | `x = 10.5` | `double x = 10.5;` | `let x: number = 10.5;` |
| String | `s = "hello"` | `String s = "hello";` | `let s: string = "hello";` |
| Boolean | `x = True` | `boolean x = true;` | `let x: boolean = true;` |
| Null | `None` | `null` | `null` |
| Constant | `X = 10` | `final int X = 10;` | `const X = 10;` |
| Print | `print(x)` | `System.out.println(x);` | `console.log(x);` |
| Type | `type(x)` | `x.getClass()` | `typeof x` |

---

 # 2\. If / Else

 ### Python

```
if x > 10:
    print("big")
elif x == 10:
    print("equal")
else:
    print("small")
```

 ### Java

```
if (x > 10) {
    System.out.println("big");
} else if (x == 10) {
    System.out.println("equal");
} else {
    System.out.println("small");
}
```

 ### TypeScript

```
if (x > 10) {
    console.log("big");
} else if (x === 10) {
    console.log("equal");
} else {
    console.log("small");
}
```

 > TypeScript: Prefer `===` and `!==` instead of `==` and `!=`.

---

 # 3\. Loops

 ## Normal `for` loop

 ### Python

```
for i in range(5):
    print(i)
```

 ### Java

```
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

 ### TypeScript

```
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

---

 # 4\. Loop Through Array

 ## Values

 ### Python

```
for x in arr:
    print(x)
```

 ### Java

```
for (int x : arr) {
    System.out.println(x);
}
```

 ### TypeScript

```
for (const x of arr) {
    console.log(x);
}
```

---

 ## Index

 ### Python

```
for i in range(len(arr)):
    print(arr[i])
```

 ### Java

```
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

 ### TypeScript

```
for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

---

 ## TypeScript `for...in` vs `for...of`

```
for (const i in arr) {
    console.log(i);       // index
}

for (const value of arr) {
    console.log(value);   // value
}
```

 Remember:

```
for...in  → keys / indexes
for...of  → values
```

---

 # 5\. Strings

 Suppose:

```
s = "Hello World"
```

 | Operation | Python | Java | TypeScript |
| --- | --- | --- | --- |
| Length | `len(s)` | `s.length()` | `s.length` |
| Character | `s[i]` | `s.charAt(i)` | `s[i]` |
| Character | `s[i]` | `s.charAt(i)` | `s.charAt(i)` |
| Substring | `s[1:4]` | `s.substring(1,4)` | `s.substring(1,4)` |
| Lowercase | `s.lower()` | `s.toLowerCase()` | `s.toLowerCase()` |
| Uppercase | `s.upper()` | `s.toUpperCase()` | `s.toUpperCase()` |
| Find | `s.find("x")` | `s.indexOf("x")` | `s.indexOf("x")` |
| Contains | `"x" in s` | `s.contains("x")` | `s.includes("x")` |
| Replace | `s.replace("a","b")` | `s.replace("a","b")` | `s.replace("a","b")` |
| Split | `s.split(" ")` | `s.split(" ")` | `s.split(" ")` |
| Trim | `s.strip()` | `s.trim()` | `s.trim()` |
| Starts | `s.startswith("H")` | `s.startsWith("H")` | `s.startsWith("H")` |
| Ends | `s.endswith("d")` | `s.endsWith("d")` | `s.endsWith("d")` |

---

 # 6\. String Reverse

 ### Python

```
reverse = s[::-1]
```

 ### Java

```
String reverse = new StringBuilder(s).reverse().toString();
```

 ### TypeScript

```
const reverse = s.split("").reverse().join("");
```

 ### Manual

```
let reverse = "";

for (let i = s.length - 1; i >= 0; i--) {
    reverse += s[i];
}
```

---

 # 7\. String Traversal

 ### Python

```
for char in s:
    print(char)
```

 ### Java

```
for (int i = 0; i < s.length(); i++) {
    System.out.println(s.charAt(i));
}
```

 ### TypeScript

```
for (const char of s) {
    console.log(char);
}
```

---

 # 8\. Arrays / Lists

 ## Create

 | Python | Java | TypeScript |
| --- | --- | --- |
| `arr = [1,2,3]` | `int[] arr = {1,2,3};` | `let arr: number[] = [1,2,3];` |
| `arr = []` | `List<Integer> arr = new ArrayList<>();` | `let arr: number[] = [];` |

---

 # 9\. Array/List Methods

 | Operation | Python | Java | TypeScript |
| --- | --- | --- | --- |
| Add end | `append(x)` | `add(x)` | `push(x)` |
| Remove end | `pop()` | `remove(size()-1)` | `pop()` |
| Insert | `insert(i,x)` | `add(i,x)` | `splice(i,0,x)` |
| Remove by value | `remove(x)` | `remove(x)` | `splice(i,1)` |
| Get | `arr[i]` | `arr[i]` / `get(i)` | `arr[i]` |
| Set | `arr[i]=x` | `arr[i]=x` / `set(i,x)` | `arr[i]=x` |
| Length | `len(arr)` | `arr.length` | `arr.length` |
| Contains | `x in arr` | `contains(x)` | `includes(x)` |
| Index | `arr.index(x)` | `indexOf(x)` | `indexOf(x)` |
| Sort | `arr.sort()` | `Arrays.sort(arr)` | `arr.sort()` |
| Reverse | `arr.reverse()` | `Collections.reverse(arr)` | `arr.reverse()` |

---

 # 10\. Important Java Difference

 Java array:

```
int[] arr = {1, 2, 3};

arr.length;
```

 Java `ArrayList`:

```
List<Integer> arr = new ArrayList<>();

arr.size();
```

 TypeScript:

```
arr.length;
```

 So remember:

```
Java array       → length
Java ArrayList   → size()
Python           → len(arr)
TypeScript       → arr.length
```

---

 # 11\. Array Slicing

 ### Python

```
arr[1:4]
```

 ### Java

 No direct slicing method.

 Use:

```
Arrays.copyOfRange(arr, 1, 4);
```

 ### TypeScript

```
arr.slice(1, 4);
```

 Important:

```
slice(start, end)
```

 `end` is excluded.

---

 # 12\. Array `splice` vs `slice` in TypeScript

 ### `slice`

 Does NOT modify the original array.

```
const result = arr.slice(1, 4);
```

 ### `splice`

 MODIFIES the original array.

```
arr.splice(1, 2);
```

 General syntax:

```
arr.splice(start, deleteCount, item1, item2, ...);
```

 Example:

```
let arr = [1, 2, 3, 4];

arr.splice(1, 2);

console.log(arr);

// [1, 4]
```

---

 # 13\. Dictionary / HashMap

 ## Create

 ### Python

```
mp = {}
```

 ### Java

```
Map<String, Integer> mp = new HashMap<>();
```

 ### TypeScript

```
const mp: Map<string, number> = new Map();
```

---

 # 14\. HashMap Methods

 | Operation | Python | Java | TypeScript |
| --- | --- | --- | --- |
| Insert | `mp[key] = value` | `put(key,value)` | `set(key,value)` |
| Get | `mp[key]` | `get(key)` | `get(key)` |
| Check key | `key in mp` | `containsKey(key)` | `has(key)` |
| Remove | `del mp[key]` | `remove(key)` | `delete(key)` |
| Size | `len(mp)` | `size()` | `size` |
| Clear | `clear()` | `clear()` | `clear()` |
| Keys | `mp.keys()` | `keySet()` | `keys()` |
| Values | `mp.values()` | `values()` | `values()` |

---

 # 15\. Get With Default Value

 This is extremely important for frequency problems.

 ### Python

```
mp.get(key, 0)
```

 ### Java

```
mp.getOrDefault(key, 0)
```

 ### TypeScript

```
mp.get(key) ?? 0
```

 Example:

 ### Python

```
count[ch] = count.get(ch, 0) + 1
```

 ### Java

```
count.put(ch, count.getOrDefault(ch, 0) + 1);
```

 ### TypeScript

```
count.set(ch, (count.get(ch) ?? 0) + 1);
```

---

 # 16\. Frequency Count Problem

 ## Problem

 Given:

```
"hello"
```

 Count each character.

 Expected:

```
h → 1
e → 1
l → 2
o → 1
```

 ### Python

```
s = "hello"

count = {}

for ch in s:
    count[ch] = count.get(ch, 0) + 1

print(count)
```

 ### Java

```
String s = "hello";

Map<Character, Integer> count = new HashMap<>();

for (char ch : s.toCharArray()) {
    count.put(ch, count.getOrDefault(ch, 0) + 1);
}

System.out.println(count);
```

 ### TypeScript

```
const s: string = "hello";

const count: Map<string, number> = new Map();

for (const ch of s) {
    count.set(ch, (count.get(ch) ?? 0) + 1);
}

console.log(count);
```

---

 # 17\. Map Iteration

 ### Python

```
for key, value in mp.items():
    print(key, value)
```

 ### Java

```
for (Map.Entry<String, Integer> entry : mp.entrySet()) {
    System.out.println(entry.getKey());
    System.out.println(entry.getValue());
}
```

 ### TypeScript

```
for (const [key, value] of mp) {
    console.log(key, value);
}
```

---

 # 18\. Set

 A Set stores unique values.

 ### Python

```
s = set()

s.add(10)
```

 ### Java

```
Set<Integer> s = new HashSet<>();

s.add(10);
```

 ### TypeScript

```
const s: Set<number> = new Set();

s.add(10);
```

---

 # 19\. Set Methods

 | Operation | Python | Java | TypeScript |
| --- | --- | --- | --- |
| Add | `add(x)` | `add(x)` | `add(x)` |
| Check | `x in s` | `contains(x)` | `has(x)` |
| Remove | `remove(x)` | `remove(x)` | `delete(x)` |
| Size | `len(s)` | `size()` | `size` |
| Clear | `clear()` | `clear()` | `clear()` |

---

 # 20\. Remove Duplicates

 ## Python

```
arr = [1, 2, 2, 3, 3]

unique = list(set(arr))
```

 ## Java

```
int[] arr = {1, 2, 2, 3, 3};

Set<Integer> unique = new HashSet<>();

for (int x : arr) {
    unique.add(x);
}
```

 ## TypeScript

```
const arr = [1, 2, 2, 3, 3];

const unique = [...new Set(arr)];
```

---

 # 21\. Stack

 Stack follows:

```
LIFO
Last In → First Out
```

 ### Python

```
stack = []

stack.append(10)
stack.append(20)

stack.pop()
```

 ### Java

```
Deque<Integer> stack = new ArrayDeque<>();

stack.push(10);
stack.push(20);

stack.pop();
stack.peek();
```

 ### TypeScript

```
const stack: number[] = [];

stack.push(10);
stack.push(20);

stack.pop();
```

 Common operations:

```
push → add
pop  → remove top
peek → view top
```

---

 # 22\. Queue

 Queue follows:

```
FIFO
First In → First Out
```

 ### Python

```
from collections import deque

queue = deque()

queue.append(10)
queue.append(20)

queue.popleft()
queue[0]
```

 ### Java

```
Queue<Integer> queue = new LinkedList<>();

queue.offer(10);
queue.offer(20);

queue.poll();
queue.peek();
```

 ### TypeScript

```
const queue: number[] = [];

queue.push(10);
queue.push(20);

queue.shift();
```

 For large problems, avoid repeatedly using `shift()` because it can be inefficient.

 Use an index:

```
const queue: number[] = [10, 20, 30];

let front = 0;

while (front < queue.length) {
    const value = queue[front];
    front++;
}
```

---

 # 23\. Sorting

 ## Ascending numbers

 ### Python

```
arr.sort()
```

 ### Java

```
Arrays.sort(arr);
```

 ### TypeScript

```
arr.sort((a, b) => a - b);
```

---

 ## Descending

 ### Python

```
arr.sort(reverse=True)
```

 ### Java

```
Arrays.sort(arr);
```

 For objects / boxed values:

```
list.sort(Collections.reverseOrder());
```

 ### TypeScript

```
arr.sort((a, b) => b - a);
```

---

 # 24\. VERY IMPORTANT: TypeScript `sort()`

 This:

```
[10, 2, 5].sort()
```

 does NOT numerically sort the values.

 JavaScript treats them as strings for default sorting.

 Use:

```
[10, 2, 5].sort((a, b) => a - b);
```

 Result:

```
[2, 5, 10]
```

---

 # 25\. Min / Max

 | Task | Python | Java | TypeScript |
| --- | --- | --- | --- |
| Minimum | `min(arr)` | `Arrays.stream(arr).min()` | `Math.min(...arr)` |
| Maximum | `max(arr)` | `Arrays.stream(arr).max()` | `Math.max(...arr)` |
| Sum | `sum(arr)` | `Arrays.stream(arr).sum()` | `arr.reduce((a,b) => a+b, 0)` |

For very large arrays in TypeScript, spreading into `Math.min(...arr)` can hit argument limits; a loop or `reduce()` is safer.

---

 # 26\. `map`, `filter`, `reduce` in TypeScript

 ## `map`

 Transform every element.

```
const arr = [1, 2, 3];

const result = arr.map(x => x * 2);

// [2, 4, 6]
```

 Python:

```
result = [x * 2 for x in arr]
```

 Java:

```
List<Integer> result = arr.stream()
                          .map(x -> x * 2)
                          .toList();
```

---

 ## `filter`

 Keep elements satisfying a condition.

```
const result = arr.filter(x => x > 1);

// [2, 3]
```

 Python:

```
result = [x for x in arr if x > 1]
```

---

 ## `reduce`

 Convert many values into one value.

```
const sum = arr.reduce((total, x) => total + x, 0);
```

 Result:

```
6
```

 Python:

```
sum(arr)
```

---

 # 27\. Useful TypeScript Array Methods

 | Method | Purpose | Example |
| --- | --- | --- |
| `push()` | Add end | `arr.push(10)` |
| `pop()` | Remove end | `arr.pop()` |
| `shift()` | Remove beginning | `arr.shift()` |
| `unshift()` | Add beginning | `arr.unshift(10)` |
| `slice()` | Copy portion | `arr.slice(1,4)` |
| `splice()` | Insert/delete | `arr.splice(1,2)` |
| `includes()` | Contains | `arr.includes(5)` |
| `indexOf()` | Find index | `arr.indexOf(5)` |
| `reverse()` | Reverse | `arr.reverse()` |
| `sort()` | Sort | `arr.sort((a,b)=>a-b)` |
| `map()` | Transform | `arr.map(x=>x*2)` |
| `filter()` | Filter | `arr.filter(x=>x>5)` |
| `reduce()` | Accumulate | `arr.reduce(...)` |
| `find()` | Find element | `arr.find(x=>x>5)` |
| `some()` | Any match | `arr.some(x=>x>5)` |
| `every()` | All match | `arr.every(x=>x>5)` |

---

 # 28\. Java Collection Types

 | Collection | Purpose |
| --- | --- |
| `ArrayList` | Dynamic array |
| `LinkedList` | Linked list / Queue |
| `HashMap` | Key-value |
| `LinkedHashMap` | Key-value + insertion order |
| `TreeMap` | Key-value + sorted keys |
| `HashSet` | Unique values |
| `LinkedHashSet` | Unique + insertion order |
| `TreeSet` | Unique + sorted |
| `PriorityQueue` | Heap / priority queue |
| `ArrayDeque` | Stack / Queue |

---

 # 29\. Java → TypeScript Collection Equivalents

 | Java | TypeScript |
| --- | --- |
| `int[]` | `number[]` |
| `ArrayList<Integer>` | `number[]` |
| `HashMap<K,V>` | `Map<K,V>` |
| `LinkedHashMap<K,V>` | `Map<K,V>` |
| `TreeMap<K,V>` | `Map<K,V>` \+ sorting |
| `HashSet<T>` | `Set<T>` |
| `LinkedHashSet<T>` | `Set<T>` |
| `TreeSet<T>` | `Set<T>` \+ sorting |
| `Stack<T>` | `T[]` |
| `Deque<T>` | `T[]` |
| `Queue<T>` | `T[]` / custom queue |
| `PriorityQueue<T>` | Usually implement/use a heap |

---

 # 30\. Java HashMap Ordering

 ### HashMap

```
Map<Integer, String> map = new HashMap<>();
```

 No ordering guarantee.

 ### LinkedHashMap

```
Map<Integer, String> map = new LinkedHashMap<>();
```

 Maintains insertion order.

 ### TreeMap

```
Map<Integer, String> map = new TreeMap<>();
```

 Keys are sorted.

---

 # 31\. TypeScript Map Ordering

 JavaScript `Map` preserves insertion order:

```
const map = new Map<number, string>();

map.set(3, "C");
map.set(1, "A");
map.set(2, "B");

for (const [key, value] of map) {
    console.log(key, value);
}
```

 Output:

```
3 C
1 A
2 B
```

 If you want sorted keys:

```
const keys = [...map.keys()].sort((a, b) => a - b);

for (const key of keys) {
    console.log(key, map.get(key));
}
```

 Output:

```
1 A
2 B
3 C
```

---

 # 32\. Common DSA Problem Patterns

 ## Problem 1 — Reverse String

 Input:

```
"hello"
```

 Output:

```
"olleh"
```

 ### TypeScript

```
function reverseString(s: string): string {
    let result = "";

    for (let i = s.length - 1; i >= 0; i--) {
        result += s[i];
    }

    return result;
}
```

---

 # 33\. Problem 2 — Find Longest String

 Input:

```
const arr = ["Jashu", "Sakhamuri", "Chowdary"];
```

 Output:

```
Sakhamuri
```

 ### TypeScript

```
let maxLength = 0;
let longest = "";

for (const str of arr) {
    if (str.length > maxLength) {
        maxLength = str.length;
        longest = str;
    }
}

console.log(longest);
```

---

 # 34\. Problem 3 — Print All Longest Strings

 If:

```
const arr = ["cat", "dog", "apple", "tree"];
```

 Output:

```
apple
```

 If:

```
const arr = ["cat", "dog", "fox"];
```

 Output:

```
cat
dog
fox
```

 ### TypeScript

```
let maxLength = 0;

for (const str of arr) {
    if (str.length > maxLength) {
        maxLength = str.length;
    }
}

for (const str of arr) {
    if (str.length === maxLength) {
        console.log(str);
    }
}
```

---

 # 35\. Problem 4 — Character Frequency

 Input:

```
"programming"
```

 ### TypeScript

```
const count = new Map<string, number>();

for (const ch of "programming") {
    count.set(ch, (count.get(ch) ?? 0) + 1);
}

for (const [ch, frequency] of count) {
    console.log(ch, frequency);
}
```

---

 # 36\. Problem 5 — First Non-Repeating Character

 Input:

```
"swiss"
```

 Output:

```
w
```

 ### TypeScript

```
function firstUnique(s: string): string {

    const count = new Map<string, number>();

    // Count
    for (const ch of s) {
        count.set(ch, (count.get(ch) ?? 0) + 1);
    }

    // Find first character with count 1
    for (const ch of s) {
        if (count.get(ch) === 1) {
            return ch;
        }
    }

    return "";
}
```

 Pattern:

```
1. Count
2. Traverse again
3. Find required element
```

---

 # 37\. Problem 6 — Two Sum

 Input:

```
arr = [2, 7, 11, 15]
target = 9
```

 Output:

```
[0, 1]
```

 ### TypeScript

```
function twoSum(arr: number[], target: number): number[] {

    const map = new Map<number, number>();

    for (let i = 0; i < arr.length; i++) {

        const complement = target - arr[i];

        if (map.has(complement)) {
            return [map.get(complement)!, i];
        }

        map.set(arr[i], i);
    }

    return [];
}
```

 Important Map pattern:

```
if (map.has(x)) {
    // found
}

map.set(x, value);
```

---

 # 38\. Problem 7 — Remove Duplicates

```
const arr = [1, 2, 2, 3, 3, 4];

const unique = [...new Set(arr)];

console.log(unique);
```

 Output:

```
[1, 2, 3, 4]
```

---

 # 39\. Problem 8 — Check Duplicate

 ### TypeScript

```
function containsDuplicate(arr: number[]): boolean {

    const seen = new Set<number>();

    for (const num of arr) {

        if (seen.has(num)) {
            return true;
        }

        seen.add(num);
    }

    return false;
}
```

 Pattern:

```
Set + has() + add()
```

---

 # 40\. Problem 9 — Palindrome

 Input:

```
"madam"
```

 Output:

```
true
```

 ### TypeScript

```
function isPalindrome(s: string): boolean {

    let left = 0;
    let right = s.length - 1;

    while (left < right) {

        if (s[left] !== s[right]) {
            return false;
        }

        left++;
        right--;
    }

    return true;
}
```

 This is the **two-pointer pattern**.

---

 # 41\. Problem 10 — Maximum Number

 ### TypeScript

```
function findMax(arr: number[]): number {

    let max = arr[0];

    for (const num of arr) {
        if (num > max) {
            max = num;
        }
    }

    return max;
}
```

---

 # 42\. Problem 11 — Sum Array

 ### TypeScript

 Normal loop:

```
let sum = 0;

for (const num of arr) {
    sum += num;
}
```

 Using `reduce()`:

```
const sum = arr.reduce((total, num) => total + num, 0);
```

---

 # 43\. Problem 12 — Count Even Numbers

 ### TypeScript

```
let count = 0;

for (const num of arr) {
    if (num % 2 === 0) {
        count++;
    }
}
```

---

 # 44\. Problem 13 — Reverse Array

 ### TypeScript

```
arr.reverse();
```

 Manual:

```
let left = 0;
let right = arr.length - 1;

while (left < right) {

    [arr[left], arr[right]] = [arr[right], arr[left]];

    left++;
    right--;
}
```

---

 # 45\. Problem 14 — Find Maximum Frequency

 Input:

```
"banana"
```

 Frequency:

```
b → 1
a → 3
n → 2
```

 Output:

```
a
```

 ### TypeScript

```
const count = new Map<string, number>();

for (const ch of "banana") {
    count.set(ch, (count.get(ch) ?? 0) + 1);
}

let maxChar = "";
let maxCount = 0;

for (const [ch, frequency] of count) {

    if (frequency > maxCount) {
        maxCount = frequency;
        maxChar = ch;
    }
}

console.log(maxChar);
```

---

 # 46\. DSA Patterns to Learn

 | Pattern | Typical Data Structure |
| --- | --- |
| Frequency Count | `Map` |
| Duplicate Detection | `Set` |
| Two Sum | `Map` |
| Two Pointers | Array/String |
| Sliding Window | Array/String + `Map` |
| Binary Search | Sorted Array |
| Stack Problems | Stack |
| BFS | Queue |
| DFS | Stack / Recursion |
| Top K | Heap / Priority Queue |
| Graph | `Map` / Array |
| Tree Traversal | Queue / Stack |
| Dynamic Programming | Array / Map |

---

 # 47\. Most Important TypeScript DSA Syntax

```
// Array
const arr: number[] = [];

// String
const s: string = "hello";

// Map
const map: Map<string, number> = new Map();

// Set
const set: Set<number> = new Set();

// Stack
const stack: number[] = [];

// Queue
const queue: number[] = [];

// Loop values
for (const x of arr) {}

// Loop indexes
for (let i = 0; i < arr.length; i++) {}

// String loop
for (const ch of s) {}

// Map loop
for (const [key, value] of map) {}

// Set loop
for (const value of set) {}
```

---

 # 48\. The 20 Methods You Should Memorize

 ## Python

```
len()
append()
pop()
sort()
reverse()
split()
join()
lower()
upper()
strip()
find()
replace()
get()
items()
keys()
values()
add()
remove()
```

 ## Java

```
length()
charAt()
substring()
toLowerCase()
toUpperCase()
indexOf()
contains()
split()
trim()
add()
remove()
get()
set()
size()
put()
getOrDefault()
containsKey()
entrySet()
add()
contains()
```

 ## TypeScript / JavaScript

```
length
charAt()
slice()
substring()
toLowerCase()
toUpperCase()
indexOf()
includes()
split()
join()
trim()
replace()
push()
pop()
shift()
unshift()
splice()
slice()
sort()
reverse()
map()
filter()
reduce()
find()
some()
every()

Map:
set()
get()
has()
delete()
clear()
keys()
values()

Set:
add()
has()
delete()
clear()
```

---

 # 49\. Quick Translation Table

 When moving between languages:

```
Python                  Java                     TypeScript

len(s)                  s.length()              s.length
s[i]                    s.charAt(i)             s[i]
append(x)               add(x)                  push(x)
pop()                   remove(...)             pop()
x in arr                contains(x)             includes(x)

dict                    HashMap                 Map
set                     HashSet                 Set

dict[key] = value       put(key,value)          set(key,value)
dict.get(key)           get(key)                get(key)
key in dict             containsKey(key)        has(key)

del dict[key]           remove(key)             delete(key)

len(dict)               size()                  size

for x in arr             for (x : arr)           for (const x of arr)

for i in range(len())   for (int i...)          for (let i...)
```

---

 # 50\. Golden Rules for Switching Java → TypeScript

```
Java                         TypeScript

String.length()       →      string.length

array.length          →      array.length

ArrayList.size()      →      array.length

HashMap.put()         →      Map.set()

HashMap.get()         →      Map.get()

HashMap.containsKey() →      Map.has()

HashMap.remove()      →      Map.delete()

HashSet.add()         →      Set.add()

HashSet.contains()    →      Set.has()

HashSet.remove()      →      Set.delete()

==                    →      ===

for (x : arr)         →      for (const x of arr)
```

---

 # 51\. Practice Problems

 ## Easy — Strings

 1. Reverse a string.
2. Check if a string is palindrome.
3. Count vowels.
4. Count each character.
5. Find the first non-repeating character.
6. Find the first repeating character.
7. Check if two strings are anagrams.
8. Remove duplicate characters.
9. Find the longest word.
10. Count words in a sentence.

 ## Easy — Arrays

 1. Find maximum.
2. Find minimum.
3. Find second maximum.
4. Reverse an array.
5. Find duplicate numbers.
6. Remove duplicates.
7. Count even and odd numbers.
8. Find sum.
9. Find missing number.
10. Move zeroes to the end.

 ## HashMap / Set

 1. Character frequency.
2. Number frequency.
3. Two Sum.
4. Contains Duplicate.
5. First Unique Character.
6. Group Anagrams.
7. Intersection of two arrays.
8. Find common elements.
9. Find elements occurring more than once.
10. Find the most frequent element.

 ## Two Pointers

 1. Palindrome.
2. Reverse array.
3. Two Sum in sorted array.
4. Remove duplicates from sorted array.
5. Move zeroes.
6. Container With Most Water.

 ## Sliding Window

 1. Maximum sum subarray of size K.
2. Longest substring without repeating characters.
3. Minimum size subarray sum.
4. Longest substring with at most K distinct characters.

 ## Stack

 1. Valid Parentheses.
2. Reverse a stack.
3. Min Stack.
4. Next Greater Element.
5. Daily Temperatures.

 ## Queue / BFS

 1. Binary tree level order traversal.
2. Number of islands.
3. Rotting oranges.
4. Shortest path in a grid.

---

 # 52\. Complexity Cheat Sheet

 | Operation | Array | Map | Set |
| --- | --- | --- | --- |
| Access | O(1) | O(1)\* | — |
| Search | O(n) | O(1)\* | O(1)\* |
| Insert | O(1)\* | O(1)\* | O(1)\* |
| Delete | O(n) | O(1)\* | O(1)\* |

`*` = average/amortized complexity for typical hash-based implementations.

 Sorting:

```
O(n log n)
```

 Binary Search:

```
O(log n)
```

 Nested loop:

```
O(n²)
```

 Single loop:

```
O(n)
```

---

 # 53\. The Most Important DSA Templates

 ## Frequency Map

```
const map = new Map<string, number>();

for (const x of arr) {
    map.set(x, (map.get(x) ?? 0) + 1);
}
```

 ## Seen Set

```
const seen = new Set<number>();

for (const x of arr) {

    if (seen.has(x)) {
        // duplicate
    }

    seen.add(x);
}
```

 ## Two Pointers

```
let left = 0;
let right = arr.length - 1;

while (left < right) {

    // logic

    left++;
    right--;
}
```

 ## Sliding Window

```
let left = 0;

for (let right = 0; right < arr.length; right++) {

    // add arr[right]

    while (/* invalid */) {
        // remove arr[left]
        left++;
    }

    // update answer
}
```

 ## Binary Search

```
let left = 0;
let right = arr.length - 1;

while (left <= right) {

    const mid = Math.floor((left + right) / 2);

    if (arr[mid] === target) {
        return mid;
    }

    if (arr[mid] < target) {
        left = mid + 1;
    } else {
        right = mid - 1;
    }
}

return -1;
```

---

 # 54\. Final Mental Model

 When solving a DSA problem, ask:

```
Do I need key → value?
        ↓
       Map

Do I only need unique values?
        ↓
       Set

Do I need Last In First Out?
        ↓
       Stack

Do I need First In First Out?
        ↓
       Queue

Do I need sorted data?
        ↓
       Sort / TreeMap / Heap

Do I need left + right?
        ↓
       Two Pointers

Do I need a moving range?
        ↓
       Sliding Window

Do I need frequency?
        ↓
       Map

Do I need to quickly check "seen before"?
        ↓
       Set

Do I need target search in sorted data?
        ↓
       Binary Search
```

 # Most Important Things to Memorize for TypeScript DSA

```
// Array
const arr: number[] = [];

// String
const s: string = "";

// Map
const map = new Map<string, number>();

map.set(key, value);
map.get(key);
map.has(key);
map.delete(key);

// Set
const set = new Set<number>();

set.add(x);
set.has(x);
set.delete(x);

// Array
arr.push(x);
arr.pop();
arr.shift();
arr.unshift(x);
arr.slice(start, end);
arr.splice(start, count);
arr.includes(x);
arr.indexOf(x);
arr.sort((a, b) => a - b);
arr.reverse();

// Loops
for (const x of arr) {}
for (let i = 0; i < arr.length; i++) {}
for (const [key, value] of map) {}
for (const x of set) {}
```

 > If you're coming from Java, the biggest adjustment is that TypeScript's `Map` and `Set` APIs use JavaScript-style method names (`set`, `has`, `delete`), while arrays use methods like `push`, `pop`, `splice`, and `slice`.