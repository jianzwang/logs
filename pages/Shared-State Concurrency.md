- ((623760a2-bb6e-4580-b5b3-3b184222bb9f))
- ```rust
  use std::sync::{Arc, Mutex};
  use std::thread;
  fn main() {
    let counter = Arc::new(Mutex::new(0));
    let mut handles = vec![];
    for _ in 0..10 {
      let counter = Arc::clone(&counter);
      let handle = thread::spawn(move || {
        let mut num = counter.lock().unwrap();
        *num += 1;        
      });        
      
      handles.push(handle); 
    }
    
    for handle in handles {
      handle.join().unwrap();
    }
    println!("Result: {}", *counter.lock().unwrap());
  }
  ```
- [[RC<T>, the Reference Counted Smart Pointer]] Rc<T> is not safe to share across threads.
- Atomic Reference Counting with **Arc<T>**
	- **Arc<T>**is a type like **Rc<T>** that is safe to use in concurrent situations. The a stands for atomic, meaning _it’s an atomically reference counted_ type.