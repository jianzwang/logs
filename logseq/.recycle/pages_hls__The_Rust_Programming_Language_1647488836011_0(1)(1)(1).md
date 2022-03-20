- [assets ![The_Rust_Programming_Language.pdf](../assets/The_Rust_Programming_Language_1647766604099_0.pdf) ]
- # Known Size Types
- ## Tuple
-
- ls-type:: annotation
  hl-page:: 51
  id:: 6232c7ab-12ad-4316-8b53-326b42f26800
- A tuple is a general way of grouping together a number of values with a variety of types intoone compound type. Tuples have a fixed length: once declared, they cannot grow or shrinkin size.We create a tuple by writing a comma-separated list of values inside parentheses. Eachposition in the tuple has a type, and the types of the different values in the tuple don’t haveto be the same
  hl-page:: 51
  ls-type:: annotation
  id:: 6232c817-3f3b-48bb-ac6e-95064d9ec3b2
- ## Array
-
- Unlike arrays in some other languages, arraysin Rust have a fixed length.
  ls-type:: annotation
  hl-page:: 52
  id:: 6232c8e4-7c72-4f77-ba77-59166cf4c758
-
- ##
- # Functions
-
- Rust code uses snake case as the conventional style for function and variable names, inwhich all letters are lowercase and underscores separate words. 
  ls-type:: annotation
  hl-page:: 56
  id:: 6232c936-d680-4e42-af41-491e7560ba5f
- Statements do not return values. 
  ls-type:: annotation
  hl-page:: 58
  id:: 6232c9d3-f73f-4c1f-ae0a-557aaa60d1e6
- You can return early from a function by using the return keyword and specifying a value, but most functions return the last expression implicitly.
  hl-page:: 60
  ls-type:: annotation
  id:: 6232ca13-9409-4c02-ad9e-1a7dbc00045b
- But if we place a semicolon at the endof the line containing x + 1, changing it from an expression to a statement, we’ll get anerror.
  ls-type:: annotation
  hl-page:: 61
  id:: 6232ca3b-c6f9-4cc8-a9a9-06264e7c8ac3
- Expressions do not include ending semicolons. If you add a semicolon to the end of an expression, you turn it into a statement, and it will then not return a value.
  hl-page:: 60
  ls-type:: annotation
  id:: 6232ca66-1a91-47e5-8689-74135384d269
-
- you can add the value youwant returned after the break expression you use to stop the loop; that value will bereturned out of the loop so you can use it
  ls-type:: annotation
  hl-page:: 70
  id:: 6232cadb-dac7-415f-909e-542445cedafa
-
- # Ownership
- ## Stack And Heap
- ### Stack
- The stack stores values in the orderit gets them and removes the values in the opposite order. This is referred to as last in,first out.
  ls-type:: annotation
  hl-page:: 75
  id:: 6232cb28-d22d-49ed-96cc-ac4e7d712b96
- Adding data is called pushingonto the stack, and removing data is called popping off the stack.
  ls-type:: annotation
  hl-page:: 75
  id:: 6232cb3a-cf76-43d9-9805-06bf1f07b773
- All data stored on thestack must have a known, fixed size. Data with an unknown size at compile time or asize that might change must be stored on the heap instead.
  ls-type:: annotation
  hl-page:: 75
  id:: 6232cb43-63d7-457a-8b31-fceb8c8fa488
- ### Heap
- The heap is less organized: when you put data on the heap, you request a certainamount of space. The memory allocator finds an empty spot in the heap that is bigenough, marks it as being in use, and returns a pointer
  ls-type:: annotation
  hl-page:: 75
  id:: 6232cb8f-8020-420a-8314-1b500c0d3090
- This process is called allocating on the heap and is sometimes abbreviated asjust allocating.
  ls-type:: annotation
  hl-page:: 75
  id:: 6232cb9a-5272-444e-b269-25f963d24930
-
- ### Stack vs Heap
- Pushing to the stack is faster than allocating on the heap because the allocator neverhas to search for a place to store new data; 
  ls-type:: annotation
  hl-page:: 76
  id:: 6232cc00-f3e1-44fe-b17c-871040e1bc48
