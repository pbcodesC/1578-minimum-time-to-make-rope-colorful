# 1578-minimum-time-to-make-rope-colorful
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    int minCost(string colors, vector<int>& neededTime) {
        int n = colors.size();
        int totalTime = 0;
        int i = 0;

        while (i < n) {
            int j = i;
            int sum = 0;
            int maxTime = 0;

            // find group of same colors
            while (j < n && colors[j] == colors[i]) {
                sum += neededTime[j];
                maxTime = max(maxTime, neededTime[j]);
                j++;
            }

            // remove all except one (maxTime)
            totalTime += (sum - maxTime);

            // move to next color group
            i = j;
        }

        return totalTime;
    }
};
