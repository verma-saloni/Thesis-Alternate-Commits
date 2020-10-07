# Learning the Default Visibilities of Classes, Nested Classes and Members in C#

C# is a powerful, and simple general-purpose programming language. It is an object-oriented language implying objects are created via classes and will have various ranges or visibilities in the development environment. Understanding what the default visibilities of Classes, Nested Classes and Members is crucial for creating efficient code as per the specified requirements. 



## Classes in C#

A class is the building block of C#. It is used to form object(s), and functions are performed on them which forms the base of the whole program or software. The class is what defines the meaning i.e the type and scope of the object, and basically serves as a blueprint. The instance of a class is 'object'. Other concepts associated with a class are its methods (grouped statements that perform a  particular function) and variables (a name given to storage area depending on its type).  

#### How to Define a Class

Start by mentioning the keyword 'Class' and then the name of the class. The class body is defined by curly braces, as the example below:

``` c#
<access specifier> class  ClassName {
    // Defining the class, members and variables
}
```

Other than the basic declaration, there are some additional attributes that can be specified along with the class definition according to your need. 

- **Modifiers:** The default access specifier is *Internal* and if not mentioned, access for methods is *Private*. 
- **Class Identifier:** The variable of type class is mentioned here. The identifier is capitalized by convention.

- **Base class / Superclass:** If a class is inherited (elaborated further) the name of its base class can be mentioned, preceded by the *colon* (:). 
- **Interfaces:** A number of interfaces can be implemented by a class which are specified using the *colon (:)*. It is allowed for a class to implement more than one interface.
- **Body:** The class body is defined within the curly braces *{}*.

To familiarize yourself with these concepts, please see the below example code. 

```c#
using System;

namespace SimpleInterest {
   class Money {
      public double income;   // Income of First Person in family
      public double loan;  // Income of Second Person in family
      public double interest;   // The interest on loan to be paid
   }
   class Expenses {
      static void Main(string[] args) {
         Money Money1 = new Money();//Declare first object Money1 of type Money
         Money Money2 = new Money();//Declare second object Money2 of same type
         double expense = 0.0;    // Store the expenses here

         // Money 1 specification
         Money1.income = 5000.0;
         Money1.loan = 600.0;
         Money1.interest = 0.7;

         // Money 2 specification
         Money2.income = 10000.0;
         Money2.loan = 1200.0;
         Money2.interest = 0.85;
           
         // Expenses of first person 
         expense = Money1.income - Money1.loan * Money1.interest;
         Console.WriteLine("Expenses of First Person : {0}",  expense);

         // Expenses of second person
         expense = Money2.income - Money2.loan * Money2.interest;
         Console.WriteLine("Expenses of Second Person : {0}", expense);
         Console.ReadKey();
      }
   }
}
```

On execution, we get this output: 

```c#
Expenses of First Person : 4580
Expenses of Second Person : 8980
```

**Please note:**

- The dot operator can be used for accessing the class variables, which acts as the link between the class and the member name. 

- **Data type** will specify what type of variable it is. Meanwhile, **Return Type** is for the data type of the data the method returns, if present.

### Member Functions of a Class

<u>Member functions</u> are called so because they are defined within the class body. Consequently, they have the same prototype as other variables defined in a class. It will operate on the objects that belong to its own class and will have access to all the members of a class for that specific object.

<u>Member Variables</u> are essentially the attributes of a given object. They are private so that encapsulation can be implemented. In C#, **Encapsulation** is the ability of an object to conceal its behavior and the associated data, if it is not necessary for the user. Through this property, a set of methods and methods can be considered and acted upon as a single unit. They can be accessed via the public member functions.

To understand the concept of member functions and their scope, let us look at the following example.

```c#
using System;

namespace MoneyApplication {
   class Money {
      private double income;   
      private double loan;  
      private double interest;   
      
      public void setIncome( double inc ) {
         income = inc;
      }
      public void setLoan( double lon ) {
         loan = lon;
      }
      public void setInterest( double itr ) {
         interest = itr;
      }
      public double getExpense() {
         return income * loan * interest;
      }
   }
   class Moneytester {
      static void Main(string[] args) {
         Money Money1 = new Money();   // Declare Money1 of type Money
         Money Money2 = new Money();
         double expense;
         
         // Declare Money2 of type Money
         // Money 1 specification
         Money1.setIncome(60.0);
         Money1.setLoan (57.0);
         Money1.setInterest(0.56);
         
         // Money 2 specification
         Money2.setIncome(20.0);
         Money2.setLoan(24.0);
         Money2. setInterest (0.09);
         
         // volume of Money 1
         expense = Money1.getExpense();
         Console.WriteLine("Expense of First Person ( Money1)  : {0}" ,expense);
         
         // volume of Money 2
         expense = Money2.getExpense();
         Console.WriteLine("Expense of Second Person ( Money2) : {0}", expense);
         
         Console.ReadKey();
      }
   }
}
```

### Objects

An object is the most basic unit in OOPS and the languages that implement this practice. Once an object is created, it interacts by invoking functions. They can be thought of as the real-life entities in the programming world. 