- Accessing data in the heap is slower than accessing data on the stack because youhave to follow a pointer to get there. 
  ls-type:: annotation
  hl-page:: 76
  id:: 6232cc3d-7e7c-41ee-921b-964819392943
- Allocating a large amount of space on the heap can also take time.
  ls-type:: annotation
  hl-page:: 76
  id:: 6232cca0-f034-48a8-90a3-ab831c9a3203
- When your code calls a function, the values passed into the function (including,potentially, pointers to data on the heap) and the function’s local variables get pushedonto the stack. When the function is over, those values get popped off the stack.
  ls-type:: annotation
  hl-page:: 76
  id:: 6232cccc-02ca-4a79-941f-8eec9f071f0f
-
- ## Ownership Rules #ownership
	- hl-page:: 76
	  ls-type:: annotation
	  id:: 6232cf07-4168-4657-9cc5-80204c6665a6
	  * Each value in Rust has a variable that’s called its owner.
	  * There can only be one owner at a time.
	  * When the owner goes out of scope, the value will be dropped.
	  *
- ## String Type
- ### String literals
	- they’re immutable
	  hl-page:: 78
	  ls-type:: annotation
	  id:: 6232cfd0-82db-49ab-b4e2-6c167ba90bb9
-
- ### String
	- You can create a String from a string literal using the **from** function
	  hl-page:: 78
	  ls-type:: annotation
	  id:: 6232cffd-cfcb-4e3e-a9f8-637e7cba111e
	- With the String type, in order to support a mutable, growable piece of text, we need to allocate an amount of memory on the heap, unknown at compile time, to hold the contents.
	- * The memory must be requested from the memory allocator at runtime.
	   * We need a way of returning this memory to the allocator when we’re done with our String.
- ## Memory alloc and free #mgm
	- it’s our responsibility to identify when memory is no longer being used and call code to explicitly return it, just as we did to request it.
	  hl-page:: 79
	  ls-type:: annotation
	  id:: 6232d379-1413-4ea8-a9cf-71c38c09c436
	- Rust takes a different path: the memory is automatically returned once the variable that owns it goes out of scope.
	  hl-page:: 79
	  ls-type:: annotation
	  id:: 6232d39b-bbe1-446c-9bdd-b3aa291622ab
	- when a variable goes out of scope, Rust automatically calls the **drop** function and cleans up the heap memory
	  hl-page:: 82
	  ls-type:: annotation
	  id:: 6232d3f8-1f03-4608-b8b5-5aaad245e803
	- This is known as a double free error and is one of the memory safety bugs we mentioned previously. Freeing memory twice can lead to memory corruption, which can potentially lead to security vulnerabilities.
	  hl-page:: 82
	  ls-type:: annotation
	  id:: 6232d449-8e0c-4433-9cd5-77f99c02f98d
	- Rust will never automatically create“deep” copies of your data. Therefore, any automatic copying can be assumed to beinexpensive in terms of runtime performance.
	  ls-type:: annotation
	  hl-page:: 83
	  id:: 6232d474-5614-46c5-87f0-7735029e8e0e
-
- ### Clone
- If we do want to deeply copy the heap data of the String, not just the stack data, we canuse a common method called **clone**.
  ls-type:: annotation
  hl-page:: 83
  id:: 6232d4dc-e7ca-419d-b736-1f55ba82a510
- The reason is that types such as integers that have a known size at compile time are stored entirely on the stack, so copies of the actual values are quick to make. That means there’s no reason we would want to prevent x from being valid after we create the variable y. In other words, there’s no difference between deep and shallow copying here, so calling clone wouldn’t do anything different from the usual shallow copying and we can leave it out.
  hl-page:: 84
  ls-type:: annotation
  id:: 6232d518-6ca8-42d4-8acd-0d9a55f32cb3
- Rust has a special annotation called the **Copy** trait that we can place on types that arestored on the stack like integers are (we’ll talk more about traits in Chapter 10). If a type implements the **Copy** trait, a variable is still valid after assignment to another variable. Rust won’t let us annotate a type with **Copy** if the type, or any of its parts, has implemented the **Drop** trait.
  hl-page:: 84
  ls-type:: annotation
  id:: 6232d574-7f1f-4932-97c4-751956f4b191
