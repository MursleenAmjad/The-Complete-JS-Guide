# The Complete JS Guide

This repo contains complete information about JavaScript language up to ES 2022.

 - - - -
## Chapter 1. History and evolution of JavaScript

### How JavaScript was Created
JavaScript was created in May 1995 in 10 days, by Brendan Eich. Eich worked at Netscape and implemented JavaScript for their web browser, Netscape Navigator.

The idea was that major interactive parts of the client-side web were to be implemented in Java. JavaScript was supposed to be a glue language for those parts and to also make HTML slightly more interactive. Given its role of assisting Java, JavaScript had to look like Java. That ruled out existing solutions such as Perl, Python, TCL, and others.

Initially, JavaScript’s name changed several times:

Its code name was Mocha.
In the Netscape Navigator 2.0 betas (September 1995), it was called LiveScript.
In Netscape Navigator 2.0 beta 3 (December 1995), it got its final name, JavaScript.

### Standardizing JavaScript
There are two standards for JavaScript:

1. ECMA-262 is hosted by Ecma International. It is the primary standard. 
2. ISO/IEC 16262 is hosted by the International Organization for Standardization (ISO) and the International Electrotechnical Commission (IEC). This is a secondary standard.

The language described by these standards is called ECMAScript, not JavaScript. A different name was chosen because Sun (now Oracle) had a trademark for the latter name. The “ECMA” in “ECMAScript” comes from the organization that hosts the primary standard.

The original name of that organization was ECMA, an acronym for European Computer Manufacturers Association.

In principle, JavaScript and ECMAScript mean the same thing. Sometimes the following distinction is made:
* The term JavaScript refers to the language and its implementations.
* The term ECMAScript refers to the language standard and language versions.


### Timeline of ECMAScript versions 
This is a brief timeline of ECMAScript versions:

* ECMAScript 1 (June 1997): First version of the standard.
* ECMAScript 2 (June 1998): Small update to keep ECMA-262 in sync with the ISO standard.
* ECMAScript 3 (December 1999): Adds many core features – “[…] regular expressions, better string handling, new control statements [do-while, switch], try/catch exception handling, […]”
* ECMAScript 4 (abandoned in July 2008): Would have been a massive upgrade (with static typing, modules, namespaces, and more), but ended up being too ambitious and dividing the language’s stewards.
* ECMAScript 5 (December 2009): Brought minor improvements – a few standard library features and strict mode.
* ECMAScript 5.1 (June 2011): Another small update to keep Ecma and ISO standards in sync.
* ECMAScript 6 (June 2015): A large update that fulfilled many of the promises of ECMAScript 4. This version is the first one whose official name – ECMAScript 2015 – is based on the year of publication.
* ECMAScript 2016 (June 2016): First yearly release. The shorter release life cycle resulted in fewer new features compared to the large ES6.
* ECMAScript 2017 (June 2017). Second yearly release.
Subsequent ECMAScript versions (ES2018, etc.) are always ratified in June.

- - - -
## Chapter 2. Basic Syntax

### Basic Constructs
#### 1. Comments
    // single-line comment

    /*
    Comment with
    multiple lines
    */

#### 2. Primitive (atomic) values 
##### Booleans:
    true
    false

##### Numbers:
    1.141
    -123
The basic number type is used for both floating point numbers (doubles) and integers.

##### Bigints:
    17n
    -49n
The basic number type can only properly represent integers within a range of 53 bits plus sign. Bigints can grow arbitrarily large in size.

##### Strings:
    'abc'
    "abc"
    `String with interpolated values: ${256} and ${true}`
JavaScript has no extra type for characters. It uses strings to represent them.

#### 3. Assertions
An assertion describes what the result of a computation is expected to look like and throws an exception if those expectations aren’t correct. For example, the following assertion states that the result of the computation 7 plus 1 must be 8:
    assert.equal(7 + 1, 8);

#### 4. Logging to the console
    // Printing a value to standard out (another method call)
    console.log('Hello!');

    // Printing error information to standard error
    console.error('Something went wrong!');

