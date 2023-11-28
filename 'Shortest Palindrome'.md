https://leetcode.com/problems/shortest-palindrome/


Find the largest palindromic segment that starts at the beginning
- Run the failure function on the string concat w/ itself backwards
	- filler item in middle
	- Return the last value
	- Failure func matches prefix with suffix - this allows us to determine if the given index is palindromic in this case