- as a general rule, any group of simple scalar values can implement Copy, and **nothing** that requires allocation or is some form of resource can implement **Copy**. Here are some of the types that implement **Copy**:
  hl-page:: 84
  ls-type:: annotation
  id:: 6232d6b4-e0ef-4a9a-9b46-6120d3626488
-
- * All the **integer** types, such as u32.
  * The **Boolean** type, bool, with values true and false.
  * All the **floating point types**, such as f64.
  * The character type, **char**.
  * **Tuples**, if they only contain types that also implement Copy. For example, (i32, i32)implements Copy, but (i32, String) does not.
-
- ## Ownership and Functions #ownership
	- The semantics for passing a value to a function are similar to those for assigning a value to a variable.
	- Passing a variable to a function will move or copy, just as assignment does.
	  ls-type:: annotation
	  hl-page:: 84
	  id:: 6232d7e9-fd43-4f21-bbb7-dc75261baeac
	- Returning values can also transfer ownership.
	  ls-type:: annotation
	  hl-page:: 85
	  id:: 6232d82b-13af-48ad-b934-9507141055f3
	- Rust does let us return multiple values using a tuple
	  hl-page:: 86
	  ls-type:: annotation
	  id:: 6232d876-87fc-4f52-86db-5645a605dfbf
	- These ampersands represent references, and they allow youto refer to some value without taking ownership of it. 
	  ls-type:: annotation
	  hl-page:: 88
	  id:: 6232d8b8-6fbc-4b2c-b873-f0b823d0b121
	- Just as variables are immutable by default, so are references. We’re not allowed to modify something we have a reference to.
	  ls-type:: annotation
	  hl-page:: 90
	  id:: 6232d902-23cb-40ec-a93a-c3c38539eb67
	- Mutable references have one big restriction: you can have only one mutable reference to aparticular piece of data at a time. 
	  ls-type:: annotation
	  hl-page:: 90
	  id:: 6232d924-ae4b-42a1-8c9b-eb7bd96b7c2a
		- The benefit of having this restriction is that Rust can prevent data races at compile time. A data race is similar to a race condition and happens when these three behaviors occur:
		  hl-page:: 91
		  ls-type:: annotation
		  id:: 6232d956-065e-4493-acad-274d3d6d6ba3
			- * Two or more pointers access the same data at the same time. 
			  * At least one of the pointers is being used to write to the data.
			  * There’s no mechanism being used to synchronize access to the data.
	- Data races cause undefined behavior and can be difficult to diagnose and fix when you’re trying to track them down at runtime; Rust prevents this problem by refusing to compile code with data races!
	  hl-page:: 91
	  ls-type:: annotation
	  id:: 6232da25-f57c-4c84-b006-9b1fd4b0892b
	- also cannot have a mutable reference while we have an immutable one to the same value. Users of an immutable reference don’t expect the value to suddenly change out from under them! However, multiple immutable references are allowed because no one who is just reading the data has the ability to affect anyone else’s reading of the data.
	  hl-page:: 92
	  ls-type:: annotation
	  id:: 6232da4a-65ae-4663-b5fa-97fa7c086eeb
	- _dangling pointer_ --a pointer thatreferences a location in memory that may have been given to someone else--by freeing some memory while preserving a pointer to that memory.
	  hl-page:: 93
	  ls-type:: annotation
	  id:: 6232da7b-7ee4-41db-8072-8ac0c8ee5229
-
- ### Rules of Reference #mgm
	- * At any given time, you can have either one mutable reference or any number of immutable references.
	  * References must always be valid.
-
- ### String Slice
- A string slice is a reference to part of a **String**
  ls-type:: annotation
  hl-page:: 98
  id:: 6232dd6a-d95a-45f2-90b0-513478d0f05f
- String Literals Are Slices
  ls-type:: annotation
  hl-page:: 101
  id:: 6232dde0-fec8-42fd-8582-340d354d45c4
-
- # Structs
- we used the owned String type rather than the &str string slice type. This is a deliberate choice because we want each instance of this struct to own all of its data and for that data to be valid for as long as the entire struct is valid.
  hl-page:: 109
  ls-type:: annotation
  id:: 6232dee2-5b12-43c7-a36a-fd5679741096
