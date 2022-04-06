
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

-   That a type cannot be re-opened to add new properties vs an interface which is always extendable.
    

### Type Assertions:

