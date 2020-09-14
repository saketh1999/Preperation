Pseudo code
.............
```
vector<int> NGL(vector<int>v)
{
    stack<int> st;
    vector<int>sol;
    int n=v.size();
    for(int i=0; i< n ;i++)
    {
        if(st.empty)
        v.push_back(-1);
        if(st.size()>0 && v[i]< st.top())
        {
                v.push_back(st.top());
        }
        else if(st.size()>0 && v[i]>= st.top())
        {
            while(st.size()>0 && v[i]>= st.top())
            {
                st.pop();
            }
            if(st.size()==0
            v.push_back();
            else if(v[i]< st.top())
            v.push_back(st.top());

        }
        st.push(v[i]);

    }
    return sol;
}
```