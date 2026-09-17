# Python vs Java vs TypeScript vs JavaScript
## OOP, Functions & Modern Syntax — Complete Cheat Sheet

> Practical reference for DSA, backend, interviews, and everyday programming.
> Brush up all 4 languages at a time — same concept, side-by-side syntax.

---

# **0. NAMING CONVENTIONS — The Rules First**

Every language has its own naming style. Following these makes your code look native.

## **The Four Naming Styles**

```text
PascalCase     → MyClass, HttpRequest        (every word capitalized)
camelCase      → myMethod, userName          (first word small, rest capitalized)
snake_case     → my_method, user_name        (words joined with underscore)
UPPER_SNAKE    → MAX_RETRY, API_KEY          (all caps with underscores)
kebab-case     → my-file.ts, user-service.ts (words joined with hyphen)
```

## **Master Table — What to Name What**

| **Element**       | **Python**              | **Java**                | **TypeScript/JS**          |
|-------------------|-------------------------|-------------------------|----------------------------|
| Class             | `PascalCase`            | `PascalCase`            | `PascalCase`               |
| Interface         | — (no keyword)         | `PascalCase` (`IPrinter` optional) | `PascalCase` (`IPrinter` optional) |
| Method / Function | `snake_case`            | `camelCase`             | `camelCase`                |
| Variable          | `snake_case`            | `camelCase`             | `camelCase`                |
| Private member    | `_name` (convention)    | `private name`          | `private name` or `#name`  |
| Protected member  | `_name` (convention)    | `protected name`        | `protected name`           |
| Constant          | `UPPER_SNAKE`           | `UPPER_SNAKE`           | `UPPER_SNAKE` or `camelCase` |
| Boolean variable | `is_active`, `has_items`| `isActive`, `hasItems`  | `isActive`, `hasItems`     |
| File name         | `my_module.py`          | `MyClass.java` (must match class name!) | `my-service.ts`, `UserService.ts` |
| Package / module  | `my_package/`           | `com.company.app` (all lowercase) | `@my-org/utils` |
| Type alias        | —                       | —                       | `PascalCase` (`type User = ...`) |
| Enum              | `PascalCase` class      | `PascalCase`            | `PascalCase`               |
| Async function    | `async def fetch_data`  | `CompletableFuture<Task>` | `async function fetchData` |

## **Critical Rules You MUST Know**

### Java — file name MUST match public class name

```java
// File MUST be named Person.java — compile ERROR otherwise
public class Person { }

// One public class per file. Other non-public classes allowed in same file.
public class Person { }          // public — matches file name
class PersonHelper { }           // allowed — not public
```

### Python — snake_case everywhere except classes and constants

```python
class UserService:               # PascalCase class
    MAX_USERS = 100              # UPPER_SNAKE constant
    _secret_key = "abc"          # _private by convention

    def get_user_name(self):     # snake_case method
        user_email = "a@b.com"   # snake_case variable
        is_active = True         # is_/has_ for booleans
        return user_email
```

### JavaScript/TypeScript — the file naming depends on what's inside

```text
React component file     → PascalCase.tsx    (UserProfile.tsx)
Service / util file      → camelCase.ts      (userService.ts) or kebab (user-service.ts)
Constant file            → UPPER_SNAKE.ts    (API_ENDPOINTS.ts)
Test file                → name.test.ts      (userService.test.ts)
Type definition file     → name.d.ts        (declaration file)

Company conventions vary — pick one and stay consistent.
```

## **Real Example — Same Logic, Native Style in Each Language**

```python
# Python — snake_case
class OrderService:
    MAX_RETRIES = 3

    def __init__(self, payment_gateway):
        self._payment_gateway = payment_gateway
        self._is_connected = False

    def process_order(self, order_id):
        retry_count = 0
        while retry_count < self.MAX_RETRIES:
            if self._is_connected:
                return self._payment_gateway.charge(order_id)
            retry_count += 1
        return None
```

```java
// Java — camelCase methods, PascalCase class, UPPER_SNAKE constants
public class OrderService {
    public static final int MAX_RETRIES = 3;

    private PaymentGateway paymentGateway;
    private boolean isConnected = false;

    public OrderService(PaymentGateway paymentGateway) {
        this.paymentGateway = paymentGateway;
    }

    public Receipt processOrder(String orderId) {
        int retryCount = 0;
        while (retryCount < MAX_RETRIES) {
            if (isConnected) {
                return paymentGateway.charge(orderId);
            }
            retryCount++;
        }
        return null;
    }
}
```

```typescript
// TypeScript — camelCase methods, PascalCase class
class OrderService {
    static readonly MAX_RETRIES = 3;
    private static readonly MAX_RETRIES2 = 3;

    private paymentGateway: PaymentGateway;
    private isConnected = false;

    constructor(private readonly gateway: PaymentGateway) {}

    processOrder(orderId: string): Receipt | null {
        let retryCount = 0;
        while (retryCount < OrderService.MAX_RETRIES) {
            if (this.isConnected) {
                return this.gateway.charge(orderId);
            }
            retryCount++;
        }
        return null;
    }
}
```

---

# **1. Functions**

## **Basic Function**

### **Python**
```python
def add(a, b):
    return a + b

result = add(10, 20)
```

### **Java** (must live inside a class)
```java
static int add(int a, int b) {
    return a + b;
}

int result = add(10, 20);
```

### **TypeScript/JavaScript**
```ts
function add(a: number, b: number): number {   // JS: drop the types
    return a + b;
}

const result = add(10, 20);
```

## **2. Function Without Return**

### **Python**
```python
def greet(name):
    print("Hello", name)
```

### **Java** — `void` means "returns nothing"
```java
static void greet(String name) {
    System.out.println("Hello " + name);
}
```

### **TypeScript** — `void` type
```ts
function greet(name: string): void {
    console.log("Hello", name);
}
```

## **3. Optional / Default Parameters**

### **Python**
```python
def greet(name="Guest"):
    print(name)

greet()          # Guest
greet("Jashu")   # Jashu
```

### **Java** — no default params. Use method overloading:
```java
static void greet() {
    greet("Guest");          // delegate
}

static void greet(String name) {
    System.out.println(name);
}
```

