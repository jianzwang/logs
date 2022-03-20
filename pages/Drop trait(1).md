- ((62370f8a-7376-464e-984a-5e3a6289b893))
- Specify the code to run when a value goes out of scope by implementing the Drop trait. The Drop trait requires you to implement one method named drop that takes a mutable reference to self.
- ```rust
  fn drop(&mut self) {
    println!("Droping with Data `{}`", self.data);
  }
  ```
- The **Drop trait** is included in the prelude, so we don’t need to bring it into scope.
- Rust automatically called drop for us when our instances went out of scope, calling the code we specified. Variables are dropped in the reverse order of their creation, so d was dropped before c.
- ##