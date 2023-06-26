# Next-greater-element-solution-using-stack-in-cpp
Problem: https://www.hackerearth.com/problem/algorithm/next-greater-1/


#include <bits/stdc++.h>
using namespace std;

int main () {
    ios_base::sync_with_stdio(0); cin.tie(0);
    int n;
    cin >> n;
    vector<int> v;
    for (int i = 0; i < n; i++){
        int x;
        cin >> x;
        v.push_back(x);
    }
    stack<int> st,st1;
    st.push(*(--v.end()));
    st1.push(-1);
    auto it  = --v.end();
    while(it!=v.begin()){
        --it;
        if(*it<st.top()){
            st1.push(st.top());
            st.push(*it);
        }
        else{
            while(*it>=st.top()){
                st.pop();
                if(st.empty())  break;
            }
            if(st.empty()){
                st1.push(-1);
            }
            else st1.push(st.top());
            st.push(*it);
        }
    }
    while(!st1.empty()){
        cout << st1.top() << " ";
        st1.pop();
    }
    return 0;
}
