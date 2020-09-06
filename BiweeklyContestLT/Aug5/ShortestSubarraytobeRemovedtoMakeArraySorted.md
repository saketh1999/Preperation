1574. Shortest Subarray to be Removed to Make Array Sorted

https://leetcode.com/problems/shortest-subarray-to-be-removed-to-make-array-sorted/

Given an integer array arr, remove a subarray (can be empty) from arr such that the remaining elements in arr are non-decreasing.

A subarray is a contiguous subsequence of the array.

Return the length of the shortest subarray to remove.

 

Example 1:

Input: arr = [1,2,3,10,4,2,3,5]
Output: 3
Explanation: The shortest subarray we can remove is [10,4,2] of length 3. The remaining elements after that will be [1,2,3,3,5] which are sorted.
Another correct solution is to remove the subarray [3,10,4].
Example 2:

Input: arr = [5,4,3,2,1]
Output: 4
Explanation: Since the array is strictly decreasing, we can only keep a single element. Therefore we need to remove a subarray of length 4, either [5,4,3,2] or [4,3,2,1].
Example 3:

Input: arr = [1,2,3]
Output: 0
Explanation: The array is already non-decreasing. We do not need to remove any elements.
Example 4:

Input: arr = [1]
Output: 0

Constraints:

1 <= arr.length <= 10^5
0 <= arr[i] <= 10^9



Solution
.........

```
class Solution {
public:
    int findLengthOfShortestSubarray(vector<int>& arr) {
        int n = arr.size(), start = -1;
        vector<int> arr1;
		// inserting -1 and INT_MAX to avoid extra checking for first and last element
        arr1.push_back(-1);
        for(int i=0;i<n;i++)
            arr1.push_back(arr[i]);
        arr1.push_back(INT_MAX);
        for(int i=1;i<=n;i++) {
            if(arr1[i] < arr1[i-1]) {
                start = i-1;
                break;
            }
        }
        if(start==-1) return 0; // all the cases in which array is sorted is handled from here. 
        int ans = n+1, end = n;
        while(start>=0 && end>start) {
            if(arr1[end] >= arr1[start] && arr1[end]<=arr1[end+1]) {
                end--;
            } else {
                ans= min(end-start, ans);
                start--;
            }
        }
        return ans;
    }
};

```

