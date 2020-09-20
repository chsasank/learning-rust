# Section 3.1 - Variables and Mutability

## Variables

Variables are *immutable* by default.

```rust
let x = 5;
x = 6;
```

Creates compile error - `cannot assign twice to immutable variable x`.
Compiler errors are good for your health :P.

Make variable mutable by `mut`.

## Constants

* Constants are similar to variables but never mutable.
* Uses `const` instead of `let`.
* Type of the data must be annotated for constants.
* Can be declared in any scope, including global scope
* Can only be set to a constant expression, not a function call.

```rust
const MAX_POINTS: u32 = 100_000;
```

## Shadowing

When you declare a new variable with the same name as a previous variable, you have shadowed the previous variable.

eg.

```rust
let y = 5;
let y = y* 2;
println!("the value of y is: {}", y);
```

Note the difference between shadowing and `mut`. Essentially creating a new variable. You can change type too. This is allowed:

```rust
let spaces = "   ";
let spaces = spaces.len();
```

but this is not

```rust
let mut spaces = "   ";
spaces = spaces.len();
```