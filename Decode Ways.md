https://leetcode.com/problems/decode-ways/

- dp\[0] = 1
- dp\[1] = 1 if a\[0] > 0, 0 if a\[0] = 0
for dp\[i]...
- add dp\[i - 1] if the 1 last char is valid
- add dp\[i - 2] if the 2 last chars are valid