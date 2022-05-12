Avanade Velocity 2022
- Declaring variables:  
 Let x=5;  
 const x=5;

 # Adding to HTML file
    <script src= "../myScript.js"> </script>


# Types
- Boolean
- Number
- String
- Undefined
- Null
- Symbol
- Object

-- To check type you can use typeof

# String Concatenation
     `5 + 3 = ${sumOfNumbers}`;

# String functions
- indexOf()
- charAt()
- toUpperCase()

# Number functions
- NaN (Not a Number)
- Infinity (greatest possible value - not numeric)
- Number.POSITIVE_INFINITY
- Number.NEGATIVE_INFINITY
- Number.MIN_VALUE (smallest possible number)
- Number.MAX_VALUE (largest possible number)

# Equals
- = means assigning something
- == means same value
- === means same value and same type

# Type Conversion
- eval (string)
- parseInt (string)
- parseFloat()

-- use isNan() to check if a number is a number or not

# The Ternary if
     let now = new Date();
     let greeting = "Good" + ((not.getHours()>17)? " evening" : " day");

     //if now>17 return evening, else day

     test ? expression1 : expression2

# The switch statement
     switch (expression){
          case label:
               statement;
               break;
          case label:
               statement;
               break
          default:
               statement;
               break;
     }
     
# Loops
- while
- do while
- for
- for of
- for in


# Error Handling
## There is an error object that has 2 properties: name and message
     let error = new Error("My error message");
