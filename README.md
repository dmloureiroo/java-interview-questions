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
   > Java Stack is the memory used by the JVM threads to store the thread specific data. Stack memory is not shared
   > among all the threads and it is created for each thread separately. Any data related to method like local
   > variables, object references to heap are stored in the stack memory.
   
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

   > Auto-boxing is converting a primitive value into an object of the corresponding wrapper class. Unboxing is
   > converting 
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
   > **Explicit** (Narrowing) casting is done manually converting a larger type to a smaller size type by placing the
   > type in parentheses in front of the value, for example:
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

   > A constructor in Java is a special method that is used to initialize objects. The constructor is called when an
   > object of a class is created. It can be used to set initial values for object attributes.
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
  > context in which it is called. That is, a single method name might work in different ways depending on what
  > arguments are passed to it.
                                                        
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

   > Like a class, an interface can have methods and variables, but the methods declared in an interface are by default
   > abstract (only method signature, no body).  
   >  
   > - Interfaces specify what a class must do and not how. It is the blueprint of the class.
   > - An Interface is about capabilities like a Player may be an interface and any class implementing Player must be
   > able to (or must implement) move(). So it specifies a set of methods that the class has to implement.
   > - If a class implements an interface and does not provide method bodies for all functions specified in the
   > interface, then the class must be declared abstract.

   [GeeksforGeeks][28]

* Does an interface `extends` or `implements` another interface ?

   > An interface only can extend with the keyword `extends` another interface once it cannot implement any methods. 

* What is a *Java Abstract Class* ?

   > A class which is declared as `abstract` is known as an abstract class. It can have abstract and non-abstract
   > methods.
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

* What are the differences between **Exceptions** and an **Errors** ? Are there any similitudes?

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

  > Big O time is the language and metric used to describe the efficiency of algorithms.
  > O(n) is linear time complexity once the rate of growth scales in direct proposition to the input.
  > For **n** inputs, the algorithm might perform n operations.

  [jarednielsen.com][37]

* How does a **Stack** data-structure works ? Are there any standard Java Stack implementations?

  > A Stack is an Abstract Data Type (ADT), commonly used in most programming languages. This is a 
  > LIFO data structure. LIFO stands for Last-in-first-out. The element which is placed last is accessed
  > first. Stack have two operations to represent this, **push()** pushing an element on the Stack and 
  > **pop()** removing an element from the Stack.
  >
  > There is a Java implementation of Stack under java.utils package.

  [tutorialspoint][38]

