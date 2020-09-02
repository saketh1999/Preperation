KMP algorithm is used for solving pattern problem.
```
void lps(string s,vector<int>lp) //function used to drive get the longest proper prefix
{
    int len=0;
    int i=0;
    lp[0]=0;//very important ,initial the starting of lps to 0.
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
void KMP(string M,string P)
{
    int m=M.length();
    int n=P.length();
    
    vector<int>lp;

    lps(P,lp);
    int i=0,j=0;
    while(i<m)
    {
        if(M[i]==P[j])
        {
            i++,j++;
        }
        if(j==n)
        {
            cout<<"pattern found at position"<<i-j;
            j=lp[j-1];
        }
        else if(i<m && M[i]!=P[j])
        {
            if(j!=)
            {
                j=lp[j-1];
            }
            else
            {
                i++;
            }
        }
    }
}
```