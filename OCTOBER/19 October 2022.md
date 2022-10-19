# 19 October 2022

## Problem Statement
A Hamiltonian path, is a path in an undirected graph that visits each vertex exactly once. Given an undirected graph, the task is to check if a Hamiltonian path is present in it or not.

## Example 1:

```
Input:
N = 4, M = 4
Edges[][]= { {1,2}, {2,3}, {3,4}, {2,4} }
Output:
1 
Explanation: 
There is a hamiltonian path: 
1 -> 2 -> 3 -> 4 
```

## Example 2:

```
Input:
N = 4, M = 3 
Edges[][] = { {1,2}, {2,3}, {2,4} } 
Output: 
0 
Explanation: 
It can be proved that there is no 
hamiltonian path in the given graph
```

## Your task:
You don't need to read input or print anything. Your task is to complete the function check() which takes the N (the number of vertices), M (Number of edges) and the list of Edges[][] (where Edges[i] denotes the undirected Edge between vertices Edge[i][0] and Edges[i][1] ) as input parameter and returns true (boolean value) if the graph contains Hamiltonian path,otherwise returns false. 


- Expected Time Complexity: O(N!).
- Expected Auxiliary Space: O(N+M).


## Constraints:
- 1 ≤ N ≤ 10
- 1 ≤ M ≤ 15
- Size of Edges[i] is 2
- 1 ≤ Edges[i][0],Edges[i][1] ≤ N


## Solution
```
//{ Driver Code Starts
#include<bits/stdc++.h>
using namespace std;

// } Driver Code Ends
class Solution
{
    private:
    bool dfs(int parent,vector<bool> &vis,unordered_map<int,vector<int>> &mp,int cnt){
        
        if(cnt == mp.size()){
            return true;
        }
        
        vis[parent] = true;
        
        for(auto &it : mp[parent]){
            if(vis[it] == false){
                if(dfs(it,vis,mp,cnt+1))
                    return true;
            }
        }
        vis[parent] = false;
        
        return false;
    }
    public:
    bool check(int N,int M,vector<vector<int>> Edges)
    {
        unordered_map<int,vector<int>> mp;
        
        for(int i=0;i<Edges.size();i++){
            int u = Edges[i][0];
            int v = Edges[i][1];
            
            mp[u].push_back(v);
            mp[v].push_back(u);
        }
        
        vector<bool> vis(mp.size(),false);
        
        for(int i=0;i<mp.size();i++){
            int cnt = 1;
            if(dfs(i+1,vis,mp,cnt))
                return true;
        }
        return false;
    }
};
 

//{ Driver Code Starts.
int main()
{
	int t;
	cin>>t;
	while(t--){
    	int N,M,X,Y;
    	cin>>N>>M;
    	vector<vector<int>> Edges;
    	for(int i=0;i<M;i++)
    	{
    		cin>>X>>Y;
    		Edges.push_back({X,Y});
    	}
    	Solution obj;
    	if(obj.check(N,M,Edges)){
    		cout<<"1"<<endl;
    	}
    	else
    	cout<<"0"<<endl;
	}
}
// } Driver Code Ends
```