-
- Rust does include functionality to print out debugging information, but we have to explicitlyopt in to make that functionality available for our struct. To do that, we add the outerattribute **#[derive(Debug)]** just before the struct definition
  ls-type:: annotation
  hl-page:: 116
  id:: 6232df79-37db-4045-af95-1ca1e513d8e4
-
- Another way to print out a value using the Debug format is to use the **dbg!** macro, whichtakes ownership of an expression, prints the file and line number of where that dbg! macrocall occurs in your code along with the resulting value of that expression, and returnsownership of the value.
  ls-type:: annotation
  hl-page:: 117
  id:: 6232dfd6-4c4a-42b2-8fc3-3d5ba1de839e
- # Method #[Method]
- The &self isactually short for self: &Self. Within an impl block, the type Self is an alias for the typethat the impl block is fo
  ls-type:: annotation
  hl-page:: 120
  id:: 6232e10f-179e-4a46-9d7f-39ed119bbe32
- We’ve chosen **&self** here for the same reason we used &Rectangle in the function version:we don’t want to take ownership, and we just want to read the data in the struct, not write toit. If we wanted to change the instance that we’ve called the method on as part of what themethod does, we’d use &mut self as the first parameter. #ownership
  hl-page:: 120
  ls-type:: annotation
  id:: 6232e143-f490-4252-b878-2c40618313a0
- #[Associated_Functions]
-
- All functions defined within an impl block are called *associated functions* because they’re associated with the type named after the impl. We can define associated functions that don’t have self as their first parameter (and thus are not methods) because they don’t need an instance of the type to work with. We’ve already used one function like this: the **String::from** function that’s defined on the String type.
  hl-page:: 123
  ls-type:: annotation
  id:: 6232e26a-2ef5-4e86-99f0-fcf6fdc4d9c2
- # Enum
- ```rust
  enumIpAddr 
  {        
    V4(String),
    V6(String),    
  }
  
  let home = IpAddr::V4(String::from("127.0.0.1"));
  ```
-
- ## Option
-
- When enum values have data inside them, you can use **match** or **if let** to extract and use those values
  hl-page:: 141
  ls-type:: annotation
  id:: 6233e039-44b0-47b7-9e27-6c5a71e3a258
-
- # Packages, Crates, Modules
	- * Packages: A Cargo feature that lets you build, test, and share crates
	  * Crates: A tree of modules that produces a library or executable
	  * Modules and **use**: Let you control the organization, scope, and privacy of paths
	  * Paths: A way of naming an item, such as a struct, function, or module
	-
- A crate is a binaryor library. 
  ls-type:: annotation
  hl-page:: 143
  id:: 6233e50a-a7da-4cbb-a674-62910bd3c366
	- The crate root is a source file that the Rust compiler starts from and makes up the root module of your crate
	  hl-page:: 143
	  ls-type:: annotation
	  id:: 6233e518-5d9e-4096-9aa2-1b46dcd73a67
- A package is one or more crates that provide a set offunctionality.
  hl-page:: 143
  ls-type:: annotation
  id:: 6233e8e1-d070-4a4b-b429-82853681ff3e
	- A package can contain at most one library crate. It can contain as many binary crates as you’d like, but it must contain at least one crate (either library or binary).
	  hl-page:: 143
	  ls-type:: annotation
	  id:: 6233e916-ba0d-4b52-af3c-b9f6fdc6569d
-
- # Common Collections
- ## Vector<T>
- A vector allows you to store a variable number of values next to each other.
  ls-type:: annotation
  hl-page:: 164
  id:: 6233ee44-de44-4fe9-be4e-576b53916ee3
-
- vec! macro for convenience 
  hl-page:: 165
  ls-type:: annotation
  id:: 6233ee6f-cb8d-45ed-b840-63027b428001
  ```rust
  let v = vec![1,2,3];
  ```
	- * Using an Enum to Store Multiple Types
	- hl-page:: 169
	  ls-type:: annotation
	  id:: 6233f388-dbc7-437c-8d38-4c04f803e43f
	  * vectors can only store values that are the same type.
- what types will be in the vector at compile time so it knows exactly howmuch memory on the heap will be needed to store each element.
  ls-type:: annotation
  hl-page:: 170
  id:: 6233f3d2-95e8-43d8-98ee-6799e656e439