#### 5. Operator
    // Operators for booleans
    assert.equal(true && false, false); // And
    assert.equal(true || false, true); // Or
    assert.equal(!false,true); // not

    // Operators for numbers
    assert.equal(3 + 4, 7);
    assert.equal(5 - 1, 4);
    assert.equal(3 * 4, 12);
    assert.equal(10 / 4, 2.5);
    assert.equal(3 % 3, 0);

    // Operators for bigints
    assert.equal(3n + 4n, 7n);
    assert.equal(5n - 1n, 4n);
    assert.equal(3n * 4n, 12n);
    assert.equal(10n / 4n, 2n);

    // Operators for strings
    assert.equal('a' + 'b', 'ab');
    assert.equal('I see ' + 3 + ' monkeys', 'I see 3 monkeys');

    // Comparison operators
    assert.equal(3 < 4, true);
    assert.equal(3 <= 4, true);
    assert.equal('abc' === 'abc', true);
    assert.equal('abc' !== 'def', true);
JavaScript also has a == comparison operator.

#### 6. Declaring variables
const creates immutable variable bindings: Each variable must be initialized immediately and we can’t assign a different value later. However, the value itself may be mutable and we may be able to change its contents. In other words: const does not make values immutable.
    // Declaring and initializing x (immutable binding):
    const x = 8;

    // Would cause a TypeError:
    // x = 9;
    let creates mutable variable bindings:

    // Declaring y (mutable binding):
    let y;

    // We can assign a different value to y:
    y = 3 * 5;

    // Declaring and initializing z:
    let z = 3 * 5;

#### 7. Ordinary function declarations
    Ordinary function declarations 
    // add1() has the parameters a and b
    function add1(a, b) {
      return a + b;
    }
    // Calling function add1()
    assert.equal(add1(5, 2), 7);


#### 8. Arrow function expressions
Arrow function expressions are used especially as arguments of function calls and method calls:

    // An arrow function whose body is a code block
    const add2 = (a, b) => { return a + b };
    // Calling function add2()
    assert.equal(add2(5, 2), 7);

    // Equivalent to add2:
    // An arrow function whose body is an expression
    const add3 = (a, b) => a + b;

#### 9. Plain Objects
    // Creating a plain object via an object literal
    const obj = {
      first: 'Jane', // property
      last: 'Doe', // property
      getFullName() { // property (method)
        return this.first + ' ' + this.last;
      },
    };

    // Getting a property value
    assert.equal(obj.first, 'Jane');
    // Setting a property value
    obj.first = 'Janey';

    // Calling the method
    assert.equal(obj.getFullName(), 'Janey Doe');

#### 10. Arrays
    // Creating an Array via an Array literal
    const arr = ['a', 'b', 'c'];
    assert.equal(arr.length, 3);

    // Getting an Array element
    assert.equal(arr[1], 'b');
    // Setting an Array element
    arr[1] = 'β';

    // Adding an element to an Array:
    arr.push('d');

    assert.deepEqual(arr, ['a', 'β', 'c', 'd']);

#### 11. Control Flow Statements
Conditional statement:
    
    if (x < 0) {
      x = -x;
    }

for-of loop:
    
    const arr = ['a', 'b'];
    for (const element of arr) {
      console.log(element);
    }
    // Output:
    // 'a'
    // 'b'

### Modules
Each module is a single file. Consider, for example, the following two files with modules in them:

    file-tools.mjs
    main.mjs

The module in file-tools.mjs exports its function isTextFilePath():

    export function isTextFilePath(filePath) {
      return filePath.endsWith('.txt');
    }

The module in main.mjs imports the whole module path and the function isTextFilePath():

    // Import whole module as namespace object `path`
    import * as path from 'path';
    // Import a single export of module file-tools.mjs
    import {isTextFilePath} from './file-tools.mjs';

### Classes

    class Person {
        constructor(name) {
            this.name = name;
        }
        describe() {
            return `Person named ${this.name}`;
        }
        static logNames(persons) {
            for (const person of persons) {
            console.log(person.name);
            }
        }
    }

    class Employee extends Person {
        constructor(name, title) {
            super(name);
            this.title = title;
        }
        describe() {
            return super.describe() +
            ` (${this.title})`;
        }
    }

    const jane = new Employee('Jane', 'CTO');
    assert.equal(jane.describe(),'Person named Jane (CTO)');

### Exception Handling

    function throwsException() {
      throw new Error('Problem!');
    }

    function catchesException() {
      try {
        throwsException();
      } catch (err) {
        assert.ok(err instanceof Error);
        assert.equal(err.message, 'Problem!');
      }
    }

