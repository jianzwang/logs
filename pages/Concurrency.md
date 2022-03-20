public:: true

- Handling concurrent programming safely and efficiently is another of Rust’s major goals.
  ls-type:: annotation
  hl-page:: 421
- {{embed ((62375519-cbf3-4928-ad96-3e1ba3369e04))}}
- Programming language-provided threads are known as green threads, and languages that use these green threads will execute them in the context of a different number of operating system threads. For this reason, the green-threaded model is called the M:N model: there are M green threads per N operating system threads, where M and N are not necessarily the same number.
  hl-page:: 422
  ls-type:: annotation
	- The green-threading M:N model requires a larger language runtime to manage threads.
	- As such, the Rust standard library only provides an implementation of 1:1 threading.