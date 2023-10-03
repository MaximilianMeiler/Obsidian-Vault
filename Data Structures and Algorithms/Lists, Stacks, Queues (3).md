Previous lecture: [[Algorithm Analysis (2)]]

List types:
- Array
- Vector
- List
- Forward-list

Data structures are a way to store and organize data
- Abstract data type 
	- Class of objects whose logical behavior is defined by a set of values and operations

Lists
- Properties
	- Ordered collection of data
		- Elements are given positions
	- Linear structure
	- Can have a set size or grow/shrink
- Examples
	- Array
		- Fixed size
		- Stores similar elements
		- Contiguous storage of elements in memory
		- Allows random access
		- Operations - adding, removal
		- ![[Pasted image 20230905142935.png]]
		- Constant access time, but slow to add to front
			- arr\[i] = arr + (i * sizeOf(type))
	- Singly-linked list
		- ![[Pasted image 20230905144256.png]]
		- Consists of nodes
		- Stores similar elements
		- Elements link to each other in memory but are non-contiguous
		- Does not allow random access
		- Singly-linked:![[Pasted image 20230905144429.png]]
			- Note: AddBefore and AddAfter take in references to existing nodes
		- Singly-linked w/ tail:![[Pasted image 20230907141501.png]]
		- Doubly-linked:![[Pasted image 20230907141520.png]]
	- Arrays vs linked lists:
		- List size: Arrays are fixed size, llists are not
		- Element size: Arrays sore just element, llists also store pointers
		- Access: Arrays are constant time, llists are linear time
		- Adding and removing: Arrays have to move elements, llists are constant "if the iterator is where you want it"
	- std::vector
		- Dynamic size, implemented through arrays
	- std::list
		- Implemented as a doubly-linked list
		- To iterate: `for(list<int>::iterator it = mylist.begin(); it != mylist.end(); ++it)`

Iterators
- Variables to keep track of where we are in a data set
- Iterator class:
	- Operators to advance to next data (++)
	- Dereference to access data (\*)
	- Operators to compare two iterators (!=)
	- Assignment operator (=)
- Main structure iterated over:
	- begin() method
		- `return Iterator(arr)`
		- Points to the first element
	- end() method
		- `return Iterator(arr + SIZE)`
		- This points past the array, not to the last element
- ![[Pasted image 20230907143920.png]]
	- Forward iterator: can only ++, not --
		- ex. forward_list in c++
	- Bidirectional iterator: 
		- ex. list in c++

Stacks
- Data
		- Items
		- Capacity
		- \*Top
- Operations
	- Push
	- Pop
	- Peek
	- Size
	- isEmpty
- Implementation through array
	- Fixed size
	- Access front thru index
	- All operation complexities are constant
- Implementation using linked list
	- Dynamic size
	- Access front thru pointer (point down the stack)
	- App operation complexities are constant
	- Random access
- Use cases
	- Call stack
	- Problems (check palindrome, balanced parenthesis)
	- Undos
	- Pringles
	- Dijkstra's two-stack
		- Used to evaluate numerical expressions
		- Push values onto one stack, operators onto another
			- Right parenthesis: pop operator and two values, evaluate and push result onto values
	- Postfix expression evaluation

Queues
- First in first out
- Data
	- Items
	- Number of items
	- Front pointer
	- Back pointer
- Operations
	- Enqueue
	- Dequeue
	- Size
	- isEmpty
- Implementation using array
	- Fixed size
	- Operations O(1)
	- Rightward drift problem
- Implementation using circular array
	- Ability to enqueue back into the front of the array where elements have been removed from
- Implementation using Linked List
	- Variable size
- Usage
	- OS task scheduling

[[Fast/Slow pointers]]


Next lecture: [[Trees (4)]]