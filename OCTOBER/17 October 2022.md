# 17 October 2022

## Problem Statement
Given an array arr[] of N integers and replace every element with the least greater element on its right side in the array. If there are no greater elements on the right side, replace it with -1. 

## Example 1:
```
Input:
arr[] = {8, 58, 71, 18, 31, 32, 63, 92, 43, 3, 91, 93, 25, 80, 28}
Output: {18, 63, 80, 25, 32, 43, 80, 93, 80, 25, 93, -1, 28, -1, -1}
Explanation: 
The least next greater element of 8 is 18.
The least next greater element of 58 is 63 and so on.
```

## Example 2:
```
Input:
arr[] = {2, 6, 9, 1, 3, 2}
Output: {3, 9, -1, 2, -1, -1}
Explanation: 
The least next greater element of 2 is 3. 
The least next greater element of 6 is 9.
least next greater element for 9 does not
exist and so on.
```

## Your Task:  
You don't need to read input or print anything. Your task is to complete the function findLeastGreater() which takes an array arr[] of size N and returns a list as an output.

- Expected Time Complexity: O(N* log N)
- Expected Auxiliary Space: O(N)

## Constraints:
```
1 <= N <= 10^5
1 <= A[i] <= 10^5
```

## Solution
```
//{ Driver Code Starts
/* Driver program to test above function */

#include<bits/stdc++.h>
using namespace std;

// } Driver Code Ends
//Back-end complete function Template for C++

class Solution{
    struct Tnode{
        struct Tnode *left,*right;
        int val;
        Tnode(int v)
        {
            left = NULL;
            right = NULL;
            val = v;
        }
    };
    int temp = -1;
    int insert(Tnode *root,int ele)
    {
        if(ele < root->val)
        {
            temp = root->val;
            if(root->left==NULL)
            {
                root->left = new Tnode(ele);
                return temp;
            }
            else
            return insert(root->left,ele);
        }
        else
        {
            if(root->right==NULL)
            {
                root->right = new Tnode(ele);
                return temp;
            }
            else
            return insert(root->right,ele);
        }
        
    }
    public:
    vector<int> findLeastGreater(vector<int>& arr, int n) {
        vector<int> ans(n);
        Tnode *root = new Tnode(arr[n-1]);
        ans[n-1] = -1;
        //int ng=-1;
        for(int i=n-2;i>=0;i--)
        {
            temp = -1;
            ans[i] =insert(root,arr[i]);
        }
        return ans;
    }
};

//{ Driver Code Starts.
int main()
{
	int t;
	cin>>t;
	while(t--)
	{
	    int n;
	    cin >> n;
	    vector<int>arr(n);
	    for(int i = 0 ; i < n; i++){
	        cin >> arr[i];
	    }
	    Solution ob;
	    vector<int> ans = ob.findLeastGreater(arr, n);
	    for(auto it : ans){
	        cout << it << " ";
	    }
	    cout <<endl;
	}
	return 0;
}

// } Driver Code Ends
```