* Recursively calculate the sum of numbers from a `List<Integer>` (don't use for/do/while loops).

  >   ```java
  >   public static int summer(List<Integer> list) {
  >       if (list.size() == 0) {
  >           return 0;
  >       } else if (list.size() == 1) {
  >           return list.get(0);
  >       } else {
  >           int left = summer(list.subList(0, list.size()/2));
  >           int right = summer(list.subList(list.size()/2, list.size()));
  >           return left + right;
  >       }
  >   }
  >   ``` 
  
  [stackoverflow][39]

* Why is not possible to use primitives as generic types?

  > Generics in Java are an entirely compile-time construct, the compiler turns all generic 
  > uses into casts to the right type. So, anything that is used as generics has to be converted
  > to Object and the primitive types aren't, that is the reason why primitives can't be used in
  > generics.

  [stackoverflow][40]

* Explain the concept of **Type Erasure**.

  > Generics were introduced to the Java language to provide tighter checks at compile time
  > and to support generic programming. But an important constraint was the need for compatibility
  > with previous versions of Java, generic code had to be compatible with preexisting, nongeneric
  > code. To achieve that what type erasure does is replacing type parameters with their bound type,
  > which is Object if no explicit bound is specified, and then applying the appropriate casts (as
  > determined by the type arguments) to mantain type compatibility with the types specified by the  
  > type arguments.

  [stackoverflow][41]

* Explain the following data structures: *List*, *Map*, *Queue*, *Set*.

  > #### List
  > List in Java provides the facility to mantain the ordered collection the index-based methods to insert,
  > update, delete and search the elements. It can have the duplicate elements also. We can also store the
  > null in the list.
  >
  > The list interface is found in the **java.util** package and inherits the Collection interface. It is a 
  > factory of ListIterator interface. Through the ListIterator, we can iterate the list in forward and backward
  > directions. The implementation classes of List interface are ArrayList, LinkedList, Stack and Vector.
  >
  > #### Map
  > A map contains values on the basis of key, i.e. key and value pair. Each key and value pair is know as an
  > entry A Map contains unique keys.
  > A map is useful if you have to search, update or delete elements on the bases of a key. 
  > 
  >         +++++++                                     +++++++++++++
  >         | Map | <  * * * * * * * *                  | Interface |
  >         +++++++                   *                 +++++++++++++
  >            ^                      *                  
  >            |                      *                 +-------+                       
  >            |                      *                 | Class |                       
  >      ++++++++++++++         +------------+          +-------+
  >      | Sorted Map |         | Sorted Map |      
  >      ++++++++++++++         +------------+              ^       
  >            ^                      ^                     * implements
  >            *                      |                     *      
  >            *                      |                         
  >       +----------+         +---------------+            ^
  >       | Tree Map |         | LinkedHashMap |            | extends
  >       +----------+         +---------------+            |
  >                                    
  > A map doesn't allow duplicate keys, but you can have duplicate values. HashMap and LinkedHashMap allow                                              
  > null keys and values, but TreeMap doesn't allow any null key or value.                                                                          
  > A Map can't be traversed, so you need to convert it into Set using keySet() or entrySet() method.                                              
  >                                   
  >   | Class  | Description  |
  >   |---|---|
  >   | HashMap  | HashMap is the implementation of Map, but it doesn't maintain any order.  |
  >   | LinkedHashMap  | LinkedHashMap is the implementation of Map. It inherits HashMap class. It maintains insertion order.  |
  >   | TreeMap  | TreeMap is the implementation of Map and SortedMap. It maintains ascending order.  |
  >
  > #### Queue
  > The queue interface is provided in **java.util** package and it implements the Collection interface. The queue
  > implements FIFO i.e. First In First Out. This means that the element entered first are the ones that are deleted
  > first.
  >                                 
  > A collection designed for holding elements prior to processing. Besides basic Collection operations, queues provide
  > additional insertion, extraction, and inspection operations. Each of these methods exists in two forms: one throws 
  > an exception if the operation fails, the other returns a special value (either null or false, depending on the
  > operation). The latter from of the insert operation is designed specifically for use with capacity-restricted Queue
  > implementations, insert, operations cannot fail.
  >       
  > #### Set
  > A collection that constains no duplicate elements. The Set interface contains only methods inherited from Collection
  > and adds the restriction that duplicate elements are prohibited.
  > Set also adds a stronger contract on the behavior of the equals and hashCode operations, allowing Set instances to
  > be compared meaningfully even if their implementation types differ.       
                                                                                                     
  [javaTpoint][42]
  [javaTpoint][43]
  [javaTpoint][44]
  [javaTpoint][45]
  [tutorialspoint][46]

* Name a few implementations for each interface:

  > | List<T>    | Set<T>        | Map<K,V>      | Queue<T>           |
  > | ---------- | -------       | ------------- | ------------------ |
  > | ArrayList  | HashSet       | HashMap       | AbstractQueue      |
  > | LinkedList | TreeSet       | TreeMap       | ArrayBlockingQueue |
  > |            | LinkedHashSet | LinkedHashMap | ArrayDeque         |
  > |            |               |               |                    |

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

  > // 3

* Explain how a **HashMap** is implemented. What is the relationship between *equals()* and *hashCode()*.

  > Hash table based implementation of the Map interface. This implementation provides all of the optional map
  > operations, and **permits null values and the null key**. (The HashMap class is roughly equivalent to HashTable,
  > except that it is unsynchronized and permits nulls). This class makes no garantees as to the order of the map in
  > particular, it does not guarantee that the order will remain constant over time.
  > 
  > There is a contract between *equals()* and *hashCode()*
  > - If two objects are equal, then they must have the same hash code.
  > - If two objects have the same hash code, they may or may not be equal.

  [programcreek][47]

* What are *hash collisions* ?

  > A collision occurs when two different keys have the same hashcode, which can happen because two unequal objects in
  > java can have the same hashcode.
                                    
  [Javarevisited][48]

* What are the operations for which a **LinkedList** is more efficient than an **ArrayList** ?

  > "ArrayList should be used where more search operations are required, and LinkedList should be used where more insert
  > and delete operation is needed".
  >
  > A LinkedList is more efficient than an ArrayList inserting and deleting.
  > A LinkedList is more performant when inserting a value because it only need to find the index where we want to add
  > the value and rearranging pointers of underlying DoubleLinkedList. In another hand when inserting a value in an
  > ArrayList it is needed to:
  > 
  > - Check whether the underlying array us already full or not.
  > - If the array is full then it copies the data from the old array to a new array (size double than an old array).
  > - After that, starting from the given index, shift values by one to create space for the new value.
  > - Then add the value at given index.
  > 
  > When removing a value the difference between an ArrayList and a LinkedList is that, when removing an element from a
  > LinkedList we just need to modify pointers which is O(1) complexity, but in ArrayList, we need to shift all elements
  > after the index of the removed value to fill the gap created.

  [DZone][49]

* What is the difference between **CopyOnWriteArrayList**, **Vector** and **ArrayList** ?

  > | **CopyOnWriteArrayList**                                                           | **Vector**                                                                         | **ArrayList**                                                                                                      |
  > |------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
  > | synchronized                                                                       | synchronized                                                                       | not synchronized                                                                                                   |
  > | thread safe                                                                        | thread safe                                                                        | not thread safe                                                                                                    |
  > | not a legacy                                                                       | legacy                                                                             | not a legacy                                                                                                       |
  > | slow has some overhead in thread management/ locking etc                           | slow has some overhead in thread management/ locking etc                           | fast                                                                                                               |
  > | fail-safe and it will never throw ConcurrentModificationException during iteration | fail-safe and it will never throw ConcurrentModificationException during iteration | fail-fast and ArrayList throws ConcurrentModificationException if concurrent modification happens during iteration |

  [tutorialspoint][50]
  [javaTpoint][51]
  [HowToDoInJava][52]

* What are the key differences between a **HashMap** and **ConcurrentHashMap** ?

  > - **HashMap is non-synchronized** in nature i.e. HashMap is **not Thread-safe** whereas **ConcurrentHashMap is
  > Thread-safe** in nature. 
  >
  > - **HashMap performance is relatively high** because it is **non-synchronized** in nature and **any number of
  > threads can perform simultaneouly**. But **ConcurrentHashMap performance is low** sometimes becuse **Threads are
  > required to wait on ConcurrentHashMap**.
  >
  > - While one thread is Iterating the HashMap object if other thread try to add/modify the contents of object them we
  > will get Run-time exception saying **ConcurrentModificationException**. Whereas in ConcurrentHashMap we wont get any
  > exception while performing any modification.
  
  [GeeksForGeeks][53] 

* How does a **WeakHashMap** works ? What are the main differences between a **WeakHashMap** and a **HashMap** ?

  > Hash table based implementation of the Map interface, with weak keys. An entry in a WeakHashMao with weak keys.
  > An entry in a WeakHashMap will automatically be removed when its key is no longer in ordinary use.
  >
  > Important differences between HashMap and WeakHashMap:
  >
  > - **Strong vs Weak References**: **Weak Reference** Objects are not the default type/class of Reference Object and
  > they should be explicitly specific while using them. This type of reference is used in WeakHashMap to reference the
  > entry objects. **Strong References**: This is default type/class of Reference Object. Any object which has an active
  > strong reference are not eligible for garbage collection. In HashMap, key objects have strong reference.
  >  
  > - **Role of Garbage Collector**: Garbage Collected: In HashMap, entry object (entry object stores key-value pairs)
  > is not eligible for garbage Collecion i.e. HashMap is dominant over Garbage Collector.
  >
  > - **Clone method Implementation**: HashMap implements Cloneable interface.
  > WeakHashMap does not implement Cloneable interface, it only implements Map interface. Hence, there is no clone()
  > method in the WeakHashMap class.

  [Oracle][54]
  [Baeldung][55]
  [GeeksForGeeks][56]

* Does a **Set** accepts `null` as an element ?

  > Yes, at most one null element once Set does not accept duplicate values.

  [Oracle][57]
  
* What is the difference between an `Iterator` and `ListIterator` ?

  > **Iterators** are used in Collection framework in Java to **retrieve elements one by one**. It can be applied to any
  > Collection object. By using Iterator we can **perform both read and remove operations**. Iterator must be used
  > whenever we want to enumerate elements in all collections framework implemented interfaces like **Set, List, Queue,
  > Deque** and also in all implemented classes of Map interface. **Iterator is the only cursos available for entire
  > collection framework**.
  >
  > It is **only applicable for List collection implemented** classes like **arraylist, linkedlist** etc. It **provides
  > bi-directional iteration**. ListIterator must be used when we want to enumerate elemets of List. **This cursor has
  > more functionality (methods) than iterator**.
  > 
  > Differences:
  > 
  > | Iterator  | ListIterator  |
  > |---|---|
  > | Can traverse elements present in Collection only in the forward direction  | Can traverse elements present in Collection both in forward and backward direction  |
  > | Helps to traverse Map, List and Set  | Can only traverse List  |
  > | Indexes cannot be obtained by using Iterator  | It has methods like nextIndex() and previousIndex() to obtain indexes of elements at any time while traversing list  |
  > | Cannot modify or replace elements present in Collection  | We can modify or replace elements with the help of Set(E e)  |
  > | Cannot add elements and it throws ConcurrentModificationException  | Can easily add elements to a collection ar any time  |
  > | Certain methds of Iterator are next(), remove() and hasNext()  | Certain methods of listIterator are next(), previous(), hasNext(), add(E e)  | 

  [Oracle][58]

* Are there any **Immutable** Collection Classes ?

  > No there are not any Immutable classes in the Collection framework.

  [codefx.org][59]

* What is a **RingBuffer** ?

  > Ring Buffer (or Circular Buffer) is a **bounded circular data structure that is used for buffering data between two or
  > more threads**. As we keep writing to a ring buffer, it wraps around as it reaches the end. 
  >
  > How it works:
  > 
  > A Ring Buffer is implemented using a **fixed-size array** that wraps around at the boundaries.
  >
  > Apart from the array, it keeps track of three things:
  >
  > - the next available slot in the buffer to insert an element.
  > - the next unread element in the buffer
  > - and the end of the array- tho the start of the array

  [Baeldung][60]

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

  > It will print `A` and the will thrown the runtime exception `ConcurrentModificationException`

### Streams and Lambdas

* What is a **Functional Interface** ?

  > An Interface that contains exactly one abstract method is known as functional interface. It can hava any number of 
  > default, static methods but can only have one abstract method. It can also declare methods of object class.
  >
  > Functional Interface is also known as Single Abstract Interfaces or SAM Interfaces. It is a new feature in Java,
  > which helps to achieve functional programming approach.

  [javaTpoint][61]

* Can you please explain what is a **Predicate**, **Consumer**, **Function**, **Supplier** ?

  > **Predicate**
  > 
  > Represents a predicate (boolean-valued function) of one argument.
  > 
  > This is a functional interface whose functional method is `test(Object)`.
  > 
  > **Consumer**
  > 
  > Represents an operation that **accepts a single input argument and return no result**. Unlike most other functional
  > interfaces, `Consumer` is expected to operate via side-effects.
  > 
  > This is a functional interface whose functional method is `accept(Object)`.
  > 
  > **Function**
  >
  > Represents a function that accepts one argument and produces a result.
  >
  > This is a function interface whose function method is `apply(Object)`.
  > 
  > **Supplier**
  >
  > Represents a **supplier of resuls**.
  >
  > There is no requirement that a new or distinct result be returned each time the supplier is invoked.
  >
  > This is a functional interface whose functional method is `get()`.

  [docs.oracle][62]
  [docs.oracle][63]
  [docs.oracle][64]
  [docs.oracle][65]

* What is the difference between a **Stream** and an **Iterator** ?

  > 

  [][66]

* Using the `filter()` method write a method that returns only the positive numbers from a `List<Integer>`.

  > ```java
  > private static List<Integer> positiveNumbers(List<Integer> numbers) {
  >  return numbers.stream()
  >              .filter(e -> e > 0)
  >              .collect(Collectors.toList());
  > }
  > ```

* What is a `parallelStream()` ? How is different from a standard `stream()` ?

  > Parallel streams divide the provided task into many and run them in different threads, utilizing multiple cores of
  > the computer. On the other hand sequential streams work just like for-loop using single core. 

  [LogicBig.com][67]

* Find out the max element from a `List<Integer>` using the `reduce()` method.

  > ```java
  > private static List<Integer> positiveNumbers(List<Integer> numbers) {
  >  return numbers.stream()
  >              .filter(e -> e > 0)
  >              .collect(Collectors.toList());
  > }
  > ``` 

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

| Operation                  | HTTP VERB | ENDPOINT |
|----------------------------|-----------|----------|
| Add a book                 |           |          |
| Remove a book              |           |          |
| List books with pagination |           |          |
| Edit a book                |           |          |
| Get info for a book        |           |          |

### SQL

*Given the following SQL table:*

| id  | full_name      | mng_id |
|-----|----------------|--------|
| 100 | Patrick Read   | 101    |
| 101 | Bradley Hayes  | `null` |
| 102 | Kieran Bennett | 101    |
| 103 | George Barnes  | 101    |
| 104 | Alex Griffiths | 102    |
| 105 | Issac Jacobs   | 102    |
| 106 | Will Mack      | 104    |

*Write an SQL query that returns the following result:*

| id  | full_name    | mng_full_name |
|-----|--------------|---------------|
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
[37]: https://jarednielsen.com/big-o-linear-time-complexity/   "Big O Linear Time Complexity"
[38]: https://www.tutorialspoint.com/data_structures_algorithms/stack_algorithm.htm   "Data Structure and Algorithms - Stack"
[39]: https://stackoverflow.com/a/8927360   "Sum of List<Integer> recursively"
[40]: https://stackoverflow.com/a/2721557   "Why don't Java Generics support primitive types?"
[41]: https://docs.oracle.com/javase/tutorial/java/generics/erasure.html   "Type Erasure"
[42]: https://www.javatpoint.com/java-list   "Java List"
[43]: https://www.javatpoint.com/java-map   "Java Map"
[44]: https://www.javatpoint.com/data-structure-queue   "Queue"
[45]: https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html   "Interface Queue<E>"
[46]: https://www.tutorialspoint.com/java/java_set_interface.htm   "Java - The Set Interface"
[47]: https://www.programcreek.com/2011/07/java-equals-and-hashcode-contract/   "Java equals() and hashCode() Contract"
[48]: https://javarevisited.blogspot.com/2016/01/how-does-java-hashmap-or-linkedhahsmap-handles.html   "How does Java HashMap or LinkedHahsMap handles collisions?"
[49]: https://dzone.com/articles/performance-analysis-of-arraylist-and-linkedlist-i   "Performance Analysis of ArrayList and LinkedList in Java"
[50]: https://www.tutorialspoint.com/Difference-between-ArrayList-and-CopyOnWriteArrayList-in-Java   "Difference between ArrayList and CopyOnWriteArrayList in Java"
[51]: https://www.javatpoint.com/difference-between-arraylist-and-vector   "Difference between ArrayList and Vector"
[52]: https://howtodoinjava.com/java/collections/arraylist/arraylist-vs-vector/   "Difference between ArrayList vs Vector in Java"
[53]: https://www.geeksforgeeks.org/difference-hashmap-concurrenthashmap/   "Difference between HashMap and ConcurrentHashMap"
[54]: https://docs.oracle.com/javase/7/docs/api/java/util/WeakHashMap.html   "Class WeakHashMap<K,V>"
[55]: https://www.baeldung.com/java-weakhashmap   "Guide to WeakHashMap in Java"
[56]: https://www.geeksforgeeks.org/hashmap-vs-weakhashmap-java/   "Hashmap vs WeakHashMap in Java"
[57]: https://docs.oracle.com/javase/10/docs/api/java/util/Set.html   "Interface Set<E>"
[58]: https://www.geeksforgeeks.org/difference-between-an-iterator-and-listiterator-in-java/   "Difference between an Iterator and ListIterator in Java"
[59]: http://blog.codefx.org/java/immutable-collections-in-java/   "Immutable Collections In Java – Not Now, Not Ever"
[60]: https://www.baeldung.com/java-ring-buffer   "https://www.baeldung.com/java-ring-buffer"
[61]: https://www.javatpoint.com/java-8-functional-interfaces   "Java Functional Interfaces"
[62]: https://docs.oracle.com/javase/8/docs/api/java/util/function/Predicate.html   "Interface Predicate<T>"
[63]: https://docs.oracle.com/javase/8/docs/api/java/util/function/Consumer.html   "Interface Consumer<T>"
[64]: https://docs.oracle.com/javase/8/docs/api/java/util/function/Function.html   "Interface Function<T,R>"
[66]:    ""
[67]: https://www.logicbig.com/tutorials/core-java-tutorial/java-util-stream/sequential-vs-parallel.html   "Java 8 Streams - Sequential vs Parallel streams"
