- ``` rust
  impl Rectangle {
  	fn area(&self) -> u32 {
        self.width * self.height   
  	}
  }
  ```
- ((6232e10f-179e-4a46-9d7f-39ed119bbe32))
- We’ve chosen **&self** here for the same reason we used &Rectangle in the function version:we don’t want to take ownership, and we just want to read the data in the struct, not write toit. If we wanted to change the instance that we’ve called the method on as part of what themethod does, we’d use **&mut** self as the first parameter.
-