https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=102


Bounded Knapsack
- Customer has finite coins, but the cashier has infinite
- A total transaction factors in both coins given and coins returned
- Redefine coins : 1, 2, 4, 10, 20, 40
- Max transaction size: $5
	- Use a dp array to find the min number of customer's coins for every change (bounded)
	- Use a dp array to find the min number of cashier's coins for every change (unbounded)
- Check the customer's coin count for the given input
	- Then, iterate upward (make the customer give more coins)
		- If this value + the cashier's val for the difference is a min, update the min
		- Ex. compare a desired 105c from the customer vs. 110c from the customer & 5c from the cashier
