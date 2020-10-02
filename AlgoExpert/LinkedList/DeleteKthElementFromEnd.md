Delete Kth element from the End.
................................


```
#include <vector>
using namespace std;

class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value);
  void addMany(vector<int> values);
  vector<int> getNodesInArray();
};

void removeKthNodeFromEnd(LinkedList *head, int k) {
	if(k==0)
		return;
	
  int size=1;
	LinkedList *temp=head,*curr,*prev;
	
	
	while(temp->next!=NULL)
	{
		size++;
		temp=temp->next;
	}
	
	
	
if(k==size)
{
  head->value=head->next->value;
	head->next =head->next->next;

	return;
	
}		
	

	
	else if(k==1)
	{
		temp=head;
	
		while(size-1)
		{
			prev=temp;
			temp=temp->next;
			size--;
		}
	 prev->next=NULL;
		
		return;
	
	}
	else
	{
	
		size=size-k;
	  temp=head;
	
	while(size)
	{
		prev=temp;
		temp=temp->next;
		size--;
		
	}


	curr=prev->next;
	prev->next=curr->next;
		return;
	
	}
	
	
}

```
