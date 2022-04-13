Avanade Velocity 2022
-  
# C#
- Everything in c# is an object
- C# is case sensitive
- Class is a template from which objects are created
- variables are Private by default (only visible to that class)
- Class contains Object (think about what the object has- variables, and what is does- methods)
- A variable is a placeholder space in memory
- Local variables are created in a method. Instance variables are outside the method.
- Static Variable-> only one copy lives through the entire lifecycle (can only have one occurance at a time)

## Public vs Private
- All fields should be private
- User **properties** as tehese has get and set
## Namespace
- To access the class of a namespace, we need to use namespacename.classname
## Console output/input
    Console.write("hello"); // this does not go onto new line
    Console.writeLine("Hello World");
    Console.readLine();
    string name=Console.readLine(); 

## Data Types
- string
- char (one character)
- int
- float, double, decimal
- bool

## Strings
    string phrase="hello"; 
    phrase.toUpper;
    phrase.toLower;
    phrase.Lenght;
    phrase.Contains("h");
    phrase[0];

## Formatting Strings
        //either:
    String.Format ("some text with a {0} inside it",variable);
        //or
    $some text with {variable} inside it;

## Numbers
- Decimal requires an **M** after it (e.g. decimal gpq= 3.21M);

## Casting vs Parsing
- check Microsoft documentation to see what can be cast/converted or parsed  
Parse:  
     string word = "200";  
    num = int.Parse(word);
    ___
    Cast:  
    long height = 200;  
    int width = (int)height;

## Constants
    const int NUMWHEELS=4;
This means that the number of wheels are always 4. Cannot be changed  
Always write in capitals  
We have to set the value immediately

## Readonly variable
- readonly int AVALUE;
- For readonly, we can set the value now **or in a contructor** (more flexible than a constant)
- For a read only property, just don't add in the set {}

## Superclass/Subclass
    public class Car: Object
This is the syntax for superclass/sub classs. The Car is sub class and Object is superclass

## Fields
- Fields belong to a class, while variables belong in methods
- The field exists as long as instance exists
- Always use private fields
- Clients can access the data then through get functions or through properties

## Properties
- provides access to data of an object
- has getters and setters
- You can use provate field within the object to store the information if needed

### Full Property
    public class Car{
        private int speed
        public int Speed{
            get{return speed;}
            private set{speed =value}
        }
    }
- Note that the **set** is private so nobody outside of this class can set the speed. They can only get it.
- Shortcut for this in VSCode is propf

### Auto- Property
    public class Car {
        publin int speed {get; private set; }=42
    }
- the 42 here is an initialiser and it is optional. It is the default value if another value is not provided
- These can store data so you do not need to have a additional field for storage

## SWITCH example
    switch (Year)
    {
    case 2013 :
        Console.WriteLine("It's 2013!");
    break;
    case 2012 :
        Console.WriteLine("It's 2012!");
    break;
    default :
        Console.WriteLine("It's " + Year + "!");
    break;
    }

## Break, Continue, Goto in LOOPS
- **break** means STOP and get out of the loop
- **continue** means stop doing the rest of the code n the loop, and just go to the next iteration
- **goto** - do not use this!! Just lose a loop instead


## Incrementation
- In post incrementation (e.g. a++), the increment is done **after** the next line has been completed.
- In pre incrementation (e.g. ++a) the increment is done before the next line.

 ## Ternary Expression
 - This is the short form of the if else statements  
 Syntax:  
 **condition ? statement 1 : statement 2;**

 ### Example Ternary Expression
    string salutation;

    if (gender==Gender.Male){
        salutation = "Mr";
    } else {
        salutation = "Mrs"
    }
    ____________________________________
    is the same as:
    ____________________________________
    string salutation = (gender==Gender.Male) ? "Mr" : "Mrs";

## Short Circuit Evaluation
- && and || support short-circuit evaluation
- For &&, if the expression on the left is **false**, the evaluation is cut short and the expression on the right is not evaluated
- For ||, if the expression on the left is **true**, the evaluation is cut short

## Arrays
- Array is a collection of similar items
- In C#, they have a fixed menght, which is defined at the time of creation
#### Format:
    int [] arr1 = new int[4] // created
    int [] arr1 = {2,3,4,6,8,9} // initialised
    int [] arr2 = new int [] {1,2,3,4,5}; // created and initialised
    int x = arr2[2] // in this case, x=3
________________________________________________________________________
    Person[] people = {new Person(), new Person(), new Person()};

    foreach ( Person p in people){
        Console.WriteLine (p.Name);
    }



## Object initialisers
    Class Person{
        public string FirstName {get; set;}
        public string LastName {get; set;}

        Person p = new Person { Firstname = "Niamh" LastName = "Foran"}
    }
- We can initialise the object p without calling a constructor explicitily.

## Constructors
- A default () constructor is provided by the compiler in C#. But if we are creating overloaded constructors we need to add in the default one ourselves.
- Constructor has same name as class and has no return type
- Use ctor for a shortcut in VS code


### Example of constructor where all fields are mandoatory
     Class Employee{
         private readonly string firstname;
         private readonly string lastname;
         private readonly int employeeid;

         public Employee (string firstname, string lastname, int employeeid)
         {
             this.firstname=firstname;
             this.lastname=lastname;
             this.employeeid=employeeid;
         }
     }

     Employee donald = new Employee ("Donald", "Trump", 1)
     ______________________________
        To add an optional field:
     ______________________________
    Employee donald = new Employee ("Donald", "Trump", 1) {Address = "White House"};


## Constructor Chaining
    public Class Car {
    public Car () : this (0) {}

    public Car (int initialSpeed): this(initialSpeed, "BMW") {}

    public Car (int initialSpeed, string make){
        speed = initialSpeed;
        this.make= make;
    }

    }

 - Here, the first constructor calls a constructor that has an int, and the second constructor calls the constructor with a string and an int
 - This saves us writing the same thing over and over



