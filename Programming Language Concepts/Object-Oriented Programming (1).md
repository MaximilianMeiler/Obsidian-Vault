Previous lecture: [[Overview]]


#### Principles
- Abstraction
- Encapsulation
- Inheritance
- Polymorphism

#### Classes
- Contain properties (data) and methods (functions)
	- Properties should be private/protected (able to be accessed by inherited classes), and accessed/updated with a getter/setter
- Created with a constructor
- Keywords
	- `extends` - used for inheritance (`Square extends Rectangle`)
	- `abstract` - defines a polymorphic superclass or method (must be subclassed to be used)
	- `final` - const equivalent
		- cannot change an initialized property variable
		- cannot overwrite a method
		- cannot extend a class
	- `static` - class-level item, rather than being instance-specific
- Object instances are references, not pointers

#### Interfaces
- Simulate multiple inheritance - can be a child of multiple superclasses
- Properties are `static` and `final`
- No constructor
- `implements` is used to define a subclass to an interface
- Weak: subclass inheriting an interface

#### Dynamic Dispatch
- `shape rect = new Rectangle(2, 3, "blue")` 
  `rect.area()`
	- In C++, the variable type (shape) determines which method to call
	- In Java, the object reference determines which reference to call

For primitive types, `==` just compares value
- For object types, `==` compares memory location - use .equals() instead!


Next lecture: [[Regular Expressions (2)]]