### **TypeScript**
```ts
function greet(name: string = "Guest"): void {
    console.log(name);
}

// Optional without default (name is string | undefined)
function greet2(name?: string): void {
    console.log(name ?? "Guest");
}
```

## **4. Function Overloading**

| **Language** | **Support?** | **How** |
|--------------|--------------|---------|
| Java         | True overloading — compiler picks by signature | multiple methods, same name |
| TypeScript   | Overload signatures only (one implementation) | declare + implement |
| JavaScript   | No — last definition wins | check `arguments` manually |
| Python       | No — last definition wins | `*args`, `**kwargs`, or `functools.singledispatch` |

### **Java** — the only language with TRUE overloading
```java
static int add(int a, int b) { return a + b; }
static int add(int a, int b, int c) { return a + b + c; }
static double add(double a, double b) { return a + b; }
// Compiler picks the right one by argument types & count
```

### **TypeScript** — signatures only, ONE implementation
```ts
function add(a: number, b: number): number;
function add(a: string, b: string): string;
function add(a: any, b: any): any {     // implementation must accept all
    return a + b;
}
add(1, 2);        // number ✓
add("a", "b");    // string ✓
add(true, false); // ERROR — no matching signature
```

### **Python** — emulate with defaults / *args
```python
def add(*args, initial=0):
    return initial + sum(args)

add(1, 2)                # 3
add(1, 2, 3, initial=10) # 16
```

## **5. `*args` / Varargs / Rest — Variable Arguments**

### **Python** — `*args` (positional) and `**kwargs` (keyword)
```python
def add(*numbers):              # numbers is a tuple
    return sum(numbers)

def process(**options):         # options is a dict
    print(options.get("verbose", False))

add(1, 2)               # 3
add(1, 2, 3, 4)         # 10
process(verbose=True)   # {'verbose': True}
```

### **Java** — varargs `...`
```java
static int add(int... numbers) {          // numbers is int[]
    int total = 0;
    for (int n : numbers) total += n;
    return total;
}

add();              // 0 — empty is fine
add(1, 2);          // 3
add(new int[]{1,2,3}); // also works — pass an array
```

### **TypeScript/JavaScript** — rest parameters
```ts
function add(...numbers: number[]): number {
    return numbers.reduce((sum, x) => sum + x, 0);
}

// With leading fixed params — rest MUST be last
function greet(greeting: string, ...names: string[]): void {
    for (const n of names) console.log(greeting, n);
}
greet("Hi", "Jashu", "Alice");
```

## **6. Lambda / Arrow Functions**

### **Python** — `lambda` (one expression only)
```python
square = lambda x: x * x
add = lambda a, b: a + b

# mostly used inline:
sorted(users, key=lambda u: u["age"])
list(map(lambda x: x * 2, nums))
```

### **Java** — lambda expressions (Java 8+)
```java
Function<Integer, Integer> square = x -> x * x;
BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;

// multi-line lambda:
Function<Integer, Integer> factorial = n -> {
    int result = 1;
    for (int i = 2; i <= n; i++) result *= i;
    return result;
};
```

### **TypeScript/JavaScript** — arrow functions
```ts
const square = (x: number): number => x * x;
const add = (a: number, b: number) => a + b;

const factorial = (n: number): number => {
    let result = 1;
    for (let i = 2; i <= n; i++) result *= i;
    return result;
};
```

## **7. Arrow Short Syntax Rules (TS/JS only)**

```ts
// One parameter → no parentheses needed
const square = x => x * x;

// Zero or 2+ parameters → parentheses required
const greet = () => "Hello";
const add = (a, b) => a + b;

// Single expression → no braces, implicit return
const double = x => x * 2;

// Multiple statements → braces + explicit return
const compute = x => {
    const y = x * 2;
    return y + 10;
};

// Returning an object literal → wrap in parentheses!
const makeUser = name => ({ name: name, age: 25 });
// without ( ) the { } is treated as the function body!
```

**The #1 arrow function difference — `this`:**
```ts
// Regular function: gets its OWN 'this'
// Arrow function: INHERITS 'this' from surrounding scope

class Timer {
    seconds = 0;

    start() {
        // regular function: 'this' is wrong here
        setInterval(function () {
            // this.seconds  → undefined! 'this' is not the Timer
        }, 1000);

        // arrow function: 'this' is the Timer instance ✓
        setInterval(() => {
            this.seconds++;   // works correctly
        }, 1000);
    }
}
```

## **8. Callbacks**

A callback is a function passed as an argument to another function.

### **TypeScript/JavaScript** — the language of callbacks
```ts
function process(x: number, callback: (value: number) => number): number {
    return callback(x);
}

process(10, x => x * 2);   // 20

// Typed callback signature
type MapFn<T, U> = (item: T, index: number) => U;
```

### **Java** — Functional interfaces (`Function`, `Consumer`, `Supplier`, `Predicate`)
```java
import java.util.function.*;

Function<Integer, Integer> doubleIt = x -> x * 2;
Predicate<Integer> isEven = x -> x % 2 == 0;
Consumer<String> printer = s -> System.out.println(s);
Supplier<Double> random = () -> Math.random();

// Accepts a callback
static int process(int x, Function<Integer, Integer> fn) {
    return fn.apply(x);
}

process(10, x -> x * 2);   // 20
```

### **Python** — functions are objects, pass directly
```python
def process(x, callback):
    return callback(x)

process(10, lambda x: x * 2)      # 20

def double(x): return x * 2
process(10, double)               # pass named function too
```

## **9. `map()` — Transform Every Element**

### **TypeScript/JavaScript**
```ts
const nums = [1, 2, 3];
const result = nums.map(x => x * 2);          // [2, 4, 6]
const withIndex = nums.map((x, i) => x * i);  // [0, 2, 6]
```

### **Python** — list comprehension (preferred) or `map()`
```python
nums = [1, 2, 3]

result = [x * 2 for x in nums]        # [2, 4, 6] — PREFERRED
result2 = list(map(lambda x: x*2, nums))  # [2, 4, 6] — functional style
```

### **Java** — Streams
```java
List<Integer> nums = List.of(1, 2, 3);

List<Integer> result = nums.stream()
                           .map(x -> x * 2)
                           .toList();   // [2, 4, 6]
```

## **10. `filter()` — Keep Matching Elements**

