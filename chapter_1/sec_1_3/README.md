# Section 1.3: Hello, Cargo

Cargo is rust's package management tool, similar to pip/gem etc.

Check cargo's installation

```bash
$ cargo --version
cargo 1.46.0 (149022b1d 2020-07-17)
```

Create a cargo project

```
cargo new hello_cargo
cd hello_cargo
```

Cargo creates

* `Cargo.toml` containing project metadata
* `src/main.rs` containing hello world code.

Build project using

```bash
$ cargo build
   Compiling hello_cargo v0.1.0 (/Users/Sasank/Open Source/OpenGC/rust/chapter_1/sec_1_3/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 1.51s
```

Run the built binary using 

```bash
$ ./target/debug/hello_cargo
Hello, world!
```

or 

```bash
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/hello_cargo`
Hello, world!
```

Check compilability using

```bash
$ cargo check
    Checking hello_cargo v0.1.0 (/Users/Sasank/Open Source/OpenGC/rust/chapter_1/sec_1_3/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.07s
```

This is faster than cargo build - quite useful.

For release build, you can do the following for extra optimizations.

```
$ cargo build --release
   Compiling hello_cargo v0.1.0 (/Users/Sasank/Open Source/OpenGC/rust/chapter_1/sec_1_3/hello_cargo)
    Finished release [optimized] target(s) in 0.16s
```