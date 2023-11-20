# Week 1 Notes
## C# Basics
- What are some programming paradigms of C#?
    - Imperative, Object Oriented
- What do objects have?
    - Attributes
    - Behaviours
- Is C# compiled or interpreted?
    - Compiled
        - It gets compiled ino the .NET Intermediate language
            - Which gets compiled by the CLR (Common Language Runtime)
- What is the CLR?
    - Transforms source code into a form of bytecode called the CIL ( Common Intermediate Language).
        - At run time, the just-in-time compilation converts CIL code into native code for the platform.
- What is the system namespace?
    - Controls and organizes scope of classes
    - Package structure in java
    - global namspace is root
- How do you write to the console with C#?
    - System.Console.Write()
    - System.Console.WriteLine()
- How do you compile a cs file?
    - csc FileName.cs
- How do you run a C# application?
    - public static void Main(string[] args){}
- What does foreach loop do?
    - Acts like a for each loop in Java
    - foreach(string arg in args){}
- Do you need string[] args?
    - No. They can be removed.
## Starting a C# App
- Select Console App using .NET Core
- Name the file
- Create the solution name
- Choose the framework
    - Do not use top level framework (When a project is created, it will give a program file, which is where you have your main method. But you write your statements inside the Program file which will be executed at runtime, if do not use top level framework is selected)
- There is a global cs file where the namespace is brought into the file automatically
- Build it
- Run it
- Look at the console
- Close the console

## Debugging
- Select the run button, but there is an option to run without debugging
- Adding command line arguments
    - Right click on the project in the solution explorer
    - Click properties
    - Go down to debug
    - Click on Open UI
    - Enter the command line arguments
## Value Types
- Object types
    - Reference to the object
- Value types
    - The actual value is assigned
    - All primitives are value types
    - Is an abstract class
- What are structs?
    - A structure type (or struct type) is a value type that can encapsulate data and related functionality. Structures are used to represent a record. A record is a single variable that holds related data of various data types.
    - Structs can implement interfaces
    - Structs cannot be abstract, virtual or protected
    - They can't inherit from other structs or classes
    - Value types, not reference types
    - Can be instantiated without using new, but it won't be usable until all fields are initialized
    - Cannot have a default constructor
    - What can structs have?
        - methods
        - fields
        - indexers
        - properties
        - operator methods
        - events
    - Similar to classes, but they are not reference types
    - Value is directly assigned to the struct
    - Parent to all value types
- What are enums?
    - Constant values that hold names that do not change.
        - Ex: Days of the week
    - https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/enum
- BigIntegers are large integers that are immutable
## Nullable Types
- Can use ? on any type to tell the compiler that the value can be null
- When should you use a nullable value type?
    - When you need to represent the undefined value of an underlying value type.
## Partial Classes and Methods
- Gives the ability to split the implementation of a class, a struct, a method or multiple .cs files when the program is compiled.
- All partial class definitions must be in the same assembly and namespace
- A ll the parts must have the same accessibility.
- Different parts can have different base types, so the final class will inherit all the base types
- The partial modifier can only appear immediately before the keywords class, struct or interface
- Partial class or struct can contain partial methods.
    - One cs file must contain a signature of the mthod and another file can contain optional implementation of the partial method.
    - Both declaration and implementation of a mthod must have the partial keyword.
## Strings
- Strings are immutable
- In C#, string is an alias for the System.String class
- C# allows you to use String.Empty for an empty string (USELESS????)
- Can you use the double equals to compare strings?
    - Yes. You can use (==) to compare strings.
    - Can also use .Equals()
- How can you compare two strings references instead of value?
    - Using object.ReferenceEquals()
