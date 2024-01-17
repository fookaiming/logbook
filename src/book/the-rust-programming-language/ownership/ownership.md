# Ownership

## What is ownership

> 💡 a set of rules that govern how a Rust program manages memory (heap) -> make memory safety guarantee without garbage
> collector

## Ownership Rules

- Each data in ***heap*** has an owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will either be dropped or returned

```rust
fn main() {
    let s1 = gives_ownership();         // gives_ownership moves its return
                                        // value into s1

    let s2 = String::from("hello");     // s2 comes into scope

    let s3 = takes_and_gives_back(s2);  // s2 is moved into
                                        // takes_and_gives_back, which also
                                        // moves its return value into s3
} // Here, s3 goes out of scope and is dropped. s2 was moved, so nothing
  // happens. s1 goes out of scope and is dropped.

fn gives_ownership() -> String {             // gives_ownership will move its
                                             // return value into the function
                                             // that calls it

    let some_string = String::from("yours"); // some_string comes into scope

    some_string                              // some_string is returned and
                                             // moves out to the calling
                                             // function
}

// This function takes a String and returns one
fn takes_and_gives_back(a_string: String) -> String { // a_string comes into
                                                      // scope

    a_string  // a_string is returned and moves out to the calling function
}
```

#### Move

- Ownership can be transferred by moves, which happen on **_assignments_** and **_function calls_**.

> Moved heap data principle: if a variable x moves ownership of heap data to another variable y, then x cannot be used
> after the move.


---

## Reference

> References are non-owning pointers, because they do not own the data they point to

insert img

- references live in Stack
- it points to the owner not the data

## Bear in mind

- Rust will never automatically create “deep” copies of your heap data
- use clone() explicitly
- stack data are always cloned
