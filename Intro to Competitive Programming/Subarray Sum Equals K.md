https://leetcode.com/problems/subarray-sum-equals-k/


Check how many subarrays sum up to K
Negative numbers can be involved!

Use prefix sum with a hashmap to store how many indices certain prefix sums occur on
- At each index, current prefixSum - K = a possible previous prefix sum
	- If this is the case, add the number of occurrences of this sum to a total