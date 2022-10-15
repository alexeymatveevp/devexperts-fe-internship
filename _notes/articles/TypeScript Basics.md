
# What is TypeScript?
By definition, “TypeScript is JavaScript for application-scale development.”

TypeScript is a strongly typed, object oriented, compiled language. It was designed by Anders Hejlsberg (designer of C#) at Microsoft. TypeScript is both a language and a set of tools. TypeScript is a typed superset of JavaScript compiled to JavaScript. In other words, TypeScript is JavaScript plus some additional features.

TypeScript checks a program for errors before execution, and does so based on the kinds of values, it’s a static type checker. It doesn’t consider any JavaScript code to be an error because of its syntax. This means you can take any working JavaScript code and put it in a TypeScript file without worrying about exactly how it is written.
&nbsp;

# Where is the need for TypeScript?
**Compilation:** JavaScript is an interpreted language. Hence, it needs to be run to test that it is valid. It means you write all the codes just to find no output, in case there is an error. Hence, you have to spend hours trying to find bugs in the code. The TypeScript transpiler provides the error-checking feature. TypeScript will compile the code and generate compilation errors, if it finds some sort of syntax errors. This helps to highlight errors before the script is run.

**Strong Static Typing:** JavaScript is a programming language with loose typing. It does not have strict constraints on the data type of its variables. When determining if the incorrect operation is being called on a variable, independent of its type, the compiler or interpreter may overlook some mistakes.

TypeScript comes with an optional static typing and type inference system through the TLS (TypeScript Language Service). The type of a variable, declared with no type, may be inferred by the TLS based on its value. The system verifies the object type prior to performing an operation on a variable that requires a specific type, which results in either a compilation error or a runtime error.

TypeScript supports type definitions for existing JavaScript libraries. TypeScript Definition file (with .d.ts extension) provides definition for external JavaScript libraries. Hence, TypeScript code can contain these libraries.

TypeScript supports Object Oriented Programming concepts like classes, interfaces, inheritance, etc.
<br />
<br />

# Do browsers understand Typescript?
Browsers don’t understand TypeScript, the code should be _compiled_ to JavaScript. The TypeScript _npm_ package adds TypeScript support, when it is installed into the project, the corresponding version of the TypeScript language service gets loaded in the editor. It is also possible to run the methods of the package from _CLI_.
&nbsp;

# Types in JavaScript
The set of types in the JavaScript language consists of primitive values and objects. Primitive values are;
  * **Boolean**; represents a logical entity and can have two values: true and false,
  * **Null**; has exactly one value: null,
  * **Undefined**; is the value of variable which has not been assigned a value,
  * **Number**; is a [double-precision 64-bit binary format IEEE 754 value](https://en.wikipedia.org/wiki/Double_precision_floating-point_format).  It can safely store integers in the range (253 - 1) to -(253 - 1),
  * **BigInt**; is a numeric primitive that can represent integers with arbitrary precision. With BigInts, you can safely store and operate on large integers even beyond the safe integer limit for Numbers.
  * **String**; is used to represent textual data.
  * **Symbol**; is a unique value and are often used to add unique property keys to an object that won't collide with keys any other code might add to the object.

Object is a value in memory which is referenced by an identifier and would be defined as a collection of properties. There are sub-types of objects;
  * **Functions**; are regular objects with the additional capability of being callable,
  * **Arrays**; are regular objects for which there is a particular relationship between integer-keyed properties and the length property,
  * **Map - WeakMap**; are collections of key-value pairs,
  * **Set - WeakSet**, are collections of values,
&NewLine;
&NewLine;

# Types Introduced by TypeScript;
**Unknown**: We may need to describe the type of variables that we do not know when we are writing an application. These values may come from dynamic content – e.g. from the user – or we may want to intentionally accept all values in our API. In these cases, we want to provide a type that tells the compiler and future readers that this variable could be anything, so we give it the unknown type.

**Any**: In some situations, not all type information is available or its declaration would take an inappropriate amount of effort. These may occur for values from code that has been written without TypeScript or a 3rd party library. In these cases, we might want to opt-out of type checking. To do so, we label these values with the any type:

**Void**: is a little like the opposite of any: the absence of having any type at all. You may commonly see this as the return type of functions that do not return a value:

**Never**: The never type represents the type of values that never occur. For instance, never is the return type for a function expression or an arrow function expression that always throws an exception or one that never returns. Variables also acquire the type never when narrowed by any type guards that can never be true.

We can use such a function to ensure exhaustive matching within switch and if-else statement: by using it as the default case, we ensure that all cases are covered, since what remains must be of type `never`. If we accidentally leave out a possible match, we get a type error. For example:

```typescript
	function unknownColor(x: never): never {
	    throw new Error("unknown color");
	}
		
	type Color = 'red' | 'green' | 'blue'
	
	function getColorName(c: Color): string {
	    switch(c) {
	        case 'red':
	            return 'is red';
	        case 'green':
	            return 'is green';
	        default:
	            return unknownColor(c); // Argument of type 'string' is not assignable to parameter of type 'never'
	    }
	}
```
` `  
` `
# Type Annotations;
In TypeScript when you declare a variable using const, var, or let, you can optionally add a type annotation to explicitly specify the type of the variable (type annotations will always go after the thing being typed);
```typescript
	let myName: string = "Alice";
```
In most cases, though, this isn’t needed. Wherever possible, TypeScript tries to automatically infer the types in your code. For example, the type of a variable is inferred based on the type of its initializer:
```typescript
	// No type annotation needed -- 'myName' inferred as type 'string'
	let myName = "Alice";
```
Functions are the primary means of passing data around in JavaScript. TypeScript allows you to specify the types of both the input and output values of functions.
```typescript
	// Parameter type annotation
	function greet(name: string) {
	  console.log("Hello, " + name.toUpperCase() + "!!");
	}
```
When a parameter has a type annotation, arguments to that function will be checked:
```typescript
	// Would be a runtime error if executed!
	greet(42);
```
Argument of type 'number' is not assignable to parameter of type 'string'.

You can also add return type annotations. Return type annotations appear after the parameter list:
```typescript
	function getFavoriteNumber(): number {
	  return 26;
	}
```
Much like variable type annotations, you usually don’t need a return type annotation because TypeScript will infer the function’s return type based on its return statements. The type annotation in the above example doesn’t change anything. It would be a good exercise to explicitly specify a return type for documentation purposes, or to prevent accidental changes.

To define an object type, we simply list its properties and their types;
```typescript
	// The parameter's type annotation is an object type
	function printCoord(pt: { x: number; y: number }) {
	  console.log("The coordinate's x value is " + pt.x);
	  console.log("The coordinate's y value is " + pt.y);
	}
	printCoord({ x: 3, y: 7 });
```
&nbsp;

# Defining a Type:

In JavaScript, the fundamental way that we group and pass around data is through objects. In TypeScript, we represent those through _object types_. One of the ways to define a type is interface;

```typescript
	interface Person {
		name: string;
		age: number;
	}
	
	function greet(person: Person) {
		return "Hello " + person.name;
	}
```

or they can be named by using either a type alias;
```typescript
	type Person = {
		name: string;
		age: number;
	};
	
	function greet(person: Person) {
		return "Hello " + person.name;
	}
```

or anonymous;
```typescript
	function greet(person: { name: string; age: number }) {
		return "Hello " + person.name;
	}
```
For this definition Java developers might say “That’s not a Person. That’s an Object that just happens to have the same properties as Person". This is called structural typing, which cares only about the **structure** of the value. In a structural type system, an object meets the requirements of a type if it has the same properties and methods with the same types as the requested type.

Some developers may have heard this referred to as “duck typing” — if it walks like a duck and it quacks like a duck, then it’s a duck. Structural typing and duck typing are very similar — “structural typing” is often used to refer to such checks run at compile time, while “duck typing” refers to the same checks run at runtime.

There is another type system called nominal typing. A nominal type system uses the name of the type to check for equivalence (as known from Java).   
` `  
` `

# Much More:
With types, TypeScript offers a lot more capabilities. Checkout official documantation page: https://www.typescriptlang.org/docs/handbook/intro.html   
For tips, tricks and advanced features, checkout this page: https://basarat.gitbook.io/typescript/   
Do you need somebody to explain? Check this out: https://www.udemy.com/course/understanding-typescript/   
If you think you cracked it, try these challanges: https://github.com/type-challenges/type-challenges