KMP algorithm is used for solving pattern problem.
```
void lps(string s,vector<int>lp)
{
    int len=0;
    int i=0;
    while(len<s.length())
    {
        if(s[i]==s[len])
        {
            len++;
            lp[i]=len;
            i++;
        }
        else
        {
            if(len!=0)
            {
                len=lp[len-1];
            }
            else
            {

                lp[i]=0
                i++;
            }
        }
    }
}
```