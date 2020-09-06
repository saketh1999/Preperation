Longest subarray sum or Kadanes algo
```
int Kadane(vector<int>v)
{
    int max_sum,curr_sum;
    max_sum=curr_sum=v[0];
    for(int i=1;i< v.size() ; i++)
    {
        curr_sum=max(v[i],curr_sum+v[i]);// max of  v[i] || curr_sum+v[i]
        max_sum=max(max_sum,curr_sum);
    }
    return max_sum;
}
```