Avanade Velocity 2022
-  
# C#
- Everything in c# is an object
- C# is case sensitive
- Class is a template from which objects are created
- variables are Private by default (only visible to that class)
- Class contains Object (think about what the object has- variables, and what is does- methods)
- A variable is a placeholder space in memory

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

## Numbers
- Decimal requires an **M** after it (e.g. decimal gpq= 3.21M);
## Constants
    const int numwheels=4;
This means that the number of wheels are always 4. Cannot be changed

## Superclass/Subclass
    public class Car: Object
This is the syntax for superclass/sub classs. The Car is sub class and Object is superclass

## Property vs Field

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


## Parsing
    string word = "200";
    num = int.Parse(word);
    ___
    long height = 200;
    int width = (int)height;



