Reverse a given Linked List
...........................

```
using namespace std;

class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value) {
    this->value = value;
    this->next = NULL;
  }
};

LinkedList *reverseLinkedList(LinkedList *head) {
  LinkedList *curr,*future=NULL,*prev=NULL;
	if(head==NULL)
		return NULL;
	else
	{
		curr=head;
		while(curr!=NULL)
		{
			future=curr->next;
			curr->next=prev;
			
			prev=curr;
			curr=future;
			
		}
		head=prev;
	}
  return head;
}

```