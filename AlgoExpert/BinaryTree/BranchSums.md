Find the Sum of All the branches from left to right and store them in an vector array.

```
void branchUtil(vector<int >&sums,int sum ,BST * node)
{
    if(node==NULL)
    return;
    int currSum=sum+node->val;
    if(node->left==NULL && node->right==NULL)
        {
            sums.push_back(currSum);
            return;
        }
    branchUtil(sums,currSum,node->left);
    branchUtil(sums,currSum,node->right);

}
vector<int> BranchSum(BST*root)
{
    vector<int>sums;
    branchUtil(sums,0,root);
    return sums;
}
```