https://onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=978


- Light returner should be as fast as possible
- When 2 people cross, they are bottlenecked by the slowest crosser

Analyze base cases:
- 1 or 2 people: send them over
- 3 people: Send the fastest with any person, send him back and everyone else over
	- Order of others doesn't matter, always (larger cross 1) + (larger cross 2) + (fast return)

More people presents choices after return (choose the faster one):
- Send slow people together
	- Fastest two cross
	- Fastest comes back
	- Two slowest cross
	- 2nd fastest comes back
- Send fast person with slow person
	- Fastest and slowest cross
	- Fastest comes back
	- Fastest and second slowest cross
	- Fastest comes back
Both of these cross the 2 slowest people, but either may be more efficient

This code doesn't work :(

    int y;  
    cin >> y;  
  
    for (int i = 0; i < y; i++) {  
        int n;  
        cin >> n;  
        deque<int> people;  
        vector<vector<int>> strat;  
        int ans = 0;  
  
        for (int x = 0; x < n; x++) {  
            int z;  
            cin >> z;  
            people.push_back(z);  
        }  
        sort(people.begin(), people.end());  
  
        while (!people.empty()) {  
            if (people.size() == 1) {  
                ans += people[0];  
                strat.push_back({people[0]});  
                break;  
            } else if (people.size() == 2) {  
                ans += people[1];  
                strat.push_back({people[0], people[1]});  
                break;  
            } else if (people.size() == 3) {  
                ans += people[0] + people[1] + people[2];  
                strat.push_back({people[0], people[2]});  
                strat.push_back({people[0]});  
                strat.push_back({people[0], people[1]});  
                break;  
  
            } else {  
                int slowGroup = people[1] * 2 + people[0] + people[people.size() - 1];  
                int fastGroup = people[people.size() - 1] + people[people.size() - 2] + 2 * people[0];  
                if (slowGroup < fastGroup) {  
                    ans += slowGroup;  
                    strat.push_back({people[0], people[1]});  
                    strat.push_back({people[0]});  
                    strat.push_back({people[people.size() - 1], people[people.size() - 2]});  
                    strat.push_back({people[1]});  
                } else {  
                    ans += fastGroup;  
                    strat.push_back({people[0], people[people.size() - 1]});  
                    strat.push_back({people[0]});  
                    strat.push_back({people[0], people[people.size() - 2]});  
                    strat.push_back({people[0]});  
                }  
                people.pop_back();  
                people.pop_back();  
            }  
        }  
  
        cout << ans << "\n";  
        for (int j = 0; j < strat.size(); j++) {  
            for (int k = 0; k < strat[j].size(); k++)  {  
                cout << strat[j][k] << " ";  
            }  
            if (j != strat.size() - 1) {cout << "\n";}  
        }  
  
        if (i != y - 1) {cout << "\n";}  
  
    }  
  
`}				