BFS & DFS
...........


```
#include <iostream>
#include <bits\stdc++.h>

using namespace std;

class graph{
    int nVertices;
    map<char,vector<char>> mp;

public:

graph(int nV)
{
   nVertices=nV;


}
int addVertices(char V)
{

    mp.insert(make_pair(V,vector<char>()));
}
int addEdge(char v,char w)
{

    mp[v].push_back(w);
   mp[w].push_back(v);
}
int print()
{

    map<char,vector<char>>::iterator it;

    for(it=mp.begin();it!=mp.end();it++)
        {

            vector<char>::iterator itr;
            for(itr=it->second.begin();itr!=it->second.end();itr++)
                cout<<it->first<<"->"<<*itr<<endl;
            }

}
void BFS(char start)
{

    map<char,bool>v;
 map<char,vector<char>>::iterator it;

    for(it=mp.begin();it!=mp.end();it++)


    {
        v[it->first]=false;
    }

    v[start]=true;
    queue<int>q;
    q.push(start);

    while(!q.empty())
    {
        char qElement=q.front();
        q.pop();
        cout<<qElement;
        vector<char>gr=mp[qElement];
        for(int i=0;i<gr.size();i++)
        {
            char item=gr[i];

            if(v[item]==false)
                {
                    v[item]=true;
                    q.push(item);

                }
        }
    }
}

void dfs(char start)
{
    map<char,bool>v;
    map<char,vector<char>>::iterator it;

    for(it=mp.begin();it!=mp.end();it++)


    {
        v[it->first]=false;
    }
dfsUtil(start,v);

}
char dfsUtil(char start,map<char,bool>v)
{
    v[start]=true;
    cout<<start;
      vector<char>gr=mp[start];
      for(int i=0;i<gr.size();i++)
      {
          if(v[gr[i]]==false)
          {
              dfsUtil(gr[i],v);
          }
      }
}

};


int main()
{
    graph g(6);
    char vertices[6]= {'A', 'B', 'C', 'D', 'E', 'F' } ;
    for(int i=0;i<6;i++)
{
    g.addVertices(vertices[i]);
}

g.addEdge('A', 'B');
g.addEdge('A', 'D');
g.addEdge('A', 'E');
g.addEdge('B', 'C');
g.addEdge('D', 'E');
g.addEdge('E', 'F');
g.addEdge('E', 'C');
g.addEdge('C', 'F');
    g.BFS('B');
}
    
```