- Using the brace operator to call variables directly into a string literal
    - This pulls the name and todaysDate from a string value into the string location specified.
    - Using the console:
        - Ex: Console.WriteLine("Welcome {0}. {1}", name, todaysDate);
    - A way to use this without WriteLine is to use String.Format
        - Ex: String.Format("Welcome {0}. {1}", name, todaysDate);
    - With dates:
        - Ex: DateTime.Now.ToString("dddd, dd MMM yyyy hh:mm tt");
- Verbatims
    - Using the @ verbatim
        - It will turn off escape characters
        - You can use literal characters
            - Ex: Filepaths
            - Ex: SQL Queries
            ![Image of SQL Queries](images/image.png)
- Interpolation
    - Brace operator is a type of interpolation
    - Better way is to use the $ in C#
        - Ex: $"Welcome {name}. {todaysDate}";
    - Can also use ternary operators within the brackets
        - Ex: $"Welcome {name}, {age == 1 ? "" : "s"}. {todaysDate}"
- StringBuilder
    - StringBuilder is mutable
## Delegates
- Similar to lambda expressions
    - Uses Func<T1, T2>
## Operator Overloading
- Operator overloading, sometimes termed operator ad hoc/static polymorphism, is a specific case of polymorphism where different operators have different implementations depending on their arguments.
    - Operator overloading is generally defined by a programming language, a programmer or both.
- Interpretation
    - Giving an operator the ability to handle more parameters (data types)
    - Ex: The plus sign is already overloaded, in that it allows you to add integers and string, you can extend this for a custom object to specify how two or more objects should be added together.
## Control Structures
- Switch cases
    - A switch case does not need to have any information inside of some cases that will be empty.
        - Ex:
        ```csharp
        switch(guess){
            case 1: //Does not fail
            case 2: //Does not fail
            case 3: //Does not fail
                Console.WriteLine(3);
                break; //Still need breaks
            default:
                Console.WriteLine("Empty");
                break;
        }
        ```
    - Range-based switching is now possible as of C# 7
        - Ex:
        ```csharp
        switch(guess){
            case int x when (x >= 90):
                return "Distinction"; 
            case int x when (x >= 80):
                return "Distinction"; 
            case int x when (x >= 90):
                return "Pass";
            default:
                return "Fail";
        }
        ```
        - The "when" clause is used to specify an additional condition that must be set for the case statement to evaluate to true.
            - It can be any expression that returns a boolean value.
    - Lambda expressions on switches are now possible as of C# 8
        - Ex:
        ```csharp
        public static string SwitchExpressionGrading(int score) =>
        (score) switch {
            int x when (x >= 90) => "Distinction",
            int x when (x >= 80) => "Merit",
            int x when (x >= 90) => "Pass",
            _ => "Fail"
        };
        ```
        - It helps with concise syntax
        - Another example of wrong vs right
            - Ex (Wrong):
            ```csharp
                public int GetPoints(string color)
                {
                    return (color) switch
                    {
                        string x when (color == "Green") => 5,
                        string x when (color == "Red") => 10,
                        string x when (color == "Yellow") => 15,
                        _ => 0
                    };
                }
            ```
            - Ex (Right):
            ```csharp
                public int GetPoints(string color)
                {
                    return color switch
                    {
                        "Green" => 5,
                        "Red" => 10,
                        "Yellow" => 15,
                        _ => 0
                    };
                }
            ```
- Arrays
    - Creating an array
        - Ex: string [] fruit = new string[] {"item1", "item2"};
- Loops
    - Foreach loop
        - Ex: foreach(String s in stringsList){}
## Access Modifiers
- private
    - Only accessible from the class
- private protected
    - Only accessible from the class and sub classes in the same assembly
- internal
    - Only accessible from the same assembly
- protected
    - Only within the class and the sub classes of the class
- protected internal
    - Within the class, it's sub classes and within a derived class in another assembly
- public
    - Accessible anywhere in the application
- When no access modifier is present, it stays private.
## Properties
- Instead of using getters and setters, C# uses properties
    - Ex: 
    - ![Alt text](images/image-1.png)
