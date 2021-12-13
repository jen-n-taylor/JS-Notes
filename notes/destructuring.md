# Destructuring

## TL;DR
**Destructuring assignment** makes it possible to unpack values from arrays or properties from objects into distinct variables.

## Left vs. Right

### Right-side assignment: Object and array literal expression
- a way to create an ad hoc package of data. 
```
const x = [1, 2, 3, 4, 5]

console.log(x); // [1, 2, 3, 4, 5];
```

### Left-side assignment: Destructuring assignment
- a way to define what values to unpack from the variable
```
const x = [1, 2, 3, 4, 5];
const [y, z] = x;

console.log(x); // [1, 2, 3, 4, 5];
console.log(y); // 1
console.log(z); // 2
```

## Destructuring Arrays and Objects
Destructuring allows you to unpack:
- values from arrays
- properties from objects

### Basic assignment
- Left-side is used to determine what to unpack from the variable or property.

**Array Example:**
```
const foo = ['one', 'two', 'three'];

const [red, yellow, green] = foo;
console.log(red); // "one"
console.log(yellow); // "two"
console.log(green); // "three"
```

**Object Example:**
```
const user = {
    id: 42,
    isVerified: true
};

const {id, isVerified} = user;

console.log(id); // 42
console.log(isVerified); // true
```

### Assignment separate from declaration
- A variable can still be assigned to a value in an array, even if the varialble has already been declared.

**Array Example:**
```
let one, two;
[one, two] = [red, yellow];

console.log(one); // red
console.log(two); // yellow
```

**Object Example:**
- Note: The parentheses ( ... ) around the assignment statement are required when using object literal destructuring assignment without a declaration.
```
let a, b;

({a, b} = {a: 1, b: 2});
```

### Swapping variables 
- Two variables values can be swapped in one destructuring expression.
- A property can be unpacked from an object and assigned to a variable with a different name than the object property.

**Array Example:**
```
const colors = [red, green, blue];
[colors[2], colors[1]] = [colors[1], colors[2]];
console.log(colors); // [red, blue, green]
```

**Object Example:**
```
const o = {p: 42, q: true};
const {p: foo, q: bar} = o;

console.log(foo); // 42
console.log(bar); // true
```

### Setting default values
- A variable can be assigned a default to fall back to in the event that a value unpacked from the array or object is `undefined`.

**Array Example:**
```
let one, two;

[one = red, two = green] = [orange]

console.log(one); // orange
console.log(two); // green
```

**Object Example:**
```
const {a = 10, b = 5} = {a: 3};

console.log(a); // 3
console.log(b); // 5

``` 

## How to assign the rest of an array to a variable
- When destructuring you can also assign the remaining part ot a variable
- Note: A SyntaxError will be thrown if a trailing comma is used on the right-hand side of a rest element.
```
const [a, ...b] = [1, 2, 3];
console.log(a); // 1
console.log(b); // [2, 3]
```





## What is the benefit of destructuring?

-  You can set a defaults
-  You can parse an array returned from a function
- Destructuring is useful because it can make working with an array return value more concise and easier to deal with. 

```
function f() {
  return [1, 2];
}

let a, b;
[a, b] = f();
console.log(a); // 1
console.log(b); // 2
```

### You can can ignore returned values you're not interested in
- If you're only intrested in a specific value, you can ignore the ones you don't need in this context.

```
function f() {
  return [1, 2, 3];
}

const [a, , b] = f();
console.log(a); // 1
console.log(b); // 3

const [c] = f();
console.log(c); // 1

```