-
- ## UTF-8 Encoded Text with String
-
- Rust has only one string type in the corelanguage, which is the string slice str that is usually seen in its borrowed form &str.
  ls-type:: annotation
  hl-page:: 171
  id:: 6233f53a-36de-4503-9b45-554610f57b16
- String literals, for example, are stored in the program’s binary and are therefore string slices.
  ls-type:: annotation
  hl-page:: 171
  id:: 6233f549-b94b-4ed4-9974-dd9818ba747c
	- The **String** type, which is provided by Rust’s standard library rather than coded into thecore language, is a growable, mutable, owned, UTF-8 encoded string type.
	  ls-type:: annotation
	  hl-page:: 171
	  id:: 6233f556-f2c7-41f8-b9d1-ea364880c29b
	- refer to “strings” in Rust, they usually mean the String and the string slice &str types, notjust one of those types. 
	  ls-type:: annotation
	  hl-page:: 171
	  id:: 6233f582-c346-4830-abcb-ab8c61671dd7
	- both String and string slices are UTF-8 encoded
	  ls-type:: annotation
	  hl-page:: 171
	  id:: 6233f58b-a896-4a77-a4b2-c2a1764e7e89
- "+" operator #ownership
	- ```rust
	  let s1 = String::from("Hello, ");
	  let s2 = String::from("world!");
	  let s3 = s1 + &s2; // note s1 has been moved here and can no longer be used
	  ```
	-
	- ```rust
	  fn add(self, s: &str) -> String{}
	  ```
-
- Rust strings don’t support indexing.
  ls-type:: annotation
  hl-page:: 175
  id:: 6233f721-4ddc-471f-9150-0a8098f8788f
	- A **String** is a wrapper over a **Vec<u8>**.
	  hl-page:: 175
	  ls-type:: annotation
	  id:: 6233f742-87f1-46f7-87b5-8c0b3cb1651a
	- because each Unicode scalar value in that string takes 2 bytes of storage. Therefore, an index into the string’s bytes will not always correlate to a valid Unicode scalar value.
	- A final reason Rust doesn’t allow us to index into a String to get a character is that indexing operations are expected to always take constant time (O(1)). But it isn’t possible to guarantee that performance with a String, because Rust would have to walk through the contents from the beginning to the index to determine how many valid characters there were.
	  hl-page:: 177
	  ls-type:: annotation
	  id:: 6233f79e-699b-4104-84af-97333843b34b
	-
- # HashMap<K,V>
	- For types that implement the Copy trait, like i32, the values are copied into the hash map.For owned values like String, the values will be moved and the hash map will be the owner of those values #ownership
	  hl-page:: 181
	  ls-type:: annotation
	  id:: 6233fa6e-8794-4c9f-87d8-dcabb9b847a0
	- If we insert references to values into the hash map, the values won’t be moved into the hashmap. The values that the references point to must be valid for at least as long as the hashmap is valid. #ownership
-
- # Error Handle
- The **?** operator can only be used in functions that have a return type compatible with the value the ? is used on. This is because the ? operator is defined to perform an early return of a value out of the function
  hl-page:: 200
  ls-type:: annotation
  id:: 6233fde6-e3bf-4804-8ca5-6f7644ac7efe
-
- # Generics
- Rust accomplishes this by performing monomorphization of the code that is using genericsat compile time. Monomorphization is the process of turning generic code into specific codeby filling in the concrete types that are used when compiled.
  ls-type:: annotation
  hl-page:: 221
  id:: 6233ff97-23ee-4722-a195-c901030350bb
-
- Rust compiles generic code into code that specifies the type in each instance, we pay no runtime cost for using generics. When the code runs, it performs just as it would if we had duplicated each definition by hand. The process of monomorphization makes Rust’s generics extremely efficient at runtime.
  hl-page:: 222
  ls-type:: annotation
  id:: 6233ffb7-99dc-483d-b1c1-fc3c762819b1
-
- # Traits
- A trait tells the Rust compiler about functionality a particular type has and can share withother types. We can use traits to define shared behavior in an abstract way. 
  ls-type:: annotation
  hl-page:: 223
  id:: 6233ffd8-f81d-4d4c-9081-b98178077e4e
