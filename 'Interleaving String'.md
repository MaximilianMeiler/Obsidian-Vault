https://leetcode.com/problems/interleaving-string/


dp\[i]\[j] asks if it is possible to interleave s1\[0: i-1] and s2\[0: j-1] to get s3\[0: i + j - 1]

Simpler - see if new character (i/j) is the same as s3's last character
- If so, AND this with the previously associated entry in the 2d matrix
