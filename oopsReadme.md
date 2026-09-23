# 🎓 OOP Concepts — The Complete Guide
### One Program. Four Languages (Java • Python • TypeScript • JavaScript). Every Concept Explained.

> **The story we will use throughout:** A school 🏫 manages **Students**. Every student is a **Person** (has address, age). Students have a **Rank**. Students sit in a **ClassRoom**. Students have **Friends**.
> This one story contains **every major OOP concept** — class, object, encapsulation, inheritance, polymorphism (overloading + overriding), abstraction, interfaces, constructors, `super`, `static`, getters/setters.

---

## 📚 Table of Contents

1. [The Big Picture — Why OOP?](#1-the-big-picture--why-oop)
2. [Class & Object](#2-class--object)
3. [Encapsulation](#3-encapsulation)
4. [Inheritance](#4-inheritance)
5. [Polymorphism — Overloading & Overriding](#5-polymorphism)
6. [Abstraction — Abstract Class vs Interface](#6-abstraction)
7. [Constructors & `super`](#7-constructors--super)
8. [Static Members](#8-static-members)
9. [Getters & Setters](#9-getters--setters)
10. [Concept Map — Where Each Concept Lives in Our Program](#10-concept-map)
11. [The Program — Java](#11-the-program--java)
12. [The Program — Python](#12-the-program--python)
13. [The Program — TypeScript](#13-the-program--typescript)
14. [The Program — JavaScript](#14-the-program--javascript)
15. [Language Comparison Table](#15-language-comparison-table)
16. [Memory Tricks — Never Forget Again](#16-memory-tricks)
17. [Expected Output](#17-expected-output)

---

## 1. The Big Picture — Why OOP?

**Real-world scenario:** Think of how a school actually works in real life.

- The school doesn't treat every student as a random pile of data (`name`, `rollNo`, `age`, scattered in registers). It creates a **file/record structure** per student.
- The office clerk **can't directly edit** your marks — only the class teacher can, through a proper process.
- A **student** is obviously a **person** — so instead of filling the same "address, age" details again, the student's file *extends* the person's file.
- The same person is called differently in different contexts — "monitor" in class, "son" at home, "player" on the field.
- The school principal publishes rules ("every student **must** wear a uniform") without caring *how* each student follows them.

Every sentence above is one OOP concept:

| Real life | OOP concept |
|---|---|
| Record structure per student | **Class** |
| Each actual student | **Object** |
| Clerk can't edit marks directly | **Encapsulation** |
| Student's file extends person's file | **Inheritance** |
| Same person, different roles | **Polymorphism** |
| Rules published, implementation left to you | **Abstraction / Interface** |

---

## 2. Class & Object

### 🧠 Easy way to remember
> **Class = Blueprint of a house 🏠. Object = Actual houses built from it.**
> The blueprint is not a house — you can't live in it. But from ONE blueprint, you can build 100 houses, each with its own furniture (state).

- **Class** — a template. Defines *what* every student HAS (fields: `name`, `rollNo`) and *what* every student DOES (methods: `print()`, `studentRank()`).
- **Object** — one real instance created from the class. `new Ranks(...)` builds one actual student named "Jashu".

### 📍 In our program
```java
class Student { ... }        // blueprint
Ranks subj1 = new Ranks(...); // ONE real student — an object
```

---

## 3. Encapsulation

### 🧠 Easy way to remember
> **Encapsulation = A medicine capsule 💊.**
> The bitter medicine (data) is sealed inside the shell (class). You swallow the capsule (call the method) — you never touch the powder directly.

Or: **an ATM 🏧**. You press buttons (public methods) to get money. You can NEVER reach inside the machine and grab cash from the counter (private fields). The machine controls every rupee that leaves.

- Fields are marked `private` — hidden from outside.
- Access is given ONLY through public **getters** and **setters** — controlled access.
- **Why?** If `name` were public, any code could set `name = ""` or `name = null`. Through a setter, you can add validation (`if (name != null)`).

### 📍 In our program
```java
class Student {
    private int rollNo;      // 🔒 sealed inside the capsule
    private String name;     // 🔒 sealed inside the capsule

    public String getName()   { return name; }   // 🏧 the ONLY door to read
    public void setName(String name) { this.name = name; } // 🏧 the ONLY door to write
}
```

---

## 4. Inheritance

### 🧠 Easy way to remember
> **Inheritance = Family inheritance 👨‍👩‍👦.**
> You inherit your parent's surname, property, and features — but you also add your OWN things. Your parent doesn't get your bike; you get their house.

**"IS-A" test** (say it out loud):
- A Student **is a** Person ✅ → so `Student extends StudentAdditionalInfo`
- A Ranks **is a** Student ✅ → so `Ranks extends Student`
- A Car **is a** Steering Wheel ❌ → don't inherit that!

### The chain in our program
```
StudentAdditionalInfo  (Person — address, age)
        ▲ extends
      Student          (adds rollNo, name — abstract)
        ▲ extends
      Ranks           (adds rank, roomNo, floor — the real class)
```

### Types of inheritance (know the names for interviews)
| Type | Meaning | Java allows? |
|---|---|---|
| Single | B extends A | ✅ |
| Multilevel | C extends B extends A | ✅ (our program!) |
| Hierarchical | B, C both extend A | ✅ |
| Multiple | D extends B AND C (classes) | ❌ — use **interfaces** ✅ |
| Hybrid | Mix of above | Via interfaces only |

> ⚠️ **Java/TS classes: single inheritance only.** One class can extend only ONE class. For multiple inheritance of *type*, you use **interfaces** — exactly why our `Ranks` uses `implements ClassRoom, Friends`.

---

## 5. Polymorphism

### 🧠 Easy way to remember
> **Polymorphism = One person, many roles 🎭.**
> Jashu at 9 AM is a *student*, at 7 PM a *son*, on Sunday a *cricketer*. Same person — name is same, behavior changes with context. **Poly = many, morph = forms.**

It has two flavors:

### A) Method Overloading — *Compile-time polymorphism*
> 🧠 **"Same words, different sentence."** You say *"Call me"* vs *"Call me at 5 PM"* — the verb "call" is the same, but the details (parameters) differ. The compiler picks the right one **before running**.

```java
void display(String friend);                // one friend
void display(String friend1, String friend2); // two friends
```
**Rule:** same method name, **different parameter list** (count / type / order). Return type alone can't overload.

### B) Method Overriding — *Runtime polymorphism*
> 🧠 **"Child rewrites the parent's rule."** Parent says "every student must introduce themselves" (abstract). Each child writes it their OWN way. Which version runs is decided **at runtime**, based on the actual object.

```java
abstract class Student {
    abstract void studentRank();  // parent's rule: "you MUST explain your rank"
}
class Ranks extends Student {
    @Override
    void studentRank() {         // child's own way of following the rule
        System.out.println("I am a ranked student: " + rank);
    }
}
```

### Overloading vs Overriding — the exam table 📝
| | Overloading | Overriding |
|---|---|---|
| Where | Same class | Parent ↔ child classes |
| Parameters | MUST differ | MUST be same |
| Return type | Can differ | Same (or covariant) |
| Binding | Compile time | Runtime |
| Keyword | none | `@Override` (Java) |
| Memory trick | **Load** more params | **Ride** over parent's method |

---

## 6. Abstraction

### 🧠 Easy way to remember
> **Abstraction = Driving a car 🚗.**
> You know: steering turns, brake stops. You do NOT know: fuel injection, torque, engine timing. **You use WHAT it does, without knowing HOW it does it.**

It comes in two strengths:

### A) Abstract Class — *"a half-filled form" 📝*
> 🧠 Think of a **printed admission form** that's half-filled by the school (name, class fields already printed = implemented methods) and half left blank for you (`________` = abstract methods). You MUST fill the blanks to submit it.

```java
abstract class Student {
    void print() { ... }        // ✅ filled — every child gets it free
    abstract void studentRank(); // ⬜ blank — every child MUST fill this
}
```
- Can have BOTH concrete and abstract methods.
- **Cannot** be instantiated: `new Student()` ❌ — you can't submit a half-filled form!
- Can have constructors, fields — things an interface can't (pre-Java 8).

### B) Interface — *"a 100% contract" 📜*
> 🧠 An interface is like an **electricity socket 🔌**. The board publishes the shape (contract: `roomDetails()`). Any plug that fits — TV, fridge, charger — works. The board doesn't care what's inside your device.

```java
interface ClassRoom {
    void roomDetails();  // contract: anyone "is a classroom" must tell room details
}
interface Friends {
    void display(String friend);
    void display(String friend1, String friend2);
}
```

### Abstract Class vs Interface — interview table 📝
| | Abstract Class | Interface |
|---|---|---|
| Keyword | `abstract class` / `extends` | `interface` / `implements` |
| Methods | abstract + concrete | traditionally 100% abstract (Java 8+: `default` allowed) |
| Fields | any (private, static…) | `public static final` constants only |
| Constructor | ✅ has | ❌ none |
| How many | extend ONE class | implement MANY interfaces |
| Relationship | **IS-A** with shared code | **CAN-DO** capability |
| Memory trick | half-filled form | a contract/socket |

---

## 7. Constructors & `super`

### 🧠 Easy way to remember
> **Constructor = The naming ceremony of a baby 👶.** The moment the object is born, its details are set. Same name as class, no return type — not even `void`.

> **`super()` = "Ask Dad first" 🙋.** Before a child constructor finishes its own work, it MUST first let the parent constructor run. The parent's details (address, age) get filled BEFORE the child's (rank, roomNo).

### 📍 The constructor chain in our program
```
new Ranks(1, "Jashu", 1, 101, 2, "Guntur", 23)
      │
      ▼
Ranks(...)        → super(rollNo, name, address, age)
      │                        │
      ▼                        ▼
Student(...)     → super(address, age)
      │                        │
      ▼                        ▼
StudentAdditionalInfo(address, age)   ← grandparent runs FIRST
      │
      ▼
"object fully built, top-down: parent fields → child fields"
```

> ⚠️ **`super(...)` must be the FIRST line** of the child constructor. If you forget it, Java silently inserts `super()` (no-arg) — and fails if the parent has no no-arg constructor.

---

## 8. Static Members

### 🧠 Easy way to remember
> **Static = the school notice board 📋.**
> It belongs to the SCHOOL (class), not to one student (object). Every student reads the same board. If the board changes, everyone sees the change — there's only ONE board.

```java
static void rankAndName(Ranks r) { ... }
// Called as Ranks.rankAndName(subj1) — on the CLASS, not on an object.
// No object needed — like reading the notice board without being a student.
```

| | `static` | non-static (instance) |
|---|---|---|
| Belongs to | the class (1 copy) | each object (own copy) |
| Access via | `ClassName.method()` | `objectName.method()` |
| Memory trick | notice board 📋 | your own notebook 📓 |

---

## 9. Getters & Setters

### 🧠 Easy way to remember
> **Getter = a shop's display window 👀 (look, don't touch).**
> **Setter = the sales counter 🛒 (change things through the proper channel, with rules).**

```java
subj1.getName();      // 👀 look at the name
subj1.setName("Rahul"); // 🛒 change the name through the official channel
```

Python calls these **properties** (`@property` / `@name.setter`) — same idea, prettier syntax. JS/TS use `get name()` / `set name(value)`.

---

## 10. Concept Map

Where every concept lives in our one program:

| Concept | Where in our program |
|---|---|
| Class | `StudentAdditionalInfo`, `Student`, `Ranks` |
| Object | `new Ranks(1, "Jashu", ...)` |
| Encapsulation | `private` fields + `getName()`/`setName()` |
| Inheritance (multilevel) | `Ranks → Student → StudentAdditionalInfo` |
| Inheritance (multiple, via interface) | `implements ClassRoom, Friends` |
| Abstract class | `abstract class Student` |
| Abstract method | `abstract void studentRank()` |
| Interface | `ClassRoom`, `Friends` |
| Overriding | `studentRank()`, `roomDetails()`, `display(...)` with `@Override` |
| Overloading | `display(String)` vs `display(String, String)` |
| Constructor chain | `Ranks()` → `super()` → `Student()` → `super()` → `StudentAdditionalInfo()` |
| Static method | `Ranks.rankAndName(r)` |
| Getter / Setter | `getName()` / `setName(String)` |

---

## 11. The Program — Java ☕

```java
// ─────────────────────────────────────────────
// INTERFACE — a contract: anything that IS a classroom
// must explain its room details.
// ─────────────────────────────────────────────
interface ClassRoom {
    void roomDetails();
}

// ─────────────────────────────────────────────
// PARENT CLASS — Person-level details.
// Grandparent in our inheritance chain.
// ─────────────────────────────────────────────
class StudentAdditionalInfo {

    private String address;   // 🔒 encapsulated
    private int age;          // 🔒 encapsulated

    StudentAdditionalInfo(String address, int age) {
        this.address = address;
        this.age = age;
    }

    public String getAddress() { return address; }
    public int getAge()       { return age; }

    void personDetails() {
        System.out.println("Address: " + address);
        System.out.println("Age: " + age);
    }
}

// ─────────────────────────────────────────────
// ABSTRACT CLASS — extends the person class.
// Half form filled (print), half blank (studentRank).
// ─────────────────────────────────────────────
abstract class Student extends StudentAdditionalInfo {

    private int rollNo;    // 🔒 encapsulated
    private String name;   // 🔒 encapsulated

    Student(int rollNo, String name, String address, int age) {
        super(address, age);     // 🙋 "ask Dad first" — fills person details
        this.rollNo = rollNo;
        this.name = name;
    }

    public int getRollNo()      { return rollNo; }
    public String getName()     { return name; }
    public void setName(String name) { this.name = name; }

    void print() {
        System.out.println(name + " my Rollno is " + rollNo);
    }

    abstract void studentRank();   // ⬜ blank — child MUST implement
}

// ─────────────────────────────────────────────
// INTERFACE with OVERLOADED methods — same name,
// different parameter lists.
// ─────────────────────────────────────────────
interface Friends {
    void display(String friend);
    void display(String friend1, String friend2);
}

// ─────────────────────────────────────────────
// CHILD CLASS — the real student.
//   extends Student                -> single inheritance (IS-A student)
//   implements ClassRoom, Friends  -> multiple inheritance of type
// ─────────────────────────────────────────────
class Ranks extends Student implements ClassRoom, Friends {

    private int rank;
    private int roomNo;
    private int floor;

    Ranks(int rollNo, String name, int rank, int roomNo, int floor,
          String address, int age) {
        super(rollNo, name, address, age);  // 🙋 parent constructor first
        this.rank = rank;
        this.roomNo = roomNo;
        this.floor = floor;
    }

    // 📋 STATIC — notice board, called on the class itself
    static void rankAndName(Ranks r) {
        r.print();
        System.out.println("Rank: " + r.rank);
    }

    void studentDetail() {
        System.out.println("Name: " + getName());
        System.out.println("Roll No: " + getRollNo());
    }

    // 🎭 OVERRIDING the interface contract
    @Override
    public void roomDetails() {
        System.out.println("Floor: " + floor);
        System.out.println("Room No: " + roomNo);
    }

    // 🎭 OVERRIDING the abstract method
    @Override
    void studentRank() {
        System.out.println("I am a ranked student: " + rank);
    }

    // 🎭 OVERLOADING — same name, different params
    @Override
    public void display(String friend) {
        System.out.println("My friend is " + friend);
    }

    @Override
    public void display(String friend1, String friend2) {
        System.out.println("My friends are " + friend1 + " and " + friend2);
    }
}

// ─────────────────────────────────────────────
// MAIN — building objects and using everything.
// ─────────────────────────────────────────────
public class Main {
    public static void main(String[] args) {

        Ranks subj1 = new Ranks(
            1,        // rollNo
            "Jashu",  // name
            1,        // rank
            101,      // roomNo
            2,        // floor
            "Guntur", // address
            23        // age
        );

        System.out.println("----- Student Details -----");
        subj1.studentDetail();

        System.out.println("\n----- Person Details -----");
        subj1.personDetails();

        System.out.println("\n----- Rank -----");
        Ranks.rankAndName(subj1);          // 📋 static — via CLASS name

        System.out.println("\n----- Classroom -----");
        subj1.roomDetails();

        System.out.println("\n----- Student Rank -----");
        subj1.studentRank();

        System.out.println("\n----- Friends -----");
        subj1.display("Nithin");           // 🎭 overload #1
        subj1.display("Nithin", "Rahul");   // 🎭 overload #2

        System.out.println("\n----- Encapsulation -----");
        System.out.println("Current Name: " + subj1.getName());
        subj1.setName("Rahul");            // 🛒 setter — official channel
        System.out.println("Updated Name: " + subj1.getName());
        subj1.studentDetail();

        // ➕ BONUS: runtime polymorphism in action —
        //    same call, different objects, different results
        System.out.println("\n----- Runtime Polymorphism (bonus) -----");
        Ranks subj2 = new Ranks(2, "Nithin", 3, 102, 2, "Vijayawada", 24);
        Student[] students = { subj1, subj2 };
        for (Student s : students) {
            s.studentRank();   // JVM decides AT RUNTIME which override to run
        }
    }
}
```

---

## 12. The Program — Python 🐍

```python
"""
OOP concepts in Python — same school story.
Key Python differences from Java:
  • No 'interface' keyword  → use abc.ABC (Abstract Base Class)
  • No method overloading   → use default parameters (friend2=None)
  • private fields          → double underscore (__name) name-mangling
  • getters/setters         → @property / @setter decorators
"""
from abc import ABC, abstractmethod


# ─────────────────────────────────────────────
# INTERFACE — Python has no 'interface' keyword,
# so we model it as an Abstract Base Class (ABC).
# ─────────────────────────────────────────────
class ClassRoom(ABC):
    @abstractmethod
    def room_details(self) -> None: ...


# ─────────────────────────────────────────────
# INTERFACE with "overloading" — Python does NOT
# support overloading (last def wins), so we use
# a default parameter instead.
# ─────────────────────────────────────────────
class Friends(ABC):
    @abstractmethod
    def display(self, friend1: str, friend2: str | None = None) -> None: ...


# ─────────────────────────────────────────────
# PARENT CLASS — person details (encapsulated).
# __address / __age  →  "private" via name mangling
# ─────────────────────────────────────────────
class StudentAdditionalInfo:
    def __init__(self, address: str, age: int) -> None:
        self.__address = address   # 🔒 private
        self.__age = age           # 🔒 private

    @property
    def address(self) -> str:      # 👀 getter
        return self.__address

    @property
    def age(self) -> int:          # 👀 getter
        return self.__age

    def person_details(self) -> None:
        print(f"Address: {self.__address}")
        print(f"Age: {self.__age}")


# ─────────────────────────────────────────────
# ABSTRACT CLASS — inherits from BOTH a concrete
# class (StudentAdditionalInfo) and ABC.
# ─────────────────────────────────────────────
class Student(StudentAdditionalInfo, ABC):

    def __init__(self, roll_no: int, name: str,
                 address: str, age: int) -> None:
        super().__init__(address, age)      # 🙋 "ask Dad first"
        self.__roll_no = roll_no             # 🔒 private
        self.__name = name                   # 🔒 private

    @property
    def roll_no(self) -> int:                # 👀 getter
        return self.__roll_no

    @property
    def name(self) -> str:                   # 👀 getter
        return self.__name

    @name.setter
    def name(self, value: str) -> None:      # 🛒 setter
        self.__name = value

    def print_info(self) -> None:
        print(f"{self.__name} my Rollno is {self.__roll_no}")

    @abstractmethod
    def student_rank(self) -> None: ...      # ⬜ blank — child MUST fill


# ─────────────────────────────────────────────
# CHILD CLASS — Python supports REAL multiple
# inheritance of classes (MRO), which Java can't!
# ─────────────────────────────────────────────
class Ranks(Student, ClassRoom, Friends):

    def __init__(self, roll_no: int, name: str, rank: int,
                 room_no: int, floor: int,
                 address: str, age: int) -> None:
        super().__init__(roll_no, name, address, age)  # 🙋 parent first
        self.rank = rank          # (kept public for simplicity, like Java example)
        self.room_no = room_no
        self.floor = floor

    # 📋 STATIC — notice board, called on the class
    @staticmethod
    def rank_and_name(r: "Ranks") -> None:
        r.print_info()
        print(f"Rank: {r.rank}")

    def student_detail(self) -> None:
        print(f"Name: {self.name}")
        print(f"Roll No: {self.roll_no}")

    # 🎭 OVERRIDING the ClassRoom contract
    def room_details(self) -> None:
        print(f"Floor: {self.floor}")
        print(f"Room No: {self.room_no}")

    # 🎭 OVERRIDING the abstract method
    def student_rank(self) -> None:
        print(f"I am a ranked student: {self.rank}")

    # 🎭 "OVERLOADING" via default parameter —
    #    one method, both call shapes work
    def display(self, friend1: str, friend2: str | None = None) -> None:
        if friend2 is None:
            print(f"My friend is {friend1}")
        else:
            print(f"My friends are {friend1} and {friend2}")


# ─────────────────────────────────────────────
# MAIN — same flow as the Java version
# ─────────────────────────────────────────────
if __name__ == "__main__":

    subj1 = Ranks(
        1,          # roll_no
        "Jashu",    # name
        1,          # rank
        101,        # room_no
        2,          # floor
        "Guntur",   # address
        23,         # age
    )

    print("----- Student Details -----")
    subj1.student_detail()

    print("\n----- Person Details -----")
    subj1.person_details()

    print("\n----- Rank -----")
    Ranks.rank_and_name(subj1)          # 📋 static — via CLASS name

    print("\n----- Classroom -----")
    subj1.room_details()

    print("\n----- Student Rank -----")
    subj1.student_rank()

    print("\n----- Friends -----")
    subj1.display("Nithin")            # one friend
    subj1.display("Nithin", "Rahul")    # two friends

    print("\n----- Encapsulation -----")
    print(f"Current Name: {subj1.name}")   # @property getter
    subj1.name = "Rahul"                   # @setter — official channel
    print(f"Updated Name: {subj1.name}")
    subj1.student_detail()

    # ➕ BONUS: runtime polymorphism
    print("\n----- Runtime Polymorphism (bonus) -----")
    subj2 = Ranks(2, "Nithin", 3, 102, 2, "Vijayawada", 24)
    for s in [subj1, subj2]:
        s.student_rank()
```

---

## 13. The Program — TypeScript 🟦

```typescript
/**
 * OOP concepts in TypeScript — the CLOSEST to Java of the four,
 * because TS has real interfaces, abstract classes, AND overloading.
 * If you know Java, you already know TS OOP.
 */

// ─────────────────────────────────────────────
// INTERFACE — a pure contract, zero implementation
// ─────────────────────────────────────────────
interface ClassRoom {
  roomDetails(): void;
}

// ─────────────────────────────────────────────
// INTERFACE with OVERLOADS — TS supports real
// compile-time overloading: declare signatures,
// then ONE implementation.
// ─────────────────────────────────────────────
interface Friends {
  display(friend: string): void;
  display(friend1: string, friend2: string): void;
}

// ─────────────────────────────────────────────
// PARENT CLASS — encapsulation via `private`
// constructor parameter properties (shorthand!)
// ─────────────────────────────────────────────
class StudentAdditionalInfo {
  constructor(
    private address: string,   // 🔒 field + constructor in ONE line
    private age: number,
  ) {}

  getAddress(): string { return this.address; }
  getAge(): number     { return this.age; }

  personDetails(): void {
    console.log(`Address: ${this.address}`);
    console.log(`Age: ${this.age}`);
  }
}

// ─────────────────────────────────────────────
// ABSTRACT CLASS — extends a class, cannot be
// instantiated (`new Student()` is a compile error)
// ─────────────────────────────────────────────
abstract class Student extends StudentAdditionalInfo {

  constructor(
    private rollNo: number,
    private name: string,
    address: string,
    age: number,
  ) {
    super(address, age);   // 🙋 "ask Dad first" — must be first line
  }

  getRollNo(): number        { return this.rollNo; }
  getName(): string          { return this.name; }
  setName(name: string): void { this.name = name; }

  print(): void {
    console.log(`${this.name} my Rollno is ${this.rollNo}`);
  }

  abstract studentRank(): void;   // ⬜ blank — child MUST implement
}

// ─────────────────────────────────────────────
// CHILD CLASS — extends ONE class, implements
// MANY interfaces. Same shape as Java!
// ─────────────────────────────────────────────
class Ranks extends Student implements ClassRoom, Friends {

  constructor(
    rollNo: number,
    name: string,
    private rank: number,
    private roomNo: number,
    private floor: number,
    address: string,
    age: number,
  ) {
    super(rollNo, name, address, age);  // 🙋 parent constructor first
  }

  // 📋 STATIC — notice board
  static rankAndName(r: Ranks): void {
    r.print();
    console.log(`Rank: ${r.rank}`);
  }

  studentDetail(): void {
    console.log(`Name: ${this.getName()}`);
    console.log(`Roll No: ${this.getRollNo()}`);
  }

  // 🎭 OVERRIDING the ClassRoom contract
  roomDetails(): void {
    console.log(`Floor: ${this.floor}`);
    console.log(`Room No: ${this.roomNo}`);
  }

  // 🎭 OVERRIDING the abstract method
  studentRank(): void {
    console.log(`I am a ranked student: ${this.rank}`);
  }

  // 🎭 OVERLOADING — TS style:
  //    signature 1, signature 2, then ONE implementation
  display(friend: string): void;
  display(friend1: string, friend2: string): void;
  display(friend1: string, friend2?: string): void {
    if (friend2 === undefined) {
      console.log(`My friend is ${friend1}`);
    } else {
      console.log(`My friends are ${friend1} and ${friend2}`);
    }
  }
}

// ─────────────────────────────────────────────
// MAIN
// ─────────────────────────────────────────────
const subj1 = new Ranks(
  1,        // rollNo
  "Jashu",  // name
  1,        // rank
  101,      // roomNo
  2,        // floor
  "Guntur", // address
  23,       // age
);

console.log("----- Student Details -----");
subj1.studentDetail();

console.log("\n----- Person Details -----");
subj1.personDetails();

console.log("\n----- Rank -----");
Ranks.rankAndName(subj1);          // 📋 static — via CLASS name

console.log("\n----- Classroom -----");
subj1.roomDetails();

console.log("\n----- Student Rank -----");
subj1.studentRank();

console.log("\n----- Friends -----");
subj1.display("Nithin");           // 🎭 overload #1
subj1.display("Nithin", "Rahul");  // 🎭 overload #2

console.log("\n----- Encapsulation -----");
console.log(`Current Name: ${subj1.getName()}`);
subj1.setName("Rahul");            // 🛒 setter
console.log(`Updated Name: ${subj1.getName()}`);
subj1.studentDetail();

// ➕ BONUS: runtime polymorphism
console.log("\n----- Runtime Polymorphism (bonus) -----");
const subj2 = new Ranks(2, "Nithin", 3, 102, 2, "Vijayawada", 24);
const students: Student[] = [subj1, subj2];
for (const s of students) {
  s.studentRank();
}
```

---

## 14. The Program — JavaScript 🟨

```javascript
/**
 * OOP concepts in JavaScript — the WILDEST of the four.
 * JS has NO interfaces, NO abstract keyword, NO overloading.
 * Everything must be SIMULATED — this is how real JS devs do it.
 *
 *   Java concept        →  JS trick
 *   ────────────────────────────────────────
 *   interface           →  MIXIN FACTORY — a function that takes a class
 *                         and returns an extended class with throwing stubs
 *   abstract class      →  class that throws if method not overridden
 *   overloading         →  optional parameters + if/else
 *   private field       →  #field (ES2022 private fields)
 */

// ─────────────────────────────────────────────
// "INTERFACES" — the JS way. JS has no `interface`
// keyword and only single inheritance, so real JS
// devs use MIXIN FACTORIES: functions that take a
// class and return a new class extending it, with
// contract methods that THROW until the child
// overrides them. Runtime enforcement — the
// closest JS gets to `implements`.
//
// The chain below reads right-to-left:
//   class Ranks extends Friends(ClassRoom(Student))
//     = "Ranks IS-A Student, and implements
//        ClassRoom and Friends"
// ─────────────────────────────────────────────

// "INTERFACE" #1 — ClassRoom mixin
const ClassRoom = (Base) =>
  class extends Base {
    roomDetails() {
      throw new Error(
        `${this.constructor.name} must implement roomDetails()`,
      );
    }
  };

// "INTERFACE" #2 — Friends mixin (the overloaded
// one). JS has no overloading either, so the
// contract documents BOTH shapes and the ONE
// overriding method with an optional parameter
// serves them both:
//    display(friend)            → one friend
//    display(friend1, friend2)  → two friends
const Friends = (Base) =>
  class extends Base {
    display(friend1, friend2) {
      throw new Error(
        `${this.constructor.name} must implement display()`,
      );
    }
  };

// ─────────────────────────────────────────────
// PARENT CLASS — private via #fields (ES2022)
// ─────────────────────────────────────────────
class StudentAdditionalInfo {
  #address;   // 🔒 truly private — invisible outside the class
  #age;       // 🔒

  constructor(address, age) {
    this.#address = address;
    this.#age = age;
  }

  get address() { return this.#address; }   // 👀 getter
  get age()      { return this.#age; }      // 👀 getter

  personDetails() {
    console.log(`Address: ${this.#address}`);
    console.log(`Age: ${this.#age}`);
  }
}

// ─────────────────────────────────────────────
// "ABSTRACT CLASS" — simulated. The method throws
// if the child forgot to override it.
// ─────────────────────────────────────────────
class Student extends StudentAdditionalInfo {

  #rollNo;    // 🔒
  #name;      // 🔒

  constructor(rollNo, name, address, age) {
    super(address, age);   // 🙋 "ask Dad first"
    this.#rollNo = rollNo;
    this.#name = name;
  }

  get rollNo() { return this.#rollNo; }
  get name()   { return this.#name; }
  set name(value) { this.#name = value; }   // 🛒 setter

  print() {
    console.log(`${this.#name} my Rollno is ${this.#rollNo}`);
  }

  // "abstract" — child MUST override, or this error fires at runtime
  studentRank() {
    throw new Error("Abstract method 'studentRank()' must be implemented");
  }
}

// ─────────────────────────────────────────────
// CHILD CLASS — the mixin chain composes the
// interfaces ONTO Student. Read it inside-out:
//   Friends(ClassRoom(Student))
//   = Student, extended with the ClassRoom
//     contract, extended with the Friends
//     contract. THIS is "extends Student
//     implements ClassRoom, Friends" — JS style.
// ─────────────────────────────────────────────
class Ranks extends Friends(ClassRoom(Student)) {

  #rank;
  #roomNo;
  #floor;

  constructor(rollNo, name, rank, roomNo, floor, address, age) {
    super(rollNo, name, address, age);   // 🙋 parent constructor first
    this.#rank = rank;
    this.#roomNo = roomNo;
    this.#floor = floor;
  }

  // 📋 STATIC — notice board
  static rankAndName(r) {
    r.print();
    console.log(`Rank: ${r.#rank}`);   // ✅ private fields ARE
  }                                    //    class-body-accessible

  studentDetail() {
    console.log(`Name: ${this.name}`);
    console.log(`Roll No: ${this.rollNo}`);
  }

  // 🎭 OVERRIDING the "interface contract"
  roomDetails() {
    console.log(`Floor: ${this.#floor}`);
    console.log(`Room No: ${this.#roomNo}`);
  }

  // 🎭 OVERRIDING the "abstract" method
  studentRank() {
    console.log(`I am a ranked student: ${this.#rank}`);
  }

  // 🎭 "OVERLOADING" — implements the Friends
  //    contract above: optional parameter + branch.
  //    ONE method handles BOTH call shapes.
  display(friend1, friend2) {
    if (friend2 === undefined) {
      console.log(`My friend is ${friend1}`);
    } else {
      console.log(`My friends are ${friend1} and ${friend2}`);
    }
  }
}

// ─────────────────────────────────────────────
// MAIN
// ─────────────────────────────────────────────
const subj1 = new Ranks(
  1,        // rollNo
  "Jashu",  // name
  1,        // rank
  101,      // roomNo
  2,        // floor
  "Guntur", // address
  23,       // age
);

console.log("----- Student Details -----");
subj1.studentDetail();

console.log("\n----- Person Details -----");
subj1.personDetails();

console.log("\n----- Rank -----");
Ranks.rankAndName(subj1);          // 📋 static — via CLASS name

console.log("\n----- Classroom -----");
subj1.roomDetails();

console.log("\n----- Student Rank -----");
subj1.studentRank();

console.log("\n----- Friends -----");
subj1.display("Nithin");           // one friend
subj1.display("Nithin", "Rahul");  // two friends

console.log("\n----- Encapsulation -----");
console.log(`Current Name: ${subj1.name}`);
subj1.name = "Rahul";              // 🛒 setter — official channel
console.log(`Updated Name: ${subj1.name}`);
subj1.studentDetail();

// ➕ BONUS: runtime polymorphism — works identically
console.log("\n----- Runtime Polymorphism (bonus) -----");
const subj2 = new Ranks(2, "Nithin", 3, 102, 2, "Vijayawada", 24);
for (const s of [subj1, subj2]) {
  s.studentRank();
}

// ➕ PROOF the mixin "interface" is ENFORCED at runtime —
//    a class that takes the Friends contract but
//    forgets to implement display() gets the
//    throwing stub silently inherited instead:
class LazyStudent extends Friends(Student) {
  // no display() here! The contract's throwing
  // stub is silently inherited instead.
}
const lazy = new LazyStudent(9, "Oops", "Nowhere", 20);
console.log("\n----- Interface Enforcement (bonus) -----");
try {
  lazy.display("nobody");
} catch (e) {
  console.log(`💥 ${e.message}`);   // "LazyStudent must implement display()"
}

// 🔒 Proof of encapsulation — this throws at runtime:
// subj1.#name        → SyntaxError (private)
// (JS truly hides it — not even reachable)
```

---

## 15. Language Comparison Table

| Concept | Java ☕ | Python 🐍 | TypeScript 🟦 | JavaScript 🟨 |
|---|---|---|---|---|
| Class | `class` | `class` | `class` | `class` (syntactic sugar over prototypes) |
| Object | `new C()` | `C()` | `new C()` | `new C()` |
| Encapsulation | `private` keyword | `__name` mangling | `private` keyword | `#field` (ES2022) |
| Inheritance | `extends` (single) | `extends` (**multiple!** via MRO) | `extends` (single) | `extends` (single) |
| Multiple inheritance | interfaces only | ✅ real classes | interfaces only | ❌ none |
| Abstract class | `abstract class` | `ABC` + `@abstractmethod` | `abstract class` | ❌ simulate with `throw` |
| Interface | `interface` | ❌ (use ABC / `Protocol`) | `interface` | ❌ keyword — **mixin factories** / duck typing |
| Overloading | ✅ compile-time | ❌ (default params) | ✅ declare + implement | ❌ (optional params) |
| Overriding | `@Override` | just redefine | just redefine | just redefine |
| Static | `static` | `@staticmethod` | `static` | `static` |
| Getters/Setters | methods `getX()/setX()` | `@property` | `get/set` keywords | `get/set` keywords |
| Constructor | class-name method | `__init__` | `constructor()` | `constructor()` |
| Call parent | `super()` | `super().__init__()` | `super()` | `super()` |
| Type checking | compile-time | runtime (hints optional) | compile-time | none |

---

## 16. Memory Tricks — Never Forget Again

| Concept | Trick | Story |
|---|---|---|
| **Class** | Blueprint 🏠 | One blueprint → many houses |
| **Object** | Real house 🏡 | Built from the blueprint, has its own furniture (state) |
| **Encapsulation** | Capsule 💊 / ATM 🏧 | Data sealed inside; access only through controlled doors |
| **Inheritance** | Family 👨‍👩‍👦 | Child gets parent's surname + adds own property. Say the **IS-A test** out loud |
| **Overloading** | "Call me" vs "Call me at 5" 📞 | Same word, more details — decided at **compile time**. "**Load** more params" |
| **Overriding** | Child rewrites parent's rule ✍️ | Decided at **runtime**. "**Ride** over the parent's method" |
| **Polymorphism** | One person, many roles 🎭 | Student / son / cricketer — same person, different behavior |
| **Abstraction** | Driving a car 🚗 | You know WHAT (steering, brake), not HOW (engine internals) |
| **Abstract class** | Half-filled form 📝 | Some methods filled, some blank. Can't submit a half form → can't instantiate |
| **Interface** | Electric socket 🔌 / Contract 📜 | 100% rules, zero implementation. Any plug that fits works |
| **Constructor** | Naming ceremony 👶 | Runs at birth, sets initial state, same name as class |
| **`super()`** | "Ask Dad first" 🙋 | Parent's constructor runs BEFORE the child's own work |
| **Static** | Notice board 📋 | One board for the whole school — belongs to class, not to any one student |
| **Getter** | Display window 👀 | Look, don't touch |
| **Setter** | Sales counter 🛒 | Change things through the official channel, with rules |

### The 4 Pillars — one-line exam answers
1. **Encapsulation** — *hiding* data behind methods (private + getters/setters)
2. **Inheritance** — *reusing* parent code in a child (extends)
3. **Polymorphism** — *one name, many forms* (overloading + overriding)
4. **Abstraction** — *showing what, hiding how* (abstract class + interface)

### Interview one-liner: Interface vs Abstract Class
> "An abstract class is a **half-filled form** — shared code + some blanks. An interface is a **pure contract** — all blanks, no code. Java lets you extend one class but implement many interfaces, so interfaces are how Java does multiple inheritance."

---

## 17. Expected Output

All four programs print the same story:

```
----- Student Details -----
Name: Jashu
Roll No: 1

----- Person Details -----
Address: Guntur
Age: 23

----- Rank -----
Jashu my Rollno is 1
Rank: 1

----- Classroom -----
Floor: 2
Room No: 101

----- Student Rank -----
I am a ranked student: 1

----- Friends -----
My friend is Nithin
My friends are Nithin and Rahul

----- Encapsulation -----
Current Name: Jashu
Updated Name: Rahul
Name: Rahul
Roll No: 1

----- Runtime Polymorphism (bonus) -----
I am a ranked student: 1
I am a ranked student: 3
```

The JavaScript version prints one extra block at the end (the interface-enforcement proof):

```
----- Interface Enforcement (bonus) -----
💥 LazyStudent must implement display()
```

That's the mixin contract firing in action — `LazyStudent` took the `Friends` interface but never implemented `display()`, so the inherited throwing stub blew up the moment it was called. In Java this error would be caught at **compile time**; in JS it can only fire at **runtime**.

Notice the last block: `s.studentRank()` is the **same line of code** both times, but two different students print different ranks. **That single line is runtime polymorphism** — the JVM/interpreter decides at runtime which class's version of `studentRank()` to execute, based on the actual object type.

---

*Built as a study companion — Java first (the reference), then the same school story retold in Python, TypeScript, and JavaScript.*
