# 18 october 2022

## Problem Statement
Give a N * N square matrix A, return all the elements of its anti-diagonals from top to bottom.

Example 1:
```
Input: 
N = 2
A = [[1, 2],
     [3, 4]]
Output:
1 2 3 4
Explanation: 

Hence, elements will be returned in the 
order {1, 2, 3, 4}.
```

Example 2:
```
Input: 
N = 3 
A = [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]]
Output: 
1 2 4 3 5 7 6 8 9
Explanation: 

Hence, elements will be returned in 
the order {1, 2, 4, 3, 5, 7, 6, 8, 9}.
```

## Your Task:
You don't need to read input or print anything. Your task is to complete the function downwardDigonal() which takes an integer N and a 2D matrix A[ ][ ] as input parameters and returns the list of all elements of its anti-diagonals from top to bottom.

- Expected Time Complexity: O(N*N)
- Expected Auxillary Space: O(N*N)

## Constraints:
- 1 ≤ N, M ≤ 103
- 0 ≤ A[i][j] ≤ 106

## SOLUTION
```
//{ Driver Code Starts
#include<bits/stdc++.h>
using namespace std;

// } Driver Code Ends

class Solution{
	public:
	vector<int> downwardDigonal(int n, vector<vector<int>> A)
	{
		int i=0,j=0;
		vector<int>v;
		while(!(j==n-1&&i==n)){
		    int c=j,r=i;
		    while(r<n && c>=0)
		        v.push_back(A[r++][c--]);
		    (j==n-1)?i++:j++;
		}
		return v;
	}
};


//{ Driver Code Starts.



int main()
{

    
    int t;
    cin >> t;
    while(t--) 
    {
        int n;
        cin >> n;

        vector<vector<int>> A(n, vector<int>(n));

        for(int i = 0; i < n; i++)
        	for(int j = 0; j < n; j++)
        		cin >> A[i][j];

        Solution obj;
        vector<int> ans = obj.downwardDigonal(n, A);

        for(auto i:ans)
        	cout << i << " ";

	    cout << "\n";
    }

    return 0;
}

// } Driver Code Ends
  ```
