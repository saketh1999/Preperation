Given an absolute path for a file (Unix-style), simplify it. Or in other words, convert it to the canonical path.

In a UNIX-style file system, a period . refers to the current directory. Furthermore, a double period .. moves the directory up a level.

Note that the returned canonical path must always begin with a slash /, and there must be only a single slash / between two directory names. The last directory name (if it exists) must not end with a trailing /. Also, the canonical path must be the shortest string representing the absolute path.

 

Example 1:

Input: "/home/"
Output: "/home"
Explanation: Note that there is no trailing slash after the last directory name.
Example 2:

Input: "/../"
Output: "/"
Explanation: Going one level up from the root directory is a no-op, as the root level is the highest level you can go.
Example 3:

Input: "/home//foo/"
Output: "/home/foo"
Explanation: In the canonical path, multiple consecutive slashes are replaced by a single one.
Example 4:

Input: "/a/./b/../../c/"
Output: "/c"
Example 5:

Input: "/a/../../b/../c//.//"
Output: "/c"
Example 6:

Input: "/a//b////c/d//././/.."
Output: "/a/b/c" 

https://leetcode.com/problems/simplify-path/

```
#include <bits/stdc++.h>
using namespace std;
bool isImportantToken(string token)
{
	return token.length() && token!=".";
}

string shortenPath(string path) {
bool startsWithSlash= path[0]=='/';

	istringstream iss(path);
	string token;
	
	vector<string > tokens;
	vector<string> filteredTokens;
	
	while(getline(iss,token,'/'))
	{
		tokens.push_back(token);
		
	}
	
	copy_if(tokens.begin(),tokens.end(),back_inserter(filteredTokens),isImportantToken);
	vector<string>stack;
	if(startsWithSlash)
	{
		stack.push_back("");
		
	}
	for(string token: filteredTokens)
	{
		if(token=="..")
		{
			if(stack.size()==0 || stack[stack.size()-1]=="..")
			{
				stack.push_back(token);
			}
			else if(stack[stack.size()-1]!="")
			{
				stack.pop_back();
			}
		}
			else
			{
				stack.push_back(token);
			}
		
	}
	if(stack.size()==1 && stack[0]=="")
		return "/";
  ostringstream oss;
	for(auto i=0;i<stack.size();i++)
	{
		if(i!=0)
		{
			oss<<"/";
		}
		oss<<stack[i];
	}
	return oss.str();
}

```