- Can be directly assigned instead of called when using getters and setters
    - Ex:
    - ![Alt text](images/image-2.png)
- Can create additional properties that work off of previously created variables
    - Ex:
    - ![Alt text](images/image-3.png)
- Can use lambda operators for more cleaner and concise code:
    - Ex:
    - ![Alt text](images/image-4.png)
- What is a benefit of using this?
    - More cleaner and concise code
    - A use of encapsulation
    - Can directly assign a value to a variable when writing the code.
    - Ex:
    - ```csharp
        public class Example : ViewModelBase
        {
            private string _name = "";
            public string Name
            {
                get => _name;
                set => SetProperty(ref _name, value);
            }
        }
        ```
- What is const?
    - A const is a constant, it needs to be set on creation.
- What is readonly?
    - readonly can only be set once, but then cannot be set again. It can only be set inside of a constructor or init-only setter. It becomes a constant after getting set.
    - What is init?
        - Acts as a set, but only allows usage within the constructor.
        - Ex:
        - ![Alt text](images/image-5.png)
            - Now we don't need the private readonly int _id;
            - Ex:
            - ![Alt text](images/image-6.png)
            - This is called auto-implemented property
        - It can still be set from the calling code (initialization of the object)
            - And we can remove that by adding an access modifier to the get or set or init, so we can prohibit accessibility
            - Ex:
            - ![Alt text](images/image-7.png)
## Constructors
- Static constructors
    - A static constructor is used to initialize any static data.
    - Used to perform an action that needs to be performed once only
    - It's automatically called before the first instance is created or any static members are referenced
    - ![Alt text](images/image-15.png)
- base()
    - Vertical constructor chaining
    - Equivelant to super() in Java
    - A constructor can use this keyword to call the constructor of a base/super class
    - In a derived calss, if a base-class constructor is not called explicitly by using the base keyword, the default constructor is called implicitly if there is one.
    - If a base class doens't offer a default constructor, the derived class must make an explicit call to a base constructor by using base()
    - Ex:
    - ![Alt text](images/image-8.png)
    - ![Alt text](images/image-9.png)
- this()
    - Horizontal constructor chaining
    - Can use to invoke another constructor within the same class.
    - Refers to the current instance of the lass
    - Used to differentiate between method parameters and class fields when they have the same name.
    - Ex:
    - ![Alt text](images/image-10.png)
## Classes and Objects
- Abstract 
    - classes
        - Must contain at least one abstract method
    - Can be used with:
        - methods
        - classes
        - properties
        - indexers
        - events
    - Ex:
    - ![Alt text](images/image-11.png)
- Inheriting methods
    - Add virtual to the parent class
    - Add override to the child class of the method with the same signature.
- Can use keyword 'is' to see what type a class is
    - Similar to instanceof in Java
    - Usually used to check for downcasting
    - Ex: employee is Trainee
- Can use keyword 'as' to see what type a class is, similar to 'is'
    - Ex: Trainee traineeEmpl = employee as Trainee;
    - ![Alt text](images/image-12.png)
    - Use ? to get rid of error
## Interfaces
- Interfaces start with capital I
- Cannot contain a constructor
- What can you declare in an interface?
- All methods are implicitly public and abstract
- All fields are implicitly public static
- Structs can implement an interface
- Interfaces can have static methods, but must have implementation
- An interface may define a default implementation for members.
    - ![Alt text](images/image-13.png)
- Can inherit from other interfaces
    - Abstract classes can inherit interfaces, but do not need to implement the methods and fields.
        - The first concrete class that inherits from that abstract class WILL need to inherit from the interfaces in the abstract class.
            - ![Alt text](images/image-14.png)
- Explicit interface implementation
    - ![Alt text](images/image-16.png)
## Casting
- Ex: ((IbasketItem)item).Name
## Keywords
- sealed
    - Makes a class unable to be inheritied from
        - Similar to final from Java