### **TypeScript/JavaScript**
```ts
const nums = [1, 2, 3, 4, 5];
const evens = nums.filter(x => x % 2 === 0);   // [2, 4]

// Chaining
const result = nums
    .filter(x => x % 2 === 0)   // [2, 4]
    .map(x => x * 10);          // [20, 40]
```

### **Python**
```python
nums = [1, 2, 3, 4, 5]
evens = [x for x in nums if x % 2 == 0]   # [2, 4] — PREFERRED

# chain the same way:
result = [x * 10 for x in nums if x % 2 == 0]   # [20, 40]
```

### **Java**
```java
List<Integer> result = nums.stream()
                           .filter(x -> x % 2 == 0)
                           .map(x -> x * 10)
                           .toList();   // [20, 40]
```

## **11. `reduce()` — Combine to One Value**

### **TypeScript/JavaScript**
```ts
const nums = [1, 2, 3, 4];

const sum = nums.reduce((total, x) => total + x, 0);        // 10
const product = nums.reduce((acc, x) => acc * x, 1);        // 24
const max = nums.reduce((a, b) => Math.max(a, b));          // 4 (no initial)

// reduce to an object (frequency counter)
const freq = ["a","b","a"].reduce<Record<string, number>>((acc, ch) => {
    acc[ch] = (acc[ch] ?? 0) + 1;
    return acc;
}, {});   // { a: 2, b: 1 }
```

### **Python**
```python
from functools import reduce
nums = [1, 2, 3, 4]

sum_ = sum(nums)                                  # 10 (built-in)
product = reduce(lambda acc, x: acc * x, nums, 1) # 24
freq = {}
for ch in ["a", "b", "a"]:
    freq[ch] = freq.get(ch, 0) + 1
```

### **Java**
```java
int sum = nums.stream().mapToInt(Integer::intValue).sum();   // 10

int product = nums.stream().reduce(1, (acc, x) -> acc * x);  // 24
```

**Stream vs Array methods mental model:**
```text
TS/JS:   arr.filter(...).map(...).reduce(...)     — chain on array directly
Java:    list.stream().filter(...).map(...).toList() — must open stream first
Python:  [expr for x in list if cond]              — comprehension (read backwards)
```

---

# **12. Object-Oriented Programming — The Four Pillars**

```text
1. Encapsulation  → hide data behind methods
2. Inheritance    → child gets parent's features
3. Polymorphism   → same call, different behavior
4. Abstraction    → define WHAT, hide HOW
```

## **13. Class + Object**

### **Python**
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print("Hello", self.name)

person = Person("Jashu", 25)
person.greet()
```

### **Java**
```java
class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void greet() {
        System.out.println("Hello " + name);
    }
}

Person person = new Person("Jashu", 25);
person.greet();
```

### **TypeScript**
```ts
class Person {
    // parameter properties — one-line shorthand (see #18)
    constructor(
        public name: string,
        public age: number
    ) {}

    greet(): void {
        console.log("Hello " + this.name);
    }
}

const person = new Person("Jashu", 25);
person.greet();
```

## **14. Constructor — Mental Translation**

```text
Python       → def __init__(self, ...)     always named __init__, self is explicit
Java         → ClassName(...)               named after the class, this is implicit
TypeScript   → constructor(...)            keyword "constructor", this is implicit
```

**Java EXTRA rules (interview favorite):**
- If you write NO constructor → compiler gives a free no-arg constructor
- If you write ANY constructor → the free one disappears
- Constructor can be `private` (singleton pattern!), can call another via `this(...)`

```java
class Person {
    private String name;

    Person() {                    // no-arg
        this("Guest");            // calls the other constructor
    }

    Person(String name) {         // overloaded
        this.name = name;
    }

    private Person(int id) {      // private constructor → singleton pattern
        this.name = "Internal";
    }
}
```

## **15. `this` vs `self`**

```text
Python       → self    — EXPLICIT parameter, you must write it
Java         → this    — implicit keyword
TypeScript   → this    — implicit keyword, but behaves differently in arrow fns
```

**Python gotcha — `self` is just a name (but NEVER rename it):**
```python
class Counter:
    def __init__(self):
        self.count = 0        # instance attribute — per object

    def increment(self):
        self.count += 1

c1 = Counter()
c2 = Counter()
c1.increment()
c1.count   # 1
c2.count   # 0 — separate storage per object
```

**Python also has `cls` for class methods (see #26).**

## **16. Encapsulation**

### **Java** — enforced at compile time
```java
class BankAccount {
    private double balance;              // hidden — compile error if accessed outside

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;            // controlled access only
        }
    }

    public double getBalance() {
        return balance;
    }
}

// BankAccount acc = new BankAccount();
// acc.balance = 999999;   ← COMPILE ERROR — private
```

### **TypeScript** — enforced at compile time only, erased at runtime
```ts
class BankAccount {
    private balance: number = 0;

    deposit(amount: number): void {
        if (amount > 0) this.balance += amount;
    }

    getBalance(): number {
        return this.balance;
    }
}

// const acc = new BankAccount();
// acc.balance = 999999;   ← COMPILE ERROR in TS
// acc["balance"] = 999;  ← RUNS FINE in compiled JS! TS privacy is erased
```

### **JavaScript** — `#` private fields are truly private (ES2022+)
```javascript
class BankAccount {
    #balance = 0;                     // TRUE runtime privacy

    deposit(amount) {
        if (amount > 0) this.#balance += amount;
    }

    get balance() {                   // getter to read
        return this.#balance;
    }
}

const acc = new BankAccount();
// acc.#balance        ← SyntaxError — cannot even name it from outside
// acc["#balance"]     ← undefined — it's not a normal property
```

### **Python** — conventions only, no enforcement
```python
class BankAccount:
    def __init__(self):
        self._balance = 0             # "protected" — convention only

    def deposit(self, amount):
        if amount > 0:
            self._balance += amount

    @property                          # getter
    def balance(self):
        return self._balance

acc = BankAccount()
acc._balance = 999999                 # WORKS — nothing stops you!
acc._balance                          # Python trusts the developer
```

## **17. ACCESS MODIFIERS — SPECIAL POWERS IN EACH LANGUAGE**

## **The Master Table**

