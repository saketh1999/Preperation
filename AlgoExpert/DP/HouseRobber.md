Houser Robber 1 / Maximum subset sum

```
int roberry(vecot<int>houses)
{
    if(houses.size()==0)
    return 0;
    vector<int>profit(houses.size()+1,0) ;
    profit[0]=0;//if he robs 0 houses he will not have any profit;
    profit[1]=houses[1];//this is the first house he robs.

    for(int i=1;i<houses.size();i++)
    {
        profit[i+1]=max(profit[i],profit[i-1]+house[i]);
    }
    return profit[houses.size()];
}
```