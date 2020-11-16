Permutation with Cases
..........................

Aditya Verma->Recursion->https://www.youtube.com/watch?v=J2Er5XceU_I&list=PL_z_8CaSLPWeT1ffjiImo0sYTcnLzo-wY&index=15


```
int main()
{
    string ip="ab";
    string op="";
    vector<string>s;
    solve(ip,op,s);
}
void solve(string ip,string op,vector<sting>s)
{
    if(ip.length()==0)
    {
        s.push_back(op);
        return;
    }
    string op1="";
    string op2="";

    op1.push_back(ip[0]);
    op2.push_back(toupper(ip[0]));
    ip.erase(ip.begin()+0);
    solve(ip,op1);
    solve(ip,op2);
}

```