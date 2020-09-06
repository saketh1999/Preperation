Given an array of integers nums and and integer target, return the indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

example:
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1]


```
#include <vector>
using namespace std;

vector<int> twoNumberSum(vector<int> array, int targetSum) {
  // Write your code here.
	for(int i=0;i<array.size();i++)
	{
		vector<int>::iterator it;
		
		int rest=targetSum-array[i];
		
		it=find(array.begin()+i+1,array.end(),rest);
		
		if(it!=array.end())
		{
			vector<int>sol;
			sol.push_back(array[i]);
			sol.push_back(rest);
			return sol;
		}
	}
  return {};
}
```