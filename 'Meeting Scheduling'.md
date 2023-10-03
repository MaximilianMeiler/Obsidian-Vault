https://leetcode.ca/all/253.html


How do we find the max amount of mutually compatible meetings?
- Earliest start time?
- Shortest?
- Least conflicting?
- Earliest end time is the way to go
	- Take each meeting, from shortest to longest, provided that it's compatible with what's already taken
Why is this problem greedy?
- Picking smaller meets first maximizes the amount of unscheduled time remaining

Now expand to multiple rooms simultaneously
- Sort meetings in increasing start time
- Iterate, assigning a room if possible and opening a new one if not
- ![[Pasted image 20230918095719.png]]

Minimizing lateness
- Each meeting has a length and a "must-be-finished-by" time
- Sorting by ascending meeting time, deadline-length don't work
- Instead, sort by earliest deadline first
	