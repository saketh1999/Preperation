
Balanced Bracket
................



```
#include <bits/stdc++.h>
using namespace std;

bool balancedBrackets(string str) {
stack<char>s;
unordered_map<char,char>mp{{')','('},{']','['},{'}','{'}};
	string s1="[({";
	string s2="}])";
	
	
	for(int i=0;i<str.length();i++)
	{
		if(s1.find(str[i])!=string::npos)
		{
			s.push(str[i]);
		}
		else if(s2.find(str[i])!=string::npos)
		{
			if(s.size()==0)
			{
				return false;
			}
			
			if(s.top()==mp[str[i]])
		{
			s.pop();
		}
		else
		{
			
			return false;
		}
		
				
		}
		
	}
	return s.size()==0;
}
```
