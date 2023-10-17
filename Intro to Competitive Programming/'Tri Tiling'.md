https://open.kattis.com/problems/tritiling


Break it down into source configurations
- You can either take away 2 width using 3 horizontal dominoes
- Or take away 1 width, with 1 extra top/bottom removed
	- This then can be solved by evening the width (taking 2 total)
	- Or pushing back the removal w/ 3 horizontal dominoes

Dp calls - width index, bool if edge is flat
- `dp(i,0) = dp(i-2,0) + 2dp(i-1,1)
- `dp(i,1) = dp(i-1,0) + dp(i-2,1)
Base cases
- dp(0,0) = 1, dp(0,1) = impossible
- dp(1,0) = impossible, dp(1,1)  = 1