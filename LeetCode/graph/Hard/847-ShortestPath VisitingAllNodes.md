847. Shortest Path Visiting All Nodes
........................................

https://leetcode.com/problems/shortest-path-visiting-all-nodes/

-> Identify the node where to start the path from, the nodes having least number of edges will be the ideal starting points of our path.
-> Used Bitmasking to mark the visited nodes.
-> An array is maintained to store the path length upto the current node using a specific path.
-> Rest is the traditional BFS approach.

```
class Solution {
public:
    int shortestPathLength(vector<vector<int>>& A) {
       int n=A.size();       // size of the graph
    int vis_all= (1<<n)-1;  //bitmasking by left shiting ,basically multiplying with 2^n.
    
    vector<vector<int>>seen (n,vector<int>(1<<n,0));  // 2D vector for storing the states of each node
    queue<pair<int,int>>q;  // queue to store the node and state
    
    int mini=A[0].size(),x; //finding the node with the least edges => smallest vector for a give node
    for(int i=1;i<n;i++){
        x=A[i].size();
        mini=min(mini,x);
    }
    for(int i=0;i<n;i++){
        x=A[i].size();
        if(x==mini)q.push({i,1<<i});
    }
    
    int curr,path,next,nextpath,ans=INT_MAX;
    
    //bfs with bitmasking

    while(!q.empty()){
        curr=q.front().first;
        path=q.front().second;
        q.pop();
        
        if(path==vis_all){
            ans=min(ans,seen[curr][path]);
            continue;
        }
        
        for(int i=0;i<A[curr].size();i++){
            next=A[curr][i];
            nextpath= path | 1<<next;
            
            if(seen[next][nextpath])continue;
            
            seen[next][nextpath]=1+seen[curr][path];

            q.push({next,nextpath});
        }
        
    }
    return ans;
    }
};

```