Note: try-finally and try-catch-finally are also supported.

### Naming Convention

#### 1. Identifier
The grammatical category of variable names and property names is called identifier.

Identifiers are allowed to have the following characters:

* Unicode letters: A–Z, a–z (etc.)
* $, _
* Unicode digits: 0–9 (etc.)
    * Variable names can’t start with a digit

Some words have special meaning in JavaScript and are called reserved. Examples include: if, true, const.

Reserved words can’t be used as variable names:

    const if = 123;
      // SyntaxError: Unexpected token if

But they are allowed as names of properties:

    const obj = { if: 123 };
    // obj.if
    // 123

#### 2. Casing Style
Common casing styles for concatenating words are:

* Camel case: threeConcatenatedWords
* Underscore case (also called snake case): three_concatenated_words
* Dash case (also called kebab case): three-concatenated-words

#### 3. Capitalization of names 
In general, JavaScript uses camel case, except for constants.
Lowercase:
* Functions, variables: myFunction
* Methods: obj.myMethod
* CSS:
    * CSS entity: special-class
    * Corresponding JavaScript variable: specialClass

Uppercase:
* Classes: MyClass
* Constants: MY_CONSTANT
    * Constants are also often written in camel case: myConstant

#### 4. More naming conventions
The following naming conventions are popular in JavaScript.

If the name of a parameter starts with an underscore (or is an underscore) it means that this parameter is not used – for example:

    arr.map((_x, i) => i)

If the name of a property of an object starts with an underscore then that property is considered private:

    class ValueWrapper {
        constructor(value) {
            this._value = value;
        }
    }

### Statement vs. expression

#### 1. Statements 

A statement is a piece of code that can be executed and performs some kind of action. For example, if is a statement:

    let myStr;
    if (myBool) {
        myStr = 'Yes';
    } else {
        myStr = 'No';
    }

One more example of a statement: a function declaration.

    function twice(x) {
        return x + x;
    }

#### 2. Expressions 

An expression is a piece of code that can be evaluated to produce a value. For example, the code between the parentheses is an expression:

    let myStr = (myBool ? 'Yes' : 'No');   


 - - - -
## Chapter 3. Consoles: interactive JavaScript command lines

* 1. console.log()
* 2. console.error()

### 1. console.log() (stdout)
There are two variants.

    a. console.log(...values: any[]): void
    b. console.log(pattern: string, ...values: any[]): void

#### a. Printing multiple values

    console.log('abc', 123, true);
    // Output:
    // abc 123 true

At the end, console.log() always prints a newline. Therefore, if you call it with zero arguments, it just prints a newline.

#### b. Printing a string with substitutions

    console.log('Test: %s %j', 123, 'abc');
    // Output:
    // Test: 123 "abc"

These are some of the directives you can use for substitutions:

%s converts the corresponding value to a string and inserts it.

    console.log('%s %s', 'abc', 123);
    // Output:
    // abc 123

%o inserts a string representation of an object.

    console.log('%o', {foo: 123, bar: 'abc'});
    // Output:
    // { foo: 123, bar: 'abc' }

%j converts a value to a JSON string and inserts it.

    console.log('%j', {foo: 123, bar: 'abc'});
    // Output:
    // {"foo":123,"bar":"abc"}

%% inserts a single %.

    console.log('%s%%', 99);
    // Output:
    // 99%

### 2. console.error() (stderr)

console.error() works the same as console.log(), but what it logs is considered error information.

### 3. Printing nested objects via JSON.stringify()

JSON.stringify() is occasionally useful for printing nested objects:
    console.log(JSON.stringify({first: 'Jane', last: 'Doe'}, null, 2));

Output:

{
  "first": "Jane",
  "last": "Doe"
}

 - - - -
## Chapter 4. Assertion

In software development, assertions state facts about values or pieces of code that must be true. If they aren’t, an exception is thrown. Node.js supports assertions via its built-in module assert – for example:

    import * as assert from 'assert/strict';
    assert.equal(3 + 5, 8);

actual must be deeply equal to expected. If not, an AssertionError is thrown.

    assert.deepEqual([1,2,3], [1,2,3]);
    assert.deepEqual([], []);

Alternatively,

    assert.notEqual([], []);
    assert.notDeepEqual([1,2,3], [1,2]);

 - - - -
## Chapter 5. VARIABLES AND VALUES