| **Modifier**  | **Python**                          | **Java**                    | **TypeScript**              | **JavaScript**              |
|---------------|-------------------------------------|-----------------------------|-----------------------------|-----------------------------|
| public        | default — everything is public      | `public` (default for members? No — package default) | `public` (true default) | default — everything is public |
| private       | `__name` (name mangling) or `_name` (convention) | `private` — real, compile-enforced | `private` — compile-time only, erased in JS | `#name` — TRUE runtime privacy |
| protected     | `_name` (convention only)           | `protected` — package + subclasses | `protected` — compile-time only | ❌ not available |
| package       | ❌ doesn't exist                    | DEFAULT (no keyword) — same package only | ❌ doesn't exist        | ❌ doesn't exist            |
| readonly/final| ❌ (convention, or custom `__setattr__`) | `final` — cannot reassign | `readonly` — compile-time only | ❌ |
| abstract      | `@abstractmethod` + ABC             | `abstract` class/method     | `abstract` class/method      | ❌ not available |

## **Python's Special Powers — Name Mangling**

```python
class Secure:
    def __init__(self):
        self.public_data = "visible"        # public — anything
        self._protected_data = "internal"    # convention: "please don't touch"
        self.__private_data = "hidden"       # name mangled!

s = Secure()
s.public_data          # "visible" ✓
s._protected_data      # "internal" ✓ — works, but you broke the convention
s.__private_data       # AttributeError!
s._Secure__private_data  # "hidden" — name mangling exposes the trick

# Python renames __private_data → _ClassName__private_data
# Purpose: prevent ACCIDENTAL access and subclass name collisions,
# NOT real security. Everyone knows the trick.
```

## **Java's Special Power — Package-Private (the secret default)**

```java
// No modifier = package-private (default) — the ONE Java gotcha

public class User {
    public String name;       // everywhere
    private int age;          // this class only
    protected String email;   // same package + subclasses (anywhere)
    String city;              // SAME PACKAGE ONLY — no keyword needed!
}
```

```text
Visibility chart for Java:
                         ┌──────┬─────┬─────┬──────────┐
                         │ same │ sub │ sub │  world   │
                         │ class│ in  │ in  │          │
                         │      │ pkg │other│          │
    private              │  ✓   │  ✗  │  ✗  │    ✗     │
    (default/package)    │  ✓   │  ✓  │  ✗  │    ✗     │
    protected            │  ✓   │  ✓  │  ✓  │    ✗     │
    public               │  ✓   │  ✓  │  ✓  │    ✓     │
                         └──────┴─────┴─────┴──────────┘
    NOTE: "sub in other package" for (default) is ✗ — subclasses
    outside the package CANNOT see package-private members.
```

**Java `final` — three uses:**
```java
final int MAX = 100;              // 1. constant — cannot reassign

final class MathUtil { }          // 2. class — cannot be extended (String is final!)

final void calc() { }            // 3. method — cannot be overridden
```

**Java `static` — special powers:**
```java
class Counter {
    static int count = 0;              // ONE copy for ALL objects
    int instanceId;                    // separate copy per object

    static final double PI = 3.14159;  // constant — static + final

    Counter() {
        count++;                      // shared across all instances
        instanceId = count;
    }

    static int getCount() {            // static method
        return count;
        // CANNOT use 'this' or instanceId here!
        // static context sees static members only
    }
}
new Counter(); new Counter();
Counter.getCount();   // 2 — call on class, not object
```

**Static initialization block (Java) — runs ONCE when class loads:**
```java
class Config {
    static Properties props;

    static {                            // runs once, before first use
        props = new Properties();
        props.put("env", "prod");
    }
}
```

## **TypeScript's Special Powers**

```ts
class User {
    public name: string;          // default — writing it is optional
    private age: number;          // compile-time only
    protected email: string;      // compile-time only
    readonly id: number;          // can read, can't reassign (compile-time)
    #password: string;            // TRUE private — survives compilation!

    constructor(name: string, age: number, email: string, id: number) {
        this.name = name;
        this.age = age;
        this.email = email;
        this.id = id;
        this.#password = "secret";
    }
}

// Compile to JS → private/protected/readonly ALL DISAPPEAR:
// const u = new User(...)
// u.age            → TS blocks it, plain JS allows it!
// u.#password      → blocked even in plain JS (native # field)
```

## **18. TypeScript Constructor Shortcut (Parameter Properties)**

```ts
// LONG form
class Person {
    private name: string;
    private age: number;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }
}

// SHORT form — auto-declares AND auto-assigns
class Person {
    constructor(
        private name: string,
        private age: number
    ) {}
    // TS generates the fields + assignment behind the scenes
}
```

## **19. Inheritance**

```text
Python       → class Dog(Animal):
Java         → class Dog extends Animal
TypeScript   → class Dog extends Animal
```

## **20. `super` — Call the Parent**

```text
Python       → super().__init__(args)     + super().method(args)
Java         → super(args)                + super.method(args)
TypeScript   → super(args)                + super.method(args)
```

**ORDER MATTERS in constructors (Java/TS):**
```ts
class Dog extends Animal {
    constructor(name: string) {
        super(name);                    // MUST be first line in TS/Java
        console.log("Dog constructor");
    }
}
// Output order: "Animal constructor" → "Dog constructor"
// Parent builds first, then the child adds its parts.
```

```python
class Dog(Animal):
    def __init__(self):
        super().__init__()               # order flexible in Python, but convention: first
        print("Dog constructor")
```

## **21. Method Overriding**

### **Java** — `@Override` annotation (recommended, compiler-checked)
```java
class Animal {
    void speak() { System.out.println("Animal"); }
}

class Dog extends Animal {
    @Override                          // compiler verifies a parent method exists
    void speak() { System.out.println("Woof"); }
}
```

### **TypeScript** — `override` keyword (TS 4.3+, with noImplicitOverride)
```ts
class Animal {
    speak(): void { console.log("Animal"); }
}

class Dog extends Animal {
    override speak(): void { console.log("Woof"); }
}
```

### **Python** — just redefine (optionally call super)
```python
class Dog(Animal):
    def speak(self):
        print("Woof")
        # optionally: super().speak() to run parent version too
```

## **22. Polymorphism**

```ts
const animals: Animal[] = [new Dog(), new Cat()];
for (const animal of animals) {
    animal.speak();    // Woof / Meow — actual object decides
}
```

