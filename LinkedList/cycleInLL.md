Check if cycle is present in a Linked list


Driver function:
***
int detectLoop(Node* list) 
{ 
    Node *slow_p = list, *fast_p = list; 
  
    while (slow_p && fast_p && fast_p->next) { 
        slow_p = slow_p->next; 
        fast_p = fast_p->next->next; 
        if (slow_p == fast_p) { 
            return 1; 
        } 
    } 
    return 0; 
} 
//Finding the loop and printing it


LinkedList *findLoop(LinkedList *head) {
LinkedList* fast,*slow;
	slow=head->next;
	fast=head->next->next;
	while(fast!=slow)
	{
		fast=fast->next->next;
		slow=slow->next;
	}
	fast=head;
	while(fast!=slow)
	{
		fast=fast->next;
		slow=slow->next;
	}
	return fast;
}

***