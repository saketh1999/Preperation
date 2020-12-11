All Paths From Source to Target
...............................
https://leetcode.com/problems/all-paths-from-source-to-target/

```
class Solution {
public:
    vector<vector<int>> res;
    void dfs(vector<vector<int>>& graph,vector<int>store,int l,int n)
    {
        store.push_back(l);
        
        if(l==n)
        {
            res.push_back(store);
            return;
        }
        for(int i=0;i<graph[l].size();i++)
        {
            dfs(graph,store,graph[l][i],n);
        }
            
    }
    vector<vector<int>> allPathsSourceTarget(vector<vector<int>>& graph) {
        if(graph.size()==0)
            return res;
       
        int n=graph.size()-1;
        vector<int>store;
        
         if(graph[0].size()==0)
            return res;
        
        dfs(graph,store,0,n);
        return res;
    }
};

```