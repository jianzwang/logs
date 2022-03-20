- ((6236f29d-1443-4250-acdf-fbd2f8a39fe3))
- Unlike Rc<T>, the RefCell<T> type represents single ownership over the data it holds. So,what makes RefCell<T> different from a type like Box<T>? Recall the borrowing rules youlearned in Chapter 4:
  
  * At any given time, you can have either (but not both of) one mutable reference or anynumber of immutable references.
  * References must always be valid.
- With references and Box<T>, the borrowing rules’ invariants are enforced at compile time. With RefCell<T>, these invariants are enforced at runtime. With references, if you break these rules, you’ll get a compiler error. With RefCell<T>, if you break these rules, your program will panic and exit.
- ((6236f349-14fa-435f-a858-e87a2844af9a))
-