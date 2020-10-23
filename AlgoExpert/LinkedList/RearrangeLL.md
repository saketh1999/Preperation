Rearrange Linked List
.......................

=>Partitioning a linked list around a given value and keeping the original order
...................................................................................

https://www.geeksforgeeks.org/partitioning-a-linked-list-around-a-given-value-and-keeping-the-original-order/


```

using namespace std;

class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value) {
    this->value = value;
    next = NULL;
  }
};

LinkedList *rearrangeLinkedList(LinkedList *head, int k) {
	
 LinkedList* head1,*head2,*head3,*tail1,*tail2,*tail3;
	head1=head2=head3=tail1=tail2=tail3=NULL;
	
	LinkedList* temp=head;
	
	while(temp!=NULL)
	{
		 if(temp->value<k)
		{
			if(head1==NULL)
			{
				head1=tail1=temp;
			}
			else
			{
				tail1->next=temp;
				tail1=temp;
			}
		}
		
		else if(temp->value==k)
		{
			if(head2==NULL)
			{
				head2=tail2=temp;
			}
			else
			{
				tail2->next=temp;
				tail2=temp;
			}
			
		}
	
		else if(temp->value>k)
		{
			if(head3==NULL)
			{
				head3=tail3=temp;
			}
			else
			{
				tail3->next=temp;
				tail3=temp;
			}
		}
		
		temp=temp->next;
	}
	
	if(tail3!=NULL)
		tail3->next=NULL;
	
	if(head1==NULL)
	{
		if(head2==NULL)
			return head3;
		tail2->next=head3;
		return head2;
	}
	if(head2==NULL)
	{
		tail1->next=head3;
		return head1;
	}
	
	tail1->next=head2;
	tail2->next=head3;

	return head1;
	

}


```
