# What is TypeScript
TypeScript is a programming language developed and maintained by Microsoft. It is a strict syntactical superset of JavaScript and adds optional static typing to the language. It is designed for the development of large applications and transpiles to JavaScript.

# Commmands
## Install
```node
npm install -g typescript
```
## Check Version
```node
tsc -v
```

# Things to know
## Transpile file before execution
Because browser can't understand typescipt. 

## tsconfig.json
Configuration file

## var vs let vs const
### var
Variables in TypeScript can be declared using var keyword, same as in JavaScript. The scoping rules remains the same as in JavaScript.   
### let 
To solve problems with var declarations, ES6 introduced two new types of variable declarations in JavaScript, using the keywords let and const.   
###  const 
Variables can be declared using const similar to var or let declarations. The const makes a variable a constant where its value cannot be changed. Const variables have the same scoping rules as let variables.   

## Type Assertion
Type assertion allows you to set the type of a value and tell the compiler not to infer it. This is when you, as a programmer, might have a better understanding of the type of a variable than what TypeScript can infer on its own.
### There are two ways to do type assertion in TypeScript:
### 1. Using the angular bracket <> syntax. So far in this section, we have used angular brackets to show type assertion.(More common)
```typescript
let code: any = 123; 
let employeeCode = <number> code; 
```
### 2. Using as keyword
```typescript
let code: any = 123; 
let employeeCode = code as number;
```

## Use strict
The "use strict" directive was new in ECMAScript version 5.

It is not a statement, but a literal expression, ignored by earlier versions of JavaScript.

The purpose of "use strict" is to indicate that the code should be executed in "strict mode".

With strict mode, you can not, for example, use undeclared variables.
### Declaration
```typescript
"use strict";
```

## Types of Objects
TypeScript has three confusing types: Object, {} and object.
You can assign null and undefined to all three types if strictNullChecks compiler option is disabled otherwise the compile error occurs.

### Object
Contains stuff (like toString(), hasOwnProperty()) that is present in all JavaScript objects. Any value (primitive, non-primitive) can be assigned to Object type.

### {}
{} is an empty object. It is pretty much the same as Object in runtime but different in compile time. In compile time {} doesn't have Object's members and Object has more strict behavior (see the @golmschenk's comment).

### object
object was introduced in TypeScript 2.2. It is any non-primitive type. You can't assign to it any primitive type like bool, number, string, symbol.

### Thus, if you will try this:
```typescript
var strictTypeHeaders: { [key: string]: string } = {}; // non-primitive type
var header: object = {};
header = strictTypeHeaders; // its OK
strictTypeHeaders = header; // causes error "Type 'object' is not assignable to type '{ [key: string]: string }`"
```
you will get the compile error on the last line. This happens because { [key: string]: string } type is more specific than object type. There is no any error on header = strictTypeHeaders since both types are non-primitive and object is more common type than { [key: string]: string }
