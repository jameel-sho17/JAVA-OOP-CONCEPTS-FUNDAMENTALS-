*Constructors in Java - Complete Guide
A constructor is a special method used to initialize objects in Java. It's called automatically when an object is created.

1. What is a Constructor?
Special method that has the same name as the class

No return type (not even void)

Automatically called when object is created using new keyword

Used to initialize object state

2. Types of Constructors
A. Default Constructor (No-argument Constructor)
java
public class Student {
    String name;
    int age;
    
    // Default constructor
    public Student() {
        name = "Unknown";
        age = 0;
        System.out.println("Default constructor called");
    }
}

// Usage
Student s1 = new Student(); // Calls default constructor
B. Parameterized Constructor
java
public class Student {
    String name;
    int age;
    
    // Parameterized constructor
    public Student(String studentName, int studentAge) {
        name = studentName;
        age = studentAge;
        System.out.println("Parameterized constructor called");
    }
}

// Usage
Student s1 = new Student("John", 20); // Calls parameterized constructor
C. Copy Constructor
java
public class Student {
    String name;
    int age;
    
    // Parameterized constructor
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // Copy constructor
    public Student(Student original) {
        this.name = original.name;
        this.age = original.age;
        System.out.println("Copy constructor called");
    }
}

// Usage
Student s1 = new Student("John", 20);
Student s2 = new Student(s1); // Creates copy of s1
3. Constructor Characteristics
Basic Rules:
java
public class Car {
    String brand;
    String model;
    int year;
    
    // Constructor rules:
    // 1. Same name as class
    // 2. No return type
    public Car(String carBrand, String carModel, int carYear) {
        brand = carBrand;
        model = carModel;
        year = carYear;
    }
}
4. this Keyword in Constructors
A. Referring to Current Object
java
public class Employee {
    String name;
    double salary;
    
    public Employee(String name, double salary) {
        this.name = name;       // this.name refers to instance variable
        this.salary = salary;   // name refers to parameter
    }
}
B. Constructor Chaining (Calling one constructor from another)
java
public class Rectangle {
    int length;
    int width;
    
    // Default constructor
    public Rectangle() {
        this(1, 1); // Calls parameterized constructor
        System.out.println("Default constructor");
    }
    
    // Parameterized constructor
    public Rectangle(int length, int width) {
        this.length = length;
        this.width = width;
        System.out.println("Parameterized constructor");
    }
}

// Usage
Rectangle r1 = new Rectangle(); // Calls both constructors
5. Complete Examples
Example 1: Bank Account Class
java
public class BankAccount {
    private String accountNumber;
    private String accountHolder;
    private double balance;
    
    // Default constructor
    public BankAccount() {
        this.accountNumber = "NOT_ASSIGNED";
        this.accountHolder = "Unknown";
        this.balance = 0.0;
    }
    
    // Parameterized constructor
    public BankAccount(String accountNumber, String accountHolder) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = 0.0;
    }
    
    // Fully parameterized constructor
    public BankAccount(String accountNumber, String accountHolder, double initialBalance) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = initialBalance;
    }
    
    // Copy constructor
    public BankAccount(BankAccount original) {
        this.accountNumber = original.accountNumber;
        this.accountHolder = original.accountHolder;
        this.balance = original.balance;
    }
    
    // Methods
    public void displayAccountInfo() {
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Account Holder: " + accountHolder);
        System.out.println("Balance: $" + balance);
    }
}

// Usage
public class TestBankAccount {
    public static void main(String[] args) {
        BankAccount acc1 = new BankAccount(); // Default constructor
        BankAccount acc2 = new BankAccount("123456", "John Doe"); // 2-param constructor
        BankAccount acc3 = new BankAccount("789012", "Jane Smith", 1000.0); // 3-param constructor
        BankAccount acc4 = new BankAccount(acc3); // Copy constructor
        
        acc1.displayAccountInfo();
        acc2.displayAccountInfo();
        acc3.displayAccountInfo();
        acc4.displayAccountInfo();
    }
}
Example 2: Student Management
java
public class Student {
    private int rollNumber;
    private String name;
    private String[] subjects;
    
    // Constructor with array parameter
    public Student(int rollNumber, String name, String[] subjects) {
        this.rollNumber = rollNumber;
        this.name = name;
        this.subjects = subjects; // Shallow copy
    }
    
    // Better constructor with deep copy
    public Student(int rollNumber, String name, String[] subjects) {
        this.rollNumber = rollNumber;
        this.name = name;
        
        // Deep copy for mutable objects
        if (subjects != null) {
            this.subjects = new String[subjects.length];
            for (int i = 0; i < subjects.length; i++) {
                this.subjects[i] = subjects[i];
            }
        }
    }
    
    public void displayStudentInfo() {
        System.out.println("Roll Number: " + rollNumber);
        System.out.println("Name: " + name);
        System.out.print("Subjects: ");
        if (subjects != null) {
            for (String subject : subjects) {
                System.out.print(subject + " ");
            }
        }
        System.out.println();
    }
}
6. Constructor Overloading
java
public class Book {
    private String title;
    private String author;
    private double price;
    private int pages;
    
    // Constructor 1: Only title
    public Book(String title) {
        this(title, "Unknown Author", 0.0, 0);
    }
    
    // Constructor 2: Title and author
    public Book(String title, String author) {
        this(title, author, 0.0, 0);
    }
    
    // Constructor 3: Title, author, price
    public Book(String title, String author, double price) {
        this(title, author, price, 0);
    }
    
    // Constructor 4: All parameters
    public Book(String title, String author, double price, int pages) {
        this.title = title;
        this.author = author;
        this.price = price;
        this.pages = pages;
    }
    
    public void displayBookInfo() {
        System.out.println("Title: " + title);
        System.out.println("Author: " + author);
        System.out.println("Price: $" + price);
        System.out.println("Pages: " + pages);
        System.out.println("-------------------");
    }
}

// Usage
public class TestBook {
    public static void main(String[] args) {
        Book book1 = new Book("Java Programming");
        Book book2 = new Book("Python Guide", "John Smith");
        Book book3 = new Book("C++ Basics", "Jane Doe", 29.99);
        Book book4 = new Book("Data Structures", "Mike Johnson", 39.99, 350);
        
        book1.displayBookInfo();
        book2.displayBookInfo();
        book3.displayBookInfo();
        book4.displayBookInfo();
    }
}
7. Important Points about Constructors
Key Rules:
Name must match class name exactly

No return type (not even void)

Can be overloaded (multiple constructors with different parameters)

Can use access modifiers (public, private, protected, package-private)

Cannot be abstract, final, or static

Cannot be inherited but can be called from subclass using super()

Private Constructors:
java
public class Singleton {
    private static Singleton instance;
    
    // Private constructor to prevent instantiation
    private Singleton() {
        // initialization code
    }
    
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
Constructor vs Method:
Constructor	Method
Same name as class	Any valid name
No return type	Must have return type
Called automatically with new	Called explicitly
Cannot be inherited	Can be inherited
8. Common Mistakes to Avoid
java
public class CommonMistakes {
    private int value;
    
    // ❌ WRONG: Has return type
    // public void CommonMistakes() { }
    
    // ✅ CORRECT: No return type
    public CommonMistakes() {
        value = 0;
    }
    
    // ❌ WRONG: Name doesn't match class
    // public MyClass() { }
    
    // ✅ CORRECT: Name matches class exactly
    public CommonMistakes(int value) {
        this.value = value;
    }
}
Constructors are fundamental to object-oriented programming in Java, providing a clean way to initialize objects with valid initial states.
