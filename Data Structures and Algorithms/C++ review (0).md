Previous lecture: N/A
1 2 3
9 18 17
Preprocessor directives
- \#include: directive replaced with content of specified file
- \#define: replaces all instances of identifier w replacement
- \#ifdef/ifndef/endif: allows sections to (not) be compiled if an identifier isn't defined
- \#pragma once: includes a source file only once during compilation (\*)

Data types
- 1 byte: char, bool
- 4 bytes: float, int (-2bil to 2bil, 0 to 4bil if unsigned)
- 8 bytes: double, long (-9quint to 9quint, 0 to 18quint if unsigned)

Type derivation
- `auto x = 5` : x will be assumed of type int
- `decltype(x) = 5` : same thing

Control flow
- If/else
- Switch/case
	- `switch(str) {
		  `case "red":
			  `// action
			  `break;
	  `}
- while/for loops

Pointers
- Declaration: `int* x`, or `int *x`
- '&' gets the memory address of a variable
- * gets the value at a given memory address
- Arrays are just pointers
	- `int numbers[5]
	  `int *num_ptr = numbers
- You can add/subtract from a pointer to access adjacent memory addresses
	- `*(num_ptr + 2) //gets third element of numbers`

Arrays
- Declaration & Initialization: `datatype name[size] = {val1, val2, ...}`
- Access elements with \[]
- 2d arrays: `int grid[4][5] //just use an additional []`
- For functions, pass the address of the start of the array
	- The length of all arrays but the first, in nested arrays, must be specified
		- `void print(int arr[][3]) {}`

Dynamic memory
- Want to make a dynamically resizing array? You don't know how much memory it will use!
- The `new` keyword returns a pointer to that datatype
	- `int *foo_ptr = new int(3);`
	- `int *foo_arr = new int[userInput];*`
- You must also use `delete` to later free this memory
	- `delete foo_ptr;`
	- `delete[] foo_arr;`

Functions
- Remember to pass by reference (&) or pointer, or else parameters will be copied!

Structs & Classes
- Create objects
- Struct members are public by default, class members are private by default

Templates
- Create generic data type functions/classes
- Just type `template <typename T>` before a class/function that uses it
	- For classes, just do it once above the entire class def, once above the dec

Const
- Disallows variable change
- `int* const x` : constant pointer (locks memory address)
- `const int* x` or `int const * x` : constant value 
- When added at the end of class functions, it disallows class mutation
	- `int getLength() const {}`
	- Const objects can only call const functions
- When a class member is const, it can only be initialized through an initializer list
	- `rectangle(int l, int w) : length(l), width(w) {}`