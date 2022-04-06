
# TypeScript

## Why TS?

-   Easier to debug
-   Improves project quality
-   Makes code easier to read and understand.
    

## Type Annotations

### Primitive:
```
let  myName: string = "Alice";
let  myAge: number= 25;
let  isMarried: boolean = false;
```

### Functions:

```
function  greet(name: string) {
	console.log("Hello, " + name.toUpperCase() + "!!");
}
greet("Saajid")
```
```
Note :  Argument of type 'number' is not assignable to parameter of type 'string'.
```
    

### Return:

```
function  getFavoriteNumber(): number {
	return  26;
}
```

### Object Types:
```
function  printCoord(pt: { x: number; y: number }) {
	console.log("The coordinate's x value is " + pt.x);
	console.log("The coordinate's y value is " + pt.y);
}

printCoord({ x:  3, y:  7 });
```

### Optional Properties:
```
function  printName(obj: { first: string; last?: string }) {
	// ...
}

// Both OK

printName({ first:  "Bob" });
printName({ first:  "Alice", last:  "Alisson" });

```

### Union Type:
```
function  printId(id: number | string) {
	console.log("Your ID is: " + id);
}
```


### Type Aliases:

```
type  Point = {
	x: number;
	y: number;
};

// Exactly the same as the earlier example

function  printCoord(pt: Point) {
	console.log("The coordinate's x value is " + pt.x);
	console.log("The coordinate's y value is " + pt.y);
}

printCoord({ x:  100, y:  100 });

```

### Interfaces:

```
interface  Point {
	x: number;
	y: number;
}

function  printCoord(pt: Point) {
	console.log("The coordinate's x value is " + pt.x);
	console.log("The coordinate's y value is " + pt.y);
}

printCoord({ x:  100, y:  100 });

```

### Interface vs Type

-   Type cannot be re-opened to add new properties 
-  Interface which is always extendable.
    

## Type Assertions:

- Sometimes you will have information about the type of a value that TypeScript can’t know about.

- For example, if you’re using  `document.getElementById`, TypeScript only knows that this will return  _some_  kind of  `HTMLElement`, but you might know that your page will always have an  `HTMLCanvasElement`  with a given ID.

### Example : 

```
const  myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
```

```
const  myCanvas = <HTMLCanvasElement>document.getElementById("main_canvas");
```

<hr>

### Literal Types

```
let  x: "hello" = "hello";

x = "hello"; // OK
x = "howdy"; // Error

// Type '"howdy"' is not assignable to type '"hello"'.
```


```
function  printText(s: string, alignment: "left" | "right" | "center") {
	// ...
}

printText("Hello, world", "left"); // OK
printText("G'day, mate", "centre"); // Error

// Argument of type '"centre"' is not assignable to parameter of type '"left" | "right" | "center"'.
```

### Literal Inference
```
// Change 1:
const  req = { url:  "https://example.com", method:  "GET"  as  "GET" };

// Change 2
handleRequest(req.url, req.method  as  "GET");
```

## `null` and `undefined`

```
function  doSomething(x: string | null) {
	if (x === null) {
		// do nothing
	} else {
		console.log("Hello, " + x.toUpperCase());
	}
}
```

### Non-null Assertion Operator (Postfix`!`)

```
function  liveDangerously(x?: number | null) {
	// No error
	console.log(x!.toFixed());
}
```





