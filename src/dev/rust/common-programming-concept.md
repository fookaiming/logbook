# Common Programming Concept
## Convention
- snake_case for function and variable
- use ***//*** for comment

---
## Shadowing
- ability to declare variable with the same name as a previous defined variable
```rust
fn main() {
    let x = 5;

    let x = true;

    {
        let x = false;
        println!("The value of x in the inner scope is: {x}");
    }

    println!("The value of x is: {x}");
}
```

---
## Data Types

### Scalar Types
- Integer
- Floating-Point
  - all floating point types are signed
- Boolean
  - one byte
- Character
  - 4 bytes
  - zero-width spaces is valid

### Compound Types
- primitive compound types: tuples and arrays

#### Tuple
- fixed length, once declared, cannot grow or shrink
- multi-types values is allowed
- empty tuple is called ***unit***
  
```rust
fn main() {
    // init
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    let tup = (500, 6.4, 1);

    // access
    let five_hundred = tup.0;
    let six_point_four = tup.1;
    let one = tup.2;
    
    // no field `3` on type occurs when accessing invlid index
    print!("{}", tup.3);

    // destructure by pattern matching
    let (x, y, z) = tup;

    // unit
    let u = ();
}
```

#### Array
- fixed length, grow or shrink is not allowed
- elements must have the same type
- allocated on stack
- index out of bounds error occurs when accessing invlid index

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];

        // [type, num of elements]
    let a: [i32; 5] = [1, 2, 3, 4, 5];

    let a = [3; 5]; // let a = [3, 3, 3, 3, 3]

    // access
    let first = a[0];
    let second = a[1];
}
```
***
## Function
- argument type of each parameter must be declared
- return type must be declared explicitly
- value can be return through the return keyword or return the **last expression** implicitly
- ***unit*** is returned implicitly for function that dont have return value

### Statement
```rust
fn main() {
    // error, statement don't return valures
    let x = (let y = 6);
}
```
- instructions that perform some action and ***do not return*** a value
- *Function* ***definitions*** are also statements

### Expression
- evaluate to a resultant value
- ***Calling*** *a function* is an expression
- A new scope block created with ***curly brackets*** is an expression

```rust
fn main() {
    let y = {
        let x = 3;       // <- this {} block is an expression
        x + 1            // this line don't hv ; which tells it is an expression
    };

    println!("The value of y is: {y}");
}
```

## Flow Control
- non boolean type is not allowed in condition expression
- three kinds of loops: ***loop***, ***while***, ***for***

### loop
- run forever, until explicitly exit by break
```rust
// return values from loop
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;
        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is {result}");
}
```
