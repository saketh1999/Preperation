Trapping Rain Water
...................

https://leetcode.com/problems/trapping-rain-water/

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.


The above elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. Thanks Marcos for contributing this image!

Example:

Input: [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6

```
class Solution {
public:
   
    int trap(vector<int>& height) {
        if(height.size()==0)
            return 0;
          int n= height.size();
        vector<int> maxToLeft(n);
        vector<int> maxToRight(n);
        vector<int> water(n);
        int sol=0;
     
        maxToLeft[0]=height[0];
        
        for(int i=1;i<n;i++)
        {
            maxToLeft[i]=max(maxToLeft[i-1],height[i]);
        }
        
        maxToRight[height.size()-1]=height[height.size()-1];
        
        for(int i=n-2;i>=0;i--)
        {
            maxToRight[i]=max(maxToRight[i+1],height[i]);
        }
        for(int i=0;i<n;i++)
        {
            water[i]=min(maxToRight[i],maxToLeft[i])-height[i];
        }
        
        for(int i=0;i<n;i++)       
        {
            
            sol+=water[i];
        }
        return sol;
    }
};

```