 Largest Rectangle in Histogram
 ................................


https://leetcode.com/problems/largest-rectangle-in-histogram/

https://www.youtube.com/watch?v=J2X70jj_I1o&list=PL_z_8CaSLPWdeOezg68SKkeLN4-T_jNHd&index=7

->In this question we need to find the Nearest lower to right for each element and store it in an array Right.
->Find the Nearest Lower to left for each element and store in an array left.
->Now find the difference for each element in the two arrays with respect to other and store in the array solution.
->Now multiply each element in the array sol with their correspoding heights and the maximum element in the array is the solution.


```

class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        if(heights.size()<=0)
            return 0;
        stack<pair<int,int>> st;
        vector<int> area;
        vector<int>left;
        vector<int>right;
        vector<int> sol;
        
        //finding the indices of the NSL
        
        int pseudoIndex=-1;
        
        for(int i=0;i<heights.size();i++)
        {
            if(st.empty())
                left.push_back(pseudoIndex);
            else if(st.size()>0 && st.top().first<heights[i])
            {
                left.push_back(st.top().second);
                
            }
            else if(st.size()>0 && st.top().first>=heights[i])
            {
                while(st.size()>0 && st.top().first>=heights[i])
                {
                    st.pop();
                }
                if(st.size()==0)
                {
                    left.push_back(pseudoIndex);
                }
                else
                {
                    left.push_back(st.top().second);
                }
            }
            
            st.push(make_pair(heights[i],i));
        }
        for(int i=0;i<left.size();i++)
            cout<<left[i]<<" ";
        //Finding the indices of NSR
        
        
          pseudoIndex=heights.size();
        
          
            while(st.size()>0)
                st.pop(); 
        
        for(int i=heights.size()-1;i>=0;i--)
        {
            if(st.empty())
                right.push_back(pseudoIndex);
            else if(st.size()>0 && st.top().first<heights[i])
            {
                right.push_back(st.top().second);
            }
            else if(st.size()>0 && st.top().first>=heights[i])
            {
                while(st.size()>0 && st.top().first>=heights[i])
                {
                    st.pop();
                }
                if(st.size()==0)
                    right.push_back(pseudoIndex);
                else
                {
                    right.push_back(st.top().second);
                }
            }
            st.push(make_pair(heights[i],i));
            
        }
        reverse(right.begin(),right.end());
        cout<<endl;
        for(int i=0;i<right.size();i++)
            cout<<right[i]<<" ";
        
        for(int i=0;i<right.size();i++)
            sol.push_back(abs(left[i]-right[i])-1);
         for(int i=0;i<right.size();i++)
            sol[i]*=heights[i];
        return *max_element(sol.begin(),sol.end());
        
        
    }
};
```