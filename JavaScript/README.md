<div align="center">
  <img height="60" src="https://img.icons8.com/color/344/javascript.png">
  <h2>JavaScript Questions</h2>
</div>

- # [Coding Questions](https://github.com/ThevergeOn/Front-end-Interview/blob/main/JavaScript/Coding%20Questions/README.md)

### 1. What is JavaScript?
  JavaScript is a client-side and server-side scripting language inserted into HTML pages and is understood by web browsers. JavaScript is also an Object-based Programming language.
  
--- 
  
### 2. What are JavaScript Data Types?
   ##### Primitive types
   - Number
   - String
   - Boolean
   - BigInt
   - Undefined
   - Null
   - Symbol
   ##### Non-primitive types
   - Object
     ```
       Note- It is important to remember that any data type that is not primitive data type, is of Object type in javascript.
     ```
     
--- 

### 3.  What are the possible ways to create objects in JavaScript ?

   There are many ways to create objects in javascript as below

   1. **Object constructor:**

      The simplest way to create an empty object is using the Object constructor. Currently this approach is not recommended.

      ```javascript
      var object = new Object();
      ```

   2. **Object's create method:**

      The create method of Object creates a new object by passing the prototype object as a parameter

      ```javascript
      var object = Object.create(null);
      ```

   3. **Object literal syntax:**

      The object literal syntax is equivalent to create method when it passes null as parameter

      ```javascript
      var object = {};
      ```

   4. **Function constructor:**

      Create any function and apply the new operator to create object instances,

      ```javascript
      function Person(name){
         this.name=name;
         this.age=21;
      }
      var object = new Person("Sudheer");
      ```

   5. **Function constructor with prototype:**

      This is similar to function constructor but it uses prototype for their properties and methods,

      ```javascript
      function Person(){}
      Person.prototype.name = "Sudheer";
      var object = new Person();
      ```

      This is equivalent to an instance created with an object create method with a function prototype and then call that function with an instance and parameters as arguments.

      ```javascript
      function func {};

      new func(x, y, z);
      ```

      **(OR)**

      ```javascript
      // Create a new instance using function prototype.
      var newInstance = Object.create(func.prototype)

      // Call the function
      var result = func.call(newInstance, x, y, z),

      // If the result is a non-null object then use it otherwise just use the new instance.
      console.log(result && typeof result === 'object' ? result : newInstance);
      ```

   6. **ES6 Class syntax:**

      ES6 introduces class feature to create the objects

      ```javascript
      class Person {
         constructor(name) {
            this.name = name;
         }
      }

      var object = new Person("Sudheer");
      ```

   7. **Singleton pattern:**

      A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance and this way one can ensure that they don't accidentally create multiple instances.

      ```javascript
      var object = new function(){
         this.name = "Sudheer";
      }
      ```

---

### 4. What is the difference between == and === operators ?

   JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,
   1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
   2. Two numbers are strictly equal when they are numerically equal. i.e, Having the same number value.
      There are two special cases in this,
      1. NaN is not equal to anything, including NaN.
      2. Positive and negative zeros are equal to one another.
   3. Two Boolean operands are strictly equal if both are true or both are false.
   4. Two objects are strictly equal if they refer to the same Object.
   5. Null and Undefined types are not equal with ===, but equal with ==. i.e,
       null===undefined --> false but null==undefined --> true

   Some of the example which covers the above cases,

   ```javascript
   0 == false   // true
   0 === false  // false
   1 == "1"     // true
   1 === "1"    // false
   null == undefined // true
   null === undefined // false
   '0' == false // true
   '0' === false // false
   []==[] or []===[] //false, refer different objects in memory
   {}=={} or {}==={} //false, refer different objects in memory
   ```
   
---

### 5.What is a first class function ?

   In Javascript, functions are first class objects. First-class functions means when functions in that language are treated like any other variable.

   For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable. For example, in the below example, handler functions assigned to a listener

   ```javascript
   const handler = () => console.log ('This is a click handler function');
   document.addEventListener ('click', handler);
   ```

   
---

### 6.What is a higher order function ?
  
   Higher-order function is a function that accepts another function as an argument or returns a function as a return value or both.

   ```javascript
   const firstOrderFunc = () => console.log ('Hello, I am a First order function');
   const higherOrder = ReturnFirstOrderFunc => ReturnFirstOrderFunc();
   higherOrder(firstOrderFunc);
   ```

   
---

