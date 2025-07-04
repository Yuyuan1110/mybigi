--- 
	tags: [TypeScript, Typescript basic, basic] 
	aliases: [TSbegin, TypeScript basic] 
	created: 2025-06-27
	updated:
	source:	
---
# Introduce

Typescipt is the superset of javascript, which is  mean all the javascript is valid typescript, or you can say that all javascript can run in typescript, actually, when typescript executed, it will be transpile to javascript before execution.

Typescript including the **static type system**, which can help to find protential type error eralier, not cause error at runtime.

## Basic types
- `number`: All of the number, including integer, float, double, negative.
	```typescript
	let age: number = 30;
	let price: number = 10.99;
	let temperature: number= -6.3;
	```
- `string`: All of the string
	```typescript
	let name: string = "Yuyuan"
	let message: string = `Hi, I'm ${name}!`
	```
- `boolean`: `ture` or `false`
	```typescript
	let isActive: boolean = ture
	```
- `Array`: 
	```typescript
	 let numbers: number[] = [1, 2, 3]; // type + [] 
	 let names: Array<string> = ["Bob", "Charlie"]; // generics array 
	```
- `Tuple`:Tuple is a special type of array that allows for a fixed number of elements.
	```typescript
	let x: [string, number]; 
	x = ["hello", 10]; // OK 
	// x = [10, "hello"]; // error
	```
- `Enum`: Like Enum in Java or Go.
	```typescript
	enum Color {
	    Red,
	    Green,
	    Blue,
	}
	let c: Color = Color.Green; // default Red = 0, Green = 1, Blue = 2
	enum StatusCode {
	    OK = 200,
	    NotFound = 404,
	    ServerError = 500,
	}
	let status: StatusCode = StatusCode.OK;
	```
- `Any`: It can accept any type variable, it can use when not sure what type variable will comming or need to accept any type. It will skip the type checking when transpile.
	```typescript
	let notSure: any = 4;
	notSure = "maybe a string instead";
	notSure = false;
	```
- `Unknow`: When you need to accept any type or don't know what type will incoming, but you don't want to skip the type checking, you can use this keyword.
	```typescript
	let unknownValue: unknown = "hello";
// console.log(unknownValue.length); // error：object is of type 'unknown'.

if (typeof unknownValue === "string") {
    console.log(unknownValue.length); // OK： Checked it is string type
}
```
- `void`: It mean nothing will be return or accept
	```typescript
	function warnUser(): void{
		console.log("This is a warning message"); 
	 }
```
- `Null` and `Undifine`: As same as javascript type `Null` and `Undifine`, it a default subtype of all other types.
- `Never`: It mean don't return never, or always throwout.
	```typescript
	function error(message: error): never{
		throw new Error(message);	
	}
	```

## How to run typescript
Need to run typescript you need to transplie the .ts file to .js file, then run it on javascript.
```bash
tsc hello.ts # It will generate a hello.js
# then can run as Node JS
node hello.js
```
