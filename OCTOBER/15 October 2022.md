# 15 October 2022
## Shortest Distance in a Binary Maze

## PROBLEM STATEMENT

Given a n * m matrix grid where each element can either be 0 or 1. You need to find the shortest distance between a given source cell to a destination cell. The path can only be created out of a cell if its value is 1. 

If the path is not possible between source cell and destination cell, then return -1.

Note : You can move into an adjacent cell if that adjacent cell is filled with element 1. Two cells are adjacent if they share a side. In other words, you can move in one of the four directions, Up, Down, Left and Right.


Example 1:
```
Input:
grid[][] = {{1, 1, 1, 1},
            {1, 1, 0, 1},
            {1, 1, 1, 1},
            {1, 1, 0, 0},
            {1, 0, 0, 1}}
source = {0, 1}
destination = {2, 2}
Output:
3
Explanation:
1 1 1 1
1 1 0 1
1 1 1 1
1 1 0 0
1 0 0 1
The highlighted part in the matrix denotes the 
shortest path from source to destination cell.
```
Example 2:
```
Input:
grid[][] = {{1, 1, 1, 1, 1},
            {1, 1, 1, 1, 1},
            {1, 1, 1, 1, 0},
            {1, 0, 1, 0, 1}}
source = {0, 0}
destination = {3, 4}
Output:
-1
Explanation:
The path is not possible between source and 
destination, hence return -1.
```

## Your Task:

You don't need to read or print anything. Your task is to complete the function shortestPath() which takes the a 2D integer array grid, source cell and destination cell as an input parameters and returns the shortest distance between source and destination cell.

- Expected Time Complexity: O(n * m)
- Expected Space Complexity: O(n * m)

### Constraints:

- 1 ≤ n, m ≤ 500
- grid[i][j] == 0 or grid[i][j] == 1
- The source and destination cells are always inside the given matrix.
- The source and destination cells always contain 1.


## SOLUTION IN CPP
```
//{ Driver Code Starts
// Initial Template for C++

#include <bits/stdc++.h>
using namespace std;


// } Driver Code Ends
// User function Template for C++

class Solution {
  public:
    int shortestPath(vector<vector<int>> &grid, pair<int, int> source,
                     pair<int, int> destination) {
        // code here 
        queue<pair<int,int>> q ;
        
        q.push({source.first,source.second}) ;
        
        int dis = 0;
        
        vector<vector<int>> vis(grid.size(), vector<int> (grid[0].size(),0)) ;
        
        vis[source.first][source.second] = 1 ;
        while(!q.empty())
        {
            int sz = q.size() ;
            
            for(int i = 0; i< sz ; i++)
            {
            int x = q.front().first ;
            int y = q.front().second ;
            
            q.pop() ;
            
            if( x == destination.first && y == destination.second ) 
            return dis ;
            
            if( x-1 >= 0 && grid[x-1][y] == 1 && vis[x-1][y] == 0)
            {
                q.push({x-1,y}) ;
                vis[x-1][y] = 1 ;
            }
            if( x+1 < grid.size() && grid[x+1][y] == 1 && vis[x+1][y] == 0) 
            {
                q.push({x+1,y}) ;
                vis[x+1][y] = 1 ;
            }
            if( y-1 >= 0 && grid[x][y-1] == 1  && vis[x][y-1] == 0)
            {
                q.push({x,y-1}) ;
                vis[x][y-1] = 1 ;
            }
            if( y+1 < grid[0].size() && grid[x][y+1] == 1 && vis[x][y+1] == 0 )
            {
                q.push({x,y+1});
                vis[x][y+1] = 1 ;
            }
            
            
            }
            dis++;
        }
        return -1 ;
    }
};


//{ Driver Code Starts.
int main() {

    int t;
    cin >> t;
    while (t--) {
        int n, m;
        cin >> n >> m;
        vector<vector<int>> grid(n, vector<int>(m));

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                cin >> grid[i][j];
            }
        }

        pair<int, int> source, destination;
        cin >> source.first >> source.second;
        cin >> destination.first >> destination.second;
        Solution obj;
        cout << obj.shortestPath(grid, source, destination) << endl;
    }
}

// } Driver Code Ends
```