```java
Animal a = new Dog();      // parent reference, child object
a.speak();                 // "Woof" — JVM looks at the REAL object type

// The interview line: "The REFERENCE TYPE decides what you CAN call.
// The OBJECT TYPE decides WHICH implementation RUNS."
```

```python
animals = [Dog(), Cat()]
for animal in animals:
    animal.speak()         # duck typing — anything with .speak() works
```

## **23. Abstraction**

### **Java**
```java
abstract class Animal {
    abstract void speak();                 // children MUST implement

    void sleep() {                         // shared concrete method
        System.out.println("Sleeping");
    }
}
// new Animal();  ← COMPILE ERROR — can't instantiate abstract class
```

### **TypeScript** — identical shape
```ts
abstract class Animal {
    abstract speak(): void;
    sleep(): void { console.log("Sleeping"); }
}
```

### **Python** — needs `ABC` + `@abstractmethod`
```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self): ...
    # Without (ABC, @abstractmethod) — a plain class, NO enforcement!
```

## **24. Interfaces**

### **TypeScript**
```ts
interface Person {
    name: string;
    age: number;
    greet(): void;
    email?: string;               // optional property
}

class Student implements Person {
    constructor(
        public name: string,
        public age: number
    ) {}
    greet(): void { console.log("Hello"); }
}
```

### **Java**
```java
interface Person {
    void greet();

    // Java 8+: default methods allowed
    default void sleep() {
        System.out.println("Sleeping");
    }
}

class Student implements Person {
    public void greet() { System.out.println("Hello"); }
}

// Java's superpower: implement MANY interfaces
class Student implements Person, Comparable<Student>, Serializable {}
```

### **Python** — Protocol (structural typing — "if it has the methods, it matches")
```python
from typing import Protocol

class Person(Protocol):
    def greet(self) -> None: ...

# ANY class with a greet() method satisfies Person —
# no "implements" keyword needed!
class Student:
    def greet(self) -> None:
        print("Hello")

def welcome(p: Person):    # accepts any object with .greet()
    p.greet()
welcome(Student())         # works — duck typing
```

## **25. Interface vs Abstract Class**

```text
Interface     → "WHAT must you provide?"     — a contract
Abstract      → "What you must provide + what I give you for free"
```

|                    | **Interface**           | **Abstract Class**           |
|--------------------|-------------------------|------------------------------|
| Constructor         | No                      | Yes                          |
| Instance state      | No (Java)               | Yes — can have fields        |
| Multiple of them   | Yes (Java/TS)           | No — single inheritance only |
| Default methods    | Java 8+, TS: yes        | Yes                          |
| Use when           | capability, contract    | shared code between siblings |

## **26. `static` — Class-Level Members**

```text
Python       → @staticmethod / @classmethod (with cls)
Java         → static keyword
TypeScript   → static keyword
```

### **Java**
```java
class MathUtil {
    static int square(int x) { return x * x; }
    static final double PI = 3.14159;
}
MathUtil.square(5);     // call on CLASS, never on an object
```

### **TypeScript**
```ts
class MathUtil {
    static square(x: number): number { return x * x; }
    static PI = 3.14159;
}
MathUtil.square(5);
```

### **Python — THREE options (know the difference!)**
```python
class MathUtil:
    pi = 3.14159                     # class attribute (shared, like static field)

    @staticmethod
    def square(x):                    # no self, no cls — a plain function in a class
        return x * x

    @classmethod
    def create_default(cls):          # gets the CLASS (not instance) as first arg
        return cls()                  # — the FACTORY PATTERN trick!

    @classmethod
    def from_string(cls, s):          # alternative constructors use classmethod
        return cls()

MathUtil.square(5)        # call on class
MathUtil.pi               # shared field
```

## **27. Getters and Setters**

### **TypeScript** — `get`/`set` keywords
```ts
class Person {
    constructor(private _age: number) {}

    get age(): number { return this._age; }

    set age(value: number) {
        if (value >= 0) this._age = value;   // validation inside setter
    }
}

const p = new Person(25);
p.age;       // 25 — looks like a field, calls the getter
p.age = 30;  // runs the setter with validation
p.age = -5;  // rejected by the setter's check
```

### **Java** — plain methods by convention `getX()` / `setX()`
```java
class Person {
    private int age;

    public int getAge() { return age; }

    public void setAge(int age) {
        if (age >= 0) this.age = age;
    }
}
Person p = new Person();
p.setAge(30);
p.getAge();
```

### **Python** — `@property` decorator (the elegant one)
```python
class Person:
    def __init__(self, age):
        self._age = age

    @property
    def age(self):                    # getter — used as p.age
        return self._age

    @age.setter
    def age(self, value):             # setter — used as p.age = x
        if value >= 0:
            self._age = value

p = Person(25)
p.age          # 25 — attribute-style access, method underneath
p.age = 30     # calls the setter
```

---

# **28–38. Modern JS/TS Syntax**

## **28. Object Destructuring**
```ts
const person = { name: "Jashu", age: 25 };
const { name, age } = person;

// rename + default
const { name: fullName, city = "Mumbai" } = person;

// in function parameters
function greet({ name, age }: { name: string; age: number }) {}
```

## **29. Array Destructuring**
```ts
const [a, b, c] = [10, 20, 30];
const [first, , third] = [10, 20, 30];    // skip

// swap (DSA favorite)
let a = 10, b = 20;
[a, b] = [b, a];

// Python equivalent:  a, b = b, a
// Java equivalent:     temp = a; a = b; b = temp;  (3 lines)
```

## **30–31. Spread `...` — Arrays**
```ts
const merged = [...[1,2,3], ...[4,5,6]];   // [1,2,3,4,5,6]
const copy = [...arr];                      // shallow copy
copy.push(4);   // original unaffected
```

## **32. Spread — Objects**
```ts
const updated = { ...person, age: 26 };     // later keys override
// { name: "Jashu", age: 26 }

// remove a key
const { age: _, ...withoutAge } = person;
```

## **33. Rest `...` — Collect**
```ts
function add(...numbers: number[]): number {
    return numbers.reduce((s, x) => s + x, 0);
}
```