**Instantiating a Class**: A class is instantiated by creating an object. A given class can have any number of objects.

**Initializing an object**: The new operator allocates memory for a new object, by initiating the class and returns a reference to that memory location.

> The C# compiler can differentiate between constructors based on the number of arguments and their types. 

### Nested Classes 

In C#, one class can be defined with the definition of another class. These are known as Nested Classes. It allows the user to logically clump classes that are used for one purpose, or together. This enhances encapsulation properties and makes the code more readable and manageable. 

For example:

```c#
using System; 
// Outer class 
public class Outer_class
{ 
    // Method of outer class 
    public   void   method1
    {         
        Console.WriteLine(   "Outer class method"   );        
    }    
    // Inner class         
    public   class   Inner_class 
    {    
        // Method of inner class             
        public   void   method2()    
        {               
            Console.WriteLine(   "Inner class Method"   );   
        }   
    }    
} 
// Driver Class   
public   class   GFG {    
    // Main method         
    static   public   void   Main()       
    {       // Create the instance of outer class          
        Outer_class obj1 =    new   Outer_class();           
        obj1.method1();       // This statement gives an error because             							 you are not allowed to access inner               								 class methods with outer class objects
        obj1. method2();       // Creating an instance of inner class
        Outer_class.Inner_class obj2 = new   Outer_class.Inner_class();       
        obj2.method2();    // Accessing the method of inner class 
    }  
```

The output of this code is:

```
Display for Outer Class 1.
Display for Inner Class 2.
```

**Note:**

- A nested class can be declared with any access modifier, namely *private, public, protected, internal, protected internal, or private protected.*

- An Outer class  cannot directly access inner class members as visible in the example above.

- It is possible to create objects of inner class in the outer class.

- An Inner class is allowed to access a static member declared in outer class. A method is shown below:

  ```c#
  // Main Driver Class 
  public class DriverClass { 
   
      // Main method 
      static public void Main() 
      {  
          // To access the static methodA of the inner class 
          Outer_class1.Inner_class2.methodA(); 
      } 
  } 
  ```

- The Inner class can access any non-static member that has been declared in the outer class.

- Scope of a nested class is limited by the scope of its (outer) enclosing class.

- If nothing is specified, the nested class is private (default).

- Any class can be inherited into another class in C# (including a nested class).

- The user can inherit a nested class from outer class.

  

This article duly explained how the classes are defined in C#, and how the scope of different objects can be used for powerful code creation. Armed with this knowledge, anyone can set preferences, permissions for using objects and polymorphism, etc. for fewer lines of code and better performance optimization. 

Happy learning C#!

------------------

### Understanding the Visibilities

We have just learnt that the nested class defaults to private access and can only be accessed through its outer class.  We can now elaborate on what is the purpose of the four kinds of access specifiers available in C#. The access specifier defines the access rules of a given type and the members associated with it, as shown below:

- **private:** very limited access for the member that is defined with the private keyword.
- **public:** all members, functions defined as public have no restrictions on their access within and even outside the class, at assembly. 
- **internal:** is an important access specifier which allows access to members within the assembly. An assembly is the produced .dll or .exe from your .NET Language code (C#). Hence, if you have a C# project that has ClassA, ClassB and ClassC then any internal type and members will become accessible across the classes with in the assembly.
- **protected:** comes into play only at the time of inheritance ie. a protected type/member is will be accessible when a child is inherited. Otherwise, the protected member is not visible.
- **Protected internal:** is the mix of two types: protected and internal at the same time. A protected internal member can be accessed within assembly due to its internal property.  It will also be accessible via inheritance due to its protected feature.  



Regardless of whether the outer type is a class or a struct, nested types default to [private](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private); they are accessible only from their containing type. In the previous example, the `Nested` class is inaccessible to external types.

You can also specify an [access modifier](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/access-modifiers) to define the accessibility of a nested type, as follows:

- Nested types of a **class** can be [public](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/public), [protected](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected), [internal](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/internal), [protected internal](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected-internal), [private](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private) or [private protected](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private-protected).

  However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/sealed) generates compiler warning [CS0628](https://docs.microsoft.com/en-us/dotnet/csharp/misc/cs0628), "new protected member declared in sealed class."

- Nested types of a **struct** can be [public](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/public), [internal](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/internal), or [private](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private).

The following example makes the `Nested` class public:

C#Copy

```csharp
class Container
{
    public class Nested
    {
        Nested() { }
    }
}
```

The nested, or inner, type can access the containing, or outer, type. To access the containing type, pass it as an argument to the constructor of the nested type. For example:

C#Copy

```csharp
public class Container
{
    public class Nested
    {
        private Container parent;

        public Nested()
        {
        }
        public Nested(Container parent)
        {
            this.parent = parent;
        }
    }
}
```

A nested type has access to all of the members that are accessible to its containing type. It can access private and protected members of the containing type, including any inherited protected members.

In the previous declaration, the full name of class `Nested` is `Container.Nested`. This is the name used to create a new instance of the nested class, as follows:

C#Copy

```csharp
Container.Nested nest = new Container.Nested();
```