- Clearer Trait Bounds with **where** Clauses
  hl-page:: 229
  ls-type:: annotation
  id:: 623400ef-1372-4e21-97a2-592dcdbc43c7
	- ```rust
	  fn some_function<T,U>(t: &T, u: &U) -> i32
	     where T: Display + Clone
	  		 U: Clone + Debug
	  ```
-
-
- We can also use the **impl Trait** syntax in the return position to return a value of some type that implements a trait
  hl-page:: 229
  ls-type:: annotation
  id:: 6234014d-7553-4b3d-b885-f80ab8d47808
	- ```rust
	  fn returns_function() -> impl Summary{}
	  ```
	-
	- you can only use impl Trait if you’re returning a single type
	  ls-type:: annotation
	  hl-page:: 230
	  id:: 62340199-2896-4b3c-87fb-b442df1b6491
- ## LifeTime #ownership
	- every reference in Rust has a **lifetime**, which is the scope for which that reference is valid.Most of the time, lifetimes are implicit and inferred, just like most of the time, types are inferred.
	  ls-type:: annotation
	  hl-page:: 236
	  id:: 623402df-afe6-4051-90e1-2c094769f904
	- Lifetime annotations don’t change how long any of the references live. Just as functions can accept any type when the signature specifies a generic type parameter, functions can accept
	- the names of lifetime parameters must start with an apostrophe (**'**) and are usually all lowercase and very short, like generic types.Most people use the name **'a**.
	  hl-page:: 240
	  ls-type:: annotation
	  id:: 62340426-8a67-4cec-b844-e46628b139ae
-
- The patterns programmed into Rust’s analysis of references are called the *lifetime elision rules* .
  hl-page:: 246
  ls-type:: annotation
  id:: 62342a4d-4d71-4f1a-a088-bf98b7f10c13
-
- The compiler uses three rules to figure out what lifetimes references have when there aren’t explicit annotations.
  hl-page:: 246
  ls-type:: annotation
  id:: 62342abe-73ad-4b9f-a5c7-6bf774c09af6
	- The first rule is that each parameter that is a reference gets its own lifetime parameter. In other words, a function with one parameter gets one lifetime parameter
	- The second rule is if there is exactly one input lifetime parameter, that lifetime is assigned to all output lifetime parameters:
		- ``` rust
		  fn foo<'a>(x: &'a i32) -> &'a i32
		  ```
	-
	- The third rule is if there are multiple input lifetime parameters, but one of them is **&self** or **&mut** self because this is a method, the lifetime of self is assigned to all output lifetime parameters.
-
- # Iterators, Closures
- Closures, a function-like construct you can store in a variable
  ls-type:: annotation
  hl-page:: 320
  id:: 62342e6e-157c-41a5-9f9f-3a8429b643da
- Iterators, a way of processing a series of elements
  ls-type:: annotation
  hl-page:: 320
  id:: 62342e79-9b7c-437e-b2ce-653536f1c086
- ## Closure
- Closure definitions will have one concrete type inferred for each of their parameters and for their return value.
  ls-type:: annotation
  hl-page:: 327
  id:: 62343f78-dd0b-4037-ab43-b4e7da78783f
- Closures can capture values from their environment in three ways, which directly map to the three ways a function can take a parameter: taking ownership, borrowing mutably, and borrowing immutably. These are encoded in the three Fn traits as follows: #ownership
  hl-page:: 333
  ls-type:: annotation
  id:: 62344225-5677-41ec-b20e-f6d243de7dcf
	- **FnOnce** consumes the variables it captures from its enclosing scope, known as the closure’s environment. To consume the captured variables, the closure must take ownership of these variables and move them into the closure when it is defined. The **Once** part of the name represents the fact that the closure can’t take ownership of the same variables more than once, so it can be called only once. 
	  hl-page:: 333
	  ls-type:: annotation
	  id:: 62344248-3ae2-4829-abb8-e5a206bbb6ab
	- **FnMut** can change the environment because it mutably borrows values.
	- **Fn** borrows values from the environment immutably.
-
- If you want to force the closure to take ownership of the values it uses in the environment, you can use the **move** keyword before the parameter list. This technique is mostly useful when passing a closure to a new thread to move the data so it’s owned by the new thread. #ownership
  hl-page:: 333
  ls-type:: annotation
  id:: 623443ce-d832-4e85-b381-b97595be82b9
-
- ## Iterator
- ```rust
  #[test]
  fn iterator_demonstration() {
    let v1 = vec![1, 2, 3];
    let mut v1_iter = v1.iter();
    assert_eq!(v1_iter.next(), Some(&1));
    assert_eq!(v1_iter.next(), Some(&2));
    assert_eq!(v1_iter.next(), Some(&3));
    assert_eq!(v1_iter.next(), None);    
  }
  ```
- Note that we needed to make v1_iter mutable: calling the **next** method on an iterator changes internal state that the iterator uses to keep track of where it is in the sequence.
  hl-page:: 337
  ls-type:: annotation
  id:: 62344480-ce5f-44ad-8187-26ee6fd3e7ef
	-
	- We didn’t need to make v1_iter mutable when we used a for loop because the loop took ownership of v1_iter and made it mutable behind the scenes.
	  ls-type:: annotation
	  hl-page:: 337
	  id:: 623444b8-eba7-4984-a36d-2cd27453f2e9
-
- iterator adaptors are lazy, and we need to consume theiterator here.
  ls-type:: annotation
  hl-page:: 339
  id:: 62344547-f618-413d-b1b4-2c69b14376b7
-
- ### Performance Loops vs Iterators #performance
-
- The point is this: iterators, although a high-level abstraction, get compiled down to roughly the same code as if you’d written the lower-level code yourself.
  hl-page:: 350
  ls-type:: annotation
  id:: 62344769-9b8b-4cd6-96f4-c03b97c93c8f
- Iterators are one of Rust’s zero-cost abstractions, by which we mean using the abstraction imposes no additional runtime overhead.
  hl-page:: 350
  ls-type:: annotation
  id:: 62344789-a982-48fe-ab77-7a621bc26605
	- > In general, C++ implementations obey the zero-overhead principle: What you don’t use,you don’t pay for. And further: What you do use, you couldn’t hand code any better.
	-
-
- Rust knows that there are 12 iterations, so it “unrolls” the loop. 
  hl-page:: 351
  ls-type:: annotation
  id:: 62344b9d-fd3e-4242-b4d8-5d98a0fd29d1
	- > Unrolling is an optimization that removes the overhead of the loop controlling code and instead generates repetitive code for each iteration of the loop.
-
- ## Smart Points
- The most common kind of pointer in Rust is a reference
  hl-page:: 376
  ls-type:: annotation
  id:: 62344cf5-d6b3-42f5-989f-b8d2fcac76f2
	- References are indicated by the &symbol and borrow the value they point to.
	  ls-type:: annotation
	  hl-page:: 376
	  id:: 62344d42-157b-4ae6-a4d8-716dc54d5788
-
- Smart pointers, on the other hand, are data structures that not only act like a pointer but also have additional metadata and capabilities.
  hl-page:: 376
  ls-type:: annotation
  id:: 62344e3e-cb33-4f00-a310-5f0a8336093f
	- In Rust, the different smart pointers defined in the standard library provide functionality beyond that provided by references. One example that we’ll explore in this chapter is the reference counting smart pointer type. This pointer enables you to have multiple owners of data by keeping track of the number of owners and, when no owners remain, cleaning up the data.
	  hl-page:: 376
	  ls-type:: annotation
	  id:: 62344e61-a8cc-4474-8a27-9bd8db82a378
-
- Smart pointers are usually implemented using structs. 
  ls-type:: annotation
  hl-page:: 376
  id:: 62344e91-8f3f-49aa-84b0-4298a6023f9f
-
- The characteristic that distinguishes a smart pointer from an ordinary struct is that smart pointers implement the **Deref** and **Drop** traits.
  hl-page:: 376
  ls-type:: annotation
  id:: 62344ea5-1d5f-4bda-9a0a-941e8a44dea1
-
	- The **Deref** trait allows an instance of the smart pointer struct to behave like a reference so you can write code that works with either references or smart pointers.
	  hl-page:: 376
	  ls-type:: annotation
	  id:: 62344ef1-154d-4646-ab34-e55d6227462b
	-
	- The **Drop** trait allows you to customize the code that is run when an instance of the smart pointer goes out of scope.
	  hl-page:: 376
	  ls-type:: annotation
	  id:: 62344f19-c415-4bc9-94b9-ece45278298e
-
- most common smart pointers in the standard library:
  hl-page:: 376
  ls-type:: annotation
  id:: 62344f41-ca1d-4ba8-bf17-f822a33a063f
	- **Box<T>** for allocating values on the heap
	- **Rc<T>**, a reference counting type that enables multiple ownership
	- **Ref<T>** and **RefMut<T>**, accessed through **RefCell<T>**, a type that enforces the borrowing rules at runtime instead of compile time
-
- #### Box<T>
	- ```rust
	  let b = Box::new(5);
	  ```
	- Boxes allow you to store data on the heap rather than the stack. What remains on the stack is thepointer to the heap data.
	  ls-type:: annotation
	  hl-page:: 378
	  id:: 62345169-4a36-445d-b8b2-63b504967a62
-
	- Boxes don’t have performance overhead, other than storing their data on the heap instead of on the stack. But they don’t have many extra capabilities either. You’ll use them most often in these situations: 
	  hl-page:: 378
	  ls-type:: annotation
	  id:: 62345184-ec95-4d8b-acf0-f6ebab140b6e
		- * When you have a type whose size can’t be known at compile time and you want to use a value of that type in a context that requires an exact size
		  * When you have a large amount of data and you want to transfer ownership but ensure the data won’t be copied when you do so
		  * When you want to own a value and you care only that it’s a type that implements a particular trait rather than being of a specific type
-
- One type whose size can’t be known at compile time is a _recursive type_, where a value can have as part of itself another value of the same type.
  hl-page:: 379
  ls-type:: annotation
  id:: 62345226-c7a8-46e9-8fe5-76ef995627c8
	- ```rust
	  enum List {
	    Cons(i32, List),
	    Nil
	  }
	  let list = Cons(1, Cons(2,Const(3, Nil)));
	  
	  ```
-
	- Most of the time when you have a list of items inRust, **Vec<T>** is a better choice to use. Other, more complex recursive data types are useful in various situations, but by starting with the cons list, we can explore how boxes let us define a recursive data type without much distraction.
	  hl-page:: 379
	  ls-type:: annotation
	  id:: 62345322-2f3e-4b09-9498-26252cc48cf1
	- ``` rust
	  enum List {
	    Cons(i32, Box<List>),
	    NIl,
	  }
	  let list = Cons(1,Box::new(Cons(2, Box::new(Cons(3, Box::new(nil))))));
	  ```
		- Because a **Box<T>** is a pointer, Rust always knows how much space a Because a **Box<T>** is a pointer, Rust always knows how much space a **Box<T>** needs: a pointer’s size doesn’t change based on the amount of data it’s pointing to.  needs: a pointer’s size doesn’t change based on the amount of data it’s pointing to.
-
	- Boxes provide only the indirection and heap allocation;
	  ls-type:: annotation
	  hl-page:: 383
	  id:: 623453f2-8fb3-404b-802e-4df5e5309e1e
	-
- The **Box<T>** type is a smart pointer because it implements the **Deref** trait, which allows **Box<T>** values to be treated like references. When a **Box<T>** value goes out of scope, the heap data that the box is pointing to is cleaned up as well because of the Drop trait implementation.  #mgm
  hl-page:: 384
  ls-type:: annotation
  id:: 6234540d-19a3-405b-a5ca-df93a7a52c10
-
- Using Box<T> Like a Reference
  ls-type:: annotation
  hl-page:: 386
  id:: 6236e6c6-07b7-40c3-9b11-f5a01a5e644b
-
- Rust substitutes the ** * ** operator with a call to the **deref** method and then a plain dereference so we don’t have to think about whether or not we need to call the **deref** method. This Rust feature lets us write code that functions identically whether we have a regular reference or a type that implements Deref.
  hl-page:: 389
  ls-type:: annotation
  id:: 6236e6f3-6dbf-49ae-9e76-6af5fdc05327
- The (*m) dereferences the MyBox<String> into a String
  ls-type:: annotation
  hl-page:: 390
  id:: 6236e73b-5a99-4f51-a720-7c6e8e724d70
	- ```rust
	  let m = MyBox::new(String::from("Rust"))
	  hello(&(*m)[..])
	  
	  ```
-