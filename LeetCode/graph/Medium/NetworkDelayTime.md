Network Delay Time
..................

https://leetcode.com/problems/network-delay-time/

```
class Solution {
public:
    int networkDelayTime(vector<vector<int>>& times, int N, int k) {
        
        
        unordered_map<int,list<pair<int,int>>> graph;
        
        for(vector<int>&x:times){
            graph[x[0]].push_back({x[1],x[2]});
        }
        unordered_map<int ,int > dis;
        
         for(int i=1;i<=N;i++){
            dis[i] = INT_MAX ;
        }
        dis[k]=0;
        
        set<pair<int,int>>closest;
        closest.insert({0,k});
        
        while(closest.size()>0)
        {
            
            int curr_node= (*(closest.begin())).second ;
            int curr_dist= (*(closest.begin())).first ;
 
            closest.erase(closest.begin());
            
            for(auto childPair:graph[curr_node])
            {
                if(curr_dist+childPair.second < dis[childPair.first])
                {
                    int child_node=childPair.first;
                    
                    if(closest.find({dis[child_node],child_node})!=closest.end())
                    {
                        closest.erase({dis[child_node],child_node});
                    }
                    dis[child_node]=curr_dist+childPair.second;
                    closest.insert({dis[child_node],child_node});
                }
            }
        }
        
        int res=-1;
         for(auto x:dis){
            res = max(res,x.second);
        }
        return res==INT_MAX?-1:res; 
    }
};

```