### 7.What is the purpose of the let keyword ?

   The `let` statement declares a **block scope local variable**. Hence the variables defined with let keyword are limited in scope to the block, statement, or expression on which it is used. Whereas variables declared with the `var` keyword used to define a variable globally, or locally to an entire function regardless of block scope.
    
   Let's take an example to demonstrate the usage,
   
   ```javascript
   let counter = 30;
   if (counter === 30) {
     let counter = 31;
     console.log(counter); // 31
   }
   console.log(counter); // 30 (because the variable in if block won't exist here)
   ```

   
---

### 8.What is the difference between let and var ?

   You can list out the differences in a tabular format
   
   | var | let |
   |---- | ---------
   | It is been available from the beginning of JavaScript  | Introduced as part of ES6 |
   | It has function scope | It has block scope  |
   | Variables will be hoisted | Hoisted but not initialized |

   Let's take an example to see the difference,

   ```javascript
   function userDetails(username) {
      if(username) {
        console.log(salary); // undefined due to hoisting
        console.log(age); // ReferenceError: Cannot access 'age' before initialization
        let age = 30;
        var salary = 10000;
      }
      console.log(salary); //10000 (accessible to due function scope)
      console.log(age); //error: age is not defined(due to block scope)
   }
   userDetails('John');
   ```
   
---

### 9.What is the reason to choose the name let as a keyword ?

   `let` is a mathematical statement that was adopted by early programming languages like **Scheme** and **Basic**. It has been borrowed from dozens of other languages that use `let` already as a traditional keyword as close to `var` as possible.

   
---

### 10.How do you redeclare variables in switch block without an error ?

   If you try to redeclare variables in a `switch block` then it will cause errors because there is only one block. For example, the below code block throws a syntax error as below,
   
   ```javascript
   let counter = 1;
   switch(x) {
     case 0:
       let name;
       break;

     case 1:
       let name; // SyntaxError for redeclaration.
       break;
   }
   ```

   To avoid this error, you can create a nested block inside a case clause and create a new block scoped lexical environment.

   ```javascript
   let counter = 1;
       switch(x) {
        case 0: {
           let name;
           break;
         }
         case 1: {
           let name; // No SyntaxError for redeclaration.
           break;
         }
       }
   ```
   
---

 ### 11.What is IIFE(Immediately Invoked Function Expression) ?

   IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined. The signature of it would be as below,

   ```javascript
   (function ()
       {
         // logic here
       }
    )
   ();
   ```

   The primary reason to use an IIFE is to obtain data privacy because any variables declared within the IIFE cannot be accessed by the outside world. i.e, If you try to access variables with IIFE then it throws an error as below,
   
   ```javascript
   (function ()
           {
             var message = "IIFE";
             console.log(message);
           }
    )
   ();
   console.log(message); //Error: message is not defined
   ```
   
---
 
 ### 12.What is Hoisting ?

   Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. Remember that JavaScript only hoists declarations, not initialisation.
   Let's take a simple example of variable hoisting,

   ```javascript
   console.log(message); //output : undefined
   var message = 'The variable Has been hoisted';
   ```

   The above code looks like as below to the interpreter,

   ```javascript
   var message;
   console.log(message);
   message = 'The variable Has been hoisted';
   ```
   
---

### 13.What are closures ?

   A closure is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function’s variables. The closure has three scope chains
    
   1. Own scope where variables defined between its curly brackets
   2. Outer function’s variables
   3. Global variables
    
   Let's take an example of closure concept,

   ```javascript
   function Welcome(name){
     var greetingInfo = function(message){
      console.log(message+' '+name);
     }
   return greetingInfo;
   }
   var myFunction = Welcome('John');
   myFunction('Welcome '); //Output: Welcome John
   myFunction('Hello Mr.'); //output: Hello Mr.John
   ```

   As per the above code, the inner function(i.e, greetingInfo) has access to the variables in the outer function scope(i.e, Welcome) even after the outer function has returned.
   
---

### 14.What are closures?

   A closure is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function’s variables. The closure has three scope chains
    
   1. Own scope where variables defined between its curly brackets
   2. Outer function’s variables
   3. Global variables
    
   Let's take an example of closure concept,
   
   ```javascript
   function Welcome(name){
     var greetingInfo = function(message){
      console.log(message+' '+name);
     }
   return greetingInfo;
   }
   var myFunction = Welcome('John');
   myFunction('Welcome '); //Output: Welcome John
   myFunction('Hello Mr.'); //output: Hello Mr.John
   ```
   
   As per the above code, the inner function(i.e, greetingInfo) has access to the variables in the outer function scope(i.e, Welcome) even after the outer function has returned.
---

### 15.What are modules

   Modules refer to small units of independent, reusable code and also act as the foundation of many JavaScript design patterns.  Most of the JavaScript modules export an object literal, a function, or a constructor
