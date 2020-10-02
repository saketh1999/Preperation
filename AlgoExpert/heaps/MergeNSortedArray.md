Merge N sorted Arrays
......................

```
#include<bits/stdc++.h>
using namespace std;
typedef pair<int,pair<int,int>> p;

vector<int> mergeSortedArrays(vector<vector<int>> arrays) {

 vector<int> res;
priority_queue<p,vector<p>,greater<p>> q;

	for(int i=0;i<arrays.size();i++)
		q.push(make_pair(arrays[i][0],make_pair(i,0)));
		
	while(q.size()>0)
	{
		p curr= q.top();
		q.pop();
		
		int i=curr.second.first;
		int j=curr.second.second;
		
		res.push_back(curr.first);
		
		if(j+1<arrays[i].size())
			q.push(make_pair(arrays[i][j+1],make_pair(i,j+1)));
	}
  return res;
}

```