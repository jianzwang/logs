title:: Box<T>, Point to Data on the Heap

- ((62370a01-b3fa-4358-878a-0acf04c3a9f5))
- Boxes don’t have performance overhead, other than storing their data on the heap instead of on the stack.
	- id:: 6237098b-8399-4a3d-a635-3dc7f54dee49
	  * When you have a type whose size can’t be known at compile time and you want to use a value of that type in a context that requires an exact size [[Enabling Recursive Types With Boxes]] 
	  * When you have a large amount of data and you want to transfer ownership but ensure the data won’t be copied when you do so. To improve performance in this situation, we can store the large amount of data on the heap in a box. Then, only the small amount of pointer data is copied around on the stack, while the data it references stays in one place on the heap. 
	  * When you want to own a value and you care only that it’s a type that implements a particular trait rather than being of a specific type [[Using Trait Objects That Allow for Values of Different Types]]
- Using Box<T> Like a Reference
	- ```rust
	  fn main() {
	    let x = 5;
	    let y = Box::new(x);
	    assert_eq!(5,*y);
	  }
	  ```