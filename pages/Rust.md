- id:: 622feb80-47da-4704-b183-2902de122fc6
- Rust takes a different path: the memory is automatically returned once the variable that owns it goes out of scope.
-
- There is a natural point at which we can return the memory our String needs to the allocator: when s goes out of scope. When a variable goes out of scope, Rust calls a special function for us. This function is called drop, and it’s where the author of String can put the code to return the memory. Rust calls drop automatically at the closing curly bracket.
-
- Note: In C++, this pattern of deallocating resources at the end of an item’s lifetime is sometimes called Resource Acquisition Is Initialization (RAII). The drop function in Rust will be familiar to you if you’ve used RAII patterns.
-
- Rust will never automatically create “deep” copies of your data. Therefore, any automatic copying can be assumed to be inexpensive in terms of runtime performance.
-
- The reason is that types such as integers that have a known size at compile time are stored entirely on the stack, so copies of the actual values are quick to make. That means there’s no reason we would want to prevent x from being valid after we create the variable y. In other words, there’s no difference between deep and shallow copying here, so calling clone wouldn’t do anything different from the usual shallow copying and we can leave it out.
-
- If a type implements the Copy trait, a variable is still valid after assignment to another variable.
-
- Here are some of the types that implement Copy:
- All the integer types, such as u32.
  id:: 6232c7e7-f3f2-45d0-8dfd-dc69ed72cc9a
  The Boolean type, bool, with values true and false.
  All the floating point types, such as f64.
  The character type, char.
  Tuples, if they only contain types that also implement Copy. For example, (i32, i32) implements Copy, but (i32, String) does not.
-
- Unlike a pointer, a reference is guaranteed to point to a valid value of a particular type.
- These ampersands represent references, and they allow you to refer to some value without taking ownership of it.
-
-
- We’re not allowed to modify something we have a reference to.
-
- Mutable references have one big restriction: you can have only one mutable reference to a particular piece of data at a time. This code that attempts to create two mutable references to s will fail:
-
- The restriction preventing multiple mutable references to the same data at the same time allows for mutation but in a very controlled fashion. It’s something that new Rustaceans struggle with, because most languages let you mutate whenever you’d like. The benefit of having this restriction is that Rust can prevent data races at compile time. A data race is similar to a race condition and happens when these three behaviors occur:
- Two or more pointers access the same data at the same time.
  At least one of the pointers is being used to write to the data.
  There’s no mechanism being used to synchronize access to the data.
-
- The scopes of the immutable references r1 and r2 end after the println! where they are last used, which is before the mutable reference r3 is created. These scopes don’t overlap, so this code is allowed. The ability of the compiler to tell that a reference is no longer being used at a point before the end of the scope is called Non-Lexical Lifetimes (NLL for short), and you can read more about it in
-
- The Rules of References
  Let’s recap what we’ve discussed about references:
- At any given time, you can have either one mutable reference or any number of immutable references.
  References must always be valid.
-
- if we have an immutable reference to something, we cannot also take a mutable reference.
-
-
- A crate is a binary or library. The crate root is a source file that the Rust compiler starts from and makes up the root
-
- A package is one or more crates that provide a set of functionality. A package contains a Cargo.toml file that describes how to build those crates.
-
- Rust accomplishes this by performing monomorphization of the code that is using generics at compile time. Monomorphization is the process of turning generic code into specific code by filling in the concrete types that are used when compiled.
  id:: 6236e601-01f0-441e-8080-84767f4f5c30
-
-
- Lifetime annotations don’t change how long any of the references live. Just as functions can accept any type when the signature specifies a generic type parameter, functions can accept references with any lifetime by specifying a generic lifetime parameter. Lifetime annotations describe the relationships of the lifetimes of multiple references to each other without affecting the lifetimes.
-
-
- The constraint we want to express in this signature is that the lifetimes of both of the parameters and the lifetime of the returned reference are related such that the returned reference will be valid as long as both the parameters are.
-
- The lifetime annotations become part of the contract of the function, much like the types in the signature are. Having function signatures contain the lifetime contract means the analysis the Rust compiler does can be simpler.
-
- Separation of Concerns for Binary Projects
  The organizational problem of allocating responsibility for multiple tasks to the main function is common to many binary projects. As a result, the Rust community has developed a process to use as a guideline for splitting the separate concerns of a binary program when main starts getting large. The process has the following steps:
- Split your program into a main.rs and a lib.rs and move your program’s logic to lib.rs.
  As long as your command line parsing logic is small, it can remain in main.rs.
  When the command line parsing logic starts getting complicated, extract it from main.rs and move it to lib.rs.
-
- The responsibilities that remain in the main function after this process should be limited to the following:
- Calling the command line parsing logic with the argument values
  Setting up any other configuration
  Calling a run function in lib.rs
  Handling the error if run returns an error