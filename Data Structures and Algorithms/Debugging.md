[[Lists, Stacks, Queues (3)]]


Using a debugger allows you to
- Understand how a program used
- Check over memory
- Avoid guess-and-check
How to use a debugger
- Breakpoints: pauses code execution on the corresponding line
- Step into: steps into an operation's implementation
- Step over: Runs the next line of code
- Step out:

Testing with Catch2
- Included through header
- Uses assertions / unit tests
	- Tests autoregister themselves
- Usage
	- `#define CATCH_CONFIG_MAIN` <- add this to main.cpp
	- `#include catch.hpp` <- add to all tested files
	- `TEST_CASE("title", "tagi1") {
		  `REQUIRE(true)
	  `}`