## **34. Spread vs Rest — Same Symbol, Opposite Jobs**
```text
In a function DEFINITION (   ...numbers )   → REST — collects IN
In a function CALL or literal ( ...arr )     → SPREAD — expands OUT
```

## **35. Optional Chaining `?.`**
```ts
user?.address?.city          // undefined instead of crash

// also works on calls:
callback?.()                  // only calls if callback exists
arr?.[0]                      // index access with safety
user?.address?.city ?? "Unknown"
```

## **36–37. `??` vs `||` — Know the Difference**
```ts
0 || 10       // 10   — || treats 0 as falsy
0 ?? 10       // 0    — ?? only null/undefined trigger fallback

"" || "hi"    // "hi"
"" ?? "hi"    // ""   — empty string is VALID for ??

// Use ?? when 0/false/"" are legitimate values
const count = map.get(ch) ?? 0;
```

## **38. Ternary**
```ts
const result = age >= 18 ? "Adult" : "Minor";
```
```python
# Python
result = "Adult" if age >= 18 else "Minor"
```
```java
// Java (works only for expressions, not statements!)
String result = age >= 18 ? "Adult" : "Minor";
```

## **39. Template Literals (TS/JS only)**
```ts
const message = `Hello ${name}, age ${age + 5}`;
```

## **40–44. TypeScript Type System Quick Hits**

```ts
// 40. optional param
function greet(name?: string): void {}

// 41. union
let id: string | number;

// 42. narrowing
function print(v: string | number) {
    if (typeof v === "string") v.toUpperCase();  // string here
    else v.toFixed(2);                            // number here
}

// 43. type alias
type User = { name: string; age: number };

// 44. interface
interface User2 { name: string; age: number }
```

## **45–48. Generics**

```ts
// TypeScript
function identity<T>(value: T): T { return value; }
class Box<T> {
    constructor(private value: T) {}
    getValue(): T { return this.value; }
}
```

```java
// Java — generics exist ONLY at compile time (type erasure)
class Box<T> {
    private T value;
    Box(T value) { this.value = value; }
    T getValue() { return value; }
}
Box<Integer> box = new Box<>(100);     // diamond operator infers Integer
List<String> names = new ArrayList<>();

// Java special powers: bounded generics
<T extends Comparable<T>>               // T must be comparable
static <T extends Comparable<T>> T max(List<T> list) { ... }

// wildcards (Java only!)
List<? extends Number>   // any list of some Number subtype
List<? super Integer>    // any list that can hold Integers
```

```python
# Python — generics are optional typing hints (runtime doesn't enforce)
from typing import TypeVar, Generic

T = TypeVar("T")

class Box(Generic[T]):
    def __init__(self, value: T):
        self.value = value
    def get_value(self) -> T:
        return self.value

# Python 3.12+ new syntax:
# class Box[T]:
#     def __init__(self, value: T): ...
```

---

# **49–50. Exception Handling — COMPLETE**

## **The Syntax Table**

|                  | **Python**            | **Java**                    | **TS/JS**              |
|------------------|-----------------------|-----------------------------|-------------------------|
| try              | `try:`                | `try { }`                   | `try { }`               |
| catch            | `except Type as e:`   | `catch (Exception e)`       | `catch (e)`             |
| multiple catches | multiple except blocks| multiple catch blocks       | ONE catch, check inside  |
| finally          | `finally:`            | `finally { }`               | `finally { }`           |
| throw            | `raise Error(msg)`    | `throw new Exception(msg)`  | `throw new Error(msg)`  |
| cleanup          | —                     | try-with-resources          | —                       |

## **49. Basic try/catch/finally**

### **Python**
```python
try:
    x = 10 / 0
except ZeroDivisionError as e:
    print("Divide error:", e)
except (ValueError, TypeError) as e:     # multiple types in one block
    print("Other error")
except Exception as e:                    # catch-all (last)
    print("Something:", e)
else:
    print("ONLY runs if NO exception")    # Python-only feature!
finally:
    print("Always runs")
```

### **Java**
```java
try {
    int x = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Divide error: " + e.getMessage());
} catch (Exception e) {                 // child → parent order matters!
    System.out.println("Other");
} finally {
    System.out.println("Always runs");
}
// COMPILE ERROR if parent catch comes FIRST — unreachable code
```

### **TypeScript/JavaScript**
```ts
try {
    const x: number = 10 / 0;    // NOTE: JS division by 0 = Infinity, not error!
} catch (error) {
    if (error instanceof Error) {       // TS 4.4+: error is `unknown`
        console.log(error.message);
    }
} finally {
    console.log("Always runs");
}
```

## **50. Throwing**

```python
raise ValueError("Invalid value")           # Python
```
```java
throw new IllegalArgumentException("Invalid value");   // Java
```
```ts
throw new Error("Invalid value");           // TS/JS
```

## **Java Special Power — CHECKED vs UNCHECKED (interview favorite!)**

```java
// CHECKED   → compiler FORCES you to try/catch or declare "throws"
// UNCHECKED → compiler doesn't care

try {
    BufferedReader r = new BufferedReader(new FileReader("data.txt"));
    // FileReader throws IOException (CHECKED)
    // → Won't compile without catch or "throws" on the method!
} catch (IOException e) {
    e.printStackTrace();
}

// OR declare that your method passes the problem up:
void readFile() throws IOException {
    BufferedReader r = new BufferedReader(new FileReader("data.txt"));
}
```

```text
CHECKED (must handle):     IOException, SQLException, FileNotFoundException
UNCHECKED (no forcing):    RuntimeException, NullPointerException,
                           ArithmeticException, IllegalArgumentException,
                           IndexOutOfBoundsException
```
**Python and TS/JS have NO checked exceptions — nothing forces you to catch.**

## **Java try-with-resources (auto-close)**

```java
try (BufferedReader r = new BufferedReader(new FileReader("data.txt"))) {
    System.out.println(r.readLine());
} catch (IOException e) {
    e.printStackTrace();
}
// r.close() called AUTOMATICALLY — even on exception
// Any class implementing AutoCloseable can be used here
```

## **Python Special Power — `else` block and context managers**

```python
# else runs ONLY when no exception occurred
try:
    data = load_config()
except FileNotFoundError:
    data = DEFAULT
else:
    validate(data)          # skip this when using the default

# context manager = Java's try-with-resources
with open("data.txt") as f:     # closes automatically
    content = f.read()
```

