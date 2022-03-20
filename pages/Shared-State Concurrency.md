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
	- [[Send And Sync Trait]]: it’s one of the traits that ensures the types we use with threads are meant for use in concurrent situations.
	- **Arc<T>**is a type like **Rc<T>** that is safe to use in concurrent situations. The a stands for atomic, meaning _it’s an atomically reference counted_ type.
	- thread safety comes with a performance penalty that you only want to pay when you really need to.
	- **Arc<T>** and **Rc<T>** have the same API
	- Similarities Between **RefCell<T>**/**Rc<T>** and  **Mutex<T>**/**Arc<T>**
		- counter is immutable, Mutex<T> provides interior mutability, as the Cell family does.
		- Mutex<T> comes with the risk of creating deadlocks. These occur when an operation needs to lock two resources and two threads have each acquired one of the locks, causing them to wait for each other forever.