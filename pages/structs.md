- ```rust
  pub struct AveragedCollection { 
    list: Vec<i32>,    
    average: f64,
  }
  ```
- ((62376b0c-89da-4e0e-8e2a-5921d6cfca5d))
- There is no way to define a struct that inherits the parent struct’s fields and method implementations.
	- choose inheritance for two main reasons. One is for reuse of code:
		- can implement particular behavior for one type, and inheritance enables you to reuse that implementation for a different type.
			- can share Rust code using default [[trait method]] implementations
			- can also override the default implementation of the method when we implement the trait
	- to enable a child type to be used in the same places as the parent type. This is also called _polymorphism, which means that you can substitute multiple objects for each other at runtime if they share certain characteristics. _
		- Rust instead uses generics to abstract over different possible types and trait bounds to impose constraints on what those types must provide. This is sometimes called _bounded parametric polymorphism._
		-