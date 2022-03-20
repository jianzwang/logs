- When we use trait objects, Rust must use _dynamic dispatch_. The compiler doesn’t know all the types that might be used with the code that is using trait objects, so it doesn’t know which method implemented on which type to call. #monomorphization
	- There is a runtime cost when this lookup happens that doesn’t occur with static dispatch. Dynamic dispatch also prevents the compiler from choosing to inline a method’s code, which in turn prevents some optimizations.
-
- Object Safety Is Required for Trait Objects
	- ((62377170-7440-4968-8664-b6901eb5881f))
	- but in practice, only two rules are relevant. A trait is object safe if all the methods defined in the trait have the following properties:
	  * The return type isn’t Self. 
	  * There are no generic type parameters.
	- Trait objects must be object safe because once you’ve used a trait object, Rust no longer knows the concrete type that’s implementing that trait
	- If a trait method returns the concrete **Self** type, but a trait object forgets the exact type that Self is, there is no way the method can use the original concrete type.
	- a trait whose methods are not object safe is the standard library’s [[Clone trait]].
		- ```rust
		  pub trait Clone {
		    fn clone(&self) -> Self;
		  }
		  ```
		- The String type implements the Clone trait, and when we call the clone method on an instance of String we get back an instance of String. Similarly, if we call clone on an instance of **Vec<T>**, we get back an instance of Vec<T>. The signature of clone needs toknow what type will stand in for Self, because that’s the return type.