## **Custom Exceptions**

```python
class InsufficientFundsError(Exception):
    def __init__(self, balance, amount):
        super().__init__(f"Need {amount}, have {balance}")
        self.balance = balance
        self.amount = amount

raise InsufficientFundsError(500, 1000)
```

```java
class InsufficientFundsException extends Exception {      // checked
    public InsufficientFundsException(String msg) {
        super(msg);
    }
}
// extends RuntimeException instead → unchecked
throw new InsufficientFundsException("Need 1000, have 500");
```

```typescript
class InsufficientFundsError extends Error {
    constructor(
        public balance: number,
        public amount: number
    ) {
        super(`Need ${amount}, have ${balance}`);
        this.name = "InsufficientFundsError";    // keeps the right name
    }
}
throw new InsufficientFundsError(500, 1000);
```

---

# **51–53. Modules / Import / Export**

## **The Master Table**

|                    | **Python**                  | **Java**                        | **TS/JS**                            |
|--------------------|-----------------------------|---------------------------------|---------------------------------------|
| import all        | `import math`               | `import java.util.*;`           | `import * as math from "./math"`      |
| import specific    | `from collections import deque` | `import java.util.List;`   | `import { add } from "./math"`        |
| export             | top-level `name = ...`      | — (public class = visible)      | `export` / `export default`          |
| rename on import  | `import numpy as np`        | ❌                              | `import { add as sum } from "./m"`    |
| default import     | —                           | —                               | `import Person from "./Person"`       |

## **51. Import**

```python
# Python
import math                                    # whole module
from collections import deque, defaultdict     # specific names
import numpy as np                              # alias
from mypackage.mymodule import MyClass          # package path with .
```

```java
// Java — only specific classes, or .* for a package
import java.util.List;             // one class
import java.util.*;                // everything in package
import static java.lang.Math.max;  // static import — use max() directly!
```

```ts
// TypeScript/JavaScript (ES Modules)
import { add, subtract } from "./math";        // named (must match names)
import { add as sum } from "./math";           // rename
import Person from "./Person";                 // default (any name you like!)
import * as MathLib from "./math";             // namespace
import type { User } from "./types";           // type-only import (erased!)
```

## **52. Named Exports (TS/JS)**

```ts
// math.ts
export function add(a: number, b: number) { return a + b; }
export const PI = 3.14;
export class Calculator { }

// consumer
import { add, PI, Calculator } from "./math";
```

## **53. Default Export — ONE per file**

```ts
// Person.ts
export default class Person { }

// consumer — name is your choice (no braces!)
import Person from "./Person";       // Person
import Human from "./Person";        // also fine — default is anonymous

// default + named together
export default class Person { }
export const MAX = 10;
import Person, { MAX } from "./Person";
```

## **Python `__all__` — controlling `from module import *`**

```python
# mymodule.py
__all__ = ["MyClass", "helper"]    # only these export with *

def helper(): ...
def _internal(): ...               # _private never exports anyway
class MyClass: ...
```

---

# **54–58. Async — COMPLETE (was cut off at #55)**

## **54. async / await — TypeScript/JavaScript**

```ts
async function getData(): Promise<string> {
    const response = await fetch("https://example.com");
    return response.text();
}

async function main() {
    const data = await getData();
    console.log(data);
}
main();
```

## **55. Promise — Creation and .then (completed)**

```ts
function getNumber(): Promise<number> {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(100);           // success path
            // reject(new Error("failed")) — failure path
        }, 1000);
    });
}

// Consume with .then chain
getNumber()
    .then(n => n * 2)              // 200
    .then(n => console.log(n))     // logs 200
    .catch(err => console.error(err))
    .finally(() => console.log("done"));
```

**Promise.all / allSettled / race / any:**
```ts
const [a, b] = await Promise.all([fetchA(), fetchB()]);   // parallel, fail-fast

const results = await Promise.allSettled([fa(), fb()]);    // parallel, never fails
// → [{ status: "fulfilled", value: 1 }, { status: "rejected", reason: Error }]

const first = await Promise.race([fa(), timeout(100)]);    // first done wins

const firstOk = await Promise.any([try1(), try2()]);       // first SUCCESS wins
```

## **56. Async in Java — CompletableFuture**

```java
// Java has no async/await keyword! Uses CompletableFuture:

import java.util.concurrent.CompletableFuture;

CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    return fetchData();                    // runs on another thread
});

future
    .thenApply(s -> s.toUpperCase())      // like .then
    .thenAccept(System.out::println)
    .exceptionally(e -> "fallback");      // like .catch

// BLOCKING wait (avoid on main thread):
String result = future.get();             // blocks until done

// Parallel (Promise.all equivalent):
CompletableFuture<Void> all = CompletableFuture.allOf(f1, f2, f3);
all.join();
```

## **57. Async in Python — asyncio**

```python
import asyncio

async def fetch_data():                     # async def — coroutine
    print("start")
    await asyncio.sleep(1)                  # await — non-blocking pause
    return "data"

async def main():
    # sequential
    a = await fetch_data()
    b = await fetch_data()

    # parallel (Promise.all equivalent)
    a, b = await asyncio.gather(
        fetch_data(),
        fetch_data(),
    )

asyncio.run(main())                         # entry point
```

## **58. Sequential vs Parallel — All 4 Languages**

```ts
// TS/JS
const [a, b] = await Promise.all([fa(), fb()]);   // parallel ✓
```
```python
# Python
a, b = await asyncio.gather(fa(), fb())           # parallel ✓
```
```java
// Java
CompletableFuture.allOf(fa, fb).join();           // parallel ✓
```
```javascript
// JavaScript — you CANNOT block the single thread:
// await is non-blocking by design. The event loop keeps running.
// There is NO thread.sleep() — only non-blocking setTimeout-based sleep:
const sleep = (ms: number) => new Promise(r => setTimeout(r, ms));
await sleep(1000);     // pauses THIS function, nothing else
```

---

# **59. ONE-GLANCE MENTAL TRANSLATION TABLE**

