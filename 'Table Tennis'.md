https://codeforces.com/problemset/problem/879/B

Note that k is much larger than n
- If k is greater than n, the person with max power just wins

Take the max from the front of the array, up to k + 1 (?)
- If the max is replaced, turn the max iteration to k + x (+ 1)?
- If x ever exceeds n, just return the max