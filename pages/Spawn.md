- To create a new thread, we call the **thread::spawn** function and pass it a closure
	- Waiting for All Threads to Finish Using **join** Handles
		- ```rust
		  use std::thread;
		  use std::time::Duration;
		  fn main() {
		    let handle = thread::spawn(|| {
		      for i in1..10 {
		        println!("hi number {} from the spawned thread!", i); 
		        thread::sleep(Duration::from_millis(1));    
		      }   
		    });
		    
		    for i in 1..5 {
		      println!("hi number {} from the main thread!", i);    
		      thread::sleep(Duration::from_millis(1)); 
		    }   
		    handle.join().unwrap();
		  }
		  
		  ```
	- Using **move** Closures with Threads #ownership
		- The **move** closure is often used alongside thread::spawn because it allows you to use data from one thread in another thread.
			- ```rust
			  let v = vec![1, 2, 3];
			  let handle = thread::spawn(move || {
			    println!("Here's a vector: {:?}", v);    
			  });
			  ```
-