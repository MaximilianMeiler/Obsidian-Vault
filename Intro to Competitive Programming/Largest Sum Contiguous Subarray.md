-2 1 5 6 -3 10 -5 3

Kadane's algorithms solves this in O(n) time
- With one element, max sum is that element
- With two, add them both or just take one

- Keep adding element by element. 
- Keep the value of the currently highest subarray
	- If this val is ever higher than a global max, update the global max


int maxSum = 0, currentSum = 0;
for (int i = 0; i < n; i++) {
	currentSum = max(a[i], currentSum + a[i]);
	maxSum = max(currentSum, maxSum);
}

Extension:
[[Maximum Sub-sequence Product]]