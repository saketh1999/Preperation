Continuous Median
..................


https://www.algoexpert.io/questions/Continuous%20Median

https://www.geeksforgeeks.org/median-of-stream-of-running-integers-using-stl/

```

#include<bits/stdc++.h> 
using namespace std;

// Do not edit the class below except for
// the insert method. Feel free to add new
// properties and methods to the class.
class ContinuousMedianHandler {
public:
	int f=0;
	priority_queue<double> q1;
	priority_queue<double,vector<double>,greater<double>> q2;

  double median=0;

  void insert(int number) {

		if(f==0)
		
		{
			q1.push(number);
			median =number;
			f=1;
			return;
		}
		
		else
		{
			if(q1.size()>q2.size())
			{
				if(number<median)
				{
					q2.push(q1.top());
					q1.pop();
					q1.push(number);
				}
				else
				{
						q2.push(number);
				}
				
			
				median=(q1.top()+q2.top())/2.0;
			}

			else if(q1.size()==q2.size())
			{
				
				if(number<median)
				{
					q1.push(number);
					median=(double)q1.top();
				}
				else
				{
					q2.push(number);
				median=(double)q2.top();
				}
					
			}
		
			 else
        { 	
            if (number > median) 
            { 
                q1.push(q2.top()); 
                q2.pop(); 
                q2.push(number); 
            } 
            else
                q1.push(number); 
  
            median = (q1.top() + q2.top())/2.0; 
        } 

		}
		
  }

  double getMedian() { return median; }
};

```