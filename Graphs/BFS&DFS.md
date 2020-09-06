Here we will See how to create a graph as an adjacent list.
Then how to traverse using bfs and dfs .


```
class graph{
    int vectices;
    map<int ,vector<int>>mp;

    public:
    graph(int v)
    {
        vectices=v;

    }
    int addvertices(int V)
    {
        mp.insert(make_pair(V,vector<int>()));
    }
    int addedge(int u,int v)
    {
        mp[u].push_back(v);
        mp[v].push_back(u);
    }


}
int BFS(int v)
{
    vector<bool>visisted(vertices,false);
    queue<int>  q;
    v.push_back(v);
    visited[v]=true;
    while(q.empty!=false)
    {
        cout<<q.front();
        q.pop();
        vector<int>arr=mp[v];
        for(int i=0;i<arr.size();i++)
        {
            if(visited[arr[i]]==false)
            {
                visited[arr[i]]=true;
                q.push(v);
            }
        }
    }
}
int DFSutil(int v,vector<bool>visited)
{
    visited[v]=true;
    cout<<v;
    vector<int>arr=mp[v];
    for(int i=0;i<v.size();i++)
    {
        if(visited[arr[i]]==false)
        {
            DFSutil(arr[i],visited);
        }
    }
}
int DFS(int v)
{
    vector<bool>visited(vertices,false);
    DFSutil(v,visited);

}
int main()
{
 graph g(6);
    char vertices[6]= {1,2,3,4,5,6 } ;
    for(int i=0;i<6;i++)
{
    g.addVertices(vertices[i]);
}

g.addEdge(1, 2);
g.addEdge(1, 4);
g.addEdge(1, 5);
g.addEdge(2, 3);
g.addEdge(4, 5);
g.addEdge(5, 6);
g.addEdge(5, 3);
g.addEdge(3, 6);
g.BFS(1);
g.DFS(1);
}

```