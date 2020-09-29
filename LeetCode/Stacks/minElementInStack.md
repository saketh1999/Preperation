MIN ELEMENT IN STACK
.....................
https://leetcode.com/problems/min-stack/submissions/

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
getMin() -- Retrieve the minimum element in the stack.
 

Example 1:

Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]

Explanation
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2

Using Extra space

```
class MinStack {
public:
    /** initialize your data structure here. */
    stack<int> st,ss;
    
    MinStack() {
        
    }
    
    
    void push(int x) {
          st.push(x);
        if( ss.size()==0)
        {
          
            ss.push(x);
            
        }
        else
        {
            
            if(x<=ss.top())
            {
                ss.push(x);
            }
        }
    }
    
    void pop() {
        if(st.size()==0)
            return ;
        int y=st.top();
        st.pop();
        if(y==ss.top())
        {
            ss.pop();
        }
    }
    
    int top() {
        return st.top();
    }
    
    int getMin() {
        if(ss.size()==0)
            return 0;
        cout<<ss.top()<<" ";
        return ss.top();
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */

```
passes all cases except one in LEET CODE 18/19

```
class MinStack {
public:
    stack<long long int > s;
    long long int minV;
    /** initialize your data structure here. */
    MinStack() {
        
    }
    
    void push(long long int x) {
        if(s.size()==0)
        {minV=x;
         s.push(x);
        }
        if(x>=minV)
            s.push(x);
        else
        {
            s.push((2*x)-minV);
            minV=x;
        }
    }
    
    void pop() {
        if(s.size()==0)
            return;
        
            long long int t=s.top();
        
            s.pop();
            if(t<minV)
            {
                minV=(2*minV)-t;
            }
        
        
    }
    
    int top() {
        if(s.size()>0)
        {
            if(s.top()<minV)
                return minV;
            else
                
            return s.top();
            
        }
            
        else
            return 0;
    }
    
    int getMin() {
        if(s.size()==0)
            return -1;
        return minV;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */

```
Code without Extra Space

```
class MinStack {
public:
    stack<long long> st;
    long long min;
    /** initialize your data structure here. */
    MinStack() {
        
    }
    
    void push(int x) {
        if(st.empty())
        {st.push(0);
        min=x;}
        else
        {
            long long compare=x-min;
            if(compare<0)
                min=x;
            st.push(compare);
        }
    }
    
    void pop() {
     long long t=st.top();
        if(t<0)
            min=min-t;
        st.pop();
    }
    
    int top() {
        long long t=st.top();
        if(t<0)
            return min;
        else
            return min+t;
    }
    
    int getMin() {
        return min;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```
