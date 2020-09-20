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

Crate are libraries - can be code or binary. Let's use `rand` crate.
Add the following lines to `Cargo.toml`. 

```
[dependencies]
rand = "0.5.5"
```

```
$ cargo build
    Updating crates.io index
  Downloaded rand_core v0.3.1
  Downloaded rand_core v0.4.2
  Downloaded libc v0.2.77
  Downloaded rand v0.5.6
  Downloaded 4 crates (680.2 KB) in 1.64s
   Compiling libc v0.2.77
   Compiling rand_core v0.4.2
   Compiling rand_core v0.3.1
   Compiling rand v0.5.6
   Compiling guessing_game v0.1.0 (/Users/Sasank/Open Source/OpenGC/rust/chapter_2/guessing_game)
    Finished dev [unoptimized + debuginfo] target(s) in 20.25s
```

## Comparing

`std::cmp::Ordering` is another enum like `Result`. Its variants are `Less`, `Greater` and `Equal`.

```rust
match guess.cmp(&secret_number) {
     Ordering::Less => println!("Too small!"),
     Ordering::Greater => println!("Too big!"),
     Ordering::Equal => println!("You win!"),
};
```

`match` expression is made up of arms containing a pattern and code that should be run when first part of `match` (here `guess.cmp(&secret_number)`) matches the pattern. Similar to `case` of C++.

## Type conversion

Rust has both strong, static type system and type inference.We can convert string to int as follows:

```
let guess: u32 = guess.trim().parse().expect("Please type a number");
```

Apparently, variable name reuse is called shadowing. `trim` trims the white space from string. `parse` converts string to numbers, but it requires type annotation of the result `guess:u32` so that it know what kind of number we want.

We have seen `expect` before for io - same function here too. If we input `foo`, here's the error

```
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.01s
     Running `target/debug/guessing_game`
Guess the number!
The secret number is 23
Please input your guess
foo
thread 'main' panicked at 'Please type a number: ParseIntError { kind: InvalidDigit }', src/main.rs:19:43
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
```

## Loops

`loop` is for infinite loop. `break` is to break the loop! Simple stuff.

## Handling invalid input

`expect` creates a panic. Can we make it better? We can use match.

```
let guess: u32 = match guess.trim().parse() {
     Ok(num) => num,
     Err(_) => continue,
};
```