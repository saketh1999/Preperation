Permutation with Spaces
........................

Aditya verma->recursion->https://www.youtube.com/watch?v=1cspuQ6qHW0&list=PL_z_8CaSLPWeT1ffjiImo0sYTcnLzo-wY&index=14


code 

```
int main()
{
    string ip="abc";
    string op="";
    op+=ip[0];
    ip.erase(ip.begin()+0);
    vector<string> s; //vector to store all the result strings
    solve(ip,op,s);//function to get the permutation with spaces
}
void solve(string ip, string op, vector<string> s)
{
    if(ip.length()==0)
    {
        s.push_back(op);
        return;

    }
    string op1="";/ /string with spaces
    string op2=""; //string without spaces
    op1.push_back(" "); // pushing space into the string
    op1.push_back(ip[0]);
    op2.push_back(ip[0]); //without string
    ip.erase(ip.begin()+0); //removing the first char of the ip string
    solve(ip,op1,s);
    solve(ip,op2,s);
}

```