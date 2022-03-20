public:: true
title:: RC<T>, the Reference Counted Smart Pointer

- ((6236efd9-20f8-4198-8d90-245352a3e6e4))
- To enable multiple ownership, Rust has a type called **Rc<T>**, which is an abbreviation for reference counting.
- The **Rc<T>** type keeps track of the number of references to a value to determine whether or not the value is still in use. If there are zero references to a value, the value can be cleaned up without any references becoming invalid.
- We use the Rc<T> type when we want to allocate some data on the heap for multiple parts of our program to read and we can’t determine at compile time which part will finish using the data last.
- **Cloning** an Rc<T> Increases the Reference Count