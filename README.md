# Java Interview Questions

* [General Questions](#general-questions)
* [OOP Questions](#oop-questions)
* [Algorithms and Data Structures / Collections / Generics](#algorithms-and-data-structures--collections--generics)
* [Streams And Lambdas](#streams-and-lambdas)
* [Threads](#threads)
* [Design Patterns](#design-patterns)
* [Java EE](#java-ee)
* [Spring](#spring)
* [Generic WEB](#generic-web)
* [SQL](#sql)
* [Generic Questions](#generic-questions)
* [Java Interview Q&A](#java-interview-qa)
* [Bonus](#bonus)
* [Exercises](#exercises)

## General Questions

* What are the key memory segments inside JVM ? Explain **HEAP**, **STACK**.

   > Key memory segments:
   > - Program Counter (PC) Register
   > - Method Area
   > - **Heap**
   > - Java **Stack**
   > - Native Stack
   >
   > #####HEAP
   > Heap is the primary storage inside JVM for storing the runtime data that are accessed by the multiple threads. 
   > Heap memory is the common for all the threads, the data stored in the heap is accessible to all the threads 
   > running on JVM.
   > #####STACK
   > Java Stack is the memory used by the JVM threads to store the thread specific data. Stack memory is not shared among 
   > all the threads and it is created for each thread separately. Any data related to 
   > method like local variables, object references to heap are stored in the stack memory.
   
   [JAVABEAT][1]
     
* What is a **Memory Leak** ? How can a memory leak appear in **garbage collected** language?

   > Memory leak in Java is a situation where some objects are not used by application any more, but garbage collector 
   > fails to recognize them as unused.
   > As a result, these objects remain in memory indefinitely reducing the amount of memory available to the 
   > application.
   >
   > A memory leak can appear in garbage collector because sometimes it is difficult to determine the lifespan of a 
   > given object.
   
   [DZone][2] [Stackify][3]
   
* Is Java *pass-by-value* or *pass-by-reference*?

   > Java always passes parameter variables by value.
   
   [InfoWorld][4]
                                                     
* Write a Java method to swap the values of two integer values (*Is it possible?*):

   > ```java
   > public void swap(int x, int y) {
   >     System.out.println("Before swaping x = " + x + " and y = " + y);
   >     int temp = 0;
   >     temp = x;
   >     x = y;
   >     y = temp;
   >     System.out.println("After swaping x = " + x + " and y = " + y);
   > }
   >```
   
   [tutorialspoint][5]
                                                                                         
* What is a *primitive type* in Java ? What are the main *primitive types*?

   > A primitive type in Java is the most basic data types available. The main primitive types are 8: **boolean**, 
   > **byte**, **char**, **short**, **int**, **long**, **float** and **double**.
   
   [WIKIBOOKS][6]
    
* What is *auto-boxing/unboxing* ?

   > Auto-boxing is converting a primitive value into an object of the corresponding wrapper class. Unboxing is converting 
   > an object of a wrapper type to its corresponding primitive.
   
   [GeeksforGeeks][7]
                                                                                                                                                                                                                                          
* What is *implicit casting* ? What is *explicit casting*?

   > **Implicit** (Widening) casting is done automatically when passing a smaller size type to a larger size type, for 
   > example:
   > 
   > byte -> short -> char -> int -> long -> float -> double
   >
   > ```java
   > public class MyClass {
   >     public static void main(String[] args) {
   >      int myInt = 9;
   >      double myDouble = myInt; // Automatic casting: int to double
   >  
   >      System.out.println(myInt);      // Outputs 9
   >      System.out.println(myDouble);   // Outputs 9.0
   >     }
   > }
   > ```
   >
   > **Explicit** (Narrowing) casting is done manually converting a larger type to a smaller size type by placing the type
   > in parentheses in front of the value, for example:
   > 
   > double -> float -> long -> int -> char -> short -> byte
   >
   > ```java
   > public class MyClass {
   >     public static void main(String[] args) {
   >       double myDouble = 9.78;
   >       int myInt = (int) myDouble; // Manual casting: double to int
   >   
   >       System.out.println(myDouble);   // Outputs 9.78
   >       System.out.println(myInt);      // Outputs 9
   >     }
   > }
   > ```

   [w3schools.com][8]
    
* If developing an e-commerce site, what is the recommend type to use for the *price* if performance is not an issue.
 What is performance is an issue?
   > 
* Explain the usage of the following keywords: `strictfp`, `native`.

   > The **strictfp** keyword is used to force the precision of floating point calculations (float or double) in Java 
   > conform to [IEEE’s 754](https://en.wikipedia.org/wiki/IEEE_754#Standards) standard, explicitly.
   >
   > ```java
   > class StrictFPMethod {
   >     strictfp double computeTotal(double x, double y) {
   >         return x + y;
   >     }
   > }
   >```
   > 
   > The **native** keyword is used to declare a method which is implemented in platform-dependent code such as C or 
   > C++.
   >
   > ```java
   > public class NativeExample {
   >     public native void fastCopyFile(String sourceFile, String destFile);
   > }
   > ```

   [CodeJava][9] [CodeJava][10]
    
* Explain the usage of the following keyword: `final`.
   > The **final** keyword could be used in three different contexts:
   > - **Varible**
   >                                                     
   >   To create constant variables
   >   ```java
   >   // a final static variable PI
   >   static final double PI = 3.141592653589793;
   >   // a  blank final static  variable
   >   static final double PI;
   >   ```
   > - **Methods**
   >
   >   To prevent method overriding
   >   ```java
   >   private static final class RandomNumberGeneratorHolder {
   >       static final Random randomNumberGenerator = new Random();
   >   }
   >   ```
   > - **Classes**
   >
   >   To prevent inheritance
   >   ```java
   >   public final class Math {
   >       (...)
   >   }
   >   ```
    
   [GeeksforGeeks][11]
    
* Can you give example of a `final` class from the Java Standard library?

   > java.lang.Math
    
   [docs.oracle][12]
    
    
* What is the difference between `==` and `equals()`?

   > The main difference between the `.equals()` method and `==` operator is that one is method and the other is as operator.
   > Moreover, we can use `==` operator for reference comparison **(address comparison)** and the `.equals()` method for 
   > content comparison. In simple words, `==` checks if both objects point to the same memory location whereas `.equals()` 
   > evaluates the comparison of values in the objects.
    
   [GeeksforGeeks][13]

## OOP Questions

* What is a **constructor**?

   > A constructor in Java is a special method that is used to initialize objects. The constructor is called when an object
   > of a class is created. It can be used to set initial values for object attributes.
   >
   > ```java
   > public class MyClass {
   >    int x;
   > 
   >    // constructor
   >    public MyClass(int y) {
   >        x = y;
   >    }
   > 
   >    public static void main(String[] args) {
   >        MyClass myObj = new MyClass(5);
   >        System.out.println(myObj.x);
   >    }
   > }
   > // Outputs 5
   > ```

   [w3schools.com][14]

* What is the **default constructor**?

   > When any constructor is implemented in a given class, the Java compiler inserts default constructor into the code.
   > It will not be seen in the source code(the .java file) as it is inserted during compilation and 
   > present in the bytecode(.class file).
                                          
    [BeginnersBook][15]
                                           
* Explain the the concept of *Inheritance*. Why doesn't Java supports the concept of *Multiple Inheritance*?

   > Inheritance allows to create new classes that share some of attributes of existing classes **(parent classes)**. It 
   > works by letting a new class **(child class)** adopt the properties of the parent. For this is used the keyword 
   > **extends** to define a new class that inherits properties from an old class.
   >
   > Java doesn't support the concept of **Multiple Inheritance** for a matter of **simplicity** and for being **rarely
   > used**.This avoid for example the **diamond problem of multiple inheritance**.
   
   [Stackify][16] [javapapers][17]
   
* What is **Polymorphism** ?

   > Polymorphism allows the same word to mean different things in different contexts. There are two different ways of 
   > polymorphism in Java, **method overloading** and **method overriding**.
   
   [Stackify][18]
                               
* What is **Overloading** ? What is **Overriding**?

  > **Overriding**, OOP polymorphism concept that allows to use one method in different ways depending on whether it is
  > invoked by an object of the parent class or by an object of the child class.
  >
  > **Overloading**, OOP polymorphism concept that a single method may perform different functions depending on the 
  > context in which it is called. That is, a single method name might work in different ways depending on what arguments
  > are passed to it.
                                                        
  [Stackify][19]

* What is the output if we execute the following code:
   ```java
   public abstract class Engineer {
       public static String name() {
           return "Engineer";
       }
  
       public String favorite() {
           return "Math and Physics";
       }
  
       public static void main(String[] args) {
           Engineer e2 = new ElectricalEngineer();
           Engineer e3 = new SoftwareEngineer();
           System.out.format("%s %s \n", e2.name(), e2.favorite());
           System.out.format("%s %s", e3.name(), e3.favorite());
       }
   }
  
   class ElectricalEngineer extends Engineer {
       public static String name() { return "Electrical Engineer" }
       public String favorite() { return "Electricity"; }
   }
  
   class SoftwareEngineer extends Engineer {
       public static String name() { return "Software Engineer"; }
       public String favorite() { return "Java"; }
   }
   ```
  
  > // Engineer Electricity
  >
  > // Engineer Java
* Can a `static` method be overwritten ?

   > No you cannot override `static` methods in Java. Because they are resolved during compile time.
   > Overriding depends on having an instance of a class. The point of polymorphism is that you can subclass a class and
   > the objects implementing those subclasses will have different behaviors for the same methods defined in the 
   > superclass (and overridden in the subclasses). A static method is not associated with any instance of a class so 
   > the concept is not applicable.

   [Javarevisited][20]                                            
                                                      
* Explain the concept of *Encapsulation*.

   > **Encapsulation** allows keeping fields within a class private, the providing access to them via a public method. 
   > It's a protective barrier that keeps the data and code safe within the class itself. This way we can reuse objects
   > like code components or variables without allowing open access to the data system-wide.
   
   [Stackify][21]

* How would you encapsulate the following class:

   ```java
   public class Circle {
      double radius;
      double area;   
   }
   ```
  
   > ```java
   > public class Circle {
   >    double radius;
   >    double area;
   >  
   >    double getRadius() {
   >       return this.radius;
   >    }
   >  
   >    void setRadius(double radius) {
   >       this.radius = radius;
   >    }
   >  
   >    double getArea() {
   >       return this.area;
   >    }
   >  
   >    void setArea(double area) {
   >       this.area = area;   
   >    } 
   > }
   >   ```

* What is *immutability* ?

   > When you have a reference to an instance of an object, the contents of that instance cannot be changed. That is
   > objects that you cannot change the contents after they have been set.
   >
   > ```java
   > // Point is a mutable class
   > Point myPoint = new Point( 0, 0 );
   > System.out.println( myPoint );
   > myPoint.setLocation( 1.0, 0.0 );
   > System.out.println( myPoint );
   >
   > // String is an imutable class
   > String myString = new String( "old String" );
   > System.out.println( myString );
   > myString.replaceAll( "old", "new" );
   > System.out.println( myString );
   >  ```
   > 
   > // java.awt.Point[0.0, 0.0]
   >
   > //	java.awt.Point[1.0, 0.0]
   >
   > //	old String
   >
   > //	old String
   
   [JavaRanch][22]

* How can we write an **Immutable** class ?

   > * Private fields
   >
   >   ```java
   >   public class ImmutablePerson {
   >      // note there are no mutators!
   >      private String firstName;
   >      private String lastName;
   >   
   >      // etc...   
   >   ```
   >   
   > * Methods can't be overridden.
   >   
   >   If a given class gets extended, it could be added extra fields that are not immutable, or the methods could be
   >   overridden to return a different value each time. There is two different ways to avoid it, by either **making the
   >   class final** (Strong Immutability) or **making your methods final** (Weak Immutability).
   >
   > * Don't provide mutators
   >
   > * If a field isn't primitive or immutable, make a deep clone on the way in and the way out.
   >
   >    ```java
   >    import java.util.Date;
   >       public final class ImmutablePerson {
   >          private String firstName;
   >          private String lastName;
   >          // Date is a mutable Class
   >          private Date dob;
   >       
   >          public BetterPerson(String firstName, String lastName, Date dob) {
   >             this.firstName = firstName;
   >             this.lastName = lastName;
   >   
   >             // it is needed to take a copy of the Date instance
   >             // when it is passed in rather than trusting the
   >             // reference to the instance we are given
   >             this.dob = new Date(dob.getTime());
   >          }
   >          
   >          public Date getDOB() {
   >              // it is needed to pass out a copy of the Data
   >              // instance to prevent anyone from getting
   >              // a reference to our mutable Date field
   >              return new Date(this.dob.getTime());
   >          }
   >   
   >          // etc...
   >   ```
   
   [JavaRanch][23]

* Explain of the concept of **Marker Inteface**.

   > A marker interface is an interface that has no methods or constants inside it. It provides run-time type 
   > information about objects, so the compiler and JVM have additional information about the object.

   [Baeldung][24]

* Explain the concept of **Serialization**.

   > Serialization is a mechanism to convert an object into stream of bytes so that it can be written into a file,
   > transported through a network or stored into database. In simple words serialization is converting an object to
   > stream of bytes.
                                               
   [BeginnersBook][25]
                                                  
* Explain how the keyword **transient** works.

   > Java `transient` keyword is used in serialization. If you define any data member as transient, it will not be
   > serialized.
   >
   > Let's take an example, I have declared a class as User, it has five data members password, age, username, email
   > and dob. If you serialize the object, all the values will be serialized but I don't want to serialize one value,
   > e.g. password and age then we can declare the password and age as `transient`.
   >
   >   ```java
   >   // A sample class that uses transient keyword to 
   >   // skip their serialization. 
   >   class User implements Serializable {
   >  
   >      // making password transient for security  
   >      private transient String password; 
   >   
   >      // making age transient as age is auto- 
   >      // computable from DOB and current date. 
   >      transient int age; 
   >   
   >      // serialize other fields 
   >      private String username, email; 
   >      Date dob; 
   >   
   >      // other code 
   >   } 
   >   ```
   
   [javaTpoint][26] [GeeksforGeeks][27]
    
* Explain the concept behind the **Cloneable** interface and how does it work.
   
   >    The concept behind the **Cloneable** interface is **Marker Interface** which was explained in more detail above. 
   
* What is the output if we execute the following code:

   ```java
   public class Constructors {
       public static void main(String[] args) {
           new Dog();
       }
   }
  
   class Animal {
   
       public Animal() {
           System.out.println("1");
       }
   
       public Animal(String s) {
           this();
           System.out.println("2");
       }
   }
  
   class Dog extends Animal {
       public Dog() {
           super("3");
           System.out.println("4");
       }
   }
   ```
  
  > // 1    
  >
  > // 2
  >
  > // 4
  
* What is the output if we execute the following code:

   ```java
   public class Ternary {
       public static void main(String[] args) {
           Integer x = 1987;
           Integer y = 1987;
           System.out.println(x == y ? "A" : "B");
       }
   }
   ```
  
  

* What is the output if we execute the following code:

```java
public class Strings {
    public static final String DELOITTE = new String("Deloitte");
    public static void main(String[] args) {
        String s1 = "Deloitte";
        String s2 = new String(s1);
        String s3 = new String("Deloitte");
        String s4 = "Deloitte";
        System.out.println(s1==s2);
        System.out.println(s1==s3);
        System.out.println(s1==s4);
        System.out.println(s1==DELOITTE);
        System.out.println(s2==DELOITTE);
        System.out.println(s3==DELOITTE);
    }
}
```
* What is a *Java Interface* ?

   > Like a class, an interface can have methods and variables, but the methods declared in an interface are by default abstract (only method signature, no body).  
   >  
   >  - Interfaces specify what a class must do and not how. It is the blueprint of the class.
   >  - An Interface is about capabilities like a Player may be an interface and any class implementing Player must be able to (or must implement) move(). So it specifies a set of methods that the class has to implement.
   >  - If a class implements an interface and does not provide method bodies for all functions specified in the interface, then the class must be declared abstract.

   [GeeksforGeeks][28]

* Does an interface `extends` or `implements` another interface ?

   > An interface only can extend with the keyword `extends` another interface once it cannot implement any methods. 

* What is a *Java Abstract Class* ?

   > A class which is declared as `abstract` is known as an abstract class. It can have abstract and non-abstract methods.
   > It needs to be extended and its method implemented. It cannot be instantiated.

  [javaTpoint][29]

* Does a *Java Abstract Class* `extends` or `implements` another *Java Abstract Class* ?

   > An abstract class  only can `extends` another abstract class since an abstract 
   > class cannot implement abstract methods.

* Explain the usage of the `default` keyword (Java 8 onwards).

   > This feature was introduced on Java 8 allowing an interface to provide a default implementation.

* With the introduction of the `default` keyword are there any reasons to use *Abstract Classes* instead of
 *Interfaces* ?
 
   > Yes, although Java 8 interface default methods has bridge down the differences between interfaces ans
   > abstract classes, still have major differences.
   > - Varibles in interface are **public static final**. But abstract class can have other type of variables
   > like **private, protected** etc.
   >
   > - Methods in interface are **public** or **public static** but methods in abstract class can be **private**
   > and **protected** too.
   >
   > - **Abstract class** in used to establish relation between interrelated objects. Use **interface** to
   > establish relation between unrelated classes.

  [stackoverflow][30]
 
* **Unchecked Exceptions** vs. **Checked Exceptions**.
   
   > In Java there are two types of exceptions.
   > - **Checked** are the exceptions that are **checked at compile time**. If some code within a method throws
   > checked exception, then the method must either handle the exception or it must specify the exception using
   > throws keyword.
   > 
   > - **Unchecked** are the exceptions that **are not checked at compile time**. In C++, qll the exceptions are
   > unchecked, so it is not forced by compiler to either handle or specify the exception. It is up to the
   > programmers to be civilized, and specify or catch the exceptions. 
   > 
   > In Java exceptions under Error and RuntimeException classes are unchecked exceptions, everything else under
   > throwable is checked.
   >
   >                 +-----------+
   >                 | Throwable |
   >                 +-----------+
   >                  /         \
   >                /             \
   >        +-------+            +-----------+
   >        | Error |            | Exception |
   >        +-------+            +-----------+
   >         /  |  \             / |        \
   >       \________/         \______/        \
   >       unchecked           checked       +------------------+
   >                                         | RuntimeException |
   >                                         +------------------+
   >                                           /   |    |      \
   >                                          \_________________/
   >                                              unchecked

  [GeeksForGeeks][31]

* What are the differences between **Exceptions** and an **Errors** ? Are there any similitudes ?

  > Exceptions and Errors are both one subclasse of Throwable class. The error indicates a problem that
  > mainly occurs due the lack of system resources and our application should not catch these types of 
  > problems. Some of the examples of erros are system crash error and out of memory error. **Error mostly
  > occur at runtime that's they belong to an unchecked type**.
  >
  > Exceptions are problems which can **occur at runtime and compile time**. It mainly occurs in the code
  > written by the developers. Exceptions are divided into two categories such as checked exceptions
  > and unchecked exceptions.
  >  
  > #### Summary of Differences
  >
  > | Errors  | Exceptions   |
  > |---|---|
  > | Recovering from Errors in not possible  | We can recover from exceptions by either using try-catch block or throwing exceptions back to caller   |
  > | All errors in java are unckecked type  | Exceptions include both checked as well as unchecked type   |
  > | Errors are mostly caused by the environment in which program is running  | Program itself is responsible for causing excpetions   |
  > | Errors occur at runtime and not know to the compiler  | All exceptions occur at runtime but checked exceptions are know to compile while unchecked are not   |
  > | They are defined in java.lang.Error package  | They are defined in java.lang.Exception package   |
  > | Examples: java.lang.StackOverflowError, java.lang.OutOfMemoryError  | Checked Exceptions: SQLException, IOException Unchecked Exceptions: ArrayIndexOutOfBoundException, NullPointerException, ArithemeticException   |

  [tutorialspoint][32] [GeeksForGeeks][33]

* Name 3 **Unchecked Exceptions**.

  > IndexOutOfBoundsException, IllegalArgumentException, ArithmeticException

  [Programming Pearls][34]

* Name 3 **Checked Exceptions**.

  > IOException, ClassNotFoundException, IllegalAccessException

  [Programming Pearls][35]

* What are **Java Annotations** ?

  > Annotations are used to provide supplement information about a program.
  > - Annotations start with '@'
  > - Annotations do not change action of a compiled program
  > - Annotations help to associate metadata (information) to the program element i.e. instance variables,
  > constants, contructors, methods, classes, etc
  > - Annotations are not pure comments as they can change the way a program is treated by compiler
  > 
  > There are 3 categories of Annotations:
  > ##### Marker Annotations
  > 
  > The only **purpose is to mark a declaration**. These annotations contain no members and do not consist any data.
  > Thus, its presence as an annotation us sufficient. Since, marker interface contains no members, simply determining 
  > wheter is present or absent is suffucient. **@Override** is an example of Marker Annotations.
  > Example: @TestAnnotation()
  > ##### Single value Annotations
  > 
  > These annotations contain only one member and allow a shorthand from specifying the value of the member.
  > We only need to specify the value for that member when the annotations applied and don't need to specify
  > the name of the member However is order to use this shorthand, the name of the member must be value.
  > Example: @TestAnnotation("testing")
  > ##### Full Annotations
  > 
  > These annotations consist of multiple data members/name, value, pairs.
  > Example: @TestAnnotation(owner="Rahul", value="Class Geeks")

  [GeeksForGeeks][36]

## Algorithms and Data Structures / Collections / Generics

* Explain the **O(n) Notation** (Big O).
* How does a **Stack** data-structure works ? Are there any standard Java Stack implementations ?
* Recursively calculate the sum of numbers from a `List<Integer>` (don't use for/do/while loops).
* Why is not possible to use primitives as generic types ?
* Explain the concept of **Type Erasure**.
* Explain the following data structures: *List*, *Map*, *Queue*, *Set*.
* Name a few implementations for each interface:

| List<T>    | Set<T>     | Map<K,V>     | Queue<T>  |
| ------  | ------  | ------  | ------ |
|         |         |         |        |
|         |         |         |        |
|         |         |         |        |
|         |         |         |        |

* What is the output if we run the following code:
```java
import java.util.HashSet;
import java.util.Set;

class A {
    @Override
    public int hashCode() {
        return 0;
    }
}

public class HashTest {
    public static void main(String[] args) {
        Set<A> set = new HashSet<>();

        set.add(new A());
        set.add(new A());
        set.add(new A());

        System.out.println(set.size());
    }
}
```
* Explain how a **HashMap** is implemented. What is the relationship between *equals()* and *hashCode()*.
* What are *hash collisions* ?
* What are the operations for which a **LinkedList** is more efficient than an **ArrayList** ?
* What is the difference between **CopyOnWriteArrayList**, **Vector** and **ArrayList** ?
* What are the key differences between a **HashMap** and **ConcurrentHashMap** ?
* How does a **WeakHashMap** works ? What are the main differences between a **WeakHashMap** and a **HashMap** ?
* Does a **Set** accepts `null` as an element ?
* What is the difference between an `Iterator` and `ListIterator` ?
* Are there any **Immutable** Collection Classes ?
* What is a **RingBuffer** ?
* What happens if we run the following code:
```java
public static void main(String[] args) {
        List<String> list = new LinkedList<>();

        list.add("A");
        list.add("C");
        list.add("D");

        Iterator<String> it = list.iterator();

        System.out.println(it.next());

        list.add(1, "B");
        
        System.out.println(it.next());
        System.out.println(it.next());
        System.out.println(it.next());
}
```

### Streams and Lambdas

* What is a **Functional Interface** ?
* Can you please explain what is a **Predicate**, **Consumer**, **Function**, **Supplier** ?
* What is the difference between a **Stream** and an **Iterator** ?
* Using the `filter()` method write a method that returns only the positive numbers from a `List<Integer>`.
* What is a `parallelStream()` ? How is different from a standard `stream()` ?
* Find out the max element from a `List<Integer>` using the `reduce()` method.
* Find out the sum of elements from a `List<Integer>` using the `reduce()` method.
* What is the output if we run the following code:
```java
    public static void main(String[] args) {
        final List<String> l = new LinkedList<>();

        l.add("A");
        l.add("B");
        l.add("C");

        l.stream().forEach(e -> {
            l.add("Z");
            System.out.println(e);
        });
    }
```
* What is the output if we run the following code: 
```java
    public static void main(String[] args) throws InterruptedException {

        List<String> list = new LinkedList<>();

        list.add("A");
        list.add("B");
        list.add("C");
        list.add("D");
        list.add("E");
        list.add("F");
        list.add("G");
        list.add("H");

        ListIterator<String> iterator = list.listIterator();

        for (int i = 0; i < list.size(); i++) {
            CompletableFuture.runAsync(() -> System.out.println(iterator.next()));
        }

        Thread.sleep(2000);
    }
```

### Threads

* What is a Thread ?
* Is the `++` operator thread-safe ?
* How can we implement a Thread ?
* How *synchronized* keyword works ?
* How is the method `thread.join()` working ?
* Explain the concept of **Thread Starvation** ?
* Explain the concept of **Thread Pool** ?
* What can you tell about the **Executor Interface** ?
* What is a *Semaphore* in Java ?
* What is the output if we execute the following code:
```java
    public static void main(String[] args) throws ExecutionException, InterruptedException {

        CompletableFuture<Void> cf1 = CompletableFuture.runAsync(() -> {
            System.out.println("B");
        });

        CompletableFuture<Void> cf2 = CompletableFuture.runAsync(() -> {
            System.out.println("A");
        });

        cf1.get();
        cf2.get();
    }
```    

### Design Patterns

* Singleton
* Builder
* Factory
* Visitor

### Java EE

* What is a Servlet ?
* What are the main methods of a HttpServlet ?
* What are the main bean scopes ? Explain the following annotations: `@RequestScoped`, `@SessionScoped`,
 `@ApplicationScoped`, `@Dependent`, `@Conversation` .
* What is the main difference between a Servlet and Filter ?

### Spring

* Explain the concept of *Inversion of Control*. What is the **Spring IoC Container** ?
* Explain the concept of *Dependency Injection* (in Spring).
* What are the main advantages and disadvantages for *setter dependency injection* vs *constructor dependency 
injection* ?
* What is a **Spring Bean** ?
* What are the main **Spring Bean Scopes** ? Explain `singleton`, `prototype`, `request`, `session`, `global session`.
* What are the **Spring Stereotyping Annotations** ? Explain the differences between: `@Component`, `@Controller`,
 `@Repository`, `@Service`.
* Explain how the following Spring Annotations are working: `@Autowired`, `@Qualifier`, `@Required`.
* Explain how the `@Async` annotations functions.
* Explain the concept of **Spring Profiles**.
* What is **Spring Boot** ?
* What is **Spring Data** ?
* What is **Spring Integration** ?
* What is **Spring Batch** ?
* What is **Spring Security** ?

### Generic WEB

* What is **JWT** ? How does **JWT** works ?
* Where is recommended to store **JWT** tokens received from the Server on the client-side ?
* What are the main HTTP verbs ?
* What is the difference between **POST** and **PUT** ?
* What is the difference between **POST** and **PATCH** ?
* What is the difference between **POST** and **GET** ?
* You have to develop a *REST API* for a book store. This API needs to implement CRUD-like operations. How would you
 design the API ?

| Operation | HTTP VERB | ENDPOINT |
| --------- | --------- | -------- |
| Add a book | | |
| Remove a book | | |
| List books with pagination | | |
| Edit a book | | |
| Get info for a book | | |

### SQL

*Given the following SQL table:*

| id | full_name | mng_id |
| -- | --------- | ------ |
| 100 | Patrick Read | 101 |
| 101 | Bradley Hayes | `null` |
| 102 | Kieran Bennett | 101 |
| 103 | George Barnes | 101 |
| 104 | Alex Griffiths | 102 |
| 105 | Issac Jacobs | 102 |
| 106 | Will Mack | 104 |

*Write an SQL query that returns the following result:*

| id | full_name | mng_full_name |
| -- | --------- | ------------- |
| 100 | Patrick Read | Bradley Hayes |
| ... | ............ | ............. |

*Write an SQL query that returns one row containing the manager with the most direct subalterns.*

### Generic Questions
* From a protocol perspective what is the difference between **UDP** and **TCP** ? 
* What library would use to write a Scheduler in Java ?
* What are the main **Maven** alternatives ?
* What are the main **JUnit** alternatives ?
* How is **Mockito** used ? Are there any other alternatives to **Mockito**
* What is **Continuous Integration** (CI) ?
* Name other **JVM**-based languages ?
* What is **Functional Programming** ? Can you give a few examples of Functional Programming languages ?

### Java Interview Q&A
> https://javarevisited.blogspot.com/2017/08/top-10-java-concurrenthashmap-interview.html#axzz6Rma2apZA
> https://www.javatpoint.com/corejava-interview-questions
> https://www.softwaretestinghelp.com/core-java-interview-questions/
> https://www.tutorialspoint.com/java/java_interview_questions.htm
> https://www.geeksforgeeks.org/commonly-asked-java-programming-interview-questions-set-2/
> https://www.javacodegeeks.com/java-interview-questions.html
> https://www.java67.com/2012/09/top-10-tricky-java-interview-questions-answers.html

### Bonus
* Java hashmap is thread safe
* Is ++ (increment) operator thread-safe in Java?
> https://www.javapedia.net/Java-Multithreading/619
*  How Volatile in Java works? Example of volatile keyword in Java
> https://javarevisited.blogspot.com/2011/06/volatile-keyword-java-example-tutorial.html
* Difference between JVM, JIR, JRE, and JDK in Java
> https://javarevisited.blogspot.com/2011/12/jre-jvm-jdk-jit-in-java-programming.html
* HashMap Vs. ConcurrentHashMap Vs. SynchronizedMap – How a HashMap can be Synchronized in Java?
> https://crunchify.com/hashmap-vs-concurrenthashmap-vs-synchronizedmap-how-a-hashmap-can-be-synchronized-in-java/

### Exercises

#### Pangrams (Simple)

Roy wanted to increase his typing speed for programming contests. So, his friend advised him to type the sentence "The 
quick brown fox jumps over the lazy dog" repeatedly, because it is a pangram. (Pangrams are sentences constructed by 
using every letter of the alphabet at least once.)
After typing the sentence several times, Roy became bored with it. So he started to look for other pangrams.
Given a sentence s, tell Roy if it is a pangram or not.

**Input Format**
Input consists o a string s.
Example:
```
We promptly judged antique ivory buckles for the next prize
```

**Output Format**
Output a line containing “pangram” if s is pangram, otherwise print “not pangram”.
Example:
```
pangram
```

#### Balanced Parentheses (Medium)

Given a sequence consisting of parentheses, determine whether the expression is balanced.
A sequence of parentheses is balanced if every open parentheses can be paired uniquely with a closed parentheses that
occurs after the former. Also, the interval between them must be balanced. You will be given three types of
parentheses: (, {, and [.


```
{[()]} - This is a balanced parentheses.
{[(])} - This is not a balanced parentheses.
```

Example:

**Input**
```
3
{[()]}
{[(])}
{{[[(())]]}}
```

**Ouput**
```
YES
NO
YES
```

[1]: https://javabeat.net/jvm-memory/ "JVM Memory Management"
[2]: https://dzone.com/articles/what-memory-leak-java  "What is a Memory Leak in Java?"
[3]: https://stackify.com/memory-leaks-java/  "How Memory Leaks Happen in a Java Application"
[4]: https://www.infoworld.com/article/3512039/does-java-pass-by-reference-or-pass-by-value.html  "Does Java pass by reference or pass by value?"
[5]: https://www.tutorialspoint.com/Java-program-to-swap-two-integers  "Java program to swap two integers"
[6]: https://en.wikibooks.org/wiki/Java_Programming/Primitive_Types  "Primitive Types" 
[7]: https://www.geeksforgeeks.org/autoboxing-unboxing-java/  "Autoboxing and Unboxing in Java" 
[8]: https://www.geeksforgeeks.org/autoboxing-unboxing-java/  "Java Type Casting" 
[9]: https://www.codejava.net/java-core/the-java-language/java-keyword-strictfp  "Java strictfp keyword example" 
[10]: https://www.codejava.net/java-core/the-java-language/native-keyword  "Java native keyword example" 
[11]: https://www.geeksforgeeks.org/final-keyword-java/  "final keyword in java" 
[12]: https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html  "Class Math" 
[13]: https://www.geeksforgeeks.org/difference-equals-method-java/  "Difference between == and .equals() method in Java" 
[14]: https://www.w3schools.com/java/java_constructors.asp  "Java Constructors" 
[15]: https://beginnersbook.com/2014/01/default-constructor-java-example/  "Java – Default constructor with example" 
[16]: https://stackify.com/oops-concepts-in-java/  "What Are OOP Concepts in Java? The Four Main OOP Concepts in Java, How They Work, Examples, and More" 
[17]: https://javapapers.com/core-java/why-multiple-inheritance-is-not-supported-in-java/  "Why Multiple Inheritance is  Not Supported in Java" 
[18]: https://stackify.com/oops-concepts-in-java/   "What Are OOP Concepts in Java? The Four Main OOP Concepts in Java, How They Work, Examples, and More" 
[19]: https://stackify.com/oops-concepts-in-java/   "What Are OOP Concepts in Java? The Four Main OOP Concepts in Java, How They Work, Examples, and More" 
[20]: https://javarevisited.blogspot.com/2013/03/can-we-overload-and-override-static-method-java.html   "Can You Overload or Override Static methods in Java"
[21]: https://stackify.com/oops-concepts-in-java/   "What Are OOP Concepts in Java? The Four Main OOP Concepts in Java, How They Work, Examples, and More"
[22]: https://javaranch.com/journal/2003/04/immutable.htm   "Mutable and Immutable Objects"
[23]: https://javaranch.com/journal/2003/04/immutable.htm   "Mutable and Immutable Objects"
[24]: https://www.baeldung.com/java-marker-interfaces   "Marker Interfaces in Java"
[25]: https://beginnersbook.com/2014/07/java-serialization/   "Java Serialization"
[26]: https://www.javatpoint.com/transient-keyword   "Java Transient Keyword"
[27]: https://www.geeksforgeeks.org/transient-keyword-java/   "transient keyword in Java"
[28]: https://www.geeksforgeeks.org/interfaces-in-java/   "Interfaces in Java"
[29]: https://www.javatpoint.com/abstract-class-in-java   "Abstract class in Java"
[30]: https://stackoverflow.com/a/33957123   "When do I have to use interfaces instead of abstract classes?"
[31]: https://www.geeksforgeeks.org/checked-vs-unchecked-exceptions-in-java/   "Checked vs Unchecked Exceptions in Java"
[32]: https://www.geeksforgeeks.org/errors-v-s-exceptions-in-java/   "Errors V/s Exceptions In Java"
[33]: https://www.tutorialspoint.com/difference-between-exception-and-error-in-java   "Difference between Exception and Error in Java"
[34]: https://itblackbelt.wordpress.com/2015/02/17/checked-vs-unchecked-exception-in-java-example/   "Checked vs. Unchecked Exception in Java Example"
[35]: https://itblackbelt.wordpress.com/2015/02/17/checked-vs-unchecked-exception-in-java-example/   "Checked vs. Unchecked Exception in Java Example"
[36]: https://www.geeksforgeeks.org/annotations-in-java/   "Annotations in Java"