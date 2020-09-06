RodCutting problem 

Given a rod of length n inches and an array of prices that contains prices of all pieces of size smaller than n. Determine the maximum value obtainable by cutting up the rod and selling the pieces.



DP solutions 
...............
Recursion + DP

void rodCut(vector<int >prices,int l,vector<int>dp)
{
    if(l<0)
    return;
    if(dp[l]!=-1)
    return dp[l];
    int max_ele=INT_MIN;
    for(int i=0;i< l ; i++ )
    {

        max_ele=max(max_ele,p[i]+rodCut(prices,l-i-1,dp))
    } 
    dp[l]=max_ele;
    return max_ele;
}


Iterative sol
..............
void rodcutting(int l,vector<int>prices)
{
    vector<int>dp(l+1);

    dp[0]=0;
    for(int i=1;i<=l;i++)
    {
        dp[i]=MIN_INT;
        for(j=0;j<=i;j++)
        {
            dp[i]=max(dp[i],prices[i]+dp[i-j-1]);

        }
    }
    return dp[l];
}

