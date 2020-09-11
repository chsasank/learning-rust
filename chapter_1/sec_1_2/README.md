# Section 1.2: Hello, World!

## Writing Rust

* `main()` function is special
* `println!` is a rust macro. Not function.
* `x!()` means you're calling a micro instead of normal function

## Compile

```bash
$ rustc main.rs
$ ./main
Hello world
```

* `rustc` is the compiler.
* Not interpreted or JIT compiled. Ahead of time compilation.
* Cargo is better than `rustc` to manage code. 