| **Concept**        | **Python**                        | **Java**                          | **TS/JS**                          |
|--------------------|-----------------------------------|-----------------------------------|-------------------------------------|
| Function           | `def f(a, b):`                    | `int f(int a, int b)`             | `function f(a, b)`                  |
| No return          | (just no return)                  | `void`                            | `void`                             |
| Constructor        | `__init__`                        | `ClassName()`                     | `constructor()`                     |
| Self reference     | `self` (explicit)                 | `this`                            | `this`                             |
| Parent call        | `super().method()`                | `super.method()`                  | `super.method()`                    |
| Inheritance        | `class Dog(Animal):`              | `extends Animal`                  | `extends Animal`                   |
| Interface          | `Protocol` / `ABC`                | `interface`                       | `interface`                        |
| Implements         | (implicit — duck typing)          | `implements Iface`                | `implements Iface`                 |
| Static method      | `@staticmethod`                   | `static`                          | `static`                           |
| Private            | `__name` (mangling)               | `private`                         | `private` / `#name`               |
| Getter             | `@property`                       | `getX()`                          | `get x()`                          |
| Varargs            | `*args`                           | `int... nums`                     | `...nums: number[]`                |
| Lambda             | `lambda x: x*x`                  | `x -> x * x`                      | `x => x * x`                       |
| map                | `[x*2 for x in l]`                | `.stream().map(x -> x*2)`         | `.map(x => x*2)`                   |
| filter             | `[x for x in l if x>0]`           | `.stream().filter(x -> x>0)`      | `.filter(x => x>0)`                |
| reduce             | `reduce(lambda a,b: a+b, l, 0)`  | `.reduce(0, (a,b) -> a+b)`       | `.reduce((a,b) => a+b, 0)`         |
| Dictionary         | `dict` `{}`                       | `HashMap<K,V>`                    | `object` / `Map` / `Record`        |
| Null               | `None`                            | `null`                            | `null` / `undefined`               |
| Null check         | `if x is None:`                   | `if (x == null)`                  | `if (x == null)` / `x?.y`         |
| Default value      | `x or "default"` / `x ?? y` (3.8+) | `Optional.orElse("default")`    | `x ?? "default"`                   |
| String template    | f-string `f"{name}"`              | `String.format("%s", name)`       | `` `${name}` ``                    |
| Throw              | `raise ValueError("m")`           | `throw new Exception("m")`        | `throw new Error("m")`             |
| Async entry        | `asyncio.run(main())`             | `future.get()` / `.join()`        | `main()` (auto / top-level await)  |
| Constant           | `UPPER_SNAKE` (convention)        | `final int X`                     | `const x` (binding) / `readonly`   |
| Main method        | `if __name__ == "__main__":`      | `public static void main(String[] a)` | top-level code runs directly   |
| Multi-line string  | `"""..."""`                       | `"""..."""` (text block, Java 15) | `` `...` `` (template literal)    |
| Entry to class      | `obj = MyClass()`                | `MyClass obj = new MyClass()`     | `const obj = new MyClass()`        |

---

# **60. EXERCISES — Practice All 4 Languages**

## **Ex 1 — Build a `BankAccount` (encapsulation + naming)**

Requirements: private balance, deposit (reject negatives), withdraw (reject insufficient), getter for balance. Write it in Python, Java, and TypeScript. Follow each language's naming conventions.

<details><summary>Solution sketch</summary>

```python
class BankAccount:
    def __init__(self, initial_balance=0):
        self._balance = initial_balance

    def deposit(self, amount):
        if amount > 0:
            self._balance += amount

    def withdraw(self, amount):
        if 0 < amount <= self._balance:
            self._balance -= amount

    @property
    def balance(self):
        return self._balance
```

```java
public class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public void deposit(double amount) {
        if (amount > 0) balance += amount;
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) balance -= amount;
    }

    public double getBalance() { return balance; }
}
```

```ts
class BankAccount {
    constructor(private balance: number = 0) {}

    deposit(amount: number): void {
        if (amount > 0) this.balance += amount;
    }

    withdraw(amount: number): void {
        if (amount > 0 && amount <= this.balance) this.balance -= amount;
    }

    get balance_(): number { return this.balance; }  // see note below
}
```
</details>

## **Ex 2 — `Shape` hierarchy (abstraction + polymorphism)**

Abstract class Shape with abstract `area()`. Subclasses Circle, Rectangle. Loop over `Shape[]` and print each area — in all 3 languages.

## **Ex 3 — Callback / pipeline**

Write `process(nums, fn)` that applies `fn` to each element. Then implement map/filter/reduce equivalents yourself in all 3 languages.

## **Ex 4 — Frequency counter (the ?? pattern)**

Given a string, count character frequencies. 
Python: `dict` + `.get(ch, 0)`. TS: `Record<string, number>` + `(acc[ch] ?? 0) + 1`. Java: `HashMap<Character, Integer>` + `getOrDefault(ch, 0)`.

## **Ex 5 — Custom exception**

Create `InvalidAgeError` in all 3 languages. Write `registerUser(age)` that throws it when age < 18, and a caller that catches it.

---

# **61. FINAL CHEAT CARD — Memorize These**

```text
NAMING
  Python     : snake_case methods/vars, PascalCase classes, UPPER_SNAKE consts
  Java       : camelCase methods/vars, PascalCase classes, UPPER_SNAKE consts
  TS/JS      : camelCase functions/vars, PascalCase classes/types

PRIVACY
  Java       : private/protected/(default)/public — REAL, compiler-enforced
  TS         : private/protected — compile-time only, ERASED in JS
  JS         : #field — the only TRUE runtime privacy
  Python     : _name convention, __name mangling — NO enforcement

JAVA SPECIAL
  file name must match public class name
  package-private = default (no keyword)
  checked exceptions force try/catch or throws
  try-with-resources auto-closes
  final = constant / sealed class / sealed method
  no default params → overloading instead

PYTHON SPECIAL
  self is explicit, cls for classmethods
  else block on try — runs when NO exception
  Protocol = duck-typed interface
  comprehensions replace map/filter
  no overloading — *args, **kwargs

TS/JS SPECIAL
  ?.  optional chaining    — safe navigation
  ??  nullish coalescing    — only null/undefined fallback (NOT 0, "", false)
  ... spread (expand) / rest (collect)
  arrow functions inherit 'this'
  async/await IS promises — cleaner syntax, same engine
  single thread, event loop — no thread.sleep, EVER
```
