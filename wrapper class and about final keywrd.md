# wrapper class and about final keywrd::

Excellent question 👍 Let’s break down the **`final` keyword** in Java for both **primitive types** and **non-primitive types (objects, classes, methods)** with examples.

---

## 🔹 What is `final` keyword in Java?

The `final` keyword is a **modifier** in Java.

It means **“cannot be changed”** depending on where it’s used.

---

## 1. `final` with **Primitive Types**

- If a **primitive variable** (like `int`, `double`, `char`, etc.) is declared `final`, its value **cannot be changed once assigned**.

### Example:

```java
class Demo {
    public static void main(String[] args) {
        final int x = 10;
        System.out.println(x);

        // x = 20;  ❌ Error: cannot assign a value to final variable x
    }
}

```

👉 Here, once `x = 10` is assigned, it is **fixed forever**.

This makes `x` a **constant**.

---

## 2. `final` with **Non-Primitive Types (Objects, References)**

- If you declare an **object reference** as `final`, the **reference itself cannot point to another object**,
    
    but the **contents (fields) of the object can still be modified** (unless those fields are also final).
    

### Example:

```java
class Person {
    String name;
}

class Demo {
    public static void main(String[] args) {
        final Person p = new Person();
        p.name = "Alice";  // ✅ Allowed (modifying object state)
        System.out.println(p.name);

        // p = new Person(); ❌ Error: cannot reassign a final reference
    }
}

```

👉 Key Point:

- You **cannot change the reference** (`p` must always point to the same object).
- But you **can change the data** inside the object (`p.name` can change).

---

## 3. `final` with **Classes**

- If a class is declared `final`, it **cannot be extended (no inheritance allowed)**.

### Example:

```java
final class Animal { }

// class Dog extends Animal { }  // ❌ Error

```

---

## 4. `final` with **Methods**

- If a method is declared `final`, it **cannot be overridden** in subclasses.

### Example:

```java
class Parent {
    final void show() {
        System.out.println("Parent show()");
    }
}

class Child extends Parent {
    // void show() {}  ❌ Error: cannot override final method
}

```

---

## ✅ In short

- **Primitive + final** → value cannot change (constant).
- **Object reference + final** → reference cannot change, but object’s internal state can.
- **Class + final** → class cannot be inherited.
- **Method + final** → method cannot be overridden.

---

👉 Do you also want me to explain the **difference between `final`, `finally`, and `finalize`** (they sound similar but are very different)?

 

Great 👍 Let’s go step by step into **Wrapper Classes** in Java, explained in a simple and detailed way.

---

## 🔹 What are Wrapper Classes?

- In Java, **everything is an object**, except **primitive data types** (`int`, `char`, `double`, etc.).
- **Wrapper classes** are special classes in `java.lang` package that **wrap primitive data types into objects**.

👉 Each primitive type has a corresponding wrapper class:

| **Primitive** | **Wrapper Class** |
| --- | --- |
| `byte` | `Byte` |
| `short` | `Short` |
| `int` | `Integer` |
| `long` | `Long` |
| `float` | `Float` |
| `double` | `Double` |
| `char` | `Character` |
| `boolean` | `Boolean` |

---

## 🔹 Why are Wrapper Classes Important?

1. **Objects required in Collections**
    
    Collections (like `ArrayList`, `HashMap`) only store objects, not primitives.
    
    Wrapper classes let you put primitive values into collections.
    
    ```java
    ArrayList<Integer> list = new ArrayList<>();
    list.add(10); // primitive int automatically converted to Integer
    
    ```
    
2. **Utility Methods**
    
    Wrapper classes have useful methods.
    
    Example:
    
    ```java
    int num = Integer.parseInt("100");  // convert String to int
    String s = Integer.toString(50);   // convert int to String
    
    ```
    
3. **Null Handling**
    
    Primitive variables cannot hold `null`, but wrapper objects can.
    
    ```java
    Integer x = null; // possible
    // int y = null; ❌ not allowed
    
    ```
    
4. **Autoboxing and Unboxing**
    
    Java automatically converts between primitives and wrappers.
    

---

## 🔹 Examples

### Example 1: Wrapping and Unwrapping (Manual)

```java
class Demo {
    public static void main(String[] args) {
        int a = 5;

        // Manual boxing
        Integer obj = Integer.valueOf(a);

        // Manual unboxing
        int b = obj.intValue();

        System.out.println("Primitive: " + a);
        System.out.println("Wrapper: " + obj);
        System.out.println("Unboxed: " + b);
    }
}

```

---

### Example 2: Autoboxing and Unboxing (Automatic)

```java
class Demo {
    public static void main(String[] args) {
        int a = 10;

        // Autoboxing: int → Integer
        Integer obj = a;

        // Unboxing: Integer → int
        int b = obj;

        System.out.println("Wrapper: " + obj);
        System.out.println("Primitive: " + b);
    }
}

```

👉 Output:

```
Wrapper: 10
Primitive: 10

```

---

## 🔹 ✅ In short:

- **Wrapper class** = object representation of primitive type.
- Needed for **collections, utility methods, null handling, and OOP consistency**.
- **Autoboxing** = primitive → wrapper (automatic).
- **Unboxing** = wrapper → primitive (automatic).