## Common Errors:
     pi.toFixed(10000) // Range error ()

     function foo(){
          bar++        // reference error

     }

     if (foo){ //syntax error

     const foo = {}
     foo.bar();     // Type error



# Try, Catch, Finally
     try {
     let x = parseInt(prompt("Enter a number ", ""));
     if (isNaN(x)) {
     let e = new Error();
     e.message = "That wasn't a number";
     throw e;
     }
     }
     catch (e) {
     alert(`Something went wrong: ${e.message}`);
     }
     finally {
     ...
     }


# Throw Exceptions
- the **throw** keyword deliberately causes an error
### e.g.:
     if (devisor === 0){
          throw new RangeError("Attempted division by 0);
     }

# Creating Arrays
     let a = Array();
     let b = Array(10);
     let c = Array("Tom","Dick","Harry");
     let d = {1,2,3};
# Array object methods:
- **reverse()** reverses the order of the array
- **join([seperator])** joins all elements in the array with the given seperator
- **sort([compare (a,b)])** sorts the array. If you do not supply the **compare** it will sort based on dictionary order
- **push()** adds a new element to end of array
- **pop()** removes last element
- **unshift()** adds element to beginning of array
- **shift()** removes from beginning
- **Array.from()** creates array out of objects e.g:  
let formElements = document.querySelectorAll('input','select','textarea');
formElements = Array.from(formElements);
- **Array.prototype.find()** returns first elemtn for which callback returns true  
e.g.  
     ['chris','bruford',22,true].find(n => n === 'bruford'); // returns bruford

- **findIndex()** returns index of first matching element. So in the example above, it would return 1
- **fill()** overrides specified elements : ['chris','bruford',22].fill(null,1,2); //Chris,null,null

- **entries(), keys(), values()** each returns a sequence of values via an iterator
### for example:
     let arrayEntries = ['chris','bruford',22,true].entries();
     console.log(arrayEntries.next().value);        // [0,''Chris]

     let arrayKeys = ['chris','bruford',22,true].keys();
     console.log(arrayKeys.next().value);            // 0

     let arrayValues = ['chris','bruford',22,true].values();
     console.log(arrayValues.next().value);            // 'Chris'


# The for...of loop for arrays
     let myArray = [1,2,3,4];
     for (el of myArray){
          if (el === 3) break;
          console.log(el);
     }

     // prints 1, 2, 3
     // could also use entries(),values(),keys() to loop through


# Arrow Functions

     declare name = function with/without parameters => return value
     
     const noArgFnImpRet = () => `Hello World`;    // returns `Hello World` when called
     const noArgFnCodeBlk = () => {// Some implementation code with return if required };
     const sglArgFn = arg => { console.log(arg); }      // outputs value of arg
     const multiArgFn = (num1, num2) => ( num1 * num2 );    // outputs value when called

# Default values in functions
### - provides a value for a parameter if none is passed into the function during calling
     function doSomething(arg1, arg2, arg3=5){
          return (arg1+arg2+arg3);
     } 
     console.log(doSomething(5,5));   // returns 15


# Maps
### Key/Value pairs of any type

     let myMap = new Map ( [ [1,"banana"], [2, "grapefruit"], [3, "apple"]]);

## some methods:
     myMap.size()
     myMap.set(4, "strawberry");
     myMap.get(4);
     myMap.has(2);   // returns true
     myMap.delete(3) // deletes element 3
     myMap.clear() //clears all

# Iterating Maps
     for (let [key,value] of myMap) {        // or put myMap.entries() here
          console.log(`key: ${key} value: ${value})
     }


     for (let key of myMap.keys()){
          console.log(`key: ${key} );
     }

      for (let value of myMap.values()){
          console.log(`key: ${key} );
     }
     
# Sets
      let mySet = new Set()

- allows to store unique values of any type
- iterate in the same way we do for maps

## Some methods
     mySet.add("apples");
     mySet.size   // NOTE no brackets
     mySet.has("apples"); //true

# Objects
     let student = {name:"David", id= 1234};


     const student = new Object();
     student["name"]= "carrie";
     student.email="carrie@gmail.com";

# Objects - using for...in to loop
     for (let key in students){
          console.log(`${key}: ${student[key]});
     }

# Array of objects
     let class = {
          { name: "David", id: 1234},
          { name: "Carrie", id: 5678},
     };

# Dynamic property names
- storing property name in a variable
### example:
     
# Object.assign()
- can use this to merge objects 
### e.g.:
     let obj1 = {a:1};
     let obj2 = {b:2};
     let obj3 = {c:3};

     Object.assign(obj1,obj2,obj3);
     // result would be {a:1, b:2, c:3};

# Destructuring
     let first, second, third;
     {first, second, third } = {"i", "love", "javascript"};
     console.long(first);
     console.long(second);
     console.long(third);

# Selecting HTML elements from DOM
     let x = document.getElementbyid("id");

     let x = document.querySelector(#id);

     let x = document.getElementbyTagName('p');

     let x = document.querySelectorAll('div > a');

     let x = document.querySelectorAll('a#id.class');


# Child, container, attribute selectors
\* matches any element  
E matches all ements with tag E  
E F matches all elements with tag name E that descend from F
E>F matches all elements with tage name F that are direct children of E
E+F matches all elements of F immediately preceded by E
E~F matches all elements of F preceded by any sibling of E

### Example:
     ul.myList > li > a
     // this matches all links that are direct children of an li element, which in turn are direct childrn of ul elements that have the class myList


- document.querySelectorAll('a[href^="http"]'); // external hyperlink that starts with http
- document.querySelectorAll('a[href$=".doc"]'); // attribute that that ends with .doc
- document.querySelectorAll('a[href*="name"]'); // attribute that contains value "name"


# Selecting elements by position on the page
     a:first-of-type // first a element on page

     p:nth-child(odd)  //every odd paragraph  (can also do this with even)

     li:last-child //the last li child of each ul

     :only-child //returns elemtns that have no siblings

# Creating new content (adding to the DOM)
     let el = document.createElement('p');  // create <p> tag
     let text = document.createTextNode('stuff'); // create text node with the text for the p tag

     el.appendChild(text); // append the text to the p tag
     document.querySelector('#myId').appendChild(el); // append the element to the DOM tree

     CAN ALSO USE innerHTML and innerTEXT(textContent is reffered over innerText)

     let el = document.querySelector('#id');
     el.innerHTML = "<em>cool</em>";

# Reading CSS properties
      let bgColor = document.querySelector('p:nth-child(2)').style.backgroundColor;

      //computed (final) style:

      let elem = document.querySelector('p:nth-child(1)');
      let compStyle = getComputedStyle(elem).backgroundColor;

# Setting CSS properties

     //one style
     document.querySelector('p:nth-child(1)').stle.backgroundColor = '#dddddd';

     //multiple styles
     let div = document.querySelector('div');
     let styles = {
          backgroundColor: "pink",
          borderRadius: '5px',
     }
     Object.assign(div.style,styles);

# Adding or removing a class through JavaScript
     const element = document.getElementById(elementID);
     element.classList.add('special');
     element.classList.remove('another-class');