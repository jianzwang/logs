- Deref coercion was added to Rust so that programmers writing function and method calls don’t need to add as many explicit references and dereferences with & and *. The deref coercion feature also lets us write more code that can work for either references or smart pointers.
- you can use the **DerefMut trait** to override the * operator on mutable references.
- Rust does deref coercion when it finds types and trait implementations in three cases:
  * From &T to &U when T: Deref<Target=U> 
  * From &mut T to &mut U when T: DerefMut<Target=U>
  * From &mut T to &U when T: Deref<Target=U>
	-
	- immutable references will never coerce to mutable references.Because of the borrowing rules, if you have a mutable reference, that mutable referencemust be the only reference to that data #ownership
	- Converting one mutable reference to one immutable reference will never break the borrowing rules.
	- Converting an immutable reference to a mutable reference would require that the initial immutable reference is the only immutable reference to that data, but the borrowing rules don’t guarantee that
-