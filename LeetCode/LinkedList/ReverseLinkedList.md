Reverse Linked List
....................


https://leetcode.com/problems/reorder-list/

3 steps solution
................
->find Mid
->reverse the second half of the Linked List
->Merge the two list


```
class Solution {
public:
    ListNode* middleNode (ListNode* node)
    {
        ListNode *slow,*fast;
        slow=fast=node;
        while(fast->next!=NULL && fast->next->next!=NULL)
        {
            slow=slow->next;
            fast=fast->next->next;
        }
        return slow;
        
    }
    
    ListNode* reverseList(ListNode* node)
    {
        ListNode *cur,*prev;
        cur=node;
        prev = NULL;
        while(cur!=NULL)
        {
            ListNode *temp = cur->next;
            cur->next = prev;
            prev = cur;
            cur = temp;
        }
        return prev;
    }
    void reorderList(ListNode* head) {
        if(head==NULL || head->next==NULL || head->next->next==NULL)
            return ;
        ListNode *mid=middleNode(head);
        
        ListNode *nextMid=mid->next;
        
        //Important 
        mid->next=NULL;
        
       ListNode *revdList=reverseList(nextMid);
        
        //Merging

        while(head!=NULL && revdList!=NULL)
        {
            ListNode* temp=head->next;
            head->next=revdList;
            revdList=revdList->next;
            head->next->next=temp;
            head=temp;
        }
    }
};
```