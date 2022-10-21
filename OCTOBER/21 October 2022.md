# 21 October 2022
## Problem Statement
Given a matrix as 2D array. Find the reverse spiral traversal of the matrix. 

## Example 1:
```
Input: R = 3, C = 3
  a = {{9, 8, 7},
       {6, 5, 4},
       {3, 2, 1}}
Output: 5 6 3 2 1 4 7 8 9
Explanation: Spiral form of the matrix
in reverse order starts from the centre 
and goes outward.
```
![image](https://user-images.githubusercontent.com/76194423/197138279-d388512b-a9e8-457e-96f8-b0007c20689e.png)

## Example 2:
```
Input: R = 4, C = 4 
  a = {{1, 2, 3, 4},
       {5, 6, 7, 8},
       {9, 10, 11, 12}, 
       {13, 14, 15, 16}}
Output: 10 11 7 6 5 9 13 14 15 16 12 8 4 3 2 1
Explanation:
```
![image](https://user-images.githubusercontent.com/76194423/197138327-60702df1-101d-486c-9f4e-a6da54916001.png)

## Your Task:  
You dont need to read input or print anything. Complete the function reverseSpiral() which takes R, C and a as input parameters and returns the matrix in reverse spiral form.

Expected Time Complexity: O(R*C)
Expected Auxiliary Space: O(R*C)

## Constraints:
- 1 <= R,C <=100
- 1 <= a[R][C] <=100

## Solution
```
//{ Driver Code Starts
//Initial Template for Java
import java.io.*;
import java.util.*;

class GFG{
    public static void main(String args[])throws IOException
    {
        BufferedReader read = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());
        while(t-- > 0)
        {
            String[] input = new String[2]; 
            input = read.readLine().split(" "); 
            int R = Integer.parseInt(input[0]); 
            int C = Integer.parseInt(input[1]); 
            String s1[] = read.readLine().trim().split("\\s+");
            int a[][] = new int[R][C];
            for(int i = 0;i < R*C;i++)
                a[i/C][i%C] = Integer.parseInt(s1[i]);
            Solution ob = new Solution();
            int[] ans = ob.reverseSpiral(R,C,a);
            for(int i = 0; i < ans.length; i++)
            {
                System.out.print(ans[i] + " ");
            }
            System.out.println();
        }
    }
}
// } Driver Code Ends



class Solution

{

 static boolean visited[][];

    public int[] reverseSpiral(int R, int C, int[][] a)

    {

        // code here

    boolean visited[][]=new boolean[R][C];

     ArrayList<Integer> al=new ArrayList<>();

     int count=0;

     int i=0,j=0;

     while(count<R*C) {

     //goright

     while(j<C && visited[i][j]==false) {

     visited[i][j]=true;

     al.add(a[i][j]);

     count++;

     j++;

     }

     

     //godown

     i++;

     j--;

     while(i<R && visited[i][j]==false) {

     visited[i][j]=true;

     al.add(a[i][j]);

     i++;

     count++;

     }

     i--;

     j--;

     //goleft

     while(j>-1 && visited[i][j]==false) {

     visited[i][j]=true;

     al.add(a[i][j]);

     j--;

     count++;

     }

     i--;

     j++;

     //gotop

     while(i>-1 && visited[i][j]==false) {

     visited[i][j]=true;

     al.add(a[i][j]);

     i--;

     count++;

     }

     i++;

     j++;

     

     

 

     }

     Collections.reverse(al);

     int []ans=new int [count];

        for(int k=0;k<count;k++)

         ans[k]=al.get(k);

        return ans;

 

    }

}
```
