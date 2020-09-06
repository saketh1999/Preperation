Given a binary search tree and a target node K. The task is to find the node with minimum absolute difference with given target value K.

https://www.geeksforgeeks.org/find-closest-element-binary-search-tree/

```
void closestUtil(BST*root,int &min_val,int &min_diff,int target)
{
    if(root==NULL)
    return;
    if(root->val==target)
    {
        min_val=target;
        return;
    }
    if(min_diff>abs(target-root->val))
    {
        min_diff=abs(target-root->val);
        min_val=root->val;
    }
    if(target<root->val)
    closesUtil(root->left,min_val,min_diff,target);
    else
       closesUtil(root->right,min_val,min_diff,target);
}

int findClosestValueInBst(BST *tree, int target) {
  // Write your code here.
int min_diff=INT_MAX;
	int min_val=-1;
	closestUtil(tree,min_diff,min_val,target);
  return min_val;
}
```