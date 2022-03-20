- ((62370f8a-7376-464e-984a-5e3a6289b893))
- Specify the code to run when a value goes out of scope by implementing the Drop trait. The Drop trait requires you to implement one method named drop that takes a mutable reference to self.
- ```rust
  fn drop(&mut self) {
    println!("Droping with Data `{}`", self.data);
  }
  ```
- The **Drop trait** is included in the prelude, so we don’t need to bring it into scope.
- Rust automatically called drop for us when our instances went out of scope, calling the code we specified. Variables are dropped in the reverse order of their creation, so d was dropped before c.
- ## Dropping a Value Early with std::mem::drop
	- Unfortunately, it’s not straightforward to disable the automatic drop functionality.
	- One example is when using smart pointers that manage locks: you might want to force the drop method that releases the lock so that other code in the same scope can acquire the lock.
	- Rust doesn’t let you call the Drop trait’s drop method manually;
		- Rust doesn’t let us call drop explicitly because Rust would still automatically call drop on the value at the end of main. This would be a double free error because Rust would be trying to clean up the same value twice.
- you have to call the `std::mem::drop` function provided by the standard library if you want to force a value to be dropped before the end of its scope.
-