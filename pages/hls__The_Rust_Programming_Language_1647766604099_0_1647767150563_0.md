file-path:: ../assets/The_Rust_Programming_Language_1647766604099_0_1647767150563_0.pdf
file:: [The_Rust_Programming_Language_1647766604099_0_1647767150563_0.pdf](../assets/The_Rust_Programming_Language_1647766604099_0_1647767150563_0.pdf)
title:: hls__The_Rust_Programming_Language_1647766604099_0_1647767150563_0

- Rc<T>, the Reference Counted Smart Pointer
  ls-type:: annotation
  hl-page:: 396
  id:: 6236efd9-20f8-4198-8d90-245352a3e6e4
- Interior mutability is a design pattern in Rust that allows you to mutate data even when thereare immutable references to that data; 
  ls-type:: annotation
  hl-page:: 401
  id:: 6236f29d-1443-4250-acdf-fbd2f8a39fe3
- The RefCell<T> type is useful when you’re sure yourcode follows the borrowing rules but the compiler is unable to understand and guaranteethat.
  ls-type:: annotation
  hl-page:: 402
  id:: 6236f349-14fa-435f-a858-e87a2844af9a
- The most straightforward smart pointer is a box, whose type is written Box<T>
  ls-type:: annotation
  hl-page:: 378
  id:: 62370a01-b3fa-4358-878a-0acf04c3a9f5
- Implementing the Deref trait allows you to customize the behavior of the dereference operator
  ls-type:: annotation
  hl-page:: 385
  id:: 62370b67-8083-4696-9752-e0a1c3b17002
- The Deref trait, provided by the standard library, requires us to implement one method named deref that borrows self and returns a reference to the inner data
  hl-page:: 388
  ls-type:: annotation
  id:: 62370c4e-9c96-416b-8d98-79733d1d59bc
- which lets you customizewhat happens when a value is about to go out of scope.
  ls-type:: annotation
  hl-page:: 392
  id:: 62370f8a-7376-464e-984a-5e3a6289b893
- Handling concurrent programming safely and efficiently is another of Rust’s major goals.
  ls-type:: annotation
  hl-page:: 421
  id:: 623754a6-e39a-422e-96ca-5ba5b4e569f0
- Programming language-provided threads are known as green threads, and languages that use these green threads will execute them in the context of a different number of operating system threads. For this reason, the green-threaded model is called the M:N model: there are M green threads per N operating system threads, where M and N are not necessarily the same number.
  hl-page:: 422
  ls-type:: annotation
  id:: 62375519-cbf3-4928-ad96-3e1ba3369e04
	- The green-threading M:N model requires a larger language runtime to manage threads.
	- As such, the Rust standard library only provides an implementation of 1:1 threading.
- Rust needs to havenearly no runtime and cannot compromise on being able to call into C to maintainperformance.
  ls-type:: annotation
  hl-page:: 422
  id:: 62375553-688e-41d6-8dc2-f93140e967c9
- One major tool Rust has for accomplishing message-sending concurrency is the channel, aprogramming concept that Rust’s standard library provides an implementation of. 
  ls-type:: annotation
  hl-page:: 430
  id:: 623757c0-c06d-4dcb-9b18-1e92f4d256bf