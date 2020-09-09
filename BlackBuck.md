2 coding question from InterviewBit

1. Count of Range Sum

https://leetcode.com/problems/count-of-range-sum/

Explaination video : https://www.youtube.com/watch?v=ILUAY2W0s0E

```
class Solution {
public:
    int mergeSort(vector<long>& sum, int lower, int upper, int low, int high)
    {
        if(high-low <= 1) return 0;
        int mid = (low+high)/2, m = mid, n = mid, count =0;
        count =mergeSort(sum,lower,upper,low,mid) +mergeSort(sum,lower,upper,mid,high);
        for(int i =low; i< mid; i++)
        {
            while(m < high && sum[m] - sum[i] < lower) m++;
            while(n < high && sum[n] - sum[i] <= upper) n++;
            count += n - m;
        }
        inplace_merge(sum.begin()+low, sum.begin()+mid, sum.begin()+high);
        return count;
    }

    int countRangeSum(vector<int>& nums, int lower, int upper) {
        int len = nums.size();
        vector<long> sum(len + 1, 0);
        for(int i =0; i< len; i++) sum[i+1] = sum[i]+nums[i];
        return mergeSort(sum, lower, upper, 0, len+1);
    }
};
```

2. Gas Station
https://leetcode.com/problems/gas-station/

```
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int gs=0;
        int cos=0;
        int tank=0;
        int strt;
        for(int i=0;i<gas.size();i++)
        {
            gs+=gas[i];
            cos+=cost[i];
            tank+=gas[i]-cost[i];
            if(tank<0)
            {
                strt=i+1;
                tank=0;
            }
        }
        if(gs<cos)
            return -1;
        else 
            return strt;
    }
};

```