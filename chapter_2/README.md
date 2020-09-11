# Chapter 2: Programming a Guessing Game

Start new project `guessing_game`.

```
$ cargo new guessing_game
     Created binary (application) `guessing_game` package
$ cd guessing_game/
```

Look at `src/main.rs`.

* `std::io` is namespacing for io library.

```rust
let mut guess = String::new();
```

* `let` is used to create a variable
* Variables are immutable by default 
* `let mut` makes a variable immutable

```rust
let foo = 5; // immutable
let mut bar = 5; // mutable
```

* `String::new()` is an associated function of the `String` type.
  Some languages call this a static method.
* `let mut guess = String::new();` creates a mutable variable bound to a new empty `String`

```rust
io::stdin()
     .read_line(&mut guess)
     .expect("Failed to read line");
```

* `stdin()` returns a input handle, i.e instance of `std::io::Stdin`
* `readline` takes actual input.
* `guess` is passed to this function by reference (i.e `&`).
* `guess` needs to be updated (aka mutated) by `readline`. Therefore `&mut`.
* Last line is what makes rust safe
* `expect` is a function of `io::Result` object returned by `readline`.
* `Result` types are enumerations. More about it later. Variants are `Ok` and `Err`
* `expect` creates message if the io op fails. 

```rust
println!("You guessed: {}", guess);
```

* Puts value of `guess` inside braces.
* Can have multiple place holders.

```rust
let x = 5;
let y = 10;

println!("x = {} and y = {}", x, y);
```

## Using Crates

Crate are libraries - can be code or binary. Let's use `rand` crate. Add following lines to